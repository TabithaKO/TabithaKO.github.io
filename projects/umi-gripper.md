---
layout: default
title: UMI-Inspired Teleop Gripper
---

<a href="../" class="back-link">← Back to Home</a>

<div class="project-header">
  <h1>UMI-Inspired Teleop Gripper</h1>
  <p class="lead">A custom handheld teleoperation gripper designed for the LeRobot SO-101 platform, inspired by Stanford's UMI (Universal Manipulation Interface) system.</p>
</div>

## Design

- Designed in Fusion 360, 3D printed
- Fits in one hand with a squeeze-trigger mechanism
- Trigger position read by a potentiometer, fed to an Arduino
- Arduino relays gripper commands over serial to the SO-101 controller
- Same serial bus carries arm joint positions from the leader arm

<!-- CAD renders and exploded view — to be added -->
<!-- Electrical schematic — to be added -->

## Data Collection Workflow

1. Operator holds the teleop gripper and moves the leader arm
2. Joint positions + gripper trigger state streamed at 30 Hz
3. Follower arm mirrors the leader with configurable damping
4. Synchronized camera frames recorded alongside joint states
5. Output: timestamped dataset ready for imitation learning

<div class="media-block">
  <video controls muted loop playsinline>
    <source src="../assets/videos/screen-recording-teleop.mp4" type="video/mp4">
  </video>
  <div class="media-caption">Screen recording of a teleop data collection session — pipeline review and trajectory playback.</div>
</div>

## What's Different from the Original UMI

| | Original UMI | This Version |
|---|---|---|
| **Platform** | Franka / UR5 | SO-101 / LeRobot |
| **Communication** | Dynamixel / ROS topics | STS/SCS servo protocol over serial |
| **Integration** | Standalone system | Works with existing teleop recorder for synchronized multi-camera data collection |

The main challenge was adapting the UMI concept to work with the STS/SCS servo protocol instead of Dynamixel. The serial bus uses a half-duplex single-wire protocol, so the Arduino has to manage bus timing carefully to avoid collisions with the arm's joint state traffic.

---

<a href="../" class="back-link">← Back to Home</a>
