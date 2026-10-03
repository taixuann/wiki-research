---
{"dg-publish":true,"permalink":"/papers/organic-nanoparticle-transistor-behaving-biological-spiking/","title":"An Organic Nanoparticle Transistor Behaving as a Biological Spiking Synapse","tags":["neuromorphic","artificial-synapse","organic-electronics","synaptic-transistor","short-term-plasticity","nanoparticle-memory"],"dg-note-properties":{"title":"An Organic Nanoparticle Transistor Behaving as a Biological Spiking Synapse","slug":"organic-nanoparticle-transistor-behaving-biological-spiking","arxiv":"0907.2540","venue":"Advanced Functional Materials","year":2010,"tags":["neuromorphic","artificial-synapse","organic-electronics","synaptic-transistor","short-term-plasticity","nanoparticle-memory"],"importance":4,"date_added":"2026-09-30","source_type":"pdf","tldr":"A pentacene field-effect transistor whose channel holds a self-assembled network of charge-storage gold nanoparticles (NOMFET) reproduces biological short-term plasticity — the same device can be programmed to facilitate or depress, its frequency response is tuned from 0.01 to 10 Hz by channel length and nanoparticle size, and an iterative Varela-style synapse model fits the measured spike trains.","contribution_type":["method","application"],"datasets":[],"cited_by":[]}}
---

## Problem & Context

Von Neumann machines separate processing from memory, so the brain's spatiotemporal style of computation — memory and computation mixed in the same elements, weighted by activity history — does not map onto them. CMOS neuromorphic circuits can emulate neural behaviour, but they pay in transistors: at least seven silicon transistors are needed per electronic synapse, while brains have far more synapses than neurons, so a CMOS-only route never reaches brain-scale connectivity at reasonable area or power. By 2009 the field had proposals for nanoscale programmable synaptic elements — optically gated CNTFETs, organic/hybrid silicon-nanowire transistors, and the just-arrived memristor (Strukov et al. 2008) — but none of them was an organic, bottom-up-assembled device, and none had shown the *frequency-dependent* filtering behaviour (short-term plasticity, STP) that biological synapses show for free.

On the modelling side the target was already well specified: Tsodyks/Markram and Varela/Abbott had phenomenological models in which a synapse has a finite resource of neurotransmitter, each spike consumes a fraction of it, and resources recover with a time constant — depressing or facilitating responses to a spike train then follow purely from the interval between spikes. What was missing was a physical device whose own charge dynamics implement that equation.

The same group had already built the memory half of the problem: a nanoparticle-in-pentacene transistor that stores charge for seconds to ~10^3 s (Novembre et al., Appl. Phys. Lett. 92, 103314, 2008) — a leaky memory. This paper asks whether that leak is the feature, not the bug.

## Key idea

Use the stored charge itself as the neurotransmitter. Gold nanoparticles (5–20 nm) immobilized in the source–drain channel of a pentacene FET act as nanoscale capacitors: gate spikes inject holes into the nanoparticles, the trapped charge repels holes in the pentacene channel and shifts the Fermi level, and the transistor's own transconductance amplifies that shift into a channel-current change. The nanoparticle network leaks charge with a time constant of seconds, so the "weight" relaxes on its own — exactly the trace-decay term of an STP model. Because a transistor is a multiplier, the device directly computes S_j = w_ij S_i with a time-dependent w_ij. Programming the nanoparticle charge polarity (or letting the spike train itself charge/discharge the particles) selects a depressing or a facilitating synapse on the *same* hardware, and geometry — channel length L = 200 nm–20 µm, nanoparticle diameter 5–20 nm — sets the working frequency band (0.01–10 Hz).

## Method

- **Device**: bottom-gate, bottom-contact organic transistor on p++ Si / 200 nm thermally grown SiO2 (10 nm oxide for the 200 nm-channel devices). Ti/Au (20/200 nm) electrodes by vacuum evaporation + optical lithography (L = 1–20 µm); e-beam lithography for L = 0.2 µm.
- **Nanoparticle self-assembly**: SiO2 functionalized with an amino-terminated SAM (APTMS, 60 °C, 4 min in toluene) for 10/20 nm citrate-stabilized Au NPs, or vapor-deposited MPTS for 4–5 nm dodecanethiol-capped Au NPs; overnight deposition from colloidal solution, then 1,8-octanedithiol ligand exchange to interconnect the particles. NP density (10^10–10^12 cm^-2) is tuned by solution concentration and reaction time; ~10^11 cm^-2 is the synaptic-operating window (below: too little memory; above percolation: metallic source–drain shorts and gate screening).
- **Channel**: 35 nm pentacene evaporated at 0.1 Å/s at room temperature; reference devices without NPs (and a SAM-only control) fabricated in the same run.
- **Measurement**: Agilent 4155C parameter analyzer + Tabor 5061 pulse generator, probed in an N2 glovebox (<1 ppm O2/H2O). Programming phase: gate pulse V_P with source/drain grounded. Working phase: DC V_G with a spiking train (V_D1→V_D2) on the drain; alternatively the gate receives the same spike train as the drain ("pseudo two-terminal" mode, no pre-programming).
- **Model**: Vissenberg–Matters percolation conduction for the disordered pentacene film, extended so that Coulomb repulsion from the trapped nanoparticle holes shifts site energies / the Fermi level by an amount proportional to stored charge — giving G = A0 e^(−βΔF). Spike dynamics are then the simplest Varela/Abbott-style iteration: I_(n+1) = I_n K e^(−(T−P)/τ_d) + I0 (1 − e^(−(T−P)/τ_d)) K, with K the per-spike multiplicative depression, τ_d the nanoparticle discharge constant, T the spike period and P the pulse width.

## Experiment & Results

- **Process window**: synaptic behaviour appears for NP densities ~10^11–10^12 cm^-2 with all three NP sizes; devices with aggregated (non-uniform) NP layers still show it, which the authors read as defect tolerance of the mechanism. Reproducibility ~100% for 10/20 nm particles, only 50% for 5 nm.
- **Transistor cost of the storage layer**: the reference pentacene FET gives I_D ≈ 1.8×10^-4 A and mobility ≈ 0.13 cm^2 V^-1 s^-1, while NOMFETs drop to ≈ 10^-3 cm^2 V^-1 s^-1 (5/10/20 nm: 2×10^-3, 7.6×10^-4, 2.0×10^-3) with much larger dispersion — the nanoparticles and SAM disorder the pentacene (smaller grains by TM-AFM). Threshold shift after a −50 V / 30 s gate pulse: 7.5 / 9.4 / 12.8 V for 5 / 10 / 20 nm NPs (1.1 V for the reference), i.e. roughly 2, 6 and 15 holes per nanoparticle.
- **Programmable facilitation vs. depression (Figs. 4–5)**: on one device, discharging the particles with V_P > 0 before a 0.05 Hz spike train gives a monotonically decreasing response (depressing); charging them with V_P < 0 gives an increasing response (facilitating). Same bias conditions, opposite programmed history — and the same is reproduced with 20 nm particles and with aggregated networks.
- **Unprogrammed STP (Fig. 6)**: in pseudo-two-terminal mode the spike train itself charges/discharges the particles. For L = 12 µm, 5 nm NPs (τ_d ≈ 20 s), trains at 0.5 Hz and 2 Hz depress (T ≪ τ_d, charge accumulates), while a 0.05 Hz train facilitates (particles empty between spikes) — the frequency dependence of a biological depressing synapse. Reference pentacene FET with no NPs shows no such behaviour (Fig. S4).
- **Model fits and tuning knob**: one parameter set per device fits three consecutive trains (τ_d ≈ 20 s, K = 0.9, I0 = 4.1×10^-9 A for L = 12 µm; τ_d ≈ 3 s, K = 0.99 for L = 2 µm; τ_d ≈ 0.9 s, K = 0.98 for L = 200 nm). τ_d scales mainly with channel length (RC set by channel resistance), only weakly with NP size, matching independent charge/discharge measurements; together L = 200 nm–20 µm and 5–20 nm NPs span a 0.01–10 Hz working band.
- **Classification**: the authors argue the conductance is history-dependent through stored charge, i.e. the NOMFET is closer to a charge-controlled memristor/memconductance than to a memcapacitor (Di Ventra et al., Proc. IEEE 2009), and that the fitted iteration is SPICE-implementable for hybrid NOMFET/CMOS circuit design.

## Limitations

- **Voltages are huge**: programming at ±50 V, drain trains at −20/−50 V — nowhere near the sub-3 V, CMOS-compatible regime that memristive synapses were already targeting in the same year.
- **Large device penalty**: storing charge costs 2–3 orders of magnitude in mobility/current (0.13 → ~10^-3 cm^2 V^-1 s^-1) and adds heavy device-to-device dispersion.
- **Device-level demonstration only**: no array, no network task, no learning rule (no STDP), no energy-per-spike figure, and no comparison against a CMOS or memristor synapse on a common metric.
- **Short-term only**: weights decay in ~0.9–20 s by construction; nothing here addresses long-term potentiation or non-volatile weights.
- **Weak control of the time constant**: τ_d depends on channel length but also on nanoparticle count and on an uncontrolled ligand (tunnel) barrier; the paper says a distributed 2-D RC-network model and systematic ligand-length studies would be needed.
- **Fabrication**: glovebox-only organic processing, shadow/lithography mix, 50% yield for 5 nm particles, no endurance or humidity data; the single-exponential discharge is an approximation whose residuals are acknowledged.

## Open questions

- Can the device execute an actual learning rule (STDP or rate-coded Hebbian learning) in a network, rather than respond to externally generated trains?
- Can the same leaky-charge mechanism be realized at CMOS-compatible voltages (electrolyte gating, thinner dielectric, smaller particles)?
- Is τ_d engineerable independently of geometry — e.g. by tailoring the alkanethiol tunnel barrier — so the frequency band becomes a design parameter rather than a fabrication by-product?
- Does the NOMFET behave as a charge-controlled memristor or as a memcapacitor under the Di Ventra taxonomy, and does the distinction matter for circuit reuse?
- What are the energy per synaptic event and the array-scale yield/variability compared with volatile memristors and electrolyte-gated synaptic transistors?

## My take

The conceptual move is one line long and easy to miss: a leaky memory is a short-term synapse if the device that reads it is a multiplier. By embedding charge-storage nanoparticles in the channel of an ordinary transistor, the paper gets neurotransmitter-like state (trapped holes), spontaneous recovery (tunneling leakage), transistor gain for free, and — because the stored charge can be written either polarity — a hardware switch between facilitating and depressing behaviour on the same cell. Fitting a textbook Varela iteration to three consecutive spike trains with one parameter set is the right kind of evidence: it ties device physics to a neuroscience model quantitatively rather than by analogy. The weaknesses are the obvious 2009-organic-electronics ones (±50 V, mobility collapse, single devices, no learning rule), and they are exactly what the next decade of organic/electrolyte-gated synaptic transistors set out to fix. Historically it also sits at the fork where the field had to decide whether nanoscale synaptic devices are "memristors" or something else — the paper answers "charge-controlled memristor, probably", which reads as an early sign that the memristor label was being stretched to cover all history-dependent nanodevices.

## Related

- [[concepts/nanoparticle-organic-memory-transistor-synapse\|nanoparticle-organic-memory-transistor-synapse]]
- [[people/fabien-alibart\|fabien-alibart]]
- [[people/dominique-vuillaume\|dominique-vuillaume]]
