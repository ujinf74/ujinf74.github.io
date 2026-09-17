---
layout: single
title: "Projects"
permalink: /projects/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Representative Projects</p>
  <p>
    Five projects spanning numerical methods, real-vehicle autonomy, visual perception, field telemetry, and analysis tooling.
    Each summary links to the implementation details, measured results, and validation limits.
  </p>
</div>

<div class="project-card">
  <h3>ballistic-solver <small style="opacity:.7;">C/C++ · Python · Unity/C#</small></h3>
  <p>
    Native intercept solver for moving targets under gravity, quadratic drag, and optional wind. The package combines
    RK4 simulation, coordinate-residual optimization, explicit diagnostics, language bindings, and edge-hardware deployment.
  </p>
  <div class="result-strip">
    <span>0.031 ms fast median</span>
    <span>10,000/10,000 default-path cases</span>
    <span>Rock 5B + STM32 validation</span>
  </div>
  <div style="display:flex; gap:.6rem; flex-wrap:wrap; margin-top:.8rem;">
    <a class="btn" href="/projects/ballistic-solver/">Project details</a>
    <a class="btn" href="https://github.com/ujinf74/ballistic-solver">GitHub</a>
    <a class="btn" href="https://pypi.org/project/ballistic-solver/">PyPI</a>
  </div>
</div>

<div class="project-card">
  <h3>Mapless Autonomous Parking <small style="opacity:.7;">Hyundai Ioniq · ROS 2 · Autoware · FAST-LIO</small></h3>
  <p>
    Real-vehicle reverse-parking system without prebuilt pointcloud or vector maps. FAST-LIO odometry feeds live C++ occupancy mapping,
    goal-pose planning, delay-aware forward/reverse tracking, and an Autoware-compatible CAN command path.
  </p>
  <div class="proof-callout">
    <b>Physical validation</b>
    <span>Low-speed parking execution on a Hyundai Ioniq with measured actuator delay reflected in the follower.</span>
  </div>
  <a class="btn" href="/projects/mapless-autonomous-parking/">Project details</a>
</div>

<div class="project-card">
  <h3>Monoscale Visual Odometry <small style="opacity:.7;">ROS 2 · C++/CUDA · Cameras + IMU</small></h3>
  <p>
    Learning-free metric camera motion and dense occupancy from known camera height and ground-plane geometry.
    Photometric distance and anchor-map direction, attitude, and accumulated-error correction remain separate and measurable.
  </p>
  <div class="result-strip">
    <span>9 CARLA drives</span>
    <span>0.0237% mean distance-normalized ATE</span>
    <span>132 core tests</span>
  </div>
  <div style="display:flex; gap:.6rem; flex-wrap:wrap; margin-top:.8rem;">
    <a class="btn" href="/projects/monoscale/">Project details</a>
    <a class="btn" href="https://github.com/ujinf74/monoscale">GitHub</a>
  </div>
</div>

<div class="project-card">
  <h3>Racing Telemetry Stack <small style="opacity:.7;">Python · Raspberry Pi · ZED-F9R · RTK/NTRIP</small></h3>
  <p>
    Car-side runtime for receiver configuration, high-rate GPS/IMU collection, correction ingestion, buffered CSV/UBX logging,
    remote browser monitoring, and recovery from serial or correction-stream failures.
  </p>
  <div class="proof-callout">
    <b>Operational path</b>
    <span>ZED-F9R → Raspberry Pi collector → Cloudflare Worker/SSE monitor → desktop analysis.</span>
  </div>
  <a class="btn" href="/projects/racing-telemetry-stack/">Project details</a>
</div>

<div class="project-card">
  <h3>Racing Analyze GUI <small style="opacity:.7;">Python · PySide6 · Telemetry Analysis</small></h3>
  <p>
    Packaged multi-run workbench for gate-aligned timing, segment comparison, flexible plots, synchronized media,
    simulator registration, and report export for circuit-driving review.
  </p>
  <img src="/assets/images/racing_analyze_gui_2026.png" alt="PySide6 racing telemetry workspace with time-series plots, GG diagram, track map, and synchronized onboard video" loading="lazy" decoding="async"
    style="width:100%; aspect-ratio:2048/1049; object-fit:cover; object-position:center bottom; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">
  <div class="result-strip">
    <span>4 log families</span>
    <span>1,232 automated tests</span>
    <span>Windows/Linux + headless workflow</span>
  </div>
  <a class="btn" href="/projects/racing-analyze-gui/">Project details</a>
</div>

<h2>Additional Work</h2>

<div class="mini-grid">
  <div class="mini-card">
    <div class="mini-kicker">In development</div>
    <h3>HERO — Low-Vision Parking Coaching</h3>
    <p>Exploratory Qt HUD for parking-corridor, stop-line, gear-state, and degraded-state guidance using Monoscale perception.</p>
    <a class="btn" href="/projects/hero/">Development notes</a>
  </div>
  <div class="mini-card">
    <div class="mini-kicker">Early work</div>
    <h3>EV Gear Reduction Sizing</h3>
    <p>MATLAB drivetrain sizing with torque-speed modeling and longitudinal simulation across candidate gear ratios.</p>
  </div>
</div>
