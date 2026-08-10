---
layout: single
title: "HERO — Vision-Based Parking Assistance"
permalink: /projects/hero/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">In development · Vision-only parking perception · Low-vision coaching HUD</p>
  <p>
    <b>HERO</b> is a coaching-only parking-assistance project for a Hyundai Ioniq. It combines a camera-only
    perception stack with a driver interface designed around low-vision legibility. Development and measurement
    run in CARLA; the system provides guidance and does not intervene in vehicle control.
  </p>
  <div style="display:flex; gap:.6rem; flex-wrap:wrap; margin-top:.8rem;">
    <a class="btn" href="/projects/">Back to Projects</a>
  </div>
</div>

<div class="project-card">
  <h3>Vision-Only Perception</h3>
  <ul>
    <li><b>Two-camera ground-plane odometry</b> estimates vehicle motion without vehicle-mounted LiDAR.</li>
    <li><b>Plane-sweep dense occupancy</b> reconstructs parking-space geometry in C++/CUDA.</li>
    <li>A reproducible <b>CARLA evaluation harness</b> compares perception output against an Autoware LiDAR reference.</li>
    <li>Measurement outputs are separated from the presentation layer so the perception path can be evaluated independently.</li>
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
    <div class="flow-step"><b>Perception</b><span>ground-plane odometry and dense occupancy</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Coaching State</b><span>parking geometry, gear, stopping, degraded state</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>HUD</b><span>low-vision-oriented Qt presentation</span></div>
  </div>
</div>

<div class="project-card">
  <h3>Engineering Status</h3>
  <p>
    <b>In development.</b> The current implementation includes a reproducible measurement harness,
    scenario-driven HUD states, geometry tests, and visual-acuity simulation outputs for interface review.
  </p>
</div>
