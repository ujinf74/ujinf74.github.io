---
layout: single
title: "Racing Telemetry Stack"
permalink: /projects/racing-telemetry-stack/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Python · Raspberry Pi · u-blox ZED-F9R · RTK/NTRIP · Cloudflare Worker</p>
  <p>
    A <b>car-side telemetry runtime</b> for racing operations: receiver setup, correction ingestion, buffered logging,
    live remote monitoring, and field recovery around unstable serial input and intermittent correction availability.
  </p>

  <div class="flow-diagram" style="margin-top:.8rem;">
    <div class="flow-step"><b>ZED-F9R</b><span>UBX GPS/IMU + RTCM input</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Raspberry Pi Collector</b><span>configure, collect, filter, log, recover</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Cloudflare Worker</b><span>ingest latest debug state</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Browser Monitor</b><span>SSE updates + live map/debug view</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Analysis GUI</b><span>segment-based review after collection</span></div>
  </div>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap; margin-top:.8rem;">
    <a class="btn" href="/projects/">Back to Projects</a>
  </div>
</div>

<div class="project-card">
  <h3>Problem</h3>
  <ul>
    <li>The runtime had to survive real field conditions, not lab-perfect sensor input.</li>
    <li>Correction streams and serial transport could be unstable during operation.</li>
    <li>The team needed both <b>on-car logging</b> and <b>remote visibility</b> without depending on a fragile manual workflow.</li>
  </ul>
</div>

<div class="project-card">
  <h3>What I Built</h3>
  <ul>
    <li><b>Raspberry Pi runtime</b> with systemd-managed startup, environment-based configuration, and automatic restart behavior.</li>
    <li><b>ZED-F9R configuration path</b> for 20 Hz measurement, NAV-PVT, HPPOSLLH, RAWX, ESF-RAW, MON-HW/RF, and RTCM3 input preparation at startup.</li>
    <li><b>RTK correction flow</b> with NTRIP connection, GGA injection, RTCM queueing, retry handling, and fallback behavior.</li>
    <li><b>Buffered logging</b> for date-foldered drive logs, merged GPS/IMU CSV output, and optional raw UBX capture.</li>
    <li><b>Fault handling</b> for idle timeout, invalid GPS jumps, serial retry, PVT timeout handling, and optional receiver reconfiguration.</li>
    <li><b>Remote monitoring path</b> through Cloudflare Worker + Durable Object + SSE for browser-side live debug and mapping.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Operational Result</h3>
  <ul>
    <li><b>20 Hz receiver setup</b> and UBX message configuration run as part of the managed startup path.</li>
    <li><b>Local evidence</b> remains on the car as date-foldered CSV and optional raw UBX logs.</li>
    <li><b>Remote evidence</b> exposes correction, GPS, serial, and timeout state through the browser monitor.</li>
    <li><b>Downstream use</b> connects the collected logs directly to the <a href="/projects/racing-analyze-gui/">Racing Analyze GUI</a>.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Validation Scope</h3>
  <ul>
    <li>The verified scope is the implemented device-to-log-to-monitor path and its recovery behavior.</li>
    <li>No statistical uptime or positioning-accuracy claim is made without a dedicated field dataset.</li>
  </ul>
</div>
