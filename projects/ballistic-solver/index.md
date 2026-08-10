---
layout: single
title: "ballistic-solver"
permalink: /projects/ballistic-solver/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Coordinate-residual solver · Native C++ core · Stable C ABI · Python/PyPI · Unity/C# · Godot</p>
  <p>
    <b>ballistic-solver</b> is a deployable intercept solver for <b>moving targets</b> under <b>gravity</b> and
    <b>quadratic drag</b>, with optional <b>wind</b>. Its current default path minimizes a physical-space
    closest-approach residual; the paper-backed auxiliary residual remains available through <code>solve_aux</code>.
  </p>

  <video controls playsinline preload="metadata"
    style="width:100%; border-radius:18px; margin-top:.6rem; border:1px solid rgba(255,255,255,.14);">
    <source src="/assets/videos/ballistic_demo_low.mp4" type="video/mp4">
  </video>

  <div style="display:flex; gap:.6rem; flex-wrap:wrap; margin-top:.8rem;">
    <a class="btn" href="https://github.com/ujinf74/ballistic-solver">GitHub</a>
    <a class="btn" href="https://pypi.org/project/ballistic-solver/">PyPI</a>
    <a class="btn" href="/projects/">Back to Projects</a>
  </div>
</div>

<div class="project-card">
  <h3>Problem and Current Method</h3>
  <ul>
    <li>Projectile dynamics include <b>quadratic drag</b>, optional <b>wind</b>, and fixed-step RK4 integration.</li>
    <li>The target model supports relative motion, including an extended constant-acceleration target API.</li>
    <li>The default solver minimizes the <b>coordinate-space closest-approach miss vector</b>.</li>
    <li>A vacuum-lead warm start and analytic vacuum Jacobian precondition the first correction.</li>
    <li>Gauss–Newton iterations use Broyden rank-1 Jacobian updates, line search, and multistart fallback.</li>
    <li>Every solve returns an explicit status, diagnostic message, and best result found.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Architecture</h3>
  <div class="flow-diagram">
    <div class="flow-step"><b>Inputs</b><span>target motion, speed, drag, wind, solver parameters</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Simulation</b><span>RK4 projectile integration and closest-approach search</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Residual</b><span>physical-space coordinate miss</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Solve</b><span>Gauss–Newton, Broyden updates, line search, multistart</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Deploy</b><span>C++ API, C ABI, Python, Unity/C#, Godot, edge hardware</span></div>
  </div>
</div>

<div class="project-card">
  <h3>What I Built</h3>
  <ul>
    <li><b>Compiled native C++ core</b> with a modern <code>bs::</code> API for direct C++ use.</li>
    <li><b>Stable C ABI</b> with plain-C data layout for language and runtime bindings.</li>
    <li><b>Python package</b> with presets, utilities, and prebuilt binaries distributed through PyPI.</li>
    <li><b>Unity/C# and Godot integration paths</b> backed by the same native implementation.</li>
    <li><b>Explicit diagnostics</b> for invalid input, numerical failure, rejection, and iteration limits.</li>
    <li><b>Research compatibility</b> through <code>solve_aux</code>, which retains the auxiliary-solution-induced residual method.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Package Benchmarks</h3>
  <p>Current repository benchmark on a local Windows release build over 500 generated linear-target cases:</p>
  <table class="result-table">
    <thead>
      <tr>
        <th>Preset</th>
        <th>Median Solve Time</th>
        <th>P95 Solve Time</th>
        <th>P95 Miss</th>
      </tr>
    </thead>
    <tbody>
      <tr><td>fast</td><td>0.031 ms</td><td>0.131 ms</td><td>2.810e-02 m</td></tr>
      <tr><td>balanced</td><td>0.057 ms</td><td>0.261 ms</td><td>7.053e-03 m</td></tr>
      <tr><td>precise</td><td>0.087 ms</td><td>0.356 ms</td><td>5.596e-06 m</td></tr>
    </tbody>
  </table>
</div>

<div class="project-card">
  <h3>10,000-Case Default-Path Benchmark</h3>
  <table class="result-table">
    <thead>
      <tr>
        <th>Scenario</th>
        <th>Success</th>
        <th>Median Runtime</th>
        <th>P95 Runtime</th>
        <th>P95 Miss</th>
      </tr>
    </thead>
    <tbody>
      <tr><td>Low arc, moving target</td><td>10,000/10,000</td><td>0.089 ms</td><td>0.266 ms</td><td>6.450e-03 m</td></tr>
      <tr><td>High arc, stationary target</td><td>10,000/10,000</td><td>0.408 ms</td><td>0.846 ms</td><td>8.018e-03 m</td></tr>
      <tr><td>High arc, moving target</td><td>10,000/10,000</td><td>0.607 ms</td><td>1.264 ms</td><td>8.341e-03 m</td></tr>
    </tbody>
  </table>
</div>

<div class="project-card">
  <h3>Research Result</h3>
  <p>
    The ICROS 2026 manuscript evaluates the auxiliary residual now retained in <code>solve_aux</code>.
    Under identical outer-iteration settings on 10,000 stationary high-arc cases:
  </p>
  <table class="result-table">
    <thead>
      <tr>
        <th>Method</th>
        <th>Failure Rate</th>
        <th>Mean Runtime</th>
        <th>P95 Miss</th>
      </tr>
    </thead>
    <tbody>
      <tr><td>Direct line-of-sight residual</td><td>50.25%</td><td>6.791 ms</td><td>8.498e+02 m</td></tr>
      <tr><td>Auxiliary-solution-induced residual</td><td>0.00%</td><td>3.748 ms</td><td>8.128e-03 m</td></tr>
    </tbody>
  </table>
</div>

<div class="project-card">
  <h3>Real-Device Validation</h3>
  <p>
    The same native solver was integrated into an edge fire-control prototype to verify that the library works beyond
    desktop benchmarks and game-engine bindings.
  </p>
  <ul>
    <li><b>Rock 5B ARM64</b> runtime using the native solver library.</li>
    <li><b>4K camera at 60 fps</b> with AprilTag-based relative-position tracking.</li>
    <li>Solver output converted into pitch/yaw commands for an <b>STM32G431</b> motion controller.</li>
    <li><b>200 Hz encoder closed-loop control</b> on the embedded controller.</li>
    <li>Measured tracking and calculation path of approximately <b>35.8 ms</b>.</li>
  </ul>
  <div class="proof-callout">
    <b>Validation scope</b>
    <span>Native ARM64 execution, live vision input, solver integration, and closed-loop actuator command delivery on physical hardware.</span>
  </div>
</div>

<div class="project-card">
  <h3>Known Limits</h3>
  <ul>
    <li>The consuming runtime must match the solver's physics and integration assumptions.</li>
    <li>Strongly nonlinear cases remain numerical problems, so convergence depends on conditioning and solver settings.</li>
    <li>Non-converged cases return explicit statuses and the best result found for caller-side handling.</li>
  </ul>
</div>
