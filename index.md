---
layout: single
title: "∞"
permalink: /
---

# <span id="infinity">∞</span>
<span class="subline">Ujin Kwon · 권우진</span>

Mechanical & Computer Engineering student working on **numerical algorithms, dynamic systems, and real-time simulation** for **robotics and autonomous systems**.

<span class="subline"><b>Interests:</b> Robotics & Autonomous Systems — <b>Optimal Control · Numerical Optimization · Dynamics</b></span>

<a class="btn" href="/projects/">Projects</a>
<a class="btn" href="/cv/">CV</a>
<a class="btn" href="https://github.com/ujinf74">GitHub</a>

---

## Focus

I build systems where **physics, optimization, and real-time constraints** meet:

- **Numerical optimization & solvers** for nonlinear dynamics
- **Dynamics-aware planning and control** (trajectory, constraints, stability)
- **Real-time simulation & integration** (C/C++, MATLAB, Python, ROS 2, engine/FFI)

---

## Featured Projects

<div class="project-card">
  <h3>ballistic-solver <span class="badge">C/C++</span> <span class="badge">Python</span> <span class="badge">Unity/C#</span></h3>
  <div class="meta">Native solver for intercepting moving targets under gravity + quadratic drag (+ wind)</div>

  <b>What I built</b>
  <ul>
    <li>Simulation-based solver: fixed-<code>dt</code> RK4 integration with drag (+ wind)</li>
    <li>Nonlinear solve: damped least squares (Levenberg–Marquardt) with Broyden-style Jacobian refinement</li>
    <li>Integration: stable C ABI, explicit status codes, diagnostics, best-effort outputs</li>
  </ul>

  <b>Why it matters</b>
  <ul>
    <li>Works in nonlinear regimes where analytic/vacuum solvers break down (high drag / curved trajectories)</li>
    <li>Designed for real-time multi-language/engine integration (C / Python / C# / Unity)</li>
  </ul>

  <a class="btn" href="https://github.com/ujinf74/ballistic-solver">Repository</a>
</div>

<div class="project-card">
  <h3>Mapless autonomous parking <span class="badge">Isaac Sim</span> <span class="badge">ROS 2</span> <span class="badge">Autoware</span></h3>
  <div class="meta">Real-time parking stack without prebuilt maps (online mapping + replanning)</div>

  <b>What I built</b>
  <ul>
    <li>Isaac Sim PhysX vehicle + ROS 2 interface: LiDAR/IMU/odometry publishing and command application</li>
    <li>Autoware adapters (fields/frame) + cropping + ground filtering</li>
    <li>Online occupancy mapping: local grids → global accumulation with probability heuristics</li>
    <li>Compute reduction: tiled occupancy + sliding-window ROI</li>
    <li>Planning/control: occupancy-only Hybrid A* (forward/reverse) + low-speed tracking control</li>
  </ul>

  <b>Why it matters</b>
  <ul>
    <li>End-to-end pipeline with latency/QoS considerations</li>
    <li>Stepping stone toward sim-to-real validation (calibration, odometry, CAN integration)</li>
  </ul>
</div>

---

## Current Tooling

**Core strengths**
- Numerical integration (RK4/ODE), nonlinear least-squares, diagnostics-driven solver design
- Dynamics-aware planning/control for vehicles (constraints, curvature-speed profiling, reverse maneuvers)
- Real-time integration (ROS 2 QoS, TF, ABI/FFI, reproducible builds)

**Stack**
- **Languages:** C/C++, MATLAB, Python
- **Robotics:** ROS 2, Autoware Universe
- **Simulation:** NVIDIA Isaac Sim, Unity native plugin / P/Invoke patterns
- **Release quality:** CI, packaging, prebuilt binaries (where applicable)

---

## Contact

- GitHub: https://github.com/ujinf74
- Email: <a href="mailto:ujin@tukorea.ac.kr">ujin@tukorea.ac.kr</a>
