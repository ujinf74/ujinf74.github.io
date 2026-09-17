---
layout: single
title: "HERO — Vision-Based Parking Assistance"
permalink: /projects/hero/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Additional work · In development · Low-vision coaching HUD</p>
  <p>
    <b>HERO</b> is a coaching-only parking-assistance project for a Hyundai Ioniq. It connects the
    <a href="/projects/monoscale/">Monoscale</a> camera-perception stack to a driver interface designed around
    low-vision legibility. The system provides guidance and does not intervene in vehicle control.
  </p>
  <div style="display:flex; gap:.6rem; flex-wrap:wrap; margin-top:.8rem;">
    <a class="btn" href="/projects/">Back to Projects</a>
  </div>
</div>

<div class="project-card">
  <h3>Vision-Only Perception</h3>
  <ul>
    <li><b>Metric ground-plane odometry</b> estimates vehicle motion from one or more cameras and IMU without vehicle-mounted LiDAR.</li>
    <li><b>Plane-sweep dense occupancy</b> reconstructs parking-space geometry from raw fisheye images in C++/CUDA.</li>
    <li>A deterministic <b>CARLA evaluation and replay path</b> measures odometry and occupancy against ground truth.</li>
    <li>The perception implementation and measurements are documented separately on the <a href="/projects/monoscale/">Monoscale project page</a>.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Low-Vision Coaching HUD</h3>
  <ul>
    <li><b>Angular legibility budgets</b> connect display geometry to the driver's usable visual angle.</li>
    <li>Guidance includes a parking corridor, stop line, gear state, and explicit degraded-state messaging.</li>
    <li>ROS 2 coaching logic is separated from the Qt presentation layer.</li>
    <li>The current geometry layer includes <b>26 tests</b> for display and guidance calculations.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Architecture</h3>
  <div class="flow-diagram">
    <div class="flow-step"><b>Cameras</b><span>dual-view CARLA image streams</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Monoscale</b><span>metric ground-plane odometry and dense occupancy</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Coaching State</b><span>parking geometry, gear, stopping, degraded state</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>HUD</b><span>low-vision-oriented Qt presentation</span></div>
  </div>
</div>

<div class="project-card">
  <h3>Engineering Status</h3>
  <p>
    <b>Exploratory and in development.</b> The current implementation includes scenario-driven HUD states,
    geometry tests, and visual-acuity simulation outputs for interface review. It is retained as supporting work rather than a representative project.
  </p>
</div>
