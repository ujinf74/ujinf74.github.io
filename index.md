---
layout: default
title: ujinf74 Portfolio
---

# ∞

Mechanical & Computer Engineering student working on **numerical algorithms, dynamic systems, and real-time simulation** for **robotics and autonomous systems**.

**Interests:** Robotics & Autonomous Systems — **Optimal Control · Numerical Optimization · Dynamics**

---

## Focus

I build systems where **physics, optimization, and real-time constraints** meet:

- **Numerical optimization & solvers** for nonlinear dynamics
- **Dynamics-aware planning and control** (trajectory, constraints, stability)
- **Real-time simulation & integration** (C/C++, Matlab, Python, ROS 2, engine/FFI)

---

## Featured Projects

### ballistic-solver (C/C++ · Python · Unity / C#)
A native numerical solver that computes launch angles to intercept **moving targets** under **gravity** and **quadratic air drag**, with optional **wind**.

- Simulation-based solver (RK4) + nonlinear least-squares (Levenberg–Marquardt) with Broyden-style Jacobian refinement
- **Robust in strongly nonlinear regimes** (high drag / highly curved trajectories)
- **Stable C ABI** for multi-language use + PyPI package + prebuilt native releases
- Explicit **success/failure codes** and diagnostics for real-time integration

Repository: https://github.com/ujinf74/ballistic-solver

---

### Mapless autonomous parking in simulation (Isaac Sim · ROS 2 Humble · Autoware Universe)
A real-time autonomous parking stack that works **without prebuilt map data** (no pointcloud map / vector map), using online mapping and replanning.

- Isaac Sim PhysX vehicle + LiDAR/IMU/odometry publishing and control via ROS 2
- Pointcloud compatibility adapters (fields/frame) + ground filtering + cropping
- Ego-fixed local occupancy → global accumulation with probability heuristics
- **Tiled occupancy + sliding-window ROI** to reduce planning compute
- **Hybrid A\*** (forward/reverse) planning from occupancy only + custom tracking control

(Write-up and demos will be added as the system matures.)

---

## Current Tooling


- **Core topics:** numerical integration, nonlinear optimization, vehicle dynamics, planning & control
- **Languages:** C/C++, Matlab, Python
- **Robotics stack:** ROS 2, Autoware Universe
- **Simulation:** NVIDIA Isaac Sim, real-time integration patterns (ABI/FFI)

---

## Contact

- GitHub: https://github.com/ujinf74
- Email: ujin@tukorea.ac.kr
