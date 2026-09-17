---
layout: single
title: "Capabilities"
permalink: /capabilities/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Engineering Focus</p>
  <p>
    The projects below share a practical structure: model the physical or runtime problem, implement the working path,
    and leave enough tests, logs, metrics, or interfaces to inspect the result.
  </p>
</div>

<div class="project-card">
  <h3>Technical Areas</h3>
  <div class="mini-grid">
    <div class="mini-card">
      <div class="mini-kicker">Applied Algorithms</div>
      <p>Nonlinear dynamics, coordinate-residual optimization, auxiliary-residual research, convergence handling, and benchmark-minded implementation.</p>
      <a class="btn" href="/projects/ballistic-solver/">Seen in ballistic-solver</a>
    </div>
    <div class="mini-card">
      <div class="mini-kicker">Vehicle Integration</div>
      <p>FAST-LIO odometry, C++ occupancy mapping, parking planning, measured-delay control, and Ioniq CAN-facing execution in one validated vehicle system.</p>
      <a class="btn" href="/projects/mapless-autonomous-parking/">Seen in autonomous parking</a>
    </div>
    <div class="mini-card">
      <div class="mini-kicker">Vision + Automotive HMI</div>
      <p>Ground-plane metric odometry, anchor-map correction, dense plane-sweep occupancy, and low-vision coaching states.</p>
      <a class="btn" href="/projects/monoscale/">Seen in Monoscale</a>
    </div>
    <div class="mini-card">
      <div class="mini-kicker">Field Operations</div>
      <p>Serial transport, GNSS/RTK correction flow, buffered logging, recovery, and remote visibility under unstable conditions.</p>
      <a class="btn" href="/projects/racing-telemetry-stack/">Seen in telemetry runtime</a>
    </div>
    <div class="mini-card">
      <div class="mini-kicker">Tool Building</div>
      <p>Turning heterogeneous logs into gate-aligned timing, synchronized data/media replay, time-loss analysis, and reproducible reports.</p>
      <a class="btn" href="/projects/racing-analyze-gui/">Seen in analysis GUI</a>
    </div>
    <div class="mini-card">
      <div class="mini-kicker">Upstream Engineering</div>
      <p>Converting integration bottlenecks into reviewed, backward-compatible Autoware Universe changes.</p>
      <a class="btn" href="/contributions/">See merged contributions</a>
    </div>
  </div>
</div>

<div class="project-card">
  <h3>Capability Matrix</h3>
  <table class="result-table">
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
        <td>Vision and driver interface</td>
        <td>Metric camera odometry, anchor-map correction, dense occupancy, CARLA evaluation, and low-vision HUD geometry</td>
        <td><a href="/projects/monoscale/">Monoscale</a> + <a href="/projects/hero/">HERO</a></td>
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
  <h3>How I Tend To Work</h3>
  <ul>
    <li><b>Problem first</b>: I start from the engineering bottleneck before choosing the implementation path.</li>
    <li><b>Runtime matters</b>: implementations should run, fail visibly, recover, and leave inspectable state afterward.</li>
    <li><b>Diagnostics matter</b>: explicit statuses, replayable logs, plots, debug streams, and operational visibility are recurring themes.</li>
    <li><b>Interfaces matter</b>: useful cores are packaged behind APIs, launch files, services, or analysis workflows.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Evidence Map</h3>
  <ul>
    <li><b>Measured behavior</b>: current solver benchmarks, visual-odometry ablations, telemetry regression tests, research comparisons, and camera-payload measurements.</li>
    <li><b>Physical validation</b>: real-vehicle parking and a Rock 5B + STM32 solver integration with live vision input.</li>
    <li><b>Upstream validation</b>: two reviewed and merged Autoware Universe contributions.</li>
    <li><b>Operational tooling</b>: logs, monitoring, replay, and analysis interfaces that make field behavior inspectable.</li>
  </ul>
</div>
