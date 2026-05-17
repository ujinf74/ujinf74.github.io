---
layout: single
title: "Racing Analyze GUI"
permalink: /projects/racing-analyze-gui/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">MATLAB · Multi-log telemetry analysis · Replay · Segment metrics</p>
  <p>
    <b>Racing Analyze GUI</b> is a segment-based telemetry workbench for loading multiple runs,
    comparing the same track region across runs, replaying them in time, and extracting metrics for coaching-oriented review.
  </p>

  <img src="/assets/images/racing_analyze_gui.png" alt="Racing Analyze GUI"
    style="width:100%; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">

  <div style="display:flex; gap:.6rem; flex-wrap:wrap; margin-top:.8rem;">
    <a class="btn" href="/projects/">Back to Projects</a>
  </div>
</div>

<div class="project-card">
  <h3>Workflow</h3>
  <div class="flow-diagram">
    <div class="flow-step"><b>Track Build</b><span>reference core + segment definition from a track file</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Log Load</b><span>scan root folders, filter includes, cache selected runs</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Segment Slice</b><span>All, S0, S1..Sn, S(n+1)</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Replay + Plots</b><span>XY, TS, MAP, POLAR, KDE, GG with synchronized replay</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Metrics</b><span>segment time, speed stats, acceleration indicators</span></div>
  </div>
</div>

<div class="project-card">
  <h3>What I Built</h3>
  <ul>
    <li><b>Track-core and segment workflow</b> so repeated runs can be compared against the same reference structure.</li>
    <li><b>Multi-log loading and caching</b> for quick switching after one analysis pass.</li>
    <li><b>Synchronized replay system</b> with time slider, play/pause/stop, speed control, and pane-aware markers.</li>
    <li><b>Flexible pane system</b> with XY, TS, MAP, POLAR, KDE, and GG views plus per-pane rerender/pop-out tools.</li>
    <li><b>Channel-flexible visualization</b> where arbitrary logged channels can be assigned to axes or color.</li>
    <li><b>Metrics extraction</b> for segment time, speed statistics, and acceleration-related indicators.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Metrics Exposed In The App</h3>
  <ul>
    <li><b>segTime</b>: selected-segment time</li>
    <li><b>vmin / vmean / vmax</b>: speed min / mean / max</li>
    <li><b>vin / vout</b>: speed at segment entry / exit</li>
    <li><b>arms / a95 / amax</b>: acceleration magnitude statistics for quick comparison</li>
  </ul>
</div>

<div class="project-card">
  <h3>Result</h3>
  <ul>
    <li>Built a reusable telemetry inspection workflow around track segments, replay, and multi-run comparison.</li>
    <li>Implemented pane state, replay control, flexible channel mapping, and segment metrics as UI features.</li>
    <li>Connected the analysis workflow to the same racing telemetry data collection path.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Evidence</h3>
  <ul>
    <li>The GUI is structured as a workbench: track build, run caching, segment slicing, replay, plots, and metrics are separate steps in one flow.</li>
    <li>The app supports multiple analysis views and pane-level tools, which is stronger evidence of repeated real use than a single static screenshot.</li>
    <li>The telemetry workflow is connected upstream to the <a href="/projects/racing-telemetry-stack/">Racing Telemetry Stack</a>, so this page describes the analysis side of the same system.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Validation Scope</h3>
  <ul>
    <li>This page focuses on implemented UI behavior, replay workflow, and exposed segment metrics.</li>
    <li>The strongest evidence is the reusable analysis workflow: track build, multi-run loading, synchronized replay, flexible plots, and metrics extraction.</li>
  </ul>
</div>
