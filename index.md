---
layout: default
title: ∞
---

# ∞
<span style="font-size:0.95rem; opacity:0.70;">Ujin Kwon · 권우진</span>

Mechanical & Computer Engineering student working on **numerical algorithms, dynamic systems, and real-time simulation** for **robotics and autonomous systems**.

**Interests:** Robotics & Autonomous Systems — **Optimal Control · Numerical Optimization · Dynamics**

---

## Focus

I build systems where **physics, optimization, and real-time constraints** meet:

- **Numerical optimization & solvers** for nonlinear dynamics  
- **Dynamics-aware planning and control** (trajectory, constraints, stability)  
- **Real-time simulation & integration** (C/C++, MATLAB, Python, ROS 2, engine/FFI)  

---

## Featured Projects

### ballistic-solver (C/C++ · Python · Unity / C#)
A native numerical solver that computes launch angles to intercept **moving targets** under **gravity** and **quadratic air drag**, with optional **wind**.

**What I built**
- Simulation-based solver: fixed-`dt` RK4 projectile integration with drag (+ wind)
- Nonlinear solve: damped least squares (**Levenberg–Marquardt**) with Broyden-style Jacobian refinement
- Engineering for integration: **stable C ABI**, explicit status codes, diagnostics, and best-effort outputs

**Why it matters**
- Works in strongly nonlinear regimes where analytic/vacuum solvers break down (high drag / highly curved trajectories)
- Designed for real-time integration across languages and engines (C / Python / C# / Unity)

Repository: https://github.com/ujinf74/ballistic-solver

---

### Mapless autonomous parking in simulation (Isaac Sim · ROS 2 Humble · Autoware Universe)
A real-time autonomous parking stack that works **without prebuilt map data** (no pointcloud map / vector map), using online mapping and replanning.

**What I built**
- Isaac Sim PhysX vehicle + ROS 2 interface: LiDAR/IMU/odometry publishing and command application
- Pointcloud adapters for Autoware compatibility (fields/frame), plus cropping + ground filtering
- Online occupancy mapping: ego-fixed local grids → global accumulation with probability heuristics
- Compute reduction: **tiled occupancy + sliding-window ROI** to reduce planning cost
- Planning/control: occupancy-only **Hybrid A\*** (forward/reverse) + tracking control for low-speed maneuvers

**Why it matters**
- End-to-end pipeline: sensing → mapping → planning → control, with practical latency/QoS considerations
- A stepping stone toward sim-to-real validation (sensor calibration, odometry, CAN integration)

---

## Current Tooling

**Core strengths**
- Numerical integration (RK4/ODE modeling), nonlinear least-squares, diagnostics-driven solver design
- Dynamics-aware planning/control for vehicles (constraints, curvature-speed profiling, reverse maneuvers)
- Real-time system integration (ROS 2 QoS, TF, ABI/FFI boundaries, reproducible builds)

**Stack**
- **Languages:** C/C++, MATLAB, Python  
- **Robotics:** ROS 2, Autoware Universe  
- **Simulation:** NVIDIA Isaac Sim, Unity integration patterns (native plugin / P/Invoke)  
- **Release quality:** CI, packaging, prebuilt binaries (where applicable)

---

## Contact

- GitHub: https://github.com/ujinf74  
- Email: ujin@tukorea.ac.kr
