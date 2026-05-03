---
layout: single
title: "ballistic-solver"
permalink: /projects/ballistic-solver/
classes: wide
---

<div class="project-card">
  <p class="eyebrow">C/C++ core · Stable C ABI · Python/PyPI · Unity/C#</p>
  <p>
    <b>ballistic-solver</b> is a deployable intercept solver for <b>moving targets</b> under <b>gravity</b> and <b>quadratic drag</b>, with optional <b>wind</b>.
    Instead of assuming a closed-form ballistic arc, it simulates projectile motion and solves the intercept numerically.
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
    I wanted a solver that still works when the projectile path is strongly curved by drag and the target is moving.
    That rules out simple vacuum-style closed forms as the main solution path.
  </p>

  <h3>Why Numerical Instead Of Closed-Form</h3>
  <ul>
    <li>Projectile dynamics include <b>quadratic drag</b>, optional <b>wind</b>, and fixed-step RK4 integration.</li>
    <li>The hit condition is solved against a <b>moving target</b>, with an extended API for constant-acceleration targets.</li>
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
    <div class="flow-step"><b>Residual</b><span>closest-approach miss expressed in launch-angle space</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Solve</b><span>Levenberg-Marquardt + line search + Broyden-style Jacobian refinement</span></div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Deploy</b><span>C ABI, Python package, Unity/C# interop</span></div>
  </div>
</div>

<div class="project-card">
  <h3>What I Built</h3>
  <ul>
    <li><b>Header-only C++ core</b> focused on solver logic rather than app-specific wrappers.</li>
    <li><b>Stable C ABI</b> with plain-C data layout and fixed-size arrays for FFI-safe integration.</li>
    <li><b>Python package</b> with presets, utility helpers, and prebuilt binaries through PyPI.</li>
    <li><b>Unity/C# path</b> using P/Invoke so the same native solver can be used in game/runtime contexts.</li>
    <li><b>Failure handling</b> through explicit status codes such as invalid input, Jacobian failure, line-search rejection, and max-iteration exhaustion.</li>
  </ul>
</div>

<div class="project-card">
  <h3>What This Project Proves</h3>
  <ul>
    <li><b>Mathematical modeling</b>: I can translate a nonlinear physical intercept problem into a solver with explicit assumptions.</li>
    <li><b>Numerical-method judgment</b>: I can combine integration, residual design, damping, line search, and Jacobian updates into one practical method.</li>
    <li><b>Deployable engineering</b>: I can expose the same core through C ABI, Python, and Unity/C# instead of leaving it as lab-only code.</li>
    <li><b>Debuggability</b>: explicit statuses and best-effort outputs matter to me as much as nominal success cases.</li>
  </ul>
</div>

<div class="project-card">
  <h3>Verified Results</h3>
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
        <td>0.107 ms</td>
        <td>0.233 ms</td>
        <td>3.399e-02 m</td>
      </tr>
      <tr>
        <td>balanced</td>
        <td>0.219 ms</td>
        <td>0.492 ms</td>
        <td>7.287e-03 m</td>
      </tr>
      <tr>
        <td>precise</td>
        <td>0.265 ms</td>
        <td>0.583 ms</td>
        <td>7.655e-06 m</td>
      </tr>
    </tbody>
  </table>
</div>

<div class="project-card">
  <h3>Limits And Failure Cases</h3>
  <ul>
    <li>The runtime using the solver must match the same physics and integration assumptions; different timesteps or integrators can invalidate the hit.</li>
    <li>Strongly nonlinear cases are handled numerically, so convergence quality depends on solver settings and problem conditioning.</li>
    <li>This project prioritizes <b>deployable robustness</b> and explicit diagnostics rather than pretending every case has a perfect analytic solution.</li>
  </ul>
</div>
