---
layout: default
title: Tabitha Oanda
---

<div class="hero">
  <h1>Tabitha Oanda</h1>
  <p class="subtitle">Robotics Engineer · Fashion Designer · PhD Researcher at Brown University</p>

  <p class="bio">
    I build cloth manipulation systems from the ground up: custom aluminum frames, adapted robot arms, multi-camera perception pipelines, YOLO segmentation, force-sensing grippers, and teleoperation tools for data collection. My current focus is on running state-of-the-art deformable object dynamics methods on real cloth data I collected myself, and exploring whether visual feedback during training can improve dynamics predictions.
  </p>

</div>

<div class="hero-split">
  <div class="media-block">
    <img src="assets/images/sew-unit-hero.jpg" alt="Sew unit — dual SO-101 arms built from scratch at Brown">
  </div>
  <div class="media-block">
    <video autoplay muted loop playsinline>
      <source src="assets/videos/sew-unit-mirror-bimanual.mp4" type="video/mp4">
    </video>
    <div class="media-caption">Real robot executing a planned bimanual cloth manipulation trajectory.</div>
  </div>
</div>

<h2 id="projects">Projects</h2>

<div class="project-grid">
  <a class="project-card" href="projects/sew-unit">
    <h3>The Sew Unit</h3>
    <p>A bimanual cloth manipulation platform built from scratch — custom aluminum frame, SO-101 arms, MoveIt planning, and leader-follower teleoperation. All designed, built, and debugged by hand.</p>
    <span class="card-arrow">View project →</span>
  </a>

  <a class="project-card" href="projects/cloth-dynamics">
    <h3>Learning Cloth Dynamics</h3>
    <p>Ran PhysTwin and PGND on cloth data I collected, built the full perception and data pipeline, then explored whether adding visual supervision to dynamics training improves 3D predictions. Results are promising on individual fabrics; active research.</p>
    <span class="card-arrow">View project →</span>
  </a>

  <a class="project-card" href="projects/grippers">
    <h3>Custom Grippers &amp; Teleop Tools</h3>
    <p>Designed two custom end-effectors: silicone FSR grippers for contact-aware grasping, and a UMI-inspired handheld teleop gripper with ArUco markers and IMU for data collection.</p>
    <span class="card-arrow">View project →</span>
  </a>
</div>
