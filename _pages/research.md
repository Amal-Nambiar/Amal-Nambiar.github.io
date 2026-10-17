---
layout: page
title: research
permalink: /research/
description: MS research on nonlinear MEMS energy harvesting, vortex-induced vibration, bistability, and chaotic broadband response.
nav: true
nav_order: 2
---

<div class="row">
  <div class="col-sm-12">
    <div class="card mt-3">
      <div class="card-body">
        <h3 class="card-title">MS research portfolio</h3>
        <p class="lead">My research focuses on nonlinear energy harvesting in MEMS devices, where fluid-induced vibration, magnetic interaction, and piezoelectric conversion are combined to create broadband, self-powered energy harvesting systems.</p>
        <p>
          The central theme of my work is the design of a bistable piezomagnetoelastic energy harvester for vortex-induced vibration (VIV). The goal is to move beyond narrowband linear resonant systems and create a device that can harvest energy efficiently under varying flow conditions, weak excitation, and broadband operating environments.
        </p>
        <a href="/thesis/" class="btn btn-primary">Read the thesis summary</a>
        <a href="/conclusion/" class="btn btn-outline-primary ml-2">Read the conclusion</a>
      </div>
    </div>
  </div>
</div>

<div class="row mt-4">
  <div class="col-sm-4">
    <div class="card h-100">
      <div class="card-body">
        <h4>Research focus</h4>
        <p>Energy harvesting from ambient fluid flow using nonlinear MEMS beams, piezoelectric transduction, and magnetic bistability.</p>
      </div>
    </div>
  </div>

  <div class="col-sm-4">
    <div class="card h-100">
      <div class="card-body">
        <h4>Technical methods</h4>
        <p>Finite element analysis, reduced-order modeling, phase portraits, Poincaré maps, bifurcation diagrams, and Lyapunov-based chaos detection.</p>
      </div>
    </div>
  </div>

  <div class="col-sm-4">
    <div class="card h-100">
      <div class="card-body">
        <h4>Impact</h4>
        <p>Broadband energy harvesting for low-power sensing, IoT nodes, remote monitoring, and self-powered microsystems.</p>
      </div>
    </div>
  </div>
</div>

## Research problem

Traditional linear piezoelectric energy harvesters perform efficiently only near resonance. In real-world environments, however, the excitation frequency and flow conditions vary, causing the harvester to operate away from its optimal frequency and significantly reduce the power output. This challenge is particularly important for MEMS systems designed to harvest ambient energy from airflow and fluid-induced vibration.

My research addresses this by introducing nonlinear dynamics using a pair of magnetic elements. By placing a permanent magnet on the beam tip and a fixed magnet at a controlled separation distance, the system can be tuned to operate in a bistable or chaotic regime. This broadens the operating bandwidth and improves the ability to harvest energy from broadband and fluctuating flow environments.

## Core research themes

- nonlinear vibration and bistability in MEMS cantilever beams;
- vortex-induced vibration and flow-induced excitation for energy conversion;
- piezomagnetoelastic coupling for broadband performance enhancement;
- reduced-order modeling and validation against finite element simulations;
- chaotic motion as a mechanism for wideband energy harvesting;
- design principles for low-power autonomous sensing and wireless systems.

## Scientific contribution

The thesis shows that the piezomagnetoelastic beam consistently outperforms the piezoelastic beam over a broad range of operating frequencies, except at exact resonance. The nonlinear magnetic interaction increases the effective bandwidth and enables the system to maintain useful oscillation amplitudes under fluctuating flow conditions.

At a representative operating point, the system was shown to enter a chaotic regime at a natural frequency near 131 Hz and damping ratio of approximately 2.75%. In this regime, the harvester produces greater energy than its linear counterpart, although it also underscores the need for a tailored electrical harvesting circuit to take advantage of chaotic voltage output.

## Visual highlights

<div class="row mt-4">
  <div class="col-sm-6 text-center">
    <img src="{{ '/assets/IIT/Chaos_Linear.gif' | relative_url }}" class="img-fluid rounded shadow-sm" alt="Linear energy harvester response" />
    <p class="mt-2"><small>Linear response</small></p>
  </div>
  <div class="col-sm-6 text-center">
    <img src="{{ '/assets/IIT/Chaos_Nonlinear.gif' | relative_url }}" class="img-fluid rounded shadow-sm" alt="Nonlinear bistable energy harvester response" />
    <p class="mt-2"><small>Nonlinear / bistable response</small></p>
  </div>
</div>

## Related work

- [MS thesis summary](/thesis/)
- [Energy harvesting and nonlinear dynamics](/energy-harvesting/)
- [Research conclusion](/conclusion/)

---

<div class="alert alert-info" role="alert">
  <strong>Research direction:</strong> broadband MEMS energy harvesting, nonlinear mechanics, chaotic dynamics, and magnetically tuned flow-driven power generation.
</div>
