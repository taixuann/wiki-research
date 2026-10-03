---
{"dg-publish":true,"permalink":"/concepts/proton-conductor-artificial-synapse/","title":"Proton-conductor artificial synapse","tags":["neuromorphic","artificial-synapse","proton-conductor","synaptic-transistor"],"dg-note-properties":{"title":"Proton-conductor artificial synapse","aliases":["protonic/electronic hybrid synapse","oxide-based artificial synapse","proton-coupled artificial synapse","in-plane-gate synaptic transistor"],"tags":["neuromorphic","artificial-synapse","proton-conductor","synaptic-transistor"],"maturity":"active","definition":"An artificial synapse in which mobile protons in a proton-conducting electrolyte act as the neurotransmitter, so that a gate spike moves protons to the electrolyte/channel interface and thereby modulates the channel conductance that encodes synaptic weight.","key_papers":["[[papers/artificial-synapse-network-inorganic-proton-conductor]]","[[papers/physics-neuromorphic-computing]]","[[papers/emulating-complex-synapses-using-interlinked-proton]]"],"related_concepts":["[[concepts/volatile-memristive-synapse]]","[[concepts/nanoparticle-organic-memory-transistor-synapse]]","[[concepts/interfacial-proton-coupled-electron-transfer-switching]]"],"first_introduced":"2013 (arXiv:1311.0559)","date_updated":"2026-09-30"}}
---

## Definition

A three-terminal (or lateral in-plane-gate) transistor whose synaptic weight is the channel conductance, written by proton migration in a proton-conducting gate medium (nanogranular SiO2, chitosan, or similar) rather than by filament formation or dopant drift. The presynaptic spike is a short gate voltage pulse; the postsynaptic signal is the resulting channel current (EPSC); relaxation of the proton concentration gradient gives the synapse its temporal dynamics.

## Intuition

In a biological synapse the presynaptic spike releases neurotransmitters that change the efficacy of the connection. Here the "neurotransmitter" is literally H+: the pulse drives protons through nanopores to the electrolyte/IZO interface, where the resulting electric double layer gates the channel laterally. Because protons drift back on their own once the pulse ends, the device natively shows short-term plasticity (facilitation, filtering) instead of a persistent state.

## Variants

- **In-plane lateral-coupled form** (this paper): no bottom gate; one lateral EDL capacitor couples in-plane gates to a self-assembled oxide channel.
- **Bottom/top-gate protonic forms**: proton conductor as the gate dielectric with a buried gate electrode (the same group's earlier in-plane-gate transistors with a bottom conductive layer).
- **Biopolymer proton conductors**: chitosan / polysaccharide-based versions of the same protonic gating idea.
- **Multi-compartment (complex-synapse) form**: PEDOT:PSS storage compartments linked in series through Nafion proton bridges, so diffusion among hidden state variables realizes the Benna-Fusi consolidation dynamics; per-compartment timescales are set by bridge diffusion length and compartment size (arXiv:2401.15045).
- **Protonic memristors / electrochemical transistors**: two-terminal or electrolyte-gated devices where proton intercalation sets the conductance state.

## Comparison

- vs. **filamentary memristor synapses**: protonic synapses weight by a distributed interfacial (EDL) charge rather than a stochastic conducting filament, so dynamics are analog and reproducible, but they are typically volatile and short-term only.
- vs. **CMOS synapse circuits**: far lower energy per spike (~15-45 pJ demonstrated) and no transistor-per-synapse area cost, at the cost of slower (ms-scale) dynamics.
- vs. **ionic/polymer synaptic transistors (e.g. RbAg4I5 + polymer)**: inorganic oxide electrolytes are room-temperature processable with oxide TFTs and compatible with self-assembled patterning.

## Known limitations

- Volatility: state relaxes in ~hundreds of ms (tau ~ 25 ms), so no long-term memory without extra trapping engineering.
- Humidity dependence of proton conductivity (~50% RH in the reported measurements).
- Demonstrated only at device level; array variability, endurance, and network-level tasks are open.

## Open problems

- Engineering proton retention for long-term plasticity while keeping millivolt-scale EDL gating.
- Achieving energy per spike near the biological ~10-100 fJ regime.
- Integration with neuron circuits and demonstration of on-chip learning.
- Understanding and controlling device variability in self-assembled channels.

## Relationship to foundations

Stands on well-established electric-double-layer gating and proton-conduction physics (hopping between hydroxyl groups and water); connects the electrolyte-gated-transistor literature to the artificial-synapse/neuromorphic-device literature.

## Realized by

- [[methods/one-mask-self-assembled-synaptic-transistor\|one-mask-self-assembled-synaptic-transistor]]

## My understanding

The conceptual move that matters is treating a mobile-ion concentration profile — not a fixed resistance state — as the synapse: weight modulation and its decay are two faces of the same proton redistribution, which is why facilitation, high-pass filtering, and saturation all fall out of one mechanism.
