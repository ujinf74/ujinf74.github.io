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
    The stack uses FAST-LIO odometry, LiDAR-based probabilistic occupancy grids, RViz goal-pose input,
    parking trajectory generation, and Autoware-compatible control commands wired into the Ioniq CAN control path.
  </p>

  <video controls playsinline preload="metadata"
    style="width:100%; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">
    <source src="/assets/videos/real-vehicle_demo.mp4" type="video/mp4">
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
    <div class="flow-step"><b>LiDAR OGM</b><span>pointcloud adaptation, ground filtering, probabilistic occupancy grid</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Goal-Pose Planner</b><span>RViz target pose to parking trajectory without prebuilt maps</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Trajectory Follower</b><span>control, actuation, and gear command topics</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Ioniq CAN Path</b><span>control_converter/control_command to socketcan and can0</span></div>
  </div>
</div>

<div class="project-card">
  <h3>What I Built</h3>
  <ul>
    <li><b>Real-vehicle addon package</b> that layers autonomous parking and FAST-LIO linkage onto the existing HVL/Autoware/Ioniq stack.</li>
    <li><b>FAST-LIO localization bridge</b> that aligns external odometry with the Autoware pose/TF path used by the parking stack.</li>
    <li><b>LiDAR pointcloud adapter and OGM path</b> for probabilistic occupancy-grid generation without prebuilt pointcloud/vector maps.</li>
    <li><b>Parking planner</b> driven by occupancy grid, current pose, and RViz goal pose.</li>
    <li><b>Trajectory resampler / filler / follower</b> that produces Autoware control, actuation, and gear command topics.</li>
    <li><b>Ioniq command keepalive</b> for engage, hazard, and turn-indicator inputs required by the vehicle command converter.</li>
    <li><b>Launch integration</b> that can bring up the Ioniq driver, ros2_socketcan bridge, and CAN interface path around the existing vehicle stack.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Built vs Used</h3>
  <ul>
    <li><b>Used</b>: ROS 2 Humble, Autoware components, FAST-LIO, the existing HVL vehicle stack, and the Ioniq driver/CAN command interface.</li>
    <li><b>Built</b>: localization bridge, compatibility layer, occupancy accumulation path, parking planner integration, trajectory processing nodes, Ioniq command keepalive, RViz control interface, and launch integration.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Result</h3>
  <ul>
    <li>Implemented a mapless parking addon on a real Hyundai Ioniq platform.</li>
    <li>Connected FAST-LIO odometry, LiDAR occupancy mapping, RViz goal input, trajectory following, Autoware command topics, and the Ioniq CAN path.</li>
    <li>Validated low-speed parking execution with stable odometry and vehicle motion.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Evidence</h3>
  <ul>
    <li>Real Hyundai Ioniq parking execution was validated with stable odometry and vehicle motion.</li>
    <li>The launch path wires FAST-LIO odometry, occupancy-grid generation, planner output, trajectory processing, control output, and RViz interaction into one runnable parking stack.</li>
    <li>The control path publishes <code>/control/command/control_cmd</code>, <code>/control/command/actuation_cmd</code>, and <code>/control/command/gear_cmd</code>, then follows the Ioniq <code>control_converter</code> / <code>control_command</code> / CAN interface.</li>
    <li>The demo video shows the parking stack running on the real vehicle.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Implementation Notes</h3>
  <ul>
    <li>The base HVL/Autoware/Ioniq platform remains the vehicle foundation; the parking package is an addon layer, not a replacement stack.</li>
    <li>The default path uses LiDAR pointcloud-based probabilistic occupancy grids. A pose-only straight-line mode exists only for debug and bring-up.</li>
    <li>Simulation support remains useful for iteration, but the main claim here is real-vehicle Ioniq integration and validation.</li>
  </ul>
</div>
