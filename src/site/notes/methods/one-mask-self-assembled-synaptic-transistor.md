---
{"dg-publish":true,"permalink":"/methods/one-mask-self-assembled-synaptic-transistor/","tags":["neuromorphic","device-fabrication","synaptic-transistor","oxide-thin-film"],"dg-note-properties":{"name":"One-mask self-assembled synaptic transistor","slug":"one-mask-self-assembled-synaptic-transistor","type":"protocol","tags":["neuromorphic","device-fabrication","synaptic-transistor","oxide-thin-film"],"source_papers":["[[papers/artificial-synapse-network-inorganic-proton-conductor]]"],"realizes_concepts":["[[concepts/proton-conductor-artificial-synapse]]"],"date_updated":"2026-09-30"}}
---

## Problem setting

Fabricate a lateral, electrolyte-gated synaptic transistor — in-plane gate electrodes plus a shared semiconductor channel on a proton-conducting film — without lithography per device, at room temperature, on insulating substrates such as glass.

## Mechanism

Shadow-mask RF sputtering of IZO exploits back-reflection of nanoparticles at the mask edge and low-incident-angle dimensional extension: at ~80 um pattern spacing the deposited source and drain fingers meet and self-assemble a connected channel, while at ~300 um spacing they stay isolated and serve as in-plane gates. Because gate, source, and drain all come from one mask and one deposition, the transistor (and any number of dual/multi gates) forms in a single step on the PECVD nanogranular P-doped SiO2 proton-conductor film.

## Procedure

1. Deposit ~820 nm nanogranular P-doped SiO2 on glass by PECVD (SiH4/PH3 95:5 + O2 + Ar, 100 W RF, ~30 Pa, flow rates 10/60/60 sccm).
2. Load a nickel shadow mask defining source/drain/gate patterns.
3. RF magnetron sputter IZO (100 W, 14 sccm Ar, 0.5 Pa) at room temperature; choose pattern spacing to decide whether a self-assembled channel forms (<= ~80 um) or isolated gates form (~300 um).
4. Set channel thickness by mask-to-substrate distance (typical channel ~12-20 nm).
5. Wire in-plane gates as presynaptic inputs and the self-assembled source/drain channel as the postsynaptic output; characterize with a semiconductor parameter analyzer (e.g. Keithley 4200 SCS) at controlled humidity.

## Assumptions

- The proton-conducting film is sufficiently nanoporous (2-5 nm gaps) for proton migration at room temperature.
- Mask-edge scattering produces a continuous channel at the chosen spacing; no lithographic definition of the channel is available.
- Ambient humidity (~50% RH) is sufficient for proton conduction.

## Limitations

- Resolution is set by the shadow mask: channel widths stay in the tens-to-hundreds of micrometers unless optical lithography replaces the mask.
- Self-assembly statistics give channel-to-channel variability; no per-device trimming is possible.
- Contact geometry and channel thickness co-vary with mask spacing, limiting independent optimization.

## Tradeoff profile

Gains: room-temperature, one-step, lithography-free definition of an entire multi-gate synaptic crosspoint; simple and cheap. Costs: coarse feature size, variability, and channel properties coupled to geometry rather than independently engineered.

## Evaluated by

- Transfer/output curves of the lateral transistor (on/off ratio, hysteresis).
- EPSC response to presynaptic spikes and its stretched-exponential decay.
- Energy per spike, PPF index, frequency-dependent gain (A10/A1), and supralinear EPSC summation across the multi-gate structure.
