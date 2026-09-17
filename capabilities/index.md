---
layout: single
title: "Capabilities"
permalink: /capabilities/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Capability to evidence</p>
  <p>
    Each capability below points to the project that demonstrates it most directly. The detailed pages carry the
    measurements, implementation boundaries, and validation limits.
  </p>
</div>

<div class="project-card">
  <h3>Capability Matrix</h3>
  <table class="result-table capability-table">
    <thead>
      <tr><th>Capability</th><th>What Shows It</th><th>Main Evidence</th></tr>
    </thead>
    <tbody>
      <tr>
        <td>Mathematical modeling</td>
        <td>Physical dynamics, coordinate residuals, convergence paths, and explicit numerical diagnostics</td>
        <td><a href="/projects/ballistic-solver/">ballistic-solver</a></td>
      </tr>
      <tr>
        <td>API and deployability</td>
        <td>Modern C++ API, C ABI, Python/PyPI, Unity/C#, Godot, and ARM64 hardware integration</td>
        <td><a href="/projects/ballistic-solver/">ballistic-solver</a></td>
      </tr>
      <tr>
        <td>ROS 2 / vehicle autonomy integration</td>
        <td>FAST-LIO bridge, occupancy mapping, planner integration, measured-delay follower, and Ioniq CAN path</td>
        <td><a href="/projects/mapless-autonomous-parking/">Mapless Autonomous Parking</a></td>
      </tr>
      <tr>
        <td>Visual perception</td>
        <td>Metric camera odometry, anchor-map direction/attitude correction, dense occupancy, and CARLA evaluation</td>
        <td><a href="/projects/monoscale/">Monoscale</a></td>
      </tr>
      <tr>
        <td>Operational robustness</td>
        <td>NTRIP handling, serial retry, timeout detection, live monitoring, and remote deployment workflow</td>
        <td><a href="/projects/racing-telemetry-stack/">Racing Telemetry Stack</a></td>
      </tr>
      <tr>
        <td>Data analysis tooling</td>
        <td>Multi-format logs, gate-aligned timing, simulator registration, synchronized media/replay, and report export</td>
        <td><a href="/projects/racing-analyze-gui/">Racing Analyze GUI</a></td>
      </tr>
      <tr>
        <td>Open-source collaboration</td>
        <td>Reviewed upstream changes with measured impact and backward-compatible defaults</td>
        <td><a href="/contributions/">Autoware contributions</a></td>
      </tr>
    </tbody>
  </table>
</div>

<div class="project-card">
  <h3>Working Principles</h3>
  <ul>
    <li><b>Model the actual bottleneck</b> before choosing the implementation path.</li>
    <li><b>Make runtime state inspectable</b> through explicit status, logs, plots, replay, or monitoring.</li>
    <li><b>Package useful cores</b> behind stable APIs, launch paths, services, or analysis workflows.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Evidence Map</h3>
  <ul>
    <li><b>Measured behavior</b>: current solver benchmarks, visual-odometry ablations, telemetry regression tests, research comparisons, and camera-payload measurements.</li>
    <li><b>Physical validation</b>: real-vehicle parking and a Rock 5B + STM32 solver integration with live vision input.</li>
    <li><b>Upstream validation</b>: three reviewed and merged Autoware Universe contributions.</li>
    <li><b>Operational tooling</b>: logs, monitoring, replay, and analysis interfaces that make field behavior inspectable.</li>
  </ul>
</div>
