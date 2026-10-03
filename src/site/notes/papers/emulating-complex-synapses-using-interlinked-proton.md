---
{"dg-publish":true,"permalink":"/papers/emulating-complex-synapses-using-interlinked-proton/","title":"Emulating Complex Synapses Using Interlinked Proton Conductors","tags":["neuromorphic","artificial-synapse","proton-conductor","synaptic-transistor","complex-synapse","continual-learning"],"dg-note-properties":{"title":"Emulating Complex Synapses Using Interlinked Proton Conductors","slug":"emulating-complex-synapses-using-interlinked-proton","arxiv":"2401.15045","venue":"Physical Review Applied","year":2025,"tags":["neuromorphic","artificial-synapse","proton-conductor","synaptic-transistor","complex-synapse","continual-learning"],"importance":3,"date_added":"2026-09-30","source_type":"pdf","tldr":"A PEDOT:PSS/Nafion proton transistor with series-coupled storage compartments experimentally realizes the Benna-Fusi complex synapse, showing diffusion-driven memory consolidation and, in face-familiarity network simulations, familiarity-memory lifetimes over 20x longer than single-variable synapses at matched state count.","contribution_type":["method","application"],"datasets":["VGGFace2"],"cited_by":[]}}
---

## Problem & Context

Neuromorphic hardware is pushed by an energy gap (20 W for a brain vs. 170 kW for AlphaGo) and by a modelling gap: mainstream artificial synapses are single-variable devices inspired by Hopfield-style rate networks, whose memory capacity for low-precision weights scales only as the square root of the number of synapses, and whose learning trajectories are independent of past experience — so training a second task overwrites the first (catastrophic forgetting). Theory had already moved ahead: the Benna-Fusi complex-synapse model (2016) gives each synapse hidden variables that store traces at progressively longer timescales, transferring memories from fast to slow variables by diffusion-like dynamics, which lifts online-learning capacity to near-linear scaling in synapse count and, through metaplasticity, supports continual learning of sequential tasks. But the model existed only in simulation — hardware synapses (memristors, electrochemical and electrolyte-gated transistors) were overwhelmingly single-variable, so nothing on chip could exploit the consolidation dynamics the theory predicted.

## Key idea

Map the Benna-Fusi cascade of coupled beakers onto real storage compartments: build a proton (redox) transistor whose weight-bearing channel is fed by a *series of diffusion-coupled proton reservoirs*. Proton concentration in the first PEDOT:PSS compartment is the synaptic weight (read out as channel conductivity); Nafion bridges between compartments let protons diffuse with coupling coefficients set by their lateral length and by compartment size, so compartments C2..C4 act as the hidden variables with distinct timescales. Because charge flows back from the reservoirs after a write, the device's weight is pulled toward its own history — memory consolidation emerges from the same physics (diffusion) that the model posits, rather than from an added control loop.

## Method

- **Device stack**: 5/100 nm Ti/Au interconnects by lift-off on Si/SiO2 (300 nm), ~3 um Parylene-C shadow layer, photolithography + O2-plasma etching to define the transistor channel/gate and the exposed areas of the auxiliary storage components, PEDOT:PSS (with 5 vol% ethylene glycol + 1 vol% GPTMS crosslinker) spin-coated at 1000 RPM/120 s and baked at 125 C, Parylene-C peeled off to leave patterned compartments; gel Nafion drop-cast as electrolyte *and* proton-diffusion medium between compartments. Arrays were fabricated on a 2-inch wafer.
- **Write/read**: writes are electrochemical redox pulses on gate G through the reservoir R (typically -/+1 V with variable "on" fraction at 1 Hz); reads measure source-drain conductance at 0.01 V (resistivity of PEDOT:PSS is near-linear in proton concentration). Characterization with an Autolab PGSTAT302N potentiostat and an AFG1062 waveform generator (50 MOhm series resistance to suppress gate leakage), ambient conditions.
- **Modelling**: the Benna-Fusi system C du/dt = G u + input is solved in closed form by eigen-decomposition of H = C^-1/2 G C^-1/2 in MATLAB, including pulse duty cycle; coupling coefficients (g12, g23, g34) are extracted by fitting the simulated weight transient to measured data.
- **Task-level evaluation**: face familiarity detection on VGGFace2 — frozen SE-ResNet-50 features (2048-d, PCA-reduced to N, binarized) feed N Hebbian memory neurons; detection by Hamming distance. Four networks with matched total dynamic-variable count: simple synapses (N = 128^2, m = 1) at learning rates q = 1, 0.2, 0.05 vs. complex synapses (N = 64^2, m = 4) at q = 1, with C1:C2:C3:C4 = 1:1:2:4.

## Experiment & Results

- **Single-variable baseline**: potentiation/depression under -/+1 V pulses follows the programmed "on" fraction (33/50/67%); updates are nonlinear and asymmetric at large dynamic range — 80 pulses potentiate but ~108 are needed to return — with the per-pulse update s shrinking near the extremes.
- **Consolidation signature**: after one +3 V, 1 s write, the single-variable synapse shows essentially no drift, while the complex synapse (with C2) recovers ~40% of the weight change within 160 s; the fitted coupling is g12/C1 ~ 2^-7.5 per second. The reservoir behaves like a spring back toward the previous state.
- **Regularizing effect of C2**: with C2 connected, the same 80-pulse training produces a smaller total weight change and a shorter time to return to the original level in both potentiating-first and depressing-first protocols (Figs. 3b-c, 3f-g) — the coupled reservoir damps writes in both directions.
- **More compartments, shorter recovery**: the C1-2 device returns to baseline in 37/42/46 s across on-fractions under an 80-pulse depression, the C1-4 device (C2, C3, C4) in 21/23/24 s, with extracted couplings g12 : g23 : g34 ~ 2^-6 : 2^-7 : 2^-8; total depression-induced weight change also shrinks as compartments are added (Fig. 4).
- **Idealized simulations**: repeated potentiation/depression cycles on a complex synapse do not reproduce their own first cycle until a periodic u1-u2 (or u1-u4) steady state develops over many cycles; per-cycle dynamic range falls as compartments are added, matching experiment.
- **Face familiarity network (simulated dynamics, measured parameters)**: at equal learning rate q = 1 the complex-synapse network's familiarity memory lifetime t* is >20x that of the simple-synapse network for same-pose and random-pattern tests and >4x for different-pose tests, and it still beats a simple-synapse network slowed to q = 0.05 (which gains lifetime only by losing initial accuracy and generalization); forced-choice tests show the same ordering. ioSNR/rSNR agree (Fig. S6), and more dynamical variables per synapse help further (Fig. S7).

## Limitations

- The network-level claims are simulations driven by device-measured parameters: no closed-loop on-chip learning, no array running the task, and no direct multi-task continual-learning (forgetting) experiment — the catastrophic-forgetting motivation is illustrated, not measured.
- The headline lifetime gain is under a matched *state count*, not matched area or energy; energy per update is not reported.
- Fabrication mixes lithography with manual drop-casting of Nafion; compartment count is limited to four, feature sizes are hundreds of micrometers, and device-to-device variability across the 2-inch array is not quantified.
- Weight updates stay nonlinear and asymmetric (potentiation vs. depression differ), and retention is finite — consolidation slows forgetting but does not make the weight permanent.
- Humidity/ambient dependence and endurance over many cycles are untested; code and data are "available upon reasonable request" only.

## Open questions

- Does the near-linear capacity scaling predicted by Benna-Fusi actually appear in a physical network of these devices, or do nonlinearity and variability erase it?
- Can the device run a genuine sequential multi-task protocol and show reduced forgetting on-chip (rather than in simulation)?
- How far can the compartment cascade scale (more than four, tighter coupling hierarchies) before fabrication variability and leakage dominate?
- What is the energy cost per consolidation event and per read, and can Nafion/PEDOT:PSS be replaced by faster or less humidity-sensitive proton conductors?
- Can the same multi-reservoir idea be transplanted to other ion-conducting or memristive platforms where diffusion is available?

## My take

The strong move is that the hardware *is* the model: the Benna-Fusi equations are a diffusion cascade, and interlinked proton compartments realize that cascade natively, so fitting is a parameter extraction rather than a phenomenological patch. That makes the observed ~40% recovery after a single pulse a genuine physics-level validation of the consolidation picture, not just a device curve. The weak link is the evidence chain's last step — every "continual learning" claim runs through a simulation, and the paper never measures forgetting across sequential tasks, which is the thing it set out to solve. Still, as a bridge from a theoretical-neuroscience synapse model to a fabrication recipe, it is one of the cleaner examples in the neuromorphic-hardware literature.

## Related

- [[concepts/proton-conductor-artificial-synapse\|proton-conductor-artificial-synapse]]
