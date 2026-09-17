---
layout: single
title: "Racing Analyze GUI"
permalink: /projects/racing-analyze-gui/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Python · PySide6 · Multi-log telemetry analysis · Windows/Linux</p>
  <p>
    <b>Racing Analyze GUI</b> is a packaged desktop workbench for loading multiple runs,
    aligning them to the same track gates, replaying data and media together, and extracting metrics for coaching-oriented review.
  </p>

  <img src="/assets/images/racing_analyze_gui_2026.png" alt="PySide6 racing telemetry workspace with time-series plots, GG diagram, track map, and synchronized onboard video" loading="lazy" decoding="async"
    style="width:100%; aspect-ratio:2048/1049; object-fit:cover; object-position:center bottom; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">
  <p style="margin:.65rem 0 0; opacity:.72; font-size:.9em;">
    Current PySide6 workspace: multi-log time series, GG analysis, track map, and synchronized onboard video.
  </p>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap; margin-top:.8rem;">
    <a class="btn" href="/projects/">Back to Projects</a>
  </div>
</div>

<div class="project-card">
  <h3>Workflow</h3>
  <div class="flow-diagram">
    <div class="flow-step"><b>Track Definition</b><span>start line and segment gates in one reusable track file</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Log Load</b><span>CSV, MoTeC LD, GPS, and simulator-coordinate runs</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Gate Alignment</b><span>interpolated lap and segment boundaries between samples</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Replay + Plots</b><span>XY, TS, MAP, POLAR, KDE, GG, and synchronized media</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Report</b><span>metrics, time-loss decomposition, and CSV export</span></div>
  </div>
</div>

<div class="project-card">
  <h3>What I Built</h3>
  <ul>
    <li><b>Physical gate alignment</b> that interpolates each crossing between samples and applies the same boundary to timing, arrays, maps, replay markers, and video.</li>
    <li><b>Multi-log loading and caching</b> for quick switching after one analysis pass, with configurable sampling rate for large sessions.</li>
    <li><b>Synchronized replay and media</b> with time controls, pane-aware markers, recording-time estimation, and manual offset correction.</li>
    <li><b>Flexible pane system</b> with XY, TS, MAP, POLAR, KDE, GG, and MEDIA views plus split, swap, pop-out, and undo operations.</li>
    <li><b>Channel-flexible visualization</b> where arbitrary logged channels can be assigned to axes or color.</li>
    <li><b>Simulator-to-track registration</b> that aligns planar simulator logs to real GPS tracks with rotation, translation, reflection checks, and residual diagnostics.</li>
    <li><b>Metrics and report export</b> for segment time, speed and acceleration statistics, time-loss attribution, and selected-run comparison.</li>
    <li><b>Desktop and headless use</b> through Windows/Linux build paths, a CLI, and a UI-independent Python analysis session.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Measured Behavior</h3>
  <ul>
    <li><b>Sampling-rate-independent timing</b>: a measured segment that differed at 100 Hz and 10 Hz becomes 7.805 s at both rates when gate interpolation is enabled.</li>
    <li><b>Memory scaling</b>: on a 169-channel, 59-minute MoTeC export, 25 Hz used 108 MB versus 430 MB at 100 Hz while median lap distance changed by 0.3 m.</li>
    <li><b>Faster log parsing</b>: documented port measurements reduced MoTeC CSV reading from 88 ms to 8 ms on the benchmark fixture.</li>
    <li><b>Automated checks</b>: 699 unit tests and 533 integration tests cover analysis behavior and the Qt workflow.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Result</h3>
  <ul>
    <li>Maintains desktop build paths for Windows and Linux, with CLI and library access for automation.</li>
    <li>Made lap timing, plotted slices, map traces, replay markers, and media share the same gate-crossing convention.</li>
    <li>Connected real and simulator logs through a common track and analysis workflow.</li>
    <li>Kept the analysis core independent of the UI so the same workflow can run headlessly.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Evidence</h3>
  <ul>
    <li>The application handles four log families through one analysis path and checks them with generated equivalent-drive fixtures.</li>
    <li>The 1,232-test suite covers both calculation and Qt interaction paths; command-line smoke checks exercise gates, loss analysis, reports, and log inspection.</li>
    <li>The workflow is connected upstream to the <a href="/projects/racing-telemetry-stack/">Racing Telemetry Stack</a>, so this page describes the analysis side of the same field system.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Validation Scope</h3>
  <ul>
    <li>The performance figures above are repository-recorded measurements for specified fixtures and machines, not universal runtime guarantees.</li>
    <li>Simulator registration reports residual and scale diagnostics because a mathematically valid fit can still pair the wrong axes or laps.</li>
  </ul>
</div>
