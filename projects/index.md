---
layout: single
title: "Projects"
permalink: /projects/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Representative Projects</p>
  <p>
    Five representative projects covering solver design, real-vehicle autonomy integration, visual odometry, field telemetry, and analysis-tool construction.
    For a capability-first view, start from <a href="/capabilities/">Capabilities</a>.
  </p>
</div>

<div class="project-card">
  <h3>ballistic-solver <small style="opacity:.7;">(C/C++ · Python · Unity/C#)</small></h3>

  <p>
    <b>Simulate-first intercept optimizer</b> for moving targets under <b>gravity</b> and <b>quadratic drag</b> (+ optional wind).
    Its default path minimizes a <b>coordinate-space closest-approach residual</b> with Gauss–Newton, Broyden updates,
    vacuum-seeded Jacobians, and multistart recovery. The auxiliary-residual method remains available as a research and compatibility path.
  </p>

  <video controls playsinline preload="metadata"
    style="width:100%; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">
    <source src="/assets/videos/ballistic_demo_low.mp4" type="video/mp4">
  </video>

  <b>What I built</b>
  <ul>
    <li><b>Dynamics</b>: fixed-step RK4 with quadratic drag (+ wind as air-velocity)</li>
    <li><b>Default residual</b>: closest-approach miss measured directly in coordinate space</li>
    <li><b>Numerical optimization</b>: vacuum-lead warm start, analytic vacuum Jacobian preconditioning, Gauss–Newton, and multistart fallback</li>
    <li><b>Speed</b>: Broyden rank-1 Jacobian updates reduce full re-linearizations</li>
    <li><b>Robust outputs</b>: explicit status/message + best-effort solution even on non-ideal convergence</li>
    <li><b>Deployment</b>: compiled native C++ core with a modern <code>bs::</code> API, stable C ABI, Python/PyPI, Unity/C#, and Godot/tracker integrations</li>
    <li><b>Research path</b>: the paper-backed auxiliary residual remains exposed through <code>solve_aux</code></li>
  </ul>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap;">
    <a class="btn" href="/projects/ballistic-solver/">Detailed page</a>
    <a class="btn" href="https://github.com/ujinf74/ballistic-solver">Repo</a>
    <a class="btn" href="https://pypi.org/project/ballistic-solver/">PyPI</a>
  </div>

  <div class="result-strip">
    <span><b>Current package benchmark</b></span>
    <span>fast 0.031 ms median</span>
    <span>balanced 0.057 ms median</span>
    <span>precise 0.087 ms median</span>
  </div>

  <div class="proof-callout">
    <b>Result</b>
    <span>Packaged native solver with current benchmarks, explicit diagnostics, game-engine bindings, and a Rock 5B + STM32 hardware integration.</span>
  </div>
</div>

<div class="project-card">
  <h3>Mapless Autonomous Parking <small style="opacity:.7;">(Hyundai Ioniq · ROS 2 Humble · Autoware Universe · FAST-LIO)</small></h3>

  <p>
    <b>Real-vehicle mapless autonomous parking</b> on a Hyundai Ioniq without prebuilt pointcloud/vector maps:
    <b>FAST-LIO odometry → C++ LiDAR occupancy-grid updates → RViz goal-pose planning → delay-aware trajectory following → Ioniq CAN command path</b>.
  </p>

  <video controls playsinline preload="metadata"
    style="width:100%; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">
    <source src="/assets/videos/real-vehicle_demo.mp4" type="video/mp4">
  </video>

  <b>What I built</b>
  <ul>
    <li><b>Real-vehicle integration</b>: connected the parking system to an existing Hyundai Ioniq research platform</li>

    <li><b>FAST-LIO bridge</b>: LiDAR-inertial odometry aligned into the vehicle localization and TF path</li>

    <li><b>Autoware compatibility layer</b>: pointcloud fields/frame adaptation + self-cropping + ground filtering</li>

    <li><b>Occupancy mapping</b>:
      native C++ pointcloud occupancy-grid updates with timestamp pairing, log-odds sparse tiles, and <b>decay back to unknown</b> for stale cells
    </li>

    <li><b>Compute-bounded replanning</b>:
      occupancy <b>tiling</b> + <b>sliding-window ROI</b> updates to reduce cell count and keep replanning tractable
    </li>

    <li><b>Planning without vector maps</b>:
      custom node using Autoware freespace planning algorithms from occupancy-only + vehicle constraints
    </li>

    <li><b>Trajectory processing</b>:
      resampling / filling and continuous-reference preparation for low-speed forward/reverse maneuver tracking
    </li>

    <li><b>Execution layer</b>:
      delay-aware follower using measured steering/longitudinal response delay for pose prediction, velocity prediction, and separate reference preview
    </li>

    <li><b>Ioniq vehicle interface</b>:
      Autoware-compatible command output connected to the vehicle CAN interface
    </li>

    <li><b>Real-time engineering & debugging</b>:
      timing/backlog tuning, RViz2 visualization (occupancy grid/trajectory/vehicle), and CLI status reporting
    </li>
  </ul>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap;">
    <a class="btn" href="/projects/mapless-autonomous-parking/">Detailed page</a>
  </div>

  <div class="proof-callout">
    <b>Result</b>
    <span>Real Hyundai Ioniq parking execution with FAST-LIO odometry, C++ LiDAR occupancy-grid mapping, delay-aware trajectory following, and CAN-facing command output.</span>
  </div>
</div>

<div class="project-card">
  <h3>Monoscale Visual Odometry <small style="opacity:.7;">(ROS 2 · C++/CUDA · Cameras + IMU)</small></h3>

  <p>
    <b>Learning-free metric visual odometry and dense occupancy</b> for vehicles using known camera height and ground-plane geometry.
    Photometric alignment measures travel distance, while a short-lived feature anchor map estimates direction,
    corrects accumulated position error, and recovers camera roll/pitch relative to the ground.
  </p>

  <b>What I built</b>
  <ul>
    <li><b>Metric motion</b>: scale from camera mounting height and the ground plane, without stereo, LiDAR, a learned model, or a prebuilt map</li>
    <li><b>Separated estimation roles</b>: photometric distance in mapless intervals; anchor-map direction, attitude, and accumulated-error correction when anchors are available</li>
    <li><b>ROS-independent C++ core</b>: estimator logic testable without a ROS graph and reusable inside another process</li>
    <li><b>Dense occupancy</b>: C++/CUDA plane sweep over raw fisheye images, using odometry roll/pitch in the image warp</li>
    <li><b>Repeatable evaluation</b>: deterministic bag replay, CARLA ground truth scoring, held-out runs, and 132 core tests</li>
  </ul>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap;">
    <a class="btn" href="/projects/monoscale/">Detailed page</a>
    <a class="btn" href="https://github.com/ujinf74/monoscale">Repo</a>
  </div>

  <div class="result-strip">
    <span><b>CARLA, 9 drives</b></span>
    <span>mean distance-normalized ATE 0.0237%</span>
    <span>132 core tests</span>
  </div>

  <div class="proof-callout">
    <b>Result</b>
    <span>Metric camera motion and dense occupancy with measured ablations for distance, direction, attitude, and long-term trajectory error.</span>
  </div>
</div>

<div class="project-card">
  <h3>Racing Telemetry Stack <small style="opacity:.7;">(Python · Raspberry Pi · ZED-F9R · RTK/NTRIP · Cloudflare Worker)</small></h3>

  <p>
    <b>Car-side telemetry runtime</b> for racing data collection, built around a Raspberry Pi and <b>u-blox ZED-F9R GPS/IMU receiver</b>.
    The system configures the receiver at startup, collects high-rate UBX GPS/IMU messages, injects RTCM correction data from an
    <b>NTRIP caster</b>, writes buffered CSV/UBX logs, and publishes live debug state to a browser dashboard through a
    <b>Cloudflare Worker + Durable Object + SSE</b> pipeline.
  </p>

  <b>What I built</b>
  <ul>
    <li><b>Raspberry Pi runtime</b>: systemd-managed Python collector with boot persistence, automatic restart, environment-based configuration, and pre-start ZED-F9R configuration</li>
    <li><b>Receiver configuration</b>: automated UART/UBX setup for 20 Hz measurement, NAV-PVT, HPPOSLLH, RAWX, ESF-RAW, MON-HW/RF, and RTCM3 input</li>
    <li><b>RTK correction flow</b>: NTRIP connection, periodic GGA injection, RTCM queueing, retry handling, and fallback behavior under poor correction availability</li>
    <li><b>Robust field logging</b>: date-foldered drive logs, GPS/IMU merged CSV output, optional raw UBX capture, buffered writes, and post-processing helpers</li>
    <li><b>Fault tolerance</b>: serial retry, idle timeout detection, invalid GPS jump/speed filtering, frame/PVT timeout handling, and optional receiver reconfiguration</li>
    <li><b>Remote monitoring</b>: Raspberry Pi posts live debug packets to Cloudflare Worker; Durable Object stores latest state and streams updates to browser clients using SSE with Leaflet map visualization</li>
    <li><b>Wireless operations</b>: Git/SSH/Tailscale-based update workflow for deploying package changes to the Raspberry Pi</li>
  </ul>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap;">
    <a class="btn" href="/projects/racing-telemetry-stack/">Detailed page</a>
  </div>

  <div class="proof-callout">
    <b>Result</b>
    <span>Real-device receiver setup, correction ingestion, buffered logging, browser monitoring, and operational recovery paths.</span>
  </div>
</div>

<div class="project-card">
  <h3>Racing Analyze GUI <small style="opacity:.7;">(Python · PySide6 · Telemetry Analysis)</small></h3>

  <p>
    <b>Packaged racing telemetry analysis workbench</b> for comparing multiple logged runs, aligning them at track gates,
    visualizing driver and vehicle behavior, and supporting <b>coaching-oriented inspection</b> for circuit driving.
    Developed and used together with the telemetry collection workflow for <b>Luxon Racing Team</b> in the <b>GTA class of the O-NE SUPERRACE CHAMPIONSHIP</b>.
  </p>

  <img src="/assets/images/racing_analyze_gui.png" alt="Racing Analyze GUI"
    style="width:100%; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">

  <b>What I built</b>
  <ul>
    <li><b>Gate-aligned timing</b>:
      interpolate each crossing between samples so lap, segment, plot, map, replay, and video boundaries share the same physical instant
    </li>

    <li><b>Fast multi-log workflow</b>:
      efficient loading and caching of multiple logged runs, enabling quick switching across segments after a single analysis pass
    </li>

    <li><b>Segment-wise comparison</b>:
      gate/segment-based run slicing across <b>All / S0 / S1..Sn / S(n+1)</b> for aligned comparison of the same track region
    </li>

    <li><b>Interactive replay</b>:
      time-slider-based replay with <b>play / pause / stop / speed control</b> and pane-aware marker updates
    </li>

    <li><b>Flexible visualization modes</b>:
      <b>XY, TS, MAP, POLAR, KDE, GG</b> views for telemetry inspection from multiple perspectives
    </li>

    <li><b>Sensor-channel flexibility</b>:
      arbitrary logged channels can be assigned to <b>x / y / color</b>, enabling broad exploratory analysis across vehicle states and driver inputs
    </li>

    <li><b>Log compatibility</b>:
      regular and MoTeC CSV, MoTeC LD, GPS, and simulator-coordinate logs with track registration
    </li>

    <li><b>Media and pane workflow</b>:
      synchronized video/audio, configurable plot panes, drag-and-drop, pop-out windows, and restored sessions
    </li>

    <li><b>Metrics and reports</b>:
      segment time, speed and acceleration indicators, time-loss decomposition, and CSV export for further analysis
    </li>

    <li><b>Practical use case</b>:
      desktop build paths for Windows and Linux, a headless CLI/library path, and 1,232 automated tests
    </li>
  </ul>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap;">
    <a class="btn" href="/projects/racing-analyze-gui/">Detailed page</a>
  </div>

  <div class="proof-callout">
    <b>Result</b>
    <span>Packaged multi-run workbench with physical gate alignment, synchronized media/replay, flexible plots, and reproducible reports.</span>
  </div>
</div>

<h2>Additional Work</h2>

<div class="project-card">
  <p class="eyebrow">In development</p>
  <h3>HERO — Low-Vision Parking Coaching</h3>
  <p>
    A coaching-only HUD concept that applies <a href="/projects/monoscale/">Monoscale</a> perception to parking-corridor,
    stop-line, gear-state, and degraded-state guidance. The ROS 2 coaching logic and Qt presentation layer remain separate;
    the geometry layer currently has 26 tests. This work is exploratory and does not intervene in vehicle control.
  </p>
  <a class="btn" href="/projects/hero/">Development notes</a>
</div>

<div class="project-card">
  <h3 style="margin-top:.2rem;">EV Gear Reduction Sizing <small style="opacity:.72;">(early work)</small></h3>
  <div class="kicker">
    MATLAB-based drivetrain sizing: datasheet torque–speed modeling + longitudinal acceleration simulation, sweeping gear ratios to minimize run time.
  </div>
</div>
