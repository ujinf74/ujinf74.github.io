---
layout: single
title: "ballistic-solver"
permalink: /projects/ballistic-solver/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">Auxiliary residual method · C/C++ core · Stable C ABI · Python/PyPI · Unity/C# · Godot/.NET</p>
  <p>
    <b>ballistic-solver</b> is a deployable intercept solver for <b>moving targets</b> under <b>gravity</b> and <b>quadratic drag</b>, with optional <b>wind</b>.
    The core method uses an <b>auxiliary-solution-induced residual</b>: drag-inclusive trajectory error is transformed through an auxiliary vacuum ballistic response before the nonlinear correction step.
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
  <h3>Problem</h3>
  <p>
    In drag-inclusive ballistic interception, the error is measured as a closest-approach miss vector in physical space,
    while the correction variables are launch angles. A direct line-of-sight residual can give weak correction information
    when those spaces are misaligned, especially in high-arc or strongly nonlinear cases.
  </p>

  <h3>Method</h3>
  <ul>
    <li>Projectile dynamics include <b>quadratic drag</b>, optional <b>wind</b>, and fixed-step RK4 integration.</li>
    <li>The hit condition is solved against a <b>moving target</b>, with an extended API for constant-acceleration targets.</li>
    <li>A <b>vacuum ballistic auxiliary solver</b> converts drag-inclusive miss vectors into launch-angle residuals for the outer iteration.</li>
    <li>The nonlinear correction loop combines Levenberg-Marquardt damping, line search, and Broyden-style Jacobian refinement.</li>
    <li>The solver returns explicit <b>status codes</b>, <b>diagnostic messages</b>, and the <b>best result found</b> even when convergence is imperfect.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Architecture</h3>
  <div class="flow-diagram">
    <div class="flow-step"><b>Inputs</b><span>relative target motion, speed, drag, solver params</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Simulation</b><span>RK4 projectile integration with drag and wind</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Auxiliary Residual</b><span>vacuum ballistic response maps miss into launch-angle correction</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Solve</b><span>Levenberg-Marquardt + line search + Broyden-style Jacobian refinement</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Deploy</b><span>C ABI, Python package, Unity/C#, .NET, and Godot interop</span></div>
  </div>
</div>

<div class="project-card">
  <h3>What I Built</h3>
  <ul>
    <li><b>Auxiliary-solution-induced residual method</b> for nonlinear correction when residual space and correction-variable space are not directly aligned.</li>
    <li><b>Header-only C++ core</b> focused on solver logic rather than app-specific wrappers.</li>
    <li><b>Stable C ABI</b> with plain-C data layout and fixed-size arrays for FFI-safe integration.</li>
    <li><b>Python package</b> with presets, utility helpers, and prebuilt binaries through PyPI.</li>
    <li><b>Unity/C#, .NET, and Godot paths</b> so the same native solver can be used in game/runtime contexts.</li>
    <li><b>Failure handling</b> through explicit status codes such as invalid input, Jacobian failure, line-search rejection, and max-iteration exhaustion.</li>
  </ul>
</div>

<div class="project-card">
  <h3>What This Project Proves</h3>
  <ul>
    <li><b>Mathematical modeling</b>: I can translate a nonlinear physical intercept problem into a solver with explicit assumptions.</li>
    <li><b>Research-to-runtime engineering</b>: the residual transformation is paper-backed, benchmarked, and shipped through a reusable library.</li>
    <li><b>Numerical-method judgment</b>: I can combine integration, residual design, damping, line search, initialization, and Jacobian updates into one practical method.</li>
    <li><b>Deployable engineering</b>: I can expose the same core through C ABI, Python, Unity/C#, .NET, and Godot instead of leaving it as lab-only code.</li>
    <li><b>Debuggability</b>: explicit statuses and best-effort outputs matter to me as much as nominal success cases.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Research Result</h3>
  <p>
    In the ICROS 2026 manuscript, the auxiliary residual was compared against direct line-of-sight residual correction
    under identical outer-iteration settings on 10,000 stationary high-arc interception cases.
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
      <tr>
        <td>Direct line-of-sight residual</td>
        <td>50.25%</td>
        <td>6.791 ms</td>
        <td>8.498e+02 m</td>
      </tr>
      <tr>
        <td>Auxiliary-solution-induced residual</td>
        <td>0.00%</td>
        <td>3.748 ms</td>
        <td>8.128e-03 m</td>
      </tr>
    </tbody>
  </table>
</div>

<div class="project-card">
  <h3>Package Benchmarks</h3>
  <p>From the repository README benchmark on a local Windows release build over 500 generated linear-target cases:</p>
  <table class="result-table">
    <thead>
      <tr>
        <th>Preset</th>
        <th>Median Solve Time</th>
        <th>p95 Solve Time</th>
        <th>p95 Miss</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>fast</td>
        <td>0.094 ms</td>
        <td>0.228 ms</td>
        <td>3.834e-02 m</td>
      </tr>
      <tr>
        <td>balanced</td>
        <td>0.182 ms</td>
        <td>0.452 ms</td>
        <td>5.351e-03 m</td>
      </tr>
      <tr>
        <td>precise</td>
        <td>0.199 ms</td>
        <td>0.569 ms</td>
        <td>5.742e-06 m</td>
      </tr>
    </tbody>
  </table>
</div>

<div class="project-card">
  <h3>High-Arc Update</h3>
  <p>After adding the v0.6 moving-target convergence defaults, high-arc generated cases improved substantially in the repository benchmark.</p>
  <table class="result-table">
    <thead>
      <tr>
        <th>Configuration</th>
        <th>Success</th>
        <th>Median Runtime</th>
        <th>P95 Runtime</th>
        <th>P95 Miss</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Previous core path</td>
        <td>382/500</td>
        <td>4.301 ms</td>
        <td>27.124 ms</td>
        <td>3.227e+02 m</td>
      </tr>
      <tr>
        <td>v0.6.0 defaults</td>
        <td>490/500</td>
        <td>1.845 ms</td>
        <td>2.535 ms</td>
        <td>8.809e-03 m</td>
      </tr>
    </tbody>
  </table>
</div>

<div class="project-card">
  <h3>Limits And Failure Cases</h3>
  <ul>
    <li>The runtime using the solver must match the same physics and integration assumptions; different timesteps or integrators can invalidate the hit.</li>
    <li>Strongly nonlinear cases are handled numerically, so convergence quality depends on solver settings and problem conditioning.</li>
    <li>The implementation prioritizes <b>deployable robustness</b>, explicit diagnostics, and best-effort outputs instead of hiding difficult convergence states.</li>
  </ul>
</div>
