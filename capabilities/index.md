---
layout: single
title: "Capabilities"
permalink: /capabilities/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">How The Work Reads Technically</p>
  <p>
    This portfolio is strongest when read as a set of <b>ability signals</b>, not just a list of projects.
    Across the repositories, the recurring pattern is the same:
    define a hard problem, model it precisely, make it run, then expose enough diagnostics to debug it in practice.
  </p>
</div>

<div class="project-card">
  <h3>Primary Signals</h3>
  <div class="mini-grid">
    <div class="mini-card">
      <div class="mini-kicker">Numerical Thinking</div>
      <p>Nonlinear solver design, RK4 integration, residual construction, damping, convergence handling, and benchmark-minded implementation.</p>
      <a class="btn" href="/projects/ballistic-solver/">Seen in ballistic-solver</a>
    </div>
    <div class="mini-card">
      <div class="mini-kicker">System Integration</div>
      <p>Bridging perception, planning, control, messages, launch composition, and operator tooling into one working parking stack.</p>
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
        <td>Turning physical behavior into a solvable computational model</td>
        <td><a href="/projects/ballistic-solver/">ballistic-solver</a></td>
      </tr>
      <tr>
        <td>API and deployability</td>
        <td>C ABI, Python package, Unity/C# interoperability, explicit status outputs</td>
        <td><a href="/projects/ballistic-solver/">ballistic-solver</a></td>
      </tr>
      <tr>
        <td>ROS 2 / autonomy integration</td>
        <td>Localization bridge, occupancy flow, planner wiring, follower path, RViz control</td>
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
  <h3>What Is Still Weak</h3>
  <ul>
    <li>Some repos still need stronger test consistency, cleaner artifact separation, and tighter packaging discipline.</li>
    <li>The autonomy and field-runtime work shows strong prototype ability, but not full production safety validation.</li>
    <li>The strongest next step is not more project count; it is denser proof: diagrams, measured regressions, screenshots, and repeatable validation paths.</li>
  </ul>
</div>
