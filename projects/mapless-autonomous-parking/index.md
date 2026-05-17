---
layout: single
title: "Mapless Autonomous Parking"
permalink: /projects/mapless-autonomous-parking/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Hyundai Ioniq · ROS 2 Humble · Autoware Universe · FAST-LIO · HuVILab</p>
  <p>
    I implemented and validated a <b>mapless autonomous parking addon on a real Hyundai Ioniq platform</b>.
    The stack uses FAST-LIO odometry, native C++ LiDAR occupancy accumulation, RViz goal-pose input,
    delay-aware trajectory following, and Autoware-compatible control commands wired into the Ioniq CAN control path.
  </p>

  <video controls playsinline preload="metadata"
    style="width:100%; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">
    <source src="/assets/videos/real-vehicle_demo.mp4" type="video/mp4">
  </video>

  <p style="opacity:.76; margin-top:.7rem;">Earlier Isaac Sim prototype:</p>
  <video controls playsinline preload="metadata"
    style="width:100%; border-radius:18px; margin-top:.3rem; border:1px solid rgba(255,255,255,.14);">
    <source src="/assets/videos/isaac_autopark_demo.mp4" type="video/mp4">
  </video>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap; margin-top:.8rem;">
    <a class="btn" href="/projects/">Back to Projects</a>
  </div>
</div>

<div class="project-card">
  <h3>Problem</h3>
  <ul>
    <li>No prebuilt parking map available.</li>
    <li>The addon had to fit around the existing validated HVL/Autoware/Ioniq stack instead of replacing the vehicle platform.</li>
    <li>Parking had to work on the real vehicle under low-speed, reverse-capable, compute-bounded conditions with practical ROS 2 timing and visualization needs.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Architecture</h3>
  <div class="flow-diagram">
    <div class="flow-step"><b>FAST-LIO Bridge</b><span>/Odometry_base_link aligned into the Autoware localization path</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>C++ LiDAR OGM</b><span>timestamp-paired pointclouds, sparse tile updates, vehicle-centered ROI</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Goal-Pose Planner</b><span>RViz target pose to parking trajectory without prebuilt maps</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Trajectory Follower</b><span>delay-aware pose/velocity prediction with forward/reverse gear handling</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Ioniq CAN Path</b><span>control_converter/control_command to socketcan and can0</span></div>
  </div>
</div>

<div class="project-card">
  <h3>What I Built</h3>
  <ul>
    <li><b>Real-vehicle addon package</b> that layers autonomous parking and FAST-LIO linkage onto the existing HVL/Autoware/Ioniq stack.</li>
    <li><b>FAST-LIO localization bridge</b> that aligns external odometry with the Autoware pose/TF path used by the parking stack.</li>
    <li><b>LiDAR pointcloud adapter and native C++ OGM path</b> for occupancy-grid generation without prebuilt pointcloud/vector maps.</li>
    <li><b>Occupancy accumulation</b> with timestamp-paired raw/obstacle pointclouds, map-frame projection, log-odds sparse tiles, stale-cell decay, and ROI reduction.</li>
    <li><b>Parking planner</b> driven by occupancy grid, current pose, and RViz goal pose.</li>
    <li><b>Trajectory resampler / filler / follower</b> with curvature-aware velocity filling, gear-change stops, and low-speed forward/reverse tracking.</li>
    <li><b>Delay-aware control</b> using measured steering and longitudinal response delays for pose prediction, velocity prediction, and separate reference preview.</li>
    <li><b>Launch integration</b> that can bring up the Ioniq driver, ros2_socketcan bridge, and CAN interface path around the existing vehicle stack.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Built vs Used</h3>
  <ul>
    <li><b>Used</b>: ROS 2 Humble, Autoware components, FAST-LIO, the existing HVL vehicle stack, and the Ioniq driver/CAN command interface.</li>
    <li><b>Built</b>: localization bridge, pointcloud compatibility layer, C++ occupancy accumulation path, parking planner integration, delay-aware trajectory follower, RViz control interface, and launch integration.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Result</h3>
  <ul>
    <li>Implemented a mapless parking addon on a real Hyundai Ioniq platform.</li>
    <li>Connected FAST-LIO odometry, C++ LiDAR occupancy mapping, RViz goal input, delay-aware trajectory following, Autoware command topics, and the Ioniq CAN path.</li>
    <li>Validated low-speed parking execution with stable odometry and vehicle motion.</li>
    <li>Measured real vehicle response delay and reflected it in follower-side pose/velocity prediction.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Evidence</h3>
  <ul>
    <li>Real Hyundai Ioniq parking execution was validated with stable odometry and vehicle motion.</li>
    <li>The launch path wires FAST-LIO odometry, native occupancy-grid generation, planner output, trajectory processing, control output, and RViz interaction into one runnable parking stack.</li>
    <li>The localization bridge supports identity, initialpose, and reference-odometry alignment modes for adapting FAST-LIO odometry into the Autoware pose path.</li>
    <li>The follower compensates measured actuator delay by integrating predicted pose and velocity before computing tracking error and speed control.</li>
    <li>The demo video shows the parking stack running on the real vehicle.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Implementation Notes</h3>
  <ul>
    <li>The base HVL/Autoware/Ioniq platform remains the vehicle foundation; the parking package is an addon layer, not a replacement stack.</li>
    <li>The default mapping path uses the C++ pointcloud OGM accumulator; the older Python occupancy accumulator remains a fallback path.</li>
    <li>Simulation support remains useful for iteration, but the main claim here is real-vehicle Ioniq integration and validation.</li>
  </ul>
</div>
