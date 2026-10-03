---
layout: single
title: About
permalink: /about/
classes: wide
---

<div class="project-card" style="padding:1.0rem 1.0rem .9rem;">
  <span style="font-size:0.95rem; opacity:0.70;">Ujin Kwon · 권우진</span>
  <p style="margin-top:.45rem;">
    I am a Mechanical & Computer Engineering student focused on <b>optimal control</b>, <b>numerical optimization</b>, and <b>dynamics</b>.
    I build nonlinear solvers, vehicle-autonomy and perception systems, telemetry runtimes, and analysis tools—and validate them with
    measured experiments, field logs, or physical hardware.
  </p>
</div>

<div class="project-card">
  <h3>Education</h3>
  <p>
    <b>Mechanical & Computer Engineering</b><br/>
    Tech University of Korea / 한국공학대학교
  </p>
</div>

<div class="project-card">
  <h3>Research Experience</h3>
  <p>
    <b>Undergraduate Research Intern / Autonomous Driving Team Lead, HuVILab</b><br/>
    <span style="opacity:.72;">Tech University of Korea · 2026–Present</span>
  </p>
  <ul>
    <li>Led integration and real-vehicle validation of <a href="/projects/mapless-autonomous-parking/">mapless reverse parking</a> on a Hyundai Ioniq.</li>
    <li>Developed and evaluated <a href="/projects/monoscale/">learning-free metric visual odometry and dense occupancy</a> using cameras, an IMU, and ground-plane geometry.</li>
    <li>Coordinated localization, mapping, planning, control, simulation, and vehicle-integration work across the undergraduate research team.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Publications</h3>
  <ul>
    <li>
      <b>U. Kwon</b> (sole author), “Auxiliary-Solution-Induced Residual for Nonlinear Iterative Correction with Application to Ballistic Interception,”
      <i>Proc. 2026 ICROS Annual Conference (ICROS 2026)</i>, Daegu, Korea, Jul. 2026, pp. 686–687.
      <span style="opacity:.72;">[보조해 유도 잔차를 이용한 비선형 반복 보정과 탄도 요격 적용]</span>
      <br/><a href="https://www.dbpia.co.kr/journal/articleDetail?nodeId=NODE12952462">DBpia</a> · <a href="/projects/ballistic-solver/">Project page</a> · <a href="https://github.com/ujinf74/ballistic-solver">Code</a>
    </li>
  </ul>
</div>

<div class="project-card">
  <h3>Engineering Experience</h3>
  <ul>
    <li>
      <b>Racing telemetry collaboration with Luxon Racing Team</b><br/>
      Built the <a href="/projects/racing-telemetry-stack/">car-side GNSS/RTK runtime</a> and the
      <a href="/projects/racing-analyze-gui/">desktop analysis workflow</a> used for collection, monitoring, replay, and segment review.
      The team took its first podium during the collaboration: P3 in GT-A (driver Jinwook Choi) at O-NE SUPERRACE Round 5, 2026.
    </li>
    <li>
      <b>Ballistic solver hardware validation</b><br/>
      Integrated the native ARM64 solver on a Rock 5B with live AprilTag tracking and STM32G431 closed-loop actuator control.
    </li>
  </ul>
</div>

<div class="project-card">
  <h3>Open Source</h3>
  <p>
    <b>Maintainer, Autoware Universe <code>autoware_carla_interface</code></b><br/>
    <span style="opacity:.72;">Autoware Foundation · 2026-10–Present · <a href="https://github.com/autowarefoundation/autoware_universe/pull/13449">#13449</a></span>
  </p>
  <p>Seven merged changes to the package across sensor timing, camera output, simulation noise, capture rate, and timestamp correctness:</p>
  <ul>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13149">#13149</a> — corrected CARLA sensor publish timing at matched rates.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13151">#13151</a> — added configurable camera encoding with a measured 4× payload reduction for <code>mono8</code>.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13154">#13154</a> — added configurable IMU/GNSS noise and bias with backward-compatible defaults.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13407">#13407</a> — aligned CARLA sensor capture and publication rates.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13408">#13408</a> — retained the capture frame and timestamp of each sensor measurement.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13411">#13411</a> — added <code>bgr8</code> camera output with 25% less payload than <code>bgra8</code>.</li>
    <li><a href="https://github.com/autowarefoundation/autoware_universe/pull/13409">#13409</a> — published depth and semantic-segmentation cameras through the existing image path.</li>
  </ul>
  <p>Also submitted measured technical reviews on <a href="https://github.com/autowarefoundation/autoware_universe/pull/13372#pullrequestreview-5325066468">odometry frame consistency</a> and <a href="https://github.com/autowarefoundation/autoware_universe/pull/13433#pullrequestreview-5325138353">initial-pose spawning</a>.</p>
  <a class="btn" href="/contributions/">Merged work, open proposals, and reviews</a>
</div>

<div class="project-card">
  <h3>Leadership & Recognition</h3>
  <ul>
    <li><b>Maintainer</b>, Autoware Universe <code>autoware_carla_interface</code>.</li>
    <li><b>Autonomous Driving Team Lead</b>, HuVILab undergraduate research team.</li>
    <li><b>President</b>, 50-member fashion club.</li>
    <li><b>O-NE SUPERRACE 2026 Round 5, GT-A — P3</b> (Luxon Racing Team, driver Jinwook Choi) — telemetry and analysis collaborator; the team's first podium.</li>
    <li><b>KSAE 2024 Smart e-Mobility Competition, EV Division</b> — Encouragement Prize.</li>
  </ul>
</div>
