---
layout: default
title: Policy Training
---

<a href="../" class="back-link">← Back to Home</a>

<div class="project-header">
  <h1>Policy Training</h1>
  <p class="lead">Single-arm cloth folding with ACT (Action Chunking with Transformers) on the SO-101 platform. Imitation learning from teleoperated demonstrations — 267 demos, 15+ model variants, and a best deployment success rate of 40–60%.</p>
</div>

---

## Setup

| | |
|---|---|
| **Task** | Single-arm cloth folding (left arm, 6 DOF + gripper) |
| **Framework** | LeRobot (HuggingFace) |
| **Architecture** | ACT with ResNet18 vision backbone |
| **Cameras** | 2× Intel RealSense D4xx (480×640 RGB + depth), fixed overhead/angled |
| **Control rate** | 10 Hz (teleop recording and deployment) |
| **GPU** | NVIDIA RTX 5070 Ti (16 GB VRAM), ~5–8.5 hrs per run |

---

## Deployment Videos

<div class="video-grid">
  <div class="media-block">
    <video autoplay muted loop playsinline>
      <source src="../assets/videos/multi-fold.mp4" type="video/mp4">
    </video>
    <div class="media-caption">Multi-fold with cloth resets between folds.</div>
  </div>
  <div class="media-block">
    <video autoplay muted loop playsinline>
      <source src="../assets/videos/single-fold.mp4" type="video/mp4">
    </video>
    <div class="media-caption">Single fold, no disturbance.</div>
  </div>
</div>

<div class="video-grid" style="grid-template-columns:1fr;">
  <div class="media-block">
    <video autoplay muted loop playsinline>
      <source src="../assets/videos/error-fold.mp4" type="video/mp4">
    </video>
    <div class="media-caption">Extended rollout — errors compound over successive folds.</div>
  </div>
</div>

---

## Training Timeline

**v1–v2 (legacy ACT)** — Mean trajectory replay. The robot executed the average of all demonstrations regardless of cloth position. Root cause: insufficient diversity + chunk_size=100.

**v4 — first working policy.** Switching to LeRobot with MEAN_STD normalization and chunk_size=10. This single change turned a non-functional system into one with ~40% success.

**v5 (Diffusion Policy)** — Lowest training loss (0.024) but 300ms inference makes 10 Hz control impossible. Deployed with jittery, discontinuous motion.

**v7–v8 (wrist camera)** — Added a wrist-mounted camera. It occludes when the gripper closes on cloth — exactly when visual information matters most.

**v9 (DAgger on bad policy)** — Corrections collected on v8 were too far from the training distribution. Result: mean trajectory collapse.

**v10 — current best (40–60%).** DAgger on v4 (the good policy). 55 correction demos + 212 originals = 267 total. DAgger only works when the base policy is already reasonable.

**SmolVLA** — 450M param VLA. Training loss reached 0.096 but deployment blocked by language token configuration issues.

**RGBD** — Adding depth channels. Reduced-resolution variant (240×320) currently training.

---

## Key Discoveries

<div class="lesson">
  <p><strong>Normalization is everything.</strong> Without MEAN_STD normalization, raw radian inputs cause action outputs to saturate at joint limits. This was the difference between 0% and 40% success.</p>
</div>

<div class="lesson">
  <p><strong>chunk_size = 10 >> 100.</strong> Predicting 1 second of motion produces smooth, responsive behavior. Predicting 10 seconds over-commits and can't adapt to actual cloth state.</p>
</div>

<div class="lesson">
  <p><strong>Low training loss ≠ good deployment.</strong> Diffusion Policy hit the lowest loss but deployed with discontinuous motion. Stochastic sampling introduces jitter between action chunks.</p>
</div>

<div class="lesson">
  <p><strong>DAgger needs a good base.</strong> Corrections on a broken policy produce out-of-distribution data that makes retraining worse.</p>
</div>

---

## Next Steps

1. **More DAgger on v10** — targeting 40–50 more corrections for a v12 retrain
2. **RGBD integration** — depth should help with cloth height estimation and grasp planning
3. **VLA fine-tuning** — SmolVLA deployment, then larger pretrained models (OpenVLA, pi0)
4. **Data scaling** — literature suggests ACT policies improve significantly at 500+ demos

---

<a href="../" class="back-link">← Back to Home</a>
