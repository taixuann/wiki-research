---
{"dg-publish":true,"permalink":"/concepts/volatile-memristive-synapse/","title":"Volatile memristive synapse","tags":["neuromorphic","artificial-synapse","memristor","volatile-memristor","short-term-plasticity"],"dg-note-properties":{"title":"Volatile memristive synapse","aliases":["volatile memristor synapse","diffusive memristor synapse","threshold-switching synapse","volatile resistive-switching synapse","stochastic memristive synapse"],"tags":["neuromorphic","artificial-synapse","memristor","volatile-memristor","short-term-plasticity"],"maturity":"emerging","definition":"An artificial synapse built on a volatile (threshold-switching / diffusive) memristive device, where the synaptic state is a transient conductive filament that forms on a write pulse and dissolves on its own, so that the decay of conductance directly implements short-term plasticity with an electrically tunable lifetime.","key_papers":["[[papers/tunable-synaptic-working-memory-volatile-memristive]]","[[papers/electric-field-driven-interfacial-proton-coupled]]"],"related_concepts":["[[concepts/proton-conductor-artificial-synapse]]","[[concepts/nanoparticle-organic-memory-transistor-synapse]]","[[concepts/interfacial-proton-coupled-electron-transfer-switching]]"],"first_introduced":"2017 (Du et al., Nature Communications, dynamic-memristor reservoir computing)","date_updated":"2026-09-30"}}
---

## Definition

A two-terminal resistive-switching device whose low-resistance state is not retained: a write pulse above threshold migrates metal ions (Ag, or dopants in HfO2/TaOx) into a conductive filament, and once the bias falls below the hold voltage the filament rediffuses and the device returns to its high-resistance state on its own. The transient conductance is the synaptic weight, and its spontaneous decay — not an externally clocked reset — produces the short-term plasticity trace (facilitation, depression, temporal filtering) that synapses in working-memory and sequence-processing networks require.

## Intuition

Ordinary memory asks "how do I keep the state?"; this device asks "how fast do I lose it?". Because the filament's retention time scales with its diameter, and diameter is set by the compliance current during the write, lifetime becomes a circuit-level knob; because filament nucleation is stochastic, the write becomes probabilistic, with P_ON set by pulse amplitude, width and burst length. Together they give a synapse with two independently tunable knobs — how long it remembers and how easily it is written — which is precisely the pair that temporal (short-term plasticity) network models expose as free parameters. The physics supplies the decay term of the differential equation, so no capacitor bank or reset logic is needed.

## Variants

- **Ag-based threshold-switching (diffusive) devices** (this line of work): C/HfO2/Ag stacks with ~10^8 ON/OFF, no electroforming, retention from ~1 ms to 10 s set by compliance current; used for working-memory store/recall.
- **Diffusive memristor reservoir-computing synapses**: the same volatile dynamics exploited as fading-memory nonlinearity for temporal pattern recognition (Du 2017; Midya 2019; Zhong 2021) rather than as an explicit memory trace.
- **Palimpsest / short-term-memory networks**: volatile devices as the storage element of a continuously-overwriting memory network, so old items fade as new ones arrive.
- **Volatile selectors and security cells**: the same threshold-switching physics used for cross-point selectors or hardware entropy — same device family, non-synaptic role.
- **vs. non-volatile memristive synapses**: identical filament picture, but the filament is engineered to persist; forgetting then requires extra reset circuitry (area + power), which the volatile variant gets for free.

## Comparison

- vs. **proton-conductor / electrolyte-gated transistors** (`[[proton-conductor-artificial-synapse]]`): both are volatile and short-term, but the protonic synapse weights by a distributed interfacial ion profile with analog, reproducible dynamics, whereas the volatile memristive synapse weights by a single stochastic filament — far denser and two-terminal, but cycle-to-cycle retention is broad (lognormal) and write is probabilistic.
- vs. **CMOS capacitor RC synapses**: the volatile device stores the same time constant in a nanoscale filament instead of a µm-scale capacitor, consumes no standby power to hold it, and gets tunability plus intrinsic stochasticity natively — the paper's central cost argument.
- vs. **non-volatile memristive synapses**: no reset circuit and no capacity saturation from never forgetting, at the cost of being unable to hold long-term weights without extra engineering.

## Known limitations

- Broad, lognormal retention distributions (stochastic filament formation) mean the "time constant" is a distribution, not a value.
- Write is probabilistic: P_ON must be matched to the expected stimulation rate, and store speed and recall accuracy trade off against each other.
- Retention below ~1 s degrades network-level recall performance, so behavioral timescales need large compliance currents (hundreds of µA).
- Demonstrations remain at few-device or simulation scale; endurance, device-to-device variability across arrays, and energy per event are largely unquantified.

## Open problems

- Closed-loop tuning of retention and switching probability against observed spike statistics (task-adaptive timescales).
- Array-scale variability and interconnect parasitics versus the few-device demonstrations.
- On-chip learning rules (STDP and beyond) on volatile synapses rather than fixed store/recall protocols.
- Turning the intrinsic stochasticity/noise into a computationally exploited resource with a measurable capacity benefit.
- Bridging volatility and long-term storage (hybrid volatile/non-volatile stacks) without duplicating reset circuitry.

## Relationship to foundations

Builds on conductive-filament resistive switching (metal-ion drift/diffusion, threshold switching with a hold voltage) and on the theory of short-term synaptic plasticity — Tsodyks/Markram-style synapses with finite trace decay and the synaptic theory of working memory. The device physics is the classic diffusive/threshold-switching regime long used for selectors; the conceptual contribution is treating its decay as a designable temporal weight.

## Realized by

- None recorded yet.

## My understanding

The concept's pivot is that a *loss* mechanism is the computation: the conductive filament's spontaneous dissolution is exactly the exponential-ish trace that STP models need, so tuning the filament diameter with the compliance current is tuning the synapse's time constant. That makes time a device parameter rather than a circuit parameter — but it also imports filament physics into the network's behavior (broad retention distributions, probabilistic writes), which is why every useful demonstration ends up co-designing device operating point and network protocol instead of treating the synapse as an ideal component.
