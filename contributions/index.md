---
layout: single
title: "Autoware Maintainer · Open Source"
permalink: /contributions/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Upstream maintainership, code, and technical review</p>
  <p>
    Maintainer of <b>Autoware Universe <code>autoware_carla_interface</code></b> since 2026-10-01. Seven changes merged into
    the package, five proposals still open across Autoware Universe and Spark FAST-LIO, and two technical reviews on other
    contributors' Autoware PRs.
  </p>
  <p style="opacity:.72; margin-bottom:0;">PR status checked on 2026-10-02.</p>
</div>

<h2>Maintainer · Autoware Universe</h2>

<div class="project-card">
  <h3><code>autoware_carla_interface</code> <small style="opacity:.7;">CARLA ↔ Autoware bridge · 2026-10-01–present</small></h3>
  <p>
    Listed as a package maintainer in <code>simulator/autoware_carla_interface/package.xml</code>
    (<a href="https://github.com/autowarefoundation/autoware_universe/pull/13449">#13449</a>), alongside the TIER IV maintainers.
    The role followed seven merged changes to the package's sensor timing, capture-rate, timestamp, camera-output, and noise paths.
  </p>
  <div class="result-strip">
    <span>Package maintainer</span>
    <span>7 merged changes</span>
    <span>3 open interface proposals</span>
  </div>
</div>

<h2>Path to Maintainer · Merged Changes</h2>

<div class="project-card">
  <ul>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13149">#13149 · Sensor publish timing</a> — corrected a floating-point boundary that dropped equal-period frames; the measured 20 Hz and 10 Hz cases went from 134/200 to 200/200 published frames.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13151">#13151 · Mono camera output</a> — made <code>mono8</code> selectable while retaining the original default; serialized image payload was 4× smaller at 960×540.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13154">#13154 · IMU/GNSS noise</a> — added configurable noise and bias parameters with zero-valued defaults.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13407">#13407 · Sensor capture rate</a> — let a mapping set CARLA's <code>sensor_tick</code> and aligned the publish throttle; a requested 25 Hz camera measured 24.95 Hz, up from 19.92 Hz.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13408">#13408 · Capture-frame timestamps</a> — preserved each measurement's CARLA frame through publication, avoiding overwritten measurements and late-callback timestamps.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13411">#13411 · BGR camera output</a> — added selectable <code>bgr8</code> output, removing the unused alpha channel and reducing color-image payload by 25%.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13409">#13409 · All camera types</a> — matched every <code>sensor.camera.*</code> blueprint in publisher creation and dispatch, so depth and semantic-segmentation cameras publish image and camera-info streams instead of being dropped.</li>
  </ul>
</div>

<h2>Open Proposals</h2>

<div class="project-card">
  <h3>Autoware Universe</h3>
  <ul>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13150">#13150 · Gear commands</a> — reverse selection, non-driving-gear braking, and gear-status reporting for the CARLA vehicle interface.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13406">#13406 · Physics substeps</a> — proposes a bounded CARLA substep to reduce disagreement between reported angular velocity and vehicle rotation.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13410">#13410 · External ego attachment</a> — proposes attaching sensors to a vehicle owned and driven by another CARLA client.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Spark FAST-LIO</h3>
  <ul>
    <li><a href="https://github.com/MIT-SPARK/spark-fast-lio/pull/19">#19 · Velodyne point times</a> — proposes normalizing centered point timestamps to zero-based sweep offsets.</li>
    <li><a href="https://github.com/MIT-SPARK/spark-fast-lio/pull/20">#20 · Odometry twist</a> — proposes publishing frame-correct linear and angular velocity, including the offset-point term.</li>
  </ul>
  <p>Both Spark FAST-LIO branches were built on ROS 2 Humble; full public-sequence or numerical ground-truth validation is not claimed.</p>
</div>

<h2>Technical Reviews</h2>

<div class="project-card">
  <ul>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13372#pullrequestreview-5325066468">#13372 · Ego pose at <code>base_link</code></a> — measured a turning-case mismatch between the shifted pose and odometry twist, including 0.6993 m/s RMS lateral-velocity error, and suggested a follow-up correction.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13433#pullrequestreview-5325138353">#13433 · Initial-pose spawning</a> <small style="opacity:.7;">(since merged)</small> — checked the pose subscription path and reproduced a spawn-height failure mode with ground snapping disabled; requested validation on a higher-terrain map for the realistic RViz case.</li>
  </ul>
  <p>These were submitted as comment reviews before the maintainer role; neither is represented as an approval, and #13433's merge is the author's change, not mine.</p>
</div>
