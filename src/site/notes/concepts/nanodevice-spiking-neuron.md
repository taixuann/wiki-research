---
{"dg-publish":true,"permalink":"/concepts/nanodevice-spiking-neuron/","title":"Nanodevice spiking neuron","tags":["neuromorphic","spiking-neuron","neuristor","phase-transition-devices","spintronics"],"dg-note-properties":{"title":"Nanodevice spiking neuron","aliases":["artificial nano-neuron","physical spiking neuron","material neuron","neuristor","Mott spiking neuron"],"tags":["neuromorphic","spiking-neuron","neuristor","phase-transition-devices","spintronics"],"maturity":"active","definition":"An artificial neuron in which the integrate-and-fire dynamics emerge directly from a nanodevice's intrinsic physics — phase transition, negative differential resistance, stochastic magnetization or oscillator dynamics — rather than from a multi-transistor CMOS circuit model.","key_papers":["[[papers/physics-neuromorphic-computing]]"],"date_updated":"2026-09-30"}}
---

## Definition

A nanoscale device whose electrical behavior reproduces the computational primitives of a biological neuron — temporal integration, threshold, spike emission, refractory/leaky relaxation, and sometimes stochasticity or oscillation — using the device's own state variable (electron correlations, temperature, phase configuration, magnetization) as the "membrane potential".

## Intuition

Biological neurons are dynamical systems, not arithmetic units. Certain materials are dynamical systems too: a Mott insulator avalanche-triggers into a conductive state under accumulated input spikes and relaxes when input stops (depolarization/repolarization analog); a volatile switch with negative differential resistance plus an RC network spikes under constant bias; superparamagnetic tunnel junctions switch stochastically and can encode membrane potential in phase configuration. The device is the model — no transistor bank required.

## Variants

- **Mott / correlated-electron neuristors**: avalanche electronic phase transition triggered by spike trains; subthreshold firing demonstrated in nanodevices.
- **NDR relaxation oscillators**: thermally-induced negative differential resistance with added R/C (or transistor) producing periodic, chaotic and bursting spike trains under DC bias.
- **Stochastic phase-change neurons**: amorphous/crystalline phase configuration as membrane potential, exploiting transition stochasticity.
- **Spintronic neurons**: spin-torque and superparamagnetic tunnel-junction oscillators whose frequency/phase carries the signal; nanoscale and highly cyclable.
- **Superconductive (Josephson) neurons**: flux-quantization spike analogs with identical spike shapes and ultra-low dissipation (cryogenic).
- **NEMS oscillators**: resonant/self-sustained mechanical oscillation at audible-compatible frequencies for on-chip voice tasks.

## Comparison

- vs. **CMOS LIF circuits**: dozens of transistors and µm-scale area per neuron vs. 10–20 nm-class devices with intrinsic dynamics; but far less configurable and harder to characterize.
- vs. **software spiking neurons**: device neurons are free (zero static power for the dynamic itself) and asynchronous, but noisy, variable and constrained to the dynamics the material provides.
- vs. **memristive synapses**: neurons and synapses that can be made from the same materials/material effects simplify fabrication and open device-level learning rules (e.g. volatility-based STDP).

## Known limitations

- Dynamics are set by physics, so tunability is limited to what current, field or temperature can adjust; device variability maps directly into neuron-to-neuron variability.
- System-level demonstrations are still small ("toy") scale; scalability mostly to be demonstrated (Table 1 of the review).
- Noise and drift are severe at nanoscale volumes and must be engineered around (redundancy, population coding) or exploited.

## Open problems

- Extending hardware learning rules (STDP and beyond) from single devices/small ensembles to multilayer networks of spiking nano-neurons.
- Whether noise, criticality, synchronization and stochastic resonance can be harnessed in-materio for computation.
- Population/ensemble coding schemes that make fully stochastic devices (e.g. superparamagnetic junctions) computationally reliable.
- Co-integration of nano-neurons with nano-synapses and CMOS routing at millions-device scale.

## Relationship to foundations

Stands on non-linear dynamics and excitable-system physics (threshold, relaxation, oscillation) and on the specific material phase transitions used to realize them; connects device physics to the reservoir-computing and spiking-network algorithm literatures.

## Realized by

- None recorded yet.

## My understanding

The unifying move is delegation: instead of engineering a neuron out of transistors and hoping parasitics behave, pick a material whose natural instability already is the neuron. The review's evidence that this works is strong at device level (periodic/chaotic/bursting spikes, synchronization, reservoir computing) — the open question is entirely about systems, not physics.
