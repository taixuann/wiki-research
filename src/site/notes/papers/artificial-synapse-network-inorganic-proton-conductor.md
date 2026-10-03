---
{"dg-publish":true,"permalink":"/papers/artificial-synapse-network-inorganic-proton-conductor/","title":"Artificial synapse network on inorganic proton conductor for neuromorphic systems applications","tags":["neuromorphic","artificial-synapse","synaptic-transistor","proton-conductor","short-term-plasticity"],"dg-note-properties":{"title":"Artificial synapse network on inorganic proton conductor for neuromorphic systems applications","slug":"artificial-synapse-network-inorganic-proton-conductor","arxiv":"1311.0559","venue":"Nature Communications","year":2014,"tags":["neuromorphic","artificial-synapse","synaptic-transistor","proton-conductor","short-term-plasticity"],"importance":3,"date_added":"2026-09-30","source_type":"pdf","tldr":"Room-temperature self-assembled IZO synaptic transistors gated laterally by nanogranular P-doped SiO2 proton conductors reproduce paired-pulse facilitation, high-pass dynamic filtering, and supralinear spatiotemporal EPSC summation at 15-45 pJ per spike.","contribution_type":["method","application"],"datasets":[],"cited_by":[]}}
---

## Problem & Context

Hardware neuromorphic computation needs artificial synapses: each biological neuron makes >1000 synapse connections, and synaptic strength is tuned by ionic species concentrations. Before this paper, CMOS neuromorphic circuits implemented synapses but consumed far more energy than a biological synapse and do not scale to brain-like density; resistive-switching memories, memristors and atomic switches had demonstrated STDP and short-to-long-term memory transitions, but their weights depend on conducting-filament formation and electrochemical reactions, which makes device-to-device behaviour hard to control. Three-terminal synaptic transistors (channel conductance = synaptic weight, gate pulse = spike) were an emerging alternative — the best-known example coupled an RbAg4I5 ionic conductor with an ion-doped conjugated polymer in the gate dielectric — yet they still used conventional buried bottom-gate stacks and non-oxide, often organic, materials.

The Wan group had already shown in-plane-gate oxide transistors gated by nanogranular SiO2 and chitosan proton conductors, where the in-plane gate couples laterally through two series gate capacitors. This paper removes the bottom conductive layer entirely and asks whether a single lateral electric-double-layer (EDL) capacitor is enough to make a whole *network* of synapses.

## Key idea

Take the in-plane gate as pre-synapse and the self-assembled IZO channel with source/drain as post-synapse, and let mobile protons in a nanogranular P-doped SiO2 film be the neurotransmitter. Proton migration under a presynaptic gate spike accumulates charge at the SiO2/IZO channel interface, modulating channel conductance laterally; because many in-plane gates land on one shared channel through a single shadow-mask deposition, the cross-points become a synapse network with no deliberate hard-wired interconnects — spike-timed proton motion itself establishes the connections.

## Method

- **Electrolyte**: ~820 nm nanogranular P-doped SiO2 on glass by PECVD (SiH4/PH3 95:5 + O2 + Ar, 100 W, ~30 Pa); 2-5 nm interparticle gaps form nanopore channels for proton hopping between hydroxyl groups and water (proton conductivity ~10^-4 S/cm at room temperature); lateral specific capacitance ~3.0 uF/cm2 at 1.0 Hz from EDL formation.
- **One-mask self-assembly**: IZO source/drain/gate patterns by RF magnetron sputtering through a nickel shadow mask at room temperature. At 80 um pattern spacing, IZO nanoparticles reflected at the mask edge self-assemble a connected channel (~20 nm typical thickness); at 300 um spacing no channel forms, leaving isolated in-plane gates. Dual/multiple in-plane gates are drawn in the same single mask step.
- **Synaptic measurement**: presynaptic spikes on the in-plane gate; EPSC read in the IZO channel at fixed Vds (0.5-1.0 V) with a Keithley 4200 SCS at ~50% RH. EPSC decay is fitted with a stretched exponential function I(t) = I_inf + (I0 - I_inf) exp[-((t - t0)/tau)^beta].

## Experiment & Results

- **Transistor basics**: anticlockwise transfer hysteresis (Vgs swept -1.0 to 1.0 V, Vds = 1.0 V, 20 nm channel) attributed to mobile protons; drain current on/off ratio ~10^6; linear low-Vds regime = good ohmic contact, saturation at high Vds.
- **EPSC**: a 0.3 V, 10 ms presynaptic spike triggers an EPSC peaking at ~13 nA and decaying to a ~5.0 nA resting current over ~500 ms; stretched-exponential fit gives tau ~ 25 ms (the proton migration feature time). Spike duration from 10 ms to 2000 ms raises the peak from ~13 nA to ~29 nA, growing near-linearly below ~300 ms then saturating (only a limited proton population is activated).
- **Energy per spike**: ~45 pJ for a single spike on the 20 nm-channel device (better than CMOS-synapse circuits, comparable to reported hardware synapses); on a dual-gate device, biasing the second in-plane gate from 0 V to -0.7 V cuts dissipation from ~1.4 nJ to ~15 pJ per spike. Stated target for neuromorphic use: ~1.0 pJ/spike, plausible with sub-ms spikes and sub-micron channel scaling.
- **Paired-pulse facilitation**: two 0.3 V, 10 ms spikes with inter-spike interval 30-1500 ms; PPF index (A2/A1) peaks at ~180% for dt = 30 ms and decays as dt grows — residual protons from spike 1 still sit near the channel when spike 2 arrives.
- **Dynamic filtering**: trains of 10 spikes at 1-50 Hz give an A10/A1 gain rising from ~1.0 (1 Hz) to ~6.6 (50 Hz) — the device behaves as a high-pass temporal filter (facilitation-dominated), unlike the low-pass filtering of depression-dominated synapses.
- **Spatiotemporal logic**: two gates stimulated with 0.5 V/20 ms (~30 nA) and 1.0 V/20 ms (~50 nA); at dt = 0 the summed EPSC reaches ~110 nA, larger than the linear sum — supralinear amplification analogous to hippocampal CA1 pyramidal-neuron EPSP summation — decaying asymmetrically as |dt| grows.
- **Network**: multiple in-plane gates + one self-assembled channel form a multi-pre-synapse / single post-synapse network whose weights are set spatiotemporally by the applied spikes.

## Limitations

- No long-term plasticity (LTP/LTD) or STDP is demonstrated — only short-term plasticity; memory decays in hundreds of milliseconds with tau ~ 25 ms.
- Devices are large (channel width ~150 um) and unpatterned beyond shadow masks; no array-level yield, variability, or endurance statistics are reported.
- Measurements are single-device DC/pulse characterizations in ambient air at ~50% RH — proton transport is humidity-dependent and no humidity robustness study is given.
- No network task (classification, pattern recognition) is demonstrated; the "neural network" is a schematic of gates on one channel.
- Energy per spike (15-45 pJ, worse case ~1.4 nJ) remains far above the stated ~1 pJ goal and above biological synapses (~10-100 fJ); scaling benefits are argued, not measured.
- The stretched-exponential description is phenomenological; proton migration is inferred rather than imaged.

## Open questions

- Can retention be extended into the long-term-memory regime (hours+) — e.g. by engineering proton trapping sites — without losing the low-voltage EDL coupling?
- How does device-to-device variability of the self-assembled channel affect PPF index and gain across a large array?
- Does performance hold at low humidity or on flexible substrates, and what is the humidity-dependence envelope?
- Can the sub-pJ/spike target be reached experimentally with sub-ms spikes and sub-micron channels?
- Can these short-term-plasticity devices be combined with a neuron circuit to run an actual learning task?

## My take

A clean demonstration that protonics, not just filamentary resistive switching, can carry synaptic dynamics: the physics (EDL-coupled proton migration) directly explains the observed PPF, high-pass filtering, and saturation, which gives the paper more explanatory value than a pure device-demo. The one-mask self-assembly trick is the practical highlight — a whole synaptic crossbar-like structure appears from a single deposition step at room temperature. Weak spots are the absence of any learning rule or network-level task and the gap between measured and promised energy. For a neuromorphic-hardware wiki this is a canonical "proton-conductor synapse" reference and a good bridge between the electrolyte-gated-transistor and memristor-synapse literatures.

## Related

- [[concepts/proton-conductor-artificial-synapse\|proton-conductor-artificial-synapse]]
- [[methods/one-mask-self-assembled-synaptic-transistor\|one-mask-self-assembled-synaptic-transistor]]
