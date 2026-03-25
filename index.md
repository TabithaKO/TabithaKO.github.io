---
layout: default
title: Tabitha Oanda
---

<div class="hero">
  <h1>Tabitha Oanda</h1>
  <p class="subtitle">Robotics Engineer · Fashion Designer · PhD Researcher at Brown University</p>

  <p class="bio">
    Cloth is deformable, slippery, and hard to track — which means off-the-shelf robot setups don't cut it. I build the full stack: a bimanual hardware platform for manipulation, multi-camera perception using foundation vision models to detect and segment fabric across frames in 3D. I use teleoperation tools that make collecting training data practical. Following data collection, I train cloth dynamics models that can be used for model predictive control (MPC) and reinforcement learning policies for complex tasks.
  </p>

  <p class="bio">My research is on getting robots to handle fabric reliably. That requires building the whole stack:</p>
  <ul class="bio-list">
    <li><strong>Platform:</strong> custom aluminum frame, overhead-mounted bimanual arms, force-sensing silicone grippers</li>
    <li><strong>Perception:</strong> multi-camera RGB-D, object detection and segmentation, 3D point tracking</li>
    <li><strong>Data collection:</strong> leader-follower teleoperation for imitation learning, custom <a href="https://umi-gripper.github.io/">UMI-inspired</a> data collection gripper</li>
    <li><strong>Learning:</strong> cloth dynamics models trained and extended on data from my custom setup</li>
  </ul>

  <p class="bio">A consistent theme in my research is taking methods developed in academic settings and adapting them to work on real cloth manipulation problems — the kind of contact-rich, deformable-object tasks that matter for industrial textile handling.</p>

</div>

<div class="hero-split">
  <div class="media-block">
    <img src="assets/images/sew-unit-hero.jpg" alt="Sew unit, dual SO-101 arms built from scratch at Brown">
  </div>
  <div class="media-block">
    <video autoplay muted loop playsinline>
      <source src="assets/videos/multi-fold.mp4" type="video/mp4">
    </video>
    <div class="media-caption">Real robot executing a planned bimanual cloth manipulation trajectory.</div>
  </div>
</div>

<p class="bio">
  I'm a PhD researcher at Brown University advised by Professor Nora Ayanian. My work is on robotic cloth manipulation: building the hardware, perception, and learning systems needed to handle fabric reliably on real robots.
</p>

<h2 id="training">Policy Training</h2>

<p class="bio">
  In the longer videos, I'm resetting the cloth to different positions between folds to test whether the policy generalizes across initialization states. The shorter ones are single folds with no disturbance after completion. Right now, I'm experimenting with different image encoders (ResNet vs DINOv2) and pretrained action models — OpenVLA, Octo, and pi0. These videos are the baseline: no pretrained action model and simply ResNet18 (trained on ImageNet) for image encoding.
</p>

<div class="video-grid">
  <div class="media-block">
    <video autoplay muted loop playsinline>
      <source src="assets/videos/multi-fold.mp4" type="video/mp4">
    </video>
    <div class="media-caption">Multi-fold sequence with cloth resets between folds.</div>
  </div>
  <div class="media-block">
    <video autoplay muted loop playsinline>
      <source src="assets/videos/single-fold.mp4" type="video/mp4">
    </video>
    <div class="media-caption">Single fold, no disturbance after completion.</div>
  </div>
</div>

<p class="bio">
  There's definitely more room for improvement via data collection, especially in generalizing recovery methods from various failure states and exploiting the best camera positioning and end effectors.
</p>

<p class="bio">
  Happy to answer any other questions.
</p>

<p class="bio">
  Best,<br>
  Tabitha
</p>

<h2 id="projects">Projects</h2>

<div class="project-grid">
  <a class="project-card" href="projects/sew-unit">
    <h3>The Sew Unit</h3>
    <p>A bimanual cloth manipulation platform built from scratch: custom aluminum frame, SO-101 arms, MoveIt planning, and leader-follower teleoperation. All designed, built, and debugged by hand.</p>
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
