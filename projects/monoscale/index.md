---
layout: single
title: "Monoscale Visual Odometry"
permalink: /projects/monoscale/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">ROS 2 · C++17/CUDA · Ground-plane geometry · Cameras + IMU</p>
  <p>
    <b>Monoscale</b> turns ordinary monocular cameras into a <b>metric</b> odometry and occupancy stack.
    It takes scale from the one distance a road vehicle already knows — <b>the height of the camera above the road</b>.
  </p>
  <p>
    No stereo pair, no LiDAR in the loop, no learned model, no prior map, no wheel encoder. One camera is enough,
    any number is allowed, and they do not need to overlap: the development rig's two cameras face opposite ways
    and share no field of view.
  </p>
  <div class="result-strip">
    <span>0.182% ATE on a 5.2 km real drive (held out)</span>
    <span>26 mm ATE over 111 m in CARLA</span>
    <span>Nothing added to the vehicle</span>
  </div>
  <img src="/assets/images/monoscale_trajectories.png" alt="Monoscale estimate against ground truth on the CARLA slalom and the held-out parking manoeuvre" loading="lazy" decoding="async"
    style="width:100%; border-radius:18px; margin-top:.8rem; border:1px solid rgba(255,255,255,.14); background:#fff;">
  <p style="margin:.55rem 0 0; opacity:.72; font-size:.9em;">Estimate against ground truth: CARLA slalom and held-out parking manoeuvre, with a zoomed panel and scale bar.</p>
  <div style="display:flex; gap:.6rem; flex-wrap:wrap; margin-top:.8rem;">
    <a class="btn" href="https://github.com/ujinf74/monoscale">Repo</a>
    <a class="btn" href="/projects/">Back to Projects</a>
  </div>
</div>

<div class="project-card">
  <h3>Where It Is Meant to Run</h3>
  <p>
    Where GNSS does not reach and the vehicle moves slowly — indoor parking structures, loading yards, the last
    thirty metres of an automated park. The rig is the surround-view camera set a production car already carries,
    so <b>nothing has to be added to the vehicle</b> to make those cameras metric. Accuracy scales with camera height
    over distance travelled per frame, so low and slow is its best regime — the opposite of what a stereo baseline prefers.
  </p>
</div>

<div class="project-card">
  <h3>Results · Simulation and a Real Vehicle</h3>
  <p>Same code and the same metric definitions in both places; tuned figure first, held-out second.</p>
  <table class="result-table">
    <thead>
      <tr><th></th><th>CARLA, 29–150 m drives</th><th>Ford Multi-AV, 5.2 km</th></tr>
    </thead>
    <tbody>
      <tr><td><b>ATE / distance</b></td><td><b>0.0237%</b> / 0.1781%</td><td>0.451% / <b>0.182%</b></td></tr>
      <tr><td>Final error / distance</td><td>0.0324% / 0.2659%</td><td>0.519% / <b>0.097%</b></td></tr>
      <tr><td>Accumulation over a random walk (<code>walk</code>)</td><td>1.10 / 0.76</td><td>5.07 / <b>1.15</b></td></tr>
    </tbody>
  </table>
  <ul>
    <li><b>In millimetres:</b> 26 mm of ATE over a 111 m simulated drive, and 9.5 m over a 5.2 km real drive that ends 5.1 m from the true end point.</li>
    <li><b>What transferred from simulation to the vehicle</b> is accumulation — the hard half of odometry — at 1.15 held out against 1.10 and 0.76 in CARLA.</li>
    <li><b>Held-out discipline:</b> two CARLA parking drives and one Ford log are never used for tuning. In one week they rejected four changes that had won on the tuning set.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Why Scale from the Ground Plane</h3>
  <table class="result-table">
    <thead>
      <tr><th>Scale source</th><th>No extra hardware</th><th>Needs no excitation</th><th>Metric without initialisation</th><th>Needs no prior map</th></tr>
    </thead>
    <tbody>
      <tr><td>Stereo baseline</td><td>✗</td><td>◎</td><td>◎</td><td>◎</td></tr>
      <tr><td>LiDAR</td><td>✗</td><td>◎</td><td>◎</td><td>◎</td></tr>
      <tr><td>IMU-only excitation</td><td>◎</td><td>✗</td><td>✗</td><td>◎</td></tr>
      <tr><td>Learned monocular depth</td><td>◎</td><td>◎</td><td>○</td><td>◎</td></tr>
      <tr><td>Prior map / HD map</td><td>◎</td><td>◎</td><td>◎</td><td>✗</td></tr>
      <tr><td><b>Ground plane (Monoscale)</b></td><td><b>◎</b></td><td><b>◎</b></td><td><b>◎</b></td><td><b>◎</b></td></tr>
    </tbody>
  </table>
  <p>
    A plane-induced homography between two frames recovers <code>t/h</code>, and <code>h</code> is the mounting height —
    so the answer is metric without anything else on the vehicle measuring length. What it needs instead is texture on the road.
  </p>
</div>

<div class="project-card">
  <h3>Key Properties</h3>
  <ul>
    <li><b>Metric scale from mounting height alone</b> — no baseline, no range sensor.</li>
    <li><b>Non-overlapping cameras</b> — on the development rig they cannot overlap (40.53° of gap per side).</li>
    <li><b>One camera is a supported rig</b>, not a degenerate case: it costs a factor of 2.6–6.2 and still solves every drive.</li>
    <li><b>Any number of cameras</b>, each contributing its own ground observation and anchor map.</li>
    <li><b>Self-contained heading</b> integrated from the gyro; dead reckoning through a failed solve follows the gyro's arc.</li>
    <li><b>Anchor map</b> of ground sightings bounds the random walk over 1,600 frames.</li>
    <li><b>Every deployed constant carries the measurement that chose it</b>, and the alternatives it rejected.</li>
  </ul>
</div>

<div class="project-card">
  <h3>How It Works</h3>
  <div class="flow-diagram">
    <div class="flow-step"><b>KLT Tracker</b><span>images → feature tracks; the estimator never sees a frame</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Ground Projection</b><span>tracks in a distance band projected onto the road plane by height and tilt</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Hop + Photometric</b><span>robust translation vote, blended with road-texture alignment; heading from the gyro</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Anchor Map + Filter</b><span>pose correction against earlier ground sightings, cameras fused, inertial propagation</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>ROS 2 Output</b><span>kinematic state and ground points</span></div>
  </div>
</div>

<div class="project-card">
  <h3>Dense Occupancy from the Same Cameras</h3>
  <p>
    The occupancy path reads the raw fisheye frames rather than accumulating sparse features. World-horizontal planes are
    swept through each pixel, scored by ZNCC, and aggregated with SGM into a surface height, using the attitude the odometry publishes.
  </p>
  <img src="/assets/images/monoscale_occupancy.png" alt="Scored occupancy grid of a CARLA parking scene" loading="lazy" decoding="async"
    style="width:100%; max-width:640px; display:block; margin:.6rem auto 0; border-radius:14px; border:1px solid rgba(255,255,255,.14);">
  <ul>
    <li><b>Output:</b> 60 × 60 m grid at 0.1 m resolution.</li>
    <li><b>Runtime:</b> 34 ms per keyframe on CUDA, both cameras counted.</li>
    <li><b>Scored against truth</b> (<code>approach_hd60_occ_b</code>): no vehicle cell called free, coverage 0.831, 29 false occupied cells, zero path ghosts.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Software Architecture</h3>
  <ul>
    <li><b>Estimator core</b>: C++ and ROS-independent, tested without a graph and ready to share a process with a controller.</li>
    <li><b>Tracking</b>: C++ KLT front end with an optional OpenCV CUDA path.</li>
    <li><b>ROS 2 integration</b>: odometry node and <code>monoscale_replay</code>, which scores a bag directly.</li>
    <li><b>Evaluation</b>: ground-truth scoring for CARLA and the Ford Multi-AV dataset, held-out drives, explicit ablations.</li>
    <li><b>Tests</b>: 149 tests across geometry, anchors, filtering, inertial processing, and synthetic-drive behavior.</li>
  </ul>
</div>
