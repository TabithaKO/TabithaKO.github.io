# Asset Manifest
# Edit the filenames below (paths are relative to assets/videos/ or assets/images/).
# After you're done, tell Claude and the pages will be updated to match.
# Lines starting with # are comments — ignored.
# Leave a slot blank to remove that media from the page.

---

## Landing Page (index.md)

LANDING_PHOTO:        sew-unit-hero.jpg
LANDING_VIDEO:        sew-unit-denim-pinch.mp4

---

## Project 1: Sew Unit (projects/sew-unit.md)

### Hero
SEW_HERO_PHOTO:       sew-unit-hero.jpg

### Hardware — CAD spins (shown side by side)
SEW_FRAME_SPIN:       sew-unit-frame-spin.mp4
SEW_CAD_SPIN:         sew-unit-cad-spin.mp4

### Hardware — physical arm photos (shown side by side)
SEW_ARMS_FRONT:       sew-unit-arms-front.png
SEW_ARMS_WIDE:        sew-unit-arms-wide.png

### Motion Planning & Digital Twin (shown side by side)
SEW_REAL_EXECUTION:   sew-unit-mirror-bimanual.mp4
SEW_DIGITAL_TWIN:     sew-unit-digital-twin.mp4

### Teleoperation (single video)
SEW_TELEOP:           sew-unit-teleop-leader.mp4

### Teleoperation — result photos (shown side by side)
SEW_RED_PINCH:        sew-unit-red-pinch.jpg
SEW_FOLD_RESULT:      sew-unit-fold-result.jpg

---

## Project 2: Cloth Dynamics (projects/cloth-dynamics.md)

### PGND Model Comparison — Episode 0201 (3-column grid)
PGND_BASELINE:        pgnd-ep0201-baseline.mp4
PGND_PHASE2:          pgnd-ep0201-phase2.mp4
PGND_VISUAL:          pgnd-ep0201-visual.mp4

### All-episodes comparison (single full-width video)
PGND_ALL_EPISODES:    pgnd-comparison-all.mp4

### Perception — tracking pipeline (single video)
CLOTH_TRACKING:       cloth-dynamics-tracking.mp4

### Perception — point cloud grid (single image)
CLOTH_POINTCLOUD:     cloth-dynamics-pointcloud-grid.png

### Real vs Simulation — triptych cameras (shown side by side)
CLOTH_TRIPTYCH_CAM0:  cloth-dynamics-triptych-cam0.mp4
CLOTH_TRIPTYCH_CAM1:  cloth-dynamics-triptych-cam1.mp4

### Real vs Simulation — inference (single video)
CLOTH_INFERENCE:      cloth-dynamics-inference.mp4

### Real vs Simulation — bimanual sim rollouts (shown side by side)
CLOTH_DUAL_LIFT:      sew-unit-dual-lift.mp4
CLOTH_DUAL_PULL:      sew-unit-dual-pull-apart.mp4

### Evaluation Metrics (images)
CLOTH_METRICS:        cloth-dynamics-aggregate-metrics.png
CLOTH_MESH:           cloth-dynamics-mesh-subdivision.jpg

---

## Project 3: Grippers (projects/grippers.md)

### FSR Gripper — annotated CAD + physical photo (shown side by side)
GRIP_FSR_CAD:         gripper-fsr-cad-annotated.jpg
GRIP_FSR_PHYSICAL:    gripper-charuco-denim.jpg

### FSR Gripper — denim pinch demo (single video)
GRIP_DENIM_PINCH:     sew-unit-denim-pinch.mp4

### Teleop Gripper — annotated design CADs (shown side by side, 2 rows)
GRIP_TELEOP_ELEC:     gripper-teleop-cad-electronics.jpg
GRIP_TELEOP_ARUCO:    gripper-teleop-cad-aruco.jpg
GRIP_TELEOP_V1:       gripper-teleop-cad-v1.jpg
GRIP_TELEOP_V2:       gripper-teleop-cad-v2.jpg

### Teleop Gripper — 3D model spin (single video)
GRIP_TELEOP_SPIN:     gripper-teleop-cad-spin.mp4

### Teleop Gripper — clean renders (shown side by side)
GRIP_TELEOP_RENDER_A: gripper-teleop-render-a.png
GRIP_TELEOP_RENDER_B: gripper-teleop-render-b.png

---

## Unused assets (available to assign above)
# videos/cloth-dynamics-fold.mp4
# videos/sew-unit-bimanual-execution.mp4
# videos/sew-unit-dual-push-together.mp4
# videos/sew-unit-dual-twist.mp4
# videos/screen-recording-teleop.mp4
# videos/screen-recording-short.mp4
# videos/cloth-dynamics-pointcloud-cam0.mp4
# images/sew-unit-red-pinch-2.jpg
# images/gripper-teleop-render-c.png
# images/gripper-teleop-render-inverted.png
# images/gripper-charuco-calibration.png
# images/gripper-closeup-silicone.png
# gifs: cloth-dynamics-tracking.gif, cloth-dynamics-triptych.gif, cloth-dynamics-rgb-overlay.gif, sew-unit-dual-fold.gif
