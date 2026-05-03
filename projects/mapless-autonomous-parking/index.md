---
layout: single
title: "Mapless Autonomous Parking"
permalink: /projects/mapless-autonomous-parking/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Isaac Sim · ROS 2 Humble · Autoware Universe · HuVILab</p>
  <p>
    This project targets <b>real-time parking without prebuilt pointcloud/vector maps</b>.
    The stack builds local occupancy information online, plans parking motion from occupancy-only inputs, and executes low-speed forward/reverse maneuvers through a custom addon layer on top of an existing vehicle stack.
  </p>

  <video controls playsinline preload="metadata"
    style="width:100%; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">
    <source src="/assets/videos/autopark_demo.mp4" type="video/mp4">
  </video>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap; margin-top:.8rem;">
    <a class="btn" href="/projects/">Back to Projects</a>
  </div>
</div>

<div class="project-card">
  <h3>Problem</h3>
  <ul>
    <li>No prebuilt parking map available.</li>
    <li>The addon had to fit around an existing vehicle/control stack instead of replacing the whole system.</li>
    <li>Parking had to work under low-speed, reverse-capable, compute-bounded conditions with practical ROS 2 timing and visualization needs.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Architecture</h3>
  <div class="flow-diagram">
    <div class="flow-step"><b>Perception Adapter</b><span>pointcloud field/frame adaptation for occupancy-grid input</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>OGM Layer</b><span>occupancy accumulation, ROI handling, decay for stale cells</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Planner</b><span>occupancy-only parking trajectory generation</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Trajectory Processing</b><span>resampler, filler, direction-aware preparation</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Follower + UI</b><span>parking tracking, RViz control, CLI/RViz debug</span></div>
  </div>
</div>

<div class="project-card">
  <h3>What I Built</h3>
  <ul>
    <li><b>Addon package composition</b> that layers autonomous parking and FAST_LIO linkage onto an existing validated stack.</li>
    <li><b>Pointcloud adapter</b> to make LiDAR data usable by the occupancy-grid path.</li>
    <li><b>OGM accumulator</b> for occupancy-map accumulation and post-processing.</li>
    <li><b>Parking planner</b> driven by occupancy grid, current pose, and goal pose.</li>
    <li><b>Trajectory resampler / filler / follower</b> for parking-specific post-processing and execution.</li>
    <li><b>RViz control path</b> with interactive-marker-based enable/cancel UI.</li>
    <li><b>ROS 2 integration work</b> including QoS handling, topic alignment, and launch composition around the existing vehicle stack.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Built vs Used</h3>
  <ul>
    <li><b>Used</b>: ROS 2 Humble, Autoware components, Isaac Sim, FAST_LIO-linked localization path, existing vehicle/control stack.</li>
    <li><b>Built</b>: compatibility layer, occupancy accumulation path, parking planner integration, trajectory processing nodes, parking follower path, RViz control interface, launch integration.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Evidence</h3>
  <ul>
    <li>The addon package explicitly separates its scope from the base vehicle/control stack and documents the nodes it adds.</li>
    <li>The launch path wires occupancy-grid generation, planner output, trajectory processing, follower integration, and RViz interaction into one runnable parking stack.</li>
    <li>The public portfolio now shows the parking video directly so the project is not just described as text.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Current Limits</h3>
  <ul>
    <li>This page does not yet publish a public repo or rosgraph-level artifact, so the strongest proof remains the architecture summary and demo video.</li>
    <li>I am describing the control layer conservatively here as a <b>parking follower path</b> rather than over-claiming a single named controller variant.</li>
  </ul>
</div>
