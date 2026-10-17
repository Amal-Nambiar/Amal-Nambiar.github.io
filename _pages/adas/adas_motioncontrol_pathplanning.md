---
layout: page
title: ADAS MotionControl & PathPlanning
permalink: /adas/adas_motioncontrol_pathplanning/
description: Motion control and path planning framework — subdivided into modules and examples.
nav: false
toc:
  sidebar: left
---

<div class="row">
  <div class="col-sm-8">
    <h2>Overview</h2>
    <p>This repository contains motion-control algorithms, path-planning examples, and Simulink integrations used for ADAS features. Below are quick links to the submodules and example demos.</p>

    <h3 id="motion-control">Motion Control</h3>
    <p>State estimation, longitudinal and lateral controllers, tracking loops, and low-level plant models.</p>

    <h3 id="path-planning">Path Planning</h3>
    <p>Sampling-based planners, curvilinear references, and trajectory smoothing.</p>

    <h3 id="examples">Examples</h3>
    <ul>
      <li>Simulink demo: AEB and ACC scenarios</li>
      <li>Path-following with LQR and MPC</li>
      <li>Integration with OpenScenario traces</li>
    </ul>

    <h3 id="resources">Resources</h3>
    <p>Repository: <a href="https://github.com/Amal-Nambiar/ADAS_MotionControl-PathPlanning" target="_blank">ADAS_MotionControl-PathPlanning</a></p>
  </div>
  <div class="col-sm-4 text-center">
    <img src="/assets/ADAS/vehicle_controllers_comparison.gif" class="img-fluid rounded shadow-sm" alt="controllers comparison" />
    <p class="mt-2"><small>Controller comparison and planner demos (GIFs)</small></p>
  </div>
</div>

## Controllers (lateral & longitudinal)

The repository implements common lateral path-tracking and longitudinal speed controllers. Key modules and behavior:

- **Stanley controller:** front-axle error based steering that combines heading error and cross-track error with a velocity-dependent gain. Good for low-speed path tracking and robust to small map noise.
- **Pure Pursuit (geometric):** computes a lookahead point on the path and steers toward it. Simple and fast, tuned via lookahead distance and dynamic lookahead adaption.
- **LQR:** linear-quadratic regulator applied on a linearized vehicle model for smooth setpoint tracking with explicit state- and input-weight tuning.
- **MPC:** convex optimizer (cvxpy) that enforces vehicle dynamics and constraints over a finite horizon; trades off tracking error and control effort for predictive behavior.
- **PID/Longitudinal loop:** cascaded velocity control (speed setpoint → acceleration) with feedforward/braking handling.

Example GIF: controller comparison above shows lateral controllers running on the same reference path and highlights differences in overshoot and settling.

## Path planning algorithms

The planning suite includes sampling-based and graph-based planners used to generate reference paths for the controllers:

- **A* and Dijkstra:** grid/graph search producing collision-free routes on a discrete occupancy map (A* uses a heuristic for speed).
- **Hybrid A***: kinodynamic search over state-space with continuous orientation — suitable for car-like kinematics and narrow passages.
- **State Lattice:** precomputed motion primitives tiled across the state space for fast feasible maneuvers with continuity in curvature.
- **Frenet Optimal Planner:** constructs candidate lateral offsets in the Frenet frame and optimizes for smoothness, curvature, and obstacle clearance.

Visual gallery (examples from the repo):

<div class="row">
  <div class="col-sm-6 mb-3"><img src="/assets/ADAS/AStar_stanley.gif" alt="AStar + Stanley" class="img-fluid rounded" /></div>
  <div class="col-sm-6 mb-3"><img src="/assets/ADAS/Dijkstra_stanley.gif" alt="Dijkstra + Stanley" class="img-fluid rounded" /></div>
  <div class="col-sm-6 mb-3"><img src="/assets/ADAS/Hybrid_AStar.gif" alt="Hybrid AStar" class="img-fluid rounded" /></div>
  <div class="col-sm-6 mb-3"><img src="/assets/ADAS/State_Lattice_Stanley.gif" alt="State Lattice + Stanley" class="img-fluid rounded" /></div>
</div>

## Frenet planner

The Frenet planner produces smooth longitudinal/lateral trajectories in a curvilinear coordinate frame and is useful for highway-style path following. Example simulation GIF:

<p class="text-center"><img src="/assets/ADAS/frenet_simulation.gif" alt="Frenet simulation" class="img-fluid rounded" style="max-width:720px;"/></p>

## How the pieces fit (practical notes)

- Typical demo flow: generate a reference path with a planner (A*, Hybrid A*, Frenet), smooth and sample it, then feed the path to a lateral controller (Stanley / Pure Pursuit / MPC) and a longitudinal controller (PID / MPC speed) in the vehicle plant model.
- Use the `Visualization/AllinOne.py` runner to reproduce the GIFs in `assets/ADAS/` — it packs plots and exports the animation frames used for the site demos.
- Tuning tips: increase lookahead for smoother Pure Pursuit response; tune LQR weights for desired damping; for MPC, shorten horizon for faster solve times and add soft constraints to improve robustness.

## Sources & references

Repository: <a href="https://github.com/Amal-Nambiar/ADAS_MotionControl-PathPlanning" target="_blank">ADAS_MotionControl-PathPlanning</a>

If you want, I can extract specific README sections or short code excerpts (Stanley, MPC setup, Hybrid A* heuristics) into collapsible subsections on this page.

---

## Per-demo technical notes

### A* + Stanley (AStar_stanley.gif)
- Inputs: grid occupancy or graph, start/goal nodes, heuristic (Euclidean/Manhattan); vehicle initial pose and velocity for the tracker.
- Outputs: discrete path (sequence of waypoints) passed to Stanley for lateral tracking; controller steering commands over time.
- Tuning knobs: A* heuristic weight (affects optimality vs speed), grid resolution; Stanley gain and velocity scaling for cross-track correction.

### Dijkstra + Stanley (Dijkstra_stanley.gif)
- Inputs: full graph with uniform edge costs, start/goal, same tracking inputs as above.
- Outputs: cost-optimal path on the graph; steering traces and lateral error plots from the Stanley controller.
- Tuning knobs: graph connectivity and cost function; Stanley tuning for responsiveness vs chatter.

### Hybrid A* (Hybrid_AStar.gif)
- Inputs: continuous state-space (x,y,yaw), vehicle kinematic model, obstacle map, motion primitives or steering discretization.
- Outputs: kinematically-feasible path that respects nonholonomic constraints; a sequence of curvature/steering setpoints.
- Tuning knobs: motion-primitive granularity, steering discretization, search heuristic (admissible vs weighted), collision-check resolution.

### State Lattice + Stanley (State_Lattice_Stanley.gif)
- Inputs: precomputed motion primitives, state lattice resolution, initial state and goal corridor.
- Outputs: sequence of primitives forming a feasible path; smooth curvature profile fed to controller.
- Tuning knobs: primitive length/curvature set, lattice spacing, cost weights for smoothness vs clearance.

### Frenet simulation (frenet_simulation.gif)
- Inputs: reference centerline, longitudinal speed profile, obstacle candidate lanes in Frenet frame.
- Outputs: optimized lateral-lon trajectories (s, d) converted back to (x,y) for tracking.
- Tuning knobs: lateral vs longitudinal cost weights, sampling density of candidate offsets, curvature/jerk penalties.

### Controller comparison (vehicle_controllers_comparison.gif)
- Inputs: single reference path and identical vehicle initial conditions for each controller.
- Outputs: comparative steering, lateral error, and speed traces that reveal overshoot, settling, and tracking stability.
- Tuning knobs: per-controller parameters (lookahead, gains, LQR weights, MPC horizon/weights), sampling frequency, vehicle model fidelity.

Each GIF in `/assets/ADAS/` maps to a runner in `Visualization/` that reproduces the scenario and exports frames. If you want, I will add collapsible code snippets showing the Stanley controller core loop, MPC objective construction, and Hybrid A* neighbor expansion next.

