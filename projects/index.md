---
layout: single
title: "Projects"
permalink: /projects/
classes: wide
---

<div class="project-card">
  <h3>ballistic-solver <small style="opacity:.7;">(C/C++ · Python · Unity/C#)</small></h3>

  <p>
    <b>Simulate-first intercept optimizer</b> for moving targets under <b>gravity</b> and <b>quadratic drag</b> (+ optional wind).
    It integrates nonlinear projectile dynamics (RK4) and solves launch angles (θ, φ) by forming a <b>closest-approach miss residual</b> and running <b>Levenberg–Marquardt</b>.
  </p>

  <video controls playsinline preload="metadata"
    style="width:100%; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">
    <source src="/assets/videos/ballistic_demo_low.mp4" type="video/mp4">
  </video>

  <b>What I built</b>
  <ul>
    <li><b>Dynamics</b>: fixed-step RK4 with quadratic drag (+ wind as air-velocity)</li>
    <li><b>Numerical optimization</b>: closest-approach residual → LM (damped least squares) + line-search/lambda tries</li>
    <li><b>Speed</b>: Broyden-style Jacobian refinement to reduce full re-linearizations</li>
    <li><b>Robust outputs</b>: explicit status/message + best-effort solution even on non-ideal convergence</li>
    <li><b>Deployment</b>: stable C ABI (FFI-ready), PyPI package with prebuilt binaries, Unity/C# via P/Invoke</li>
  </ul>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap;">
    <a class="btn" href="https://github.com/ujinf74/ballistic-solver">Repo</a>
    <a class="btn" href="https://pypi.org/project/ballistic-solver/">PyPI</a>
  </div>
</div>


<div class="project-card">
  <h3>Mapless Autonomous Parking <small style="opacity:.7;">(Isaac Sim · ROS 2 Humble · Autoware Universe)</small></h3>

  <p>
    <b>Real-time mapless parking</b> without prebuilt pointcloud/vector maps:
    <b>online occupancy mapping → occupancy-only Hybrid A*</b> replanning → <b>PP+PD trajectory tracking</b> for forward/reverse maneuvers.
  </p>

  <video controls playsinline preload="metadata"
    style="width:100%; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">
    <source src="/assets/videos/autopark_demo.mp4" type="video/mp4">
  </video>

  <b>What I built</b>
  <ul>
    <li><b>Autoware compatibility layer</b>: pointcloud fields/frame adaptation + self-cropping + ground filtering</li>

    <li><b>Occupancy mapping</b>:
      ego-fixed local OGM → global accumulation with probability heuristics, plus <b>decay back to unknown</b> for stale cells
    </li>

    <li><b>Compute-bounded replanning</b>:
      occupancy <b>tiling</b> + <b>sliding-window ROI</b> updates to reduce cell count and keep replanning tractable
    </li>

    <li><b>Planning without vector maps</b>:
      custom node using Autoware freespace planning algorithms (<b>Hybrid A*</b>) from occupancy-only + vehicle constraints
    </li>

    <li><b>Trajectory follower (core control)</b>:
      heading feedforward + curvature-corrected Pure Pursuit feedback, with a <b>PD-style damping term</b> from discretized arc/center-error changes for low-speed convergence
    </li>

    <li><b>Forward/Reverse execution</b>:
      segment-wise direction handling + gear command integration based on trajectory direction/velocity sign
    </li>

    <li><b>Real-time engineering & debugging</b>:
      QoS tuning to avoid backlog/timing loss, RViz2 visualization (OGM/trajectory/vehicle), and CLI status reporting
    </li>
  </ul>
</div>


<div class="project-card">
  <h3 style="margin-top:.2rem;">EV Gear Reduction Sizing <small style="opacity:.72;">(early work)</small></h3>
  <div class="kicker">
    Datasheet-based drivetrain sizing: torque–speed modeling + reduction ratio sweep for minimum-time estimates.
  </div>
</div>
