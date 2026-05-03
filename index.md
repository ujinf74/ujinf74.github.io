---
layout: single
title: ∞
permalink: /
classes: wide
---

<div class="project-card" style="padding:1.0rem 1.0rem .9rem;">
  <span style="font-size:0.95rem; opacity:0.70;">Ujin Kwon · 권우진</span>

  <p class="eyebrow" style="margin-top:.35rem;">Numerical solvers, telemetry systems, control, and real-time engineering</p>

  <p style="margin-top:.45rem;">
    Mechanical & Computer Engineering student building <b>numerical solvers</b>, <b>vehicle telemetry tools</b>, <b>control software</b>,
    and <b>analysis workflows</b> for <b>vehicle dynamics</b>, <b>robotics</b>, and <b>autonomous systems</b>.
  </p>

  <p style="opacity:.86; margin-top:.25rem;">
    Interests: <b>Optimal Control</b> · <b>Numerical Optimization</b> · <b>Dynamics</b> · <b>Driving Intelligence</b> · <b>Real-time Systems</b>
  </p>
</div>

<div class="project-card">
  <h3>Highlights</h3>
  <ul>
    <li>
      <b>Award:</b> KSAE 2024 Smart e-Mobility Competition (EV Division) — <i>Encouragement Prize</i> (Honorable Mention)
    </li>
    <li>
      <b>Racing engineering collaboration:</b> built a <b>car-side telemetry runtime</b> with RTK/NTRIP correction, remote browser monitoring,
      and a <b>segment-based telemetry analysis GUI</b> for work with <b>Luxon Racing Team</b> in the <b>GTA class of the O-NE SUPERRACE CHAMPIONSHIP</b>.
    </li>
    <li>
      <b>Featured:</b>
      <a href="https://github.com/ujinf74/ballistic-solver">ballistic-solver</a>
      <span style="opacity:.75;">·</span>
      <a href="/projects/">Mapless Autonomous Parking</a>
      <small style="opacity:.7;">(Isaac Sim · ROS 2 · Autoware)</small>
    </li>
  </ul>
</div>

<div class="project-card">
  <h3>Focus</h3>
  <ul>
    <li><b>Numerical optimization & solvers</b> for nonlinear dynamics (least-squares, damping, diagnostics)</li>
    <li><b>Dynamics-aware planning & control</b> for low-speed vehicle maneuvers and constrained motion</li>
    <li><b>Telemetry collection, monitoring, and analysis</b> for racing operations and driver-performance review</li>
    <li><b>Real-time simulation & integration</b> across C/C++, MATLAB, Python, ROS 2, embedded runtime, and web tooling</li>
  </ul>
</div>

<div class="project-card">
  <h3>Selected Work</h3>
  <ul>
    <li><a href="/projects/ballistic-solver/"><b>ballistic-solver</b></a>: native intercept solver built around RK4 simulation, closest-approach residuals, damped least squares, and deployable C/Python/C# interfaces</li>
    <li><a href="/projects/mapless-autonomous-parking/"><b>Mapless Autonomous Parking</b></a>: occupancy mapping, occupancy-only Hybrid A*, trajectory processing, and low-speed parking without prebuilt maps</li>
    <li><a href="/projects/racing-telemetry-stack/"><b>Racing telemetry stack</b></a>: Raspberry Pi + ZED-F9R runtime with RTK/NTRIP correction, buffered CSV/UBX logging, fault tolerance, and browser-based live monitoring</li>
    <li><a href="/projects/racing-analyze-gui/"><b>Racing Analyze GUI</b></a>: segment-based multi-log comparison, replay, metrics extraction, and flexible telemetry visualization for coaching-oriented review</li>
  </ul>
</div>

<div class="project-card">
  <h3>Proof Points</h3>
  <div class="mini-grid">
    <div class="mini-card">
      <div class="mini-kicker">Deployable Numerics</div>
      <p><b>ballistic-solver</b> ships as a native core with a stable C ABI, PyPI package, and Unity/C# interop, with benchmark numbers and failure status reporting.</p>
      <a class="btn" href="/projects/ballistic-solver/">View details</a>
    </div>
    <div class="mini-card">
      <div class="mini-kicker">Planning + Integration</div>
      <p><b>Mapless Autonomous Parking</b> covers occupancy mapping, planner integration, trajectory processing, QoS tuning, RViz control, and reverse-capable execution.</p>
      <a class="btn" href="/projects/mapless-autonomous-parking/">View details</a>
    </div>
    <div class="mini-card">
      <div class="mini-kicker">Field Runtime</div>
      <p><b>Racing Telemetry Stack</b> handles receiver setup, correction ingestion, buffered logging, live browser monitoring, and recovery under unstable track-side conditions.</p>
      <a class="btn" href="/projects/racing-telemetry-stack/">View details</a>
    </div>
    <div class="mini-card">
      <div class="mini-kicker">Analysis Workflow</div>
      <p><b>Racing Analyze GUI</b> turns raw logs into segment metrics, synchronized replay, and multi-pane inspection for coaching-oriented comparison.</p>
      <a class="btn" href="/projects/racing-analyze-gui/">View details</a>
    </div>
  </div>
</div>
