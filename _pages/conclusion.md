---
layout: page
title: conclusion
permalink: /conclusion/
description: Summary of the research conclusions on bistable piezomagnetoelastic energy harvesting, broadband response, and future work.
nav: false
nav_order: 3
toc:
  sidebar: left
---

## Research conclusion

This study investigated broadband energy harvesting through a magnetically induced bistable piezomagnetoelastic beam subjected to vortex-induced vibration in a fluid flow environment. The work was motivated by a clear practical need: most conventional energy harvesters operate efficiently only near resonance, while real-world flow conditions are rarely constant. In such situations, a narrowband linear harvester can lose a large fraction of its available energy output.

The proposed nonlinear design addresses this limitation by exploiting bistability and chaotic dynamics. By introducing magnetic nonlinearity through repulsive magnets, the beam was tuned to operate in a regime where the natural frequency and the flow-induced forcing could interact more effectively over a wider range of operating conditions.

## Main findings

The results show that the nonlinear piezomagnetoelastic energy harvester consistently outperforms the linear piezoelastic beam over a broad frequency range, except at exact resonance where the linear harvester can exhibit a strong peak response. This confirms that magnetic nonlinearity is an effective strategy for broadening the operating bandwidth and improving energy harvesting capability under variable flow conditions.

The key contribution of the study is the demonstration that nonlinear magnetic interaction can increase the displacement amplitude and extracted power by enabling interwell oscillations, large-amplitude motion, and frequency-robust energy conversion. The phase portrait, Poincaré section, and bifurcation analysis confirm that the system can transition from periodic motion to chaotic behavior under the right combinations of forcing frequency, damping, and magnet gap.

## Role of bistability and chaos

The beam was shown to operate in a bistable region when the magnet separation was chosen appropriately. In this regime, the beam can switch between two potential wells, which leads to higher velocity and therefore greater power generation. However, a bistable system is only beneficial if the forcing amplitude is sufficient to overcome the potential barrier. If the barrier is too high or the excitation is too weak, the beam remains trapped in a single potential well and the expected gain in power is lost.

A particularly important result is that the system can also operate in a chaotic regime for a prescribed natural frequency and damping ratio. For the case considered in the thesis, the beam with a natural frequency near 131 Hz and damping ratio of approximately 2.75% shows chaotic dynamics under an excitation corresponding to a flow velocity of about 2 m/s. In this chaotic regime, the energy harvester produces more power than the linear counterpart, but it also requires a suitable energy harvesting circuit designed to accommodate irregular and broadband voltage output.

## Practical relevance

From an engineering standpoint, the study is relevant to low-power electronics, wireless sensors, Internet-of-Things systems, and remote monitoring applications where batteries may be inconvenient or impractical to replace. The work demonstrates that even modest environmental motion can be exploited more effectively when nonlinear dynamics are intentionally designed into the harvester.

This is especially important for flow-driven environments such as HVAC ducts, exhaust systems, and other compact airflow channels, where the available kinetic energy is not large but is persistent and can be exploited with appropriately tuned devices.

## Conclusion

In summary, the thesis concludes that nonlinear magnetic coupling is a powerful mechanism for improving the performance of MEMS-based piezoelectric energy harvesters in variable-flow environments. By moving beyond narrowband resonance, the system can achieve larger broadband response, greater energy extraction, and improved suitability for real-world low-power applications.

The study also reinforces a broader engineering insight: nonlinear design is not a complication to avoid, but a useful tool when the goal is robustness, adaptability, and energy harvesting under uncertain operating conditions.

## Future work

The following directions are promising for further development:

- use of anisotropic piezoelectric material models to improve fidelity;
- study of different bluff-body shapes and their influence on vortex shedding;
- optimization of magnet spacing and beam geometry for maximum power output;
- design of specialized power-conditioning circuits for chaotic voltage signals;
- exploration of multi-beam or stacked harvesting configurations;
- experimental validation of the nonlinear magnetic model and system response.

---

<div class="alert alert-success" role="alert">
  <strong>Takeaway:</strong> the research demonstrates that nonlinear bistable and chaotic energy harvesters can outperform linear harvesters in real-world broadband flow conditions, making them attractive for self-powered sensing and intelligent microsystems.
</div>
