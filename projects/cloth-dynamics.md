---
layout: default
title: Learning Cloth Dynamics
---

<a href="../" class="back-link">← Back to Home</a>

<div class="project-header">
  <h1>Learning Cloth Dynamics</h1>
  <p class="lead">Two parallel threads: building a custom cloth manipulation dataset using PhysTwin on the sew unit, and running PGND on their data while experimenting with different training mechanisms, including photometric render loss and live camera conditioning at rollout time.</p>
</div>

---

## Part 1: PhysTwin — Custom Cloth Data

I used PhysTwin to simulate and record cloth manipulation trajectories with the sew unit's bimanual setup. PhysTwin fits a particle-based simulation to real cloth by optimizing physical parameters (stiffness, damping, mass) directly from observed RGB-D sequences, so the simulated cloth behaves like the actual fabric being manipulated. That required building a multi-camera perception pipeline to turn raw RGB-D video into the 3D particle tracks PhysTwin trains on.

### Perception Infrastructure

<ul class="spec-list">
  <li><strong>Cameras:</strong> 4× Intel RealSense (D435i and D405) around the workspace</li>
  <li><strong>Calibration:</strong> ChAruco boards (DICT_4X4_50, 5×4, 40mm squares) — best stereo pair: 0.68 RMS reprojection error</li>
  <li><strong>Hand-eye calibration:</strong> Automated pipeline for camera-to-robot-base transforms</li>
  <li><strong>Gripper tracking:</strong> Started with HSV, replaced with CoTracker 3 for robustness under changing lighting</li>
  <li><strong>Dataset:</strong> 11 annotated manipulation trajectories</li>
</ul>

<div class="media-block">
  <img src="../assets/images/cloth-dynamics-pointcloud-grid.png" alt="Multi-camera point cloud grid showing cloth state across manipulation trajectories">
  <div class="media-caption">Point cloud tracking grid — reconstructed cloth state from calibrated multi-camera setup across multiple trajectories.</div>
</div>

### Simulation Rollouts

This is the training trajectory: the sequence PhysTwin is optimized on. The particle-based simulator is fit to this real cloth episode, learning stiffness and damping parameters that reproduce the observed deformation.

<div class="media-block">
  <video autoplay muted loop playsinline>
    <source src="../assets/videos/cloth-dynamics-inference.mp4" type="video/mp4">
  </video>
  <div class="media-caption">Training trajectory — particle-based cloth simulation rolling out on the real episode PhysTwin was fit to.</div>
</div>

After fitting, the simulation is validated against held-out camera views. Each wide video below shows three panels side by side: real RGB, reconstructed point cloud, and PhysTwin prediction.

<div class="media-block">
  <video autoplay muted loop playsinline>
    <source src="../assets/videos/cloth-dynamics-triptych-cam0.mp4" type="video/mp4">
  </video>
  <div class="media-caption">Camera 0 — real RGB | point cloud reconstruction | PhysTwin prediction.</div>
</div>

<div class="media-block">
  <video autoplay muted loop playsinline>
    <source src="../assets/videos/cloth-dynamics-triptych-cam1.mp4" type="video/mp4">
  </video>
  <div class="media-caption">Camera 1 — same validation sequence from the second viewpoint.</div>
</div>

Once the physical parameters are learned from a single training trajectory, the simulator generalises to novel actions. These bimanual manipulation sequences were not seen during training but can be simulated with the fitted cloth parameters.

<div class="media-block">
  <video autoplay muted loop playsinline>
    <source src="../assets/videos/sew-unit-dual-pull-apart.mp4" type="video/mp4">
  </video>
  <div class="media-caption">Novel action: bimanual pull-apart — stretching cloth from both ends with PhysTwin learned parameters.</div>
</div>

<div class="media-block">
  <video autoplay muted loop playsinline>
    <source src="../assets/videos/cloth-dynamics-fold-l-over-r-v2.mp4" type="video/mp4">
  </video>
  <div class="media-caption">Novel action: fold left over right — draping one side of the cloth across the other.</div>
</div>

<div class="media-block">
  <video autoplay muted loop playsinline>
    <source src="../assets/videos/sew-unit-dual-push-together.mp4" type="video/mp4">
  </video>
  <div class="media-caption">Novel action: bimanual push-together — both arms pushing cloth toward the center.</div>
</div>

---

## Part 2: PGND — Training Mechanism Experiments

I took Particle-Grid Neural Dynamics (PGND), a state-of-the-art method for learning deformable object models from RGB-D video, and ran it on their dataset while experimenting with different training mechanisms. Three variants, each adding a different supervisory signal on top of the baseline.

### The Three Models

**Baseline (100k)** trains on particle position and velocity loss (`loss_x`, MSE per step) alone, with no camera input or visual signal. Predicts cloth dynamics purely from geometric state.

**Phase 2 (40k)** adds a differentiable render loss during training: `λ_render = 0.1` (DINOv2 feature distance) + `λ_ssim = 0.2` (SSIM), applied every step against ground truth camera frames. A frozen diff-gaussian-rasterizer projects the predicted particle state into camera space and compares it against real RGB, giving the model an extra signal that penalises predictions which are geometrically plausible but visually wrong.

**Visual PGND (70k)** takes the render loss further with mesh-constrained Gaussian Splatting: each Gaussian is bound to a face of the particle mesh and deforms with it directly, rather than using the LBS approximation in Phase 2. This removes an approximation error in the rendering that limits how sharp the render loss gradient can be, and additionally conditions the dynamics model on camera observations at each rollout step via a frozen DINOv2 backbone, so the model can see when its predictions have drifted from reality and self-correct.

All three share the same particle-grid simulator core and are evaluated on held-out episodes, rolling out 30 steps autoregressively from ground truth initial conditions.

### Model Comparison — Episode 0201

The same cloth manipulation rollout predicted by each model. Watch how prediction quality changes as each additional supervisory signal is added.

<div class="media-block">
  <video autoplay muted loop playsinline>
    <source src="../assets/videos/pgnd-ep0201-baseline.mp4" type="video/mp4">
  </video>
  <div class="media-caption model-label baseline">Baseline (100k) — geometry only, no visual signal</div>
</div>

<div class="media-block">
  <video autoplay muted loop playsinline>
    <source src="../assets/videos/pgnd-ep0201-phase2.mp4" type="video/mp4">
  </video>
  <div class="media-caption model-label phase2">Phase 2 (40k) — + DINOv2 render loss + SSIM during training</div>
</div>

<div class="media-block">
  <video autoplay muted loop playsinline>
    <source src="../assets/videos/pgnd-ep0201-visual.mp4" type="video/mp4">
  </video>
  <div class="media-caption model-label visual">Visual PGND (70k) — + mesh-constrained GS + camera conditioning at rollout</div>
</div>

<div class="media-block">
  <video autoplay muted loop playsinline>
    <source src="../assets/videos/pgnd-comparison-all.mp4" type="video/mp4">
  </video>
  <div class="media-caption">All episodes — baseline vs. visual PGND across the full held-out eval set.</div>
</div>

### Evaluation Metrics

<div class="media-block light-bg">
  <img src="../assets/images/cloth-dynamics-aggregate-metrics.png" alt="Aggregate evaluation metrics — MDE, Chamfer, and EMD over rollout steps">
  <div class="media-caption">Prediction error over 30 rollout steps across all three models. Lower is better; all metrics grow with rollout horizon as compounding errors accumulate.</div>
</div>

Three distance metrics, each measuring a different aspect of prediction quality:

- **MDE (Mean Displacement Error)** — average Euclidean distance between each predicted particle and its ground truth counterpart, averaged over all particles at each rollout step. Sensitive to per-particle drift.
- **Chamfer Distance** — bidirectional nearest-neighbour distance: for each predicted particle find the closest GT particle and vice versa, then sum both directions. Penalises large-scale shape mismatch without requiring correspondence.
- **EMD (Earth Mover's Distance)** — minimum total work to transport the predicted point cloud to match the GT distribution. More sensitive than Chamfer to spread-out errors and global cloth deformation failure modes.

Training also tracks `loss_x` (the MSE position loss, primary signal for all models) and `loss_render` (DINOv2 + SSIM render error, Phase 2 and Visual only).

---

## What I Learned

<div class="lesson">
  <p><strong>The perception pipeline is where the real work is.</strong> Getting CoTracker running reliably on my specific cameras, lighting, and occlusion patterns required more iteration than training the dynamics model. Data quality limits everything downstream.</p>
</div>

<div class="lesson">
  <p><strong>Visual conditioning helps but training is fragile.</strong> DINOv2 features add useful information, but the training dynamics are sensitive; the render loss curriculum schedule matters a lot. Phase 2 is the most stable improvement; Visual PGND at 70k is still training.</p>
</div>

<div class="lesson">
  <p><strong>Evaluation set size matters.</strong> A 5-episode eval showed a 20% improvement. A 40-episode eval showed ~1%. Small eval sets are misleading; the 40-episode numbers are the ones I use.</p>
</div>

---

<a href="../" class="back-link">← Back to Home</a>
