---
layout: single
title: "Open Source Contributions"
permalink: /contributions/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Merged upstream work · Autoware Universe</p>
  <p>
    Contributions made while integrating CARLA-based vehicle and perception workflows. Both changes were reviewed
    and merged upstream, with existing behavior preserved by default.
  </p>
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
  <h3>Why These Changes Matter</h3>
  <p>
    The changes came from practical integration pressure: camera bandwidth affected the vision pipeline, while
    configurable sensor noise was needed for realistic evaluation. They turn local workarounds into reusable,
    backward-compatible upstream capabilities.
  </p>
</div>
