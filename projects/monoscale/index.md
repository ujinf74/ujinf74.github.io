---
layout: single
title: "Monoscale Visual Odometry"
permalink: /projects/monoscale/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">ROS 2 · C++/CUDA · Ground-plane geometry · Cameras + IMU</p>
  <p>
    <b>Monoscale</b> is a lightweight, learning-free perception stack that derives metric vehicle motion
    and dense occupancy from one or more cameras, an IMU, known camera mounting height, and the ground plane.
    It does not require stereo, vehicle-mounted LiDAR, a learned model, or a prebuilt map.
  </p>
  <div style="display:flex; gap:.6rem; flex-wrap:wrap; margin-top:.8rem;">
    <a class="btn" href="https://github.com/ujinf74/monoscale">Repo</a>
    <a class="btn" href="/projects/hero/">See the coaching system</a>
    <a class="btn" href="/projects/">Back to Projects</a>
  </div>
</div>

<div class="project-card">
  <h3>Estimation Design</h3>
  <div class="flow-diagram">
    <div class="flow-step"><b>Camera + IMU</b><span>C++ KLT tracks, road-image observations, and inertial measurements</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Separated Estimation</b><span>photometric distance plus anchor-map direction, position correction, roll, and pitch</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Metric Odometry</b><span>ROS 2 kinematic state and ground-point output</span></div>
  </div>
</div>

<div class="project-card">
  <h3>Why The Signals Stay Separate</h3>
  <ul>
    <li><b>Without an anchor match</b>, feature tracking keeps motion direction and the forward/reverse sign while photometric alignment supplies the distance.</li>
    <li><b>With an anchor match</b>, the anchor update is kept intact because it contains both current motion and accumulated position-error correction.</li>
    <li><b>For attitude</b>, roll and pitch are estimated directly from repeated anchor-bearing errors instead of continuously integrating photometric frame-to-frame increments.</li>
    <li>This separation prevents a locally useful distance estimate from overwriting the longer-term correction carried by the anchor map.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Dense Occupancy</h3>
  <p>
    The occupancy path reads the raw fisheye images rather than accumulating sparse feature points.
    It sweeps world-horizontal planes through each pixel, scores photometric agreement with ZNCC,
    aggregates the cost with SGM, and uses the odometry roll/pitch directly in the image warp.
  </p>
  <ul>
    <li><b>Output</b>: a 0.1 m occupancy grid for the parking environment.</li>
    <li><b>Deployment path</b>: C++/CUDA; the recorded CUDA runtime is about 0.2 s per keyframe.</li>
    <li><b>Measured CARLA case</b>: coverage 0.831, false occupied cells 29, and no path ghosts on <code>approach_hd60_occ_b</code>.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Measured Results</h3>
  <table class="result-table">
    <thead>
      <tr><th>Measurement</th><th>Result</th><th>What It Tests</th></tr>
    </thead>
    <tbody>
      <tr><td>Final configuration</td><td>0.0237% mean distance-normalized ATE over 9 CARLA drives</td><td>Combined long-term trajectory accuracy</td></tr>
      <tr><td>Anchor-map attitude disabled</td><td>0.0223% → 0.1114%</td><td>Effect of direct ground-relative roll/pitch estimation on a straight drive</td></tr>
      <tr><td>Photometric distance reapplied during anchor matches</td><td>5 m RTE 0.145% → 0.108%, but best ATE 0.0369% versus 0.0237% baseline</td><td>Short-window distance accuracy versus accumulated trajectory correction</td></tr>
      <tr><td>Photometric pitch/roll increment bias</td><td>up to about 0.038° per frame</td><td>Why continuously integrating the increment is drift-prone</td></tr>
    </tbody>
  </table>
</div>

<div class="project-card">
  <h3>Software Boundaries</h3>
  <ul>
    <li><b>Estimator core</b>: C++ and ROS-independent, so it can be tested without a graph or composed into another process.</li>
    <li><b>Tracking</b>: C++ KLT front end with an optional OpenCV CUDA path.</li>
    <li><b>ROS 2 integration</b>: odometry node, deterministic bag replay, launch and deployment parameters.</li>
    <li><b>Evaluation</b>: CARLA ground truth scoring, held-out runs, and explicit ablations.</li>
    <li><b>Tests</b>: 132 core tests covering geometry, anchors, filtering, inertial processing, attitude, and synthetic-drive estimator behavior.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Validation Scope</h3>
  <ul>
    <li>The trajectory figures above are CARLA measurements under the repository's recorded evaluation conditions.</li>
    <li>The photometric increment is an inter-frame estimate, not an absolute ground attitude measurement.</li>
    <li>The occupancy and odometry paths share camera geometry and pose information but remain separate consumers of the image stream.</li>
  </ul>
</div>
