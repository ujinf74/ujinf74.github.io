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
    <b>online occupancy mapping → occupancy-only Hybrid A*</b> replanning → <b>fraction-index path interpolation + Stanley-based tracking</b>
    for forward/reverse parking maneuvers.
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

    <li><b>Trajectory processing</b>:
      <b>fraction-index-based interpolation</b> over waypoint segments to construct continuous virtual references for low-speed maneuver tracking
    </li>

    <li><b>Trajectory follower (core control)</b>:
      <b>Stanley-based lateral control</b> with a <b>lateral-error derivative damping term</b>, plus longitudinal velocity control for stable low-speed convergence
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
  <h3>Racing Analyze GUI <small style="opacity:.7;">(MATLAB · Telemetry Analysis · Driver Coaching)</small></h3>

  <p>
    <b>Segment-based racing telemetry analysis GUI</b> for comparing multiple logged runs, visualizing driver/vehicle behavior,
    and supporting <b>coaching-oriented inspection</b> for circuit driving.
    Developed and used in collaboration with <b>Luxon Racing Team</b>, competing in the <b>Superrace GT-A class</b>.
  </p>

  <img src="/assets/images/racing_analyze_gui.png" alt="Racing Analyze GUI"
    style="width:100%; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">

  <b>What I built</b>
  <ul>
    <li><b>Fast core build</b>:
      GPS-fix-based <b>track core / segment reference</b> generation for repeated run comparison
    </li>

    <li><b>Fast multi-log workflow</b>:
      efficient loading and caching of multiple logged runs, enabling quick switching across segments after a single build
    </li>

    <li><b>Segment-wise comparison</b>:
      gate/segment-based run slicing to compare the same part of a lap across different sessions and drivers
    </li>

    <li><b>Flexible visualization modes</b>:
      <b>XY, TS, MAP, POLAR, KDE, GG</b> views for telemetry inspection from multiple perspectives
    </li>

    <li><b>Sensor-channel flexibility</b>:
      arbitrary logged channels can be assigned to <b>x / y / color</b>, enabling broad exploratory analysis across vehicle states and driver inputs
    </li>

    <li><b>Signal conditioning</b>:
      smoothing and abnormal-data interpolation support for more stable visualization and comparison
    </li>

    <li><b>Metrics extraction</b>:
      segment-level metrics such as <b>segment time</b>, <b>velocity statistics</b>, and <b>acceleration-related indicators</b> for quick run ranking and review
    </li>

    <li><b>Practical use case</b>:
      supports <b>visualization assistance</b> and <b>coaching workflow</b> for real racing data analysis
    </li>
  </ul>
</div>

<div class="project-card">
  <h3 style="margin-top:.2rem;">EV Gear Reduction Sizing <small style="opacity:.72;">(early work)</small></h3>
  <div class="kicker">
    MATLAB-based drivetrain sizing: datasheet torque–speed modeling + longitudinal acceleration simulation, sweeping gear ratios to minimize run time.
  </div>
</div>
