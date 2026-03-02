---
layout: default
title: The Sew Unit
---

<a href="../" class="back-link">← Back to Home</a>

<div class="project-header">
  <h1>The Sew Unit</h1>
  <p class="lead">A bimanual cloth manipulation platform I designed and built from scratch in grad school. Custom aluminum extrusion frame, two inverted SO-101 arms, ROS2/MoveIt motion planning, and a leader-follower teleoperation system for data collection.</p>
</div>

<div class="image-row">
  <div class="media-block light-bg">
    <img src="../assets/images/sew-unit-arms-front.png" alt="Sew unit arms close-up front view">
  </div>
  <div class="media-block light-bg">
    <img src="../assets/images/sew-unit-arms-wide.png" alt="Sew unit wider angle showing both arms and frame">
  </div>
</div>

---

## Hardware

<ul class="spec-list">
  <li><strong>Arms:</strong> Two <a href="https://huggingface.co/docs/lerobot/en/so101">SO-101 arms</a> from the HuggingFace LeRobot platform — open-source research arms I adapted for inverted mounting. I didn't design the robots; the work was in the URDF modifications for flipped gravity compensation, joint limit tuning, and merging two independent controllers onto a single unified serial bus.</li>
  <li><strong>Workspace:</strong> Ender 3 printer bed, flat, rigid, and replaceable</li>
  <li><strong>Servos:</strong> STS/SCS series servo motors, 12 total (6 per arm)</li>
  <li><strong>Controllers:</strong> Unified serial controller managing both arms over a single bus, built after two independent controllers kept causing port conflicts</li>
</ul>

<div class="image-row">
  <div class="media-block">
    <video autoplay muted loop playsinline>
      <source src="../assets/videos/sew-unit-frame-spin.mp4" type="video/mp4">
    </video>
    <div class="media-caption">Custom aluminum extrusion frame — CAD model.</div>
  </div>
  <div class="media-block">
    <video autoplay muted loop playsinline>
      <source src="../assets/videos/sew-unit-cad-spin.mp4" type="video/mp4">
    </video>
    <div class="media-caption">Full sew unit with both arms — CAD model spin.</div>
  </div>
</div>

---

## Motion Planning & Digital Twin

ROS2 and MoveIt with custom URDF configurations. The inverted mounting orientation required reworking joint limits and gravity compensation; small sign errors in the URDF produce impossible trajectories. The same trajectory recorded via teleoperation can be played back on the real robot and verified against its digital twin.

<div class="video-grid">
  <div class="media-block">
    <video autoplay muted loop playsinline>
      <source src="../assets/videos/sew-unit-mirror-bimanual.mp4" type="video/mp4">
    </video>
    <div class="media-caption">Real robot executing a recorded bimanual trajectory.</div>
  </div>
  <div class="media-block">
    <video autoplay muted loop playsinline>
      <source src="../assets/videos/sew-unit-digital-twin.mp4" type="video/mp4">
    </video>
    <div class="media-caption">Digital twin — the same trajectory in simulation.</div>
  </div>
</div>

---

## Teleoperation & Data Collection

The primary data collection method is leader-follower teleoperation. The leader arms share the same morphology as the follower arms, so joint angles map directly with no IK guessing. What you do with the leader is exactly what the follower does.

<div class="media-block">
  <video autoplay muted loop playsinline>
    <source src="../assets/videos/sew-unit-teleop-leader.mp4" type="video/mp4">
  </video>
  <div class="media-caption">Leader arm teleoperation — operator moves the leader, follower mirrors exactly.</div>
</div>

<div class="image-row">
  <div class="media-block photo">
    <img src="../assets/images/sew-unit-red-pinch.jpg" alt="Both follower arms pinching red cloth with silicone gripper tips">
    <div class="media-caption">Both arms pinching red cloth — silicone gripper tips visible.</div>
  </div>
  <div class="media-block photo">
    <img src="../assets/images/sew-unit-fold-result.jpg" alt="Denim cloth folded on workspace after teleop data collection run">
    <div class="media-caption">Result after a teleoperated cloth fold — denim on the workspace.</div>
  </div>
</div>

---

## Perception & Data Collection

The platform collects synchronized RGB-D video across four cameras while recording joint states at configurable rate (10–30 Hz). Turning that raw data into 3D particle tracks that dynamics models can train on required building a complete perception pipeline from scratch.

**Camera setup:** 4× Intel RealSense cameras (D435i and D405) surrounding the workspace, calibrated individually with ChAruco boards (DICT_4X4_50, 5×4, 40mm squares). Best stereo pair achieved 0.68 RMS reprojection error. Automated hand-eye calibration maps each camera into robot-base coordinates.

**Cloth and gripper segmentation:** Custom YOLOv5 models hand-annotated using labelImg — separate detectors per fabric type (black, denim, red), each trained for ~500 epochs on train/val/test splits. Multi-camera RGB-D point clouds are color-coded by source camera for registration debugging.

**Gripper tracking:** Started with HSV color thresholding. Replaced with CoTracker 3 (Meta's learned point tracker) for robustness under changing lab lighting and partial occlusion — reliable across all 11 collected trajectories.

**Dataset:** 11 annotated bimanual manipulation trajectories across single-arm and dual-arm motions, three fabric types (black, denim, red), with synchronized joint states and multi-camera RGB-D.

---

## What I Learned

<div class="lesson">
  <p><strong>Inverted mounting is not trivial.</strong> Gravity compensation and joint limits all flip. Small sign errors cause the planner to propose impossible trajectories. Found this out through hours of debugging URDF transforms.</p>
</div>

<div class="lesson">
  <p><strong>Servo calibration across 12 motors takes days.</strong> EEPROM corruption on one motor requires systematic bus isolation to diagnose without taking everything apart. I built tooling to scan individual motors on the live bus.</p>
</div>

<div class="lesson">
  <p><strong>The unified controller was born from frustration.</strong> Two independent serial controllers caused port conflicts and timing issues. Merging them onto a single bus with shared timing fixed both problems and simplified the data pipeline.</p>
</div>

---

<a href="../" class="back-link">← Back to Home</a>
