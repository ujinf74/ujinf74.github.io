---
layout: single
title: "Open Source Contributions"
permalink: /contributions/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">External pull requests · Current status</p>
  <p>
    Three changes have been reviewed and merged into Autoware Universe. Three additional proposals remain open
    and are listed separately; an open proposal is not presented as accepted upstream work.
  </p>
</div>

<h2>Merged Upstream</h2>

<div class="project-card">
  <h3>Correct CARLA Sensor Publish Timing</h3>
  <p>
    Fixed a floating-point boundary comparison that dropped frames when the configured CARLA publication rate
    matched the sensor rate. A small absolute tolerance preserves genuinely early-frame rejection while allowing
    equal-period frames through.
  </p>
  <ul>
    <li><b>Measured reproduction</b>: 20 Hz and 10 Hz cases improved from 134/200 published frames to 200/200.</li>
    <li><b>Interface impact</b>: none; the correction changes only the period comparison.</li>
    <li><b>Status</b>: approved, CI-validated, and merged upstream.</li>
  </ul>
  <a class="btn" href="https://github.com/autowarefoundation/autoware_universe/pull/13149">View merged PR #13149</a>
</div>

<div class="project-card">
  <h3>Configurable CARLA Camera Encoding</h3>
  <p>
    Added a configurable image encoding path to the CARLA camera interface so luminance-only consumers can request
    <code>mono8</code> instead of always transporting <code>bgra8</code>. The original encoding remains the default.
  </p>
  <ul>
    <li><b>Measured payload</b>: 2,073,672 bytes → 518,472 bytes at 960×540.</li>
    <li><b>Effect</b>: exactly 4× less serialized image payload for the mono8 path.</li>
    <li><b>Compatibility</b>: existing configurations keep their previous output unless the new option is selected.</li>
  </ul>
  <a class="btn" href="https://github.com/autowarefoundation/autoware_universe/pull/13151">View merged PR #13151</a>
</div>

<div class="project-card">
  <h3>Configurable IMU and GNSS Noise</h3>
  <p>
    Replaced the CARLA interface's zero-only sensor-noise behavior with configurable IMU/GNSS noise and bias
    parameters while keeping zero-valued defaults for compatibility.
  </p>
  <ul>
    <li>Added configurable noise and bias parameters for simulation and integration testing.</li>
    <li>Used attribute guards so the interface remains compatible across sensor variants.</li>
    <li>Preserved the previous zero-noise behavior as the default configuration.</li>
  </ul>
  <a class="btn" href="https://github.com/autowarefoundation/autoware_universe/pull/13154">View merged PR #13154</a>
</div>

<div class="project-card">
  <h3>Why The Merged Changes Matter</h3>
  <p>
    The changes came from practical integration pressure: sensor timing silently reduced effective rates,
    camera bandwidth affected the vision pipeline, and fixed zero-noise sensors limited realistic evaluation.
    Each local bottleneck became a reusable upstream correction or configuration path.
  </p>
</div>

<h2>Open Proposals</h2>

<div class="project-card">
  <h3>Autoware CARLA Gear Commands</h3>
  <p>
    Adds gear-command subscription, reverse selection, non-driving-gear brake behavior, and gear-status reporting
    to the CARLA vehicle interface. This is needed for reverse-capable maneuvers such as freespace parking.
  </p>
  <div class="proof-callout">
    <b>Open · Review required</b>
    <span>This proposal is not merged and currently requires upstream review and conflict resolution.</span>
  </div>
  <a class="btn" href="https://github.com/autowarefoundation/autoware_universe/pull/13150">View open PR #13150</a>
</div>

<div class="project-card">
  <h3>Normalize Negative Velodyne Point Times</h3>
  <p>
    Proposes shifting centered per-point timestamps to the zero-based sweep offsets expected by Spark FAST-LIO,
    preventing a half-length de-skew and IMU integration interval. The ROS 2 Humble build was checked; full public-sequence validation is not claimed.
  </p>
  <div class="proof-callout">
    <b>Open · Awaiting review</b>
    <span>The branch is reported mergeable, with no upstream review or CI result recorded.</span>
  </div>
  <a class="btn" href="https://github.com/MIT-SPARK/spark-fast-lio/pull/19">View open MIT-SPARK PR #19</a>
</div>

<div class="project-card">
  <h3>Publish Frame-Correct Odometry Twist</h3>
  <p>
    Proposes publishing linear and angular twist in Spark FAST-LIO's configured output frame, including the
    offset-point velocity term and gyro-bias removal. The ROS 2 Humble build was checked; numerical ground-truth validation is not claimed.
  </p>
  <div class="proof-callout">
    <b>Open · Awaiting review</b>
    <span>The branch is reported mergeable, with no upstream review or CI result recorded.</span>
  </div>
  <a class="btn" href="https://github.com/MIT-SPARK/spark-fast-lio/pull/20">View open MIT-SPARK PR #20</a>
</div>
