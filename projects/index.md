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
    <a class="btn" href="/projects/ballistic-solver/">Detailed page</a>
    <a class="btn" href="https://github.com/ujinf74/ballistic-solver">Repo</a>
    <a class="btn" href="https://pypi.org/project/ballistic-solver/">PyPI</a>
  </div>

  <div class="result-strip">
    <span><b>Verified benchmark</b></span>
    <span>fast 0.107 ms median</span>
    <span>balanced 0.219 ms median</span>
    <span>precise 0.265 ms median</span>
  </div>
</div>

<div class="project-card">
  <h3>Mapless Autonomous Parking <small style="opacity:.7;">(Isaac Sim · ROS 2 Humble · Autoware Universe)</small></h3>

  <p>
    <b>Real-time mapless parking</b> without prebuilt pointcloud/vector maps:
    <b>online occupancy mapping → occupancy-only Hybrid A*</b> replanning → <b>trajectory processing + low-speed parking execution</b>
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
      resampling / filling and continuous-reference preparation for low-speed maneuver tracking
    </li>

    <li><b>Execution layer</b>:
      parking follower path with longitudinal control, reverse-capable execution, and trajectory-direction-aware handling
    </li>

    <li><b>Forward/Reverse execution</b>:
      segment-wise direction handling + gear command integration based on trajectory direction/velocity sign
    </li>

    <li><b>Real-time engineering & debugging</b>:
      QoS tuning to avoid backlog/timing loss, RViz2 visualization (OGM/trajectory/vehicle), and CLI status reporting
    </li>
  </ul>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap;">
    <a class="btn" href="/projects/mapless-autonomous-parking/">Detailed page</a>
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
    <li><b>Wireless operations</b>: Git/SSH/Tailscale-based update workflow for deploying package changes to the Raspberry Pi without direct physical access</li>
  </ul>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap;">
    <a class="btn" href="/projects/racing-telemetry-stack/">Detailed page</a>
  </div>
</div>

<div class="project-card">
  <h3>Racing Analyze GUI <small style="opacity:.7;">(MATLAB · Telemetry Analysis · Driver Coaching)</small></h3>

  <p>
    <b>Segment-based racing telemetry analysis workbench</b> for comparing multiple logged runs, visualizing driver/vehicle behavior,
    and supporting <b>coaching-oriented inspection</b> for circuit driving.
    Developed and used together with the telemetry collection workflow for <b>Luxon Racing Team</b> in the <b>GTA class of the O-NE SUPERRACE CHAMPIONSHIP</b>.
  </p>

  <img src="/assets/images/racing_analyze_gui.png" alt="Racing Analyze GUI"
    style="width:100%; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">

  <b>What I built</b>
  <ul>
    <li><b>Fast track/core build</b>:
      GPS-fix-based <b>track core / segment reference</b> generation for repeated run comparison
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

    <li><b>Signal conditioning</b>:
      smoothing and abnormal-data interpolation support for more stable visualization and comparison
    </li>

    <li><b>Pane-level workflow tools</b>:
      per-pane rerender and pop-out windows for focused inspection without rebuilding the full workspace
    </li>

    <li><b>Metrics extraction</b>:
      segment-level metrics such as <b>segment time</b>, <b>velocity statistics</b>, and <b>acceleration-related indicators</b> for quick run ranking and review
    </li>

    <li><b>Practical use case</b>:
      supports <b>visualization assistance</b> and <b>coaching workflow</b> for real racing data analysis
    </li>
  </ul>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap;">
    <a class="btn" href="/projects/racing-analyze-gui/">Detailed page</a>
  </div>
</div>

<div class="project-card">
  <h3 style="margin-top:.2rem;">EV Gear Reduction Sizing <small style="opacity:.72;">(early work)</small></h3>
  <div class="kicker">
    MATLAB-based drivetrain sizing: datasheet torque–speed modeling + longitudinal acceleration simulation, sweeping gear ratios to minimize run time.
  </div>
</div>
