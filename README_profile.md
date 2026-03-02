### Hi, I'm Tabby 👋

I'm a PhD researcher at Brown University advised by [Professor Nora Ayanian](https://vivo.brown.edu/display/nayanian). My work is on robotic cloth manipulation: building the hardware, perception, and learning systems needed to handle fabric reliably on real robots.

---

### 🦾 [Sew Unit](https://tabithako.github.io/projects/sew-unit) — Bimanual Cloth Manipulation Platform

A bimanual robot platform I designed and built from scratch: custom aluminum extrusion frame, two inverted SO-101 arms, ROS2/MoveIt motion planning, and leader-follower teleoperation for data collection.

<table><tr>
<td><video src="https://github.com/user-attachments/assets/8458be10-d610-4612-bc3f-9db06929b35f" autoplay loop muted playsinline></video></td>
<td><video src="https://github.com/user-attachments/assets/48f85f00-bee7-4947-a7c1-6855fd8b9cf9" autoplay loop muted playsinline></video></td>
</tr></table>

*CAD model spin · Real robot executing a bimanual trajectory*

---

### 🧠 [Learning Cloth Dynamics](https://tabithako.github.io/projects/cloth-dynamics) — From Paper to Real Fabric

Took PhysTwin and PGND, got them running on cloth data I collected myself, then extended PGND with a differentiable render loss (DINOv2 + SSIM) and live camera conditioning at rollout time. Three model variants, each adding a new supervisory signal on top of the last.

<video src="https://github.com/user-attachments/assets/bd9a385b-5c1a-451b-81e4-9d1573f8b3ff" autoplay loop muted playsinline></video>

*Baseline vs. Visual PGND — all held-out episodes*

<video src="https://github.com/user-attachments/assets/6aa8d951-6bb0-4986-a588-cd9f9ee47395" autoplay loop muted playsinline></video>
<video src="https://github.com/user-attachments/assets/c4e29a6c-98f1-45e2-aa0b-c4fcbc4ace64" autoplay loop muted playsinline></video>

*PhysTwin novel actions: fold left-over-right · bimanual pull-apart, simulated with parameters learned from a single training trajectory*

---

### ✋ [Custom Grippers & Teleop Tools](https://tabithako.github.io/projects/grippers)

Two custom end-effectors: silicone FSR grippers with embedded force sensors for contact-aware grasping, and a UMI-inspired handheld teleop gripper with ArUco markers and IMU for imitation learning data collection.

<video src="https://tabithako.github.io/assets/videos/sew-unit-denim-pinch.mp4" autoplay loop muted playsinline></video>

---

### Research repos
- [`TabithaKO/PhysTwin`](https://github.com/TabithaKO/PhysTwin) — SO-101 cloth data pipeline, multi-camera perception, trajectory generation
- [`TabithaKO/pgnd`](https://github.com/TabithaKO/pgnd) — visual PGND: mesh-constrained Gaussian Splatting + DINOv2 camera conditioning

📄 [tabithako.github.io](https://tabithako.github.io) &nbsp;·&nbsp; 👗 [Fashion](https://www.tkobytabithaoanda.com/)
