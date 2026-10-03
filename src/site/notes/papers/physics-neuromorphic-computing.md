---
{"dg-publish":true,"permalink":"/papers/physics-neuromorphic-computing/","title":"Physics for neuromorphic computing","tags":["neuromorphic","artificial-synapse","memristor","crossbar","spintronics","photonics","review"],"dg-note-properties":{"title":"Physics for neuromorphic computing","slug":"physics-neuromorphic-computing","arxiv":"2003.04711","venue":"Nature Reviews Physics","year":2020,"tags":["neuromorphic","artificial-synapse","memristor","crossbar","spintronics","photonics","review"],"importance":4,"date_added":"2026-09-30","source_type":"pdf","tldr":"A Nature Reviews Physics review arguing that brain-scale neuromorphic hardware requires reinventing electronics with device physics — memristive crossbars, Mott/phase-change, ionic, spintronic, photonic and superconducting nanodevices — and setting out the co-design, variability and scaling challenges on the way to million-device networks.","contribution_type":["survey"],"datasets":[],"cited_by":[]}}
---

## Problem & Context

Neuromorphic computing takes inspiration from the brain to build energy-efficient hardware for information processing, yet current electronics cannot deliver it: the human brain runs on ~20 W while training a state-of-the-art NLP model consumes ~1000 kW·h (the brain's entire six-year energy budget, Box 1). Digital processors separate memory and computing, so AI workloads that move huge data volumes between units hit the von Neumann bottleneck in both speed and energy. CMOS alone emulates the brain badly: dozens of transistors per artificial neuron plus external memory per synapse make devices micrometers wide, so chips can only reach millions of synapses by becoming bulky multi-cubic-meter systems (Spinnaker, BrainScales) whose interconnects burn much of the efficiency gain; CMOS is 2D and fan-out-limited where the brain is 3D with ~10,000 synapses per neuron; and its reconfigurability is dwarfed by the brain's ~10^15 plastic synapses. Before this review the field had two diverging lines of work — mapping AI algorithms onto physical substrates (hybrid CMOS/memristive and photonic deep-network hardware) and neuroscience-inspired devices that add spiking, stochasticity and new learning rules — plus a device zoo (memristors, Mott systems, phase change, 2D materials, organic electrochemistry, spintronics, superconductors, NEMS), but no consolidated account of what physics contributes, which approaches scale, and where the field's real bottlenecks lie.

## Key idea

Building this hardware necessitates reinventing electronics: physics and material science are essential because nanoscale devices can embody neurons and synapses (non-linearity, memory, learnability) directly in their physical state, implement the weighted sum in-situ through Kirchhoff's laws in crossbars, and supply the density, fan-in/fan-out and 3D interconnectivity CMOS cannot. The review organizes the field around two complementary strategies — AI-mapping (efficient inference/training of deep networks on physical substrates) and neuroscience-inspired computing (spikes, dendrites, stochasticity, STDP) — and argues that progress requires algorithms and hardware developed hand in hand, small "toy" systems that surface device-level lessons invisible to theory, and scalable interconnect plus variability-tolerant design for million-device networks.

## Method

This is a review; its "method" is a structured synthesis of device physics and system demonstrations:

- **Device taxonomy (Fig. 2, Table 1)**: synapses via conductive filaments, chalcogenide phase change, van der Waals ionic motion, organic electrochemistry, magnetic Josephson junctions and magnetic tunnel junctions; neurons via Mott/phase-transition spiking, volatile NDR switches with RC/RC-transistor spike generation, stochastic phase-change, superparamagnetic and spintronic oscillators, Josephson flux quantization, and NEMS resonators. Table 1 compares CMOS, resistive-switching, photonic, spintronic and superconductive approaches on connection medium, minimum neuron/synapse size (10 nm spintronic to 100 µm photonic), advantages, disadvantages and chip readiness.
- **Architecture analysis**: memristor crossbars compute the multiply-accumulate by Kirchhoff's laws (two devices per signed weight), with passive-array size limited by sneak paths to a few hundred by a few hundred cells; scaling routes are CMOS-buffered tiled/stacked crossbars, selector devices, 3D crossnets, and optical/wireless/self-assembled interconnect.
- **Learning-vs-physics analysis**: identifies weight precision (sub-0.1% updates under vanishing gradients) and weight-independent (linear) conductance updates as the two device-level obstacles to backpropagation, then catalogues co-adaptations — binary weights, physics-inspired RBMs, device combination, capacitor-assisted weights — and hardware-friendly alternatives such as STDP implemented directly through device physics (pulse-overlap voltage addition, or volatility/Joule-heating-mediated rules).
- **Toy-system case studies**: spintronic nano-oscillator reservoir computing with a single time-multiplexed oscillator (spoken digits), population coding with stochastic superparamagnetic tunnel junctions, and a four-oscillator network classifying spoken vowels by synchronization pattern — used to extract lessons about noise, drift, tunability and variability compensation.

## Experiment & Results

As a review it reports no new experiments; its evidentiary core is the surveyed results:

- **Energy framing**: brain ≈ 20 W, 60 pJ per neuron spike and 26 fJ per synaptic event vs. BERT trained in 80 h on 64 V100 GPUs for the same 1000 kW·h budget (~100 pJ per weight update) (Box 1).
- **Scaled systems**: memristive systems are estimated to train networks with ~100× energy/speed gain over GPUs; million-memristor integrated systems report reasonable but below-software accuracy, one optimized inference chip reaches 94.4% on MNIST, and a fully hardware STDP system implements 1.4M synapses; hybrid (part-software) training remains the norm.
- **Toy-system results**: single spintronic-oscillator reservoir computing reaches state-of-the-art macroscopic-oscillator speech recognition once noise/drift windows are exploited; four coupled spin-torque oscillators classify spoken vowels via synchronization patterns, with device variability compensated in training by the oscillators' tens-of-percent DC-current frequency tunability.
- **Demonstrated device behaviors**: conductive-bridge synapses show short/long-term memory from filament growth/relaxation; Mott and NDR devices reproduce LIF spiking with periodic, chaotic and bursting regimes; memristive coupling synchronizes CMOS neurons; photonic systems demonstrate vowel recognition with phase-change synapses on waveguides.

## Limitations

- As a survey it offers no new measurements, benchmarks or datasets; all numbers are inherited from the cited primary sources and their experimental conditions.
- Coverage is selective: the AI-mapping vs. neuroscience-inspired split and the chosen device families are the authors' framing; the reference list (as extracted) and the table compress a very heterogeneous literature into five technology columns.
- The 100× training gain, sub-pJ energies and scaling arguments are largely projections from simulation/small arrays; large-scale on-chip learning remains undemonstrated at survey time.
- Some technology claims (spintronic/superconductive scalability, photonics below ~100 µm) are explicitly marked "to be demonstrated" (Table 1), so the comparison table mixes measured and aspirational entries.

## Open questions

- Can algorithms and hardware be co-designed hand in hand so learning tolerates noisy, non-linear, variable nanodevices — or even exploits them (stochastic resonance, criticality, in-materio computing)?
- Can STDP-type hardware learning rules be extended from small ensembles to complex multilayer systems?
- Which interconnect strategy — CMOS-mediated routing, 3D crossnets, optical/wireless, or self-assembly — can approach brain-level fan-out without losing the efficiency gains of nanodevices?
- Can device variability become an asset (BrainDrop-style mismatch exploitation, MCMC randomness from cycle-to-cycle variability) rather than something to compensate?
- Will quantum neurons/oscillators cross-fertilize neuromorphic computing, and can physics-based hardware keep pace with fast-moving AI algorithms and improving CMOS AI accelerators?

## My take

The most durable contribution is framing neuromorphic hardware as a physics problem rather than an architecture problem: the same material phenomena that encode the weight (filament growth, phase transition, ion motion, magnetization dynamics) also dictate what learning rules converge, how devices scale, and where variability comes from — which is why the review insists algorithms and substrates be developed together. The two-track map (AI-mapping vs. neuroscience-inspired) plus the honest "toy systems are useful science" defense is a good guide for choosing where a new device idea should plug in. Weaknesses: it is a 2020 snapshot — the million-device chips it calls preliminary have since matured — and its table mixes measured and aspirational numbers, so individual comparisons should be checked against the primary references before reuse.

## Related

- [[concepts/memristive-crossbar-memory-computing\|memristive-crossbar-memory-computing]]
- [[concepts/nanodevice-spiking-neuron\|nanodevice-spiking-neuron]]
- [[concepts/proton-conductor-artificial-synapse\|proton-conductor-artificial-synapse]]
- [[people/danijela-markovic\|danijela-markovic]]
- [[people/alice-mizrahi\|alice-mizrahi]]
- [[people/damien-querlioz\|damien-querlioz]]
- [[people/julie-grollier\|julie-grollier]]
