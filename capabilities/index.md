---
layout: single
title: "Capabilities"
permalink: /capabilities/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">How The Work Reads Technically</p>
  <p>
    The recurring pattern across the work is direct:
    define a hard physical or runtime problem, model it precisely, make it run, and expose enough diagnostics to debug it in practice.
  </p>
</div>

<div class="project-card">
  <h3>Primary Signals</h3>
  <div class="mini-grid">
    <div class="mini-card">
      <div class="mini-kicker">Applied Algorithms</div>
      <p>Nonlinear solver design, RK4 integration, auxiliary residual construction, damping, convergence handling, and benchmark-minded implementation.</p>
      <a class="btn" href="/projects/ballistic-solver/">Seen in ballistic-solver</a>
    </div>
    <div class="mini-card">
      <div class="mini-kicker">Vehicle Integration</div>
      <p>Bridging odometry, perception, planning, control messages, launch composition, and Ioniq CAN-facing tooling into one validated parking stack.</p>
      <a class="btn" href="/projects/mapless-autonomous-parking/">Seen in autonomous parking</a>
    </div>
    <div class="mini-card">
      <div class="mini-kicker">Field Operations</div>
      <p>Serial transport, GNSS/RTK correction flow, buffered logging, watchdog-style recovery, and remote visibility under unstable conditions.</p>
      <a class="btn" href="/projects/racing-telemetry-stack/">Seen in telemetry runtime</a>
    </div>
    <div class="mini-card">
      <div class="mini-kicker">Tool Building</div>
      <p>Turning raw operational data into segment-aware analysis, replay, metrics, and inspectable multi-pane workflows.</p>
      <a class="btn" href="/projects/racing-analyze-gui/">Seen in analysis GUI</a>
    </div>
  </div>
</div>

<div class="project-card">
  <h3>Capability Matrix</h3>
  <table class="result-table">
    <thead>
      <tr>
        <th>Capability</th>
        <th>What Shows It</th>
        <th>Main Evidence</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Mathematical modeling</td>
        <td>Turning physical behavior into a solvable computational model and residual formulation</td>
        <td><a href="/projects/ballistic-solver/">ballistic-solver</a></td>
      </tr>
      <tr>
        <td>API and deployability</td>
        <td>C ABI, Python package, Unity/C# interoperability, explicit status outputs</td>
        <td><a href="/projects/ballistic-solver/">ballistic-solver</a></td>
      </tr>
      <tr>
        <td>ROS 2 / vehicle autonomy integration</td>
        <td>FAST-LIO bridge, occupancy flow, planner wiring, Autoware command topics, Ioniq CAN path, RViz control</td>
        <td><a href="/projects/mapless-autonomous-parking/">Mapless Autonomous Parking</a></td>
      </tr>
      <tr>
        <td>Operational robustness</td>
        <td>NTRIP handling, serial retry, timeout detection, live monitoring, remote deployment workflow</td>
        <td><a href="/projects/racing-telemetry-stack/">Racing Telemetry Stack</a></td>
      </tr>
      <tr>
        <td>Data analysis tooling</td>
        <td>Track-core build, segment slicing, synchronized replay, pane-aware visual inspection</td>
        <td><a href="/projects/racing-analyze-gui/">Racing Analyze GUI</a></td>
      </tr>
      <tr>
        <td>Cross-domain synthesis</td>
        <td>Collection → monitoring → analysis, or simulation → solver → packaging</td>
        <td><a href="/projects/">Projects overview</a></td>
      </tr>
    </tbody>
  </table>
</div>

<div class="project-card">
  <h3>How I Tend To Work</h3>
  <ul>
    <li><b>Problem first</b>: I usually start from an engineering bottleneck rather than a technology checklist.</li>
    <li><b>Runtime matters</b>: I care whether a thing can actually run, fail visibly, recover, and be inspected afterward.</li>
    <li><b>Diagnostics matter</b>: explicit statuses, replayable logs, plots, debug streams, and operational visibility are recurring themes.</li>
    <li><b>Interfaces matter</b>: I try to package useful cores behind APIs, launch files, services, or analysis workflows rather than leaving them as one-off scripts.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Evidence To Look For</h3>
  <ul>
    <li><b>Measured behavior</b>: solver benchmark tables, regression scripts, and paper-level comparison metrics.</li>
    <li><b>Runtime integration</b>: launch paths, ROS 2 topic contracts, odometry alignment, command outputs, and real-vehicle parking validation.</li>
    <li><b>Operational tooling</b>: logs, monitoring, replay, and analysis interfaces that make field behavior inspectable.</li>
  </ul>
</div>
