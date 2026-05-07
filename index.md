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
    <div class="media-caption">Initial assembly with leader arms for teleoperation.</div>
  </div>
  <div class="media-block">
    <video autoplay muted loop playsinline>
      <source src="assets/videos/multi-fold.mp4" type="video/mp4">
    </video>
    <div class="media-caption">Single arm fold policy in action.</div>
  </div>
</div>

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
</div>

<h2 id="applied-research">Applied Research: Sew Unit</h2>

<p class="bio">Most textile automation targets a single operation on a single fabric type. The Sew Unit is designed to be a general-purpose robotic worker for 3D textile assembly — bimanual manipulation, learned from human demonstrations, deployable where an operator stands today. The platform I built for research is the foundation for a system that learns new sewing operations without reprogramming.</p>

<div class="image-row" style="grid-template-columns: 1fr 2fr;">
  <div class="media-block">
    <img src="assets/images/current-physical-setup.jpeg" alt="Current Sew Unit physical setup — bimanual SO-101 arms in aluminum frame">
    <div class="media-caption">Current physical setup — approx. 24×20×18 in (prototype).</div>
  </div>
  <div class="media-block">
    <img src="assets/images/sew-unit-vision.png" alt="Vision for Sew Unit deployment — human operator to robot operation">
    <div class="media-caption">From human operator to autonomous deployment. <em>AI-generated concept.</em></div>
  </div>
</div>

<div class="image-row">
  <div class="media-block">
    <img src="assets/images/sew-unit-jig.png" alt="Fitting textile panels into jigs — human operator vs robot operation">
    <div class="media-caption">Fitting textile panels into jigs. <em>AI-generated concept.</em></div>
  </div>
  <div class="media-block">
    <img src="assets/images/sew-unit-shoe.png" alt="Shoe upper sewing — human operator vs robot operation">
    <div class="media-caption">Shoe upper sewing. <em>AI-generated concept.</em></div>
  </div>
</div>

<h2 id="why-me">Why Me</h2>

<p class="bio">I'm a fashion designer with direct experience commissioning contract manufacturers and a robotics researcher who builds full stacks from the ground up: mechanical design, fabrication, electronics, and machine learning.</p>

<div class="image-row" style="grid-template-columns: repeat(3, 1fr);">
  <div class="media-block photo">
    <img src="assets/images/tabby-factory.jpeg" alt="Tabby visiting an apparel manufacturing factory in Kenya">
    <div class="media-caption">Visiting an apparel factory in Kenya.</div>
  </div>
  <div class="media-block photo">
    <img src="assets/images/tabby-franka.jpeg" alt="Tabby holding a handheld sewing machine against a Franka robot arm">
    <div class="media-caption">With a Franka arm and a handheld sewing machine.</div>
  </div>
  <div class="media-block photo">
    <img src="assets/images/tabby-grippers.jpeg" alt="Tabby using handheld grippers to manipulate cloth on the sewing machine inside the robot cell">
    <div class="media-caption">Collecting sewing demonstrations with handheld grippers.</div>
  </div>
</div>
