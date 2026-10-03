---
{"dg-publish":true,"permalink":"/concepts/nanoparticle-organic-memory-transistor-synapse/","title":"Nanoparticle organic memory transistor synapse","tags":["neuromorphic","artificial-synapse","organic-electronics","synaptic-transistor","short-term-plasticity","nanoparticle-memory"],"dg-note-properties":{"title":"Nanoparticle organic memory transistor synapse","aliases":["NOMFET","nanoparticle organic memory field-effect transistor","organic nanoparticle transistor synapse","charge-storage nanoparticle synapse","memristive nanoparticle/organic hybrid synapse"],"tags":["neuromorphic","artificial-synapse","organic-electronics","synaptic-transistor","short-term-plasticity","nanoparticle-memory"],"maturity":"active","definition":"An artificial synapse built from a field-effect transistor whose organic channel contains a self-assembled network of charge-storage nanoparticles, so that charge trapped by presynaptic spikes shifts the transistor's threshold and conductance while its spontaneous leakage decays the weight — a three-terminal, transistor-gain-amplified implementation of short-term plasticity.","key_papers":["[[papers/organic-nanoparticle-transistor-behaving-biological-spiking]]"],"related_concepts":["[[concepts/proton-conductor-artificial-synapse]]","[[concepts/volatile-memristive-synapse]]"],"first_introduced":"2009 (arXiv:0907.2540; Adv. Funct. Mater. 20, 330, 2010)","date_updated":"2026-09-30"}}
---

## Definition

A three-terminal organic transistor (typically pentacene channel, bottom gate) in which a bottom-up-assembled layer of metal nanoparticles (Au, 5–20 nm) inside the source–drain channel stores charge injected by gate spikes. The trapped charge Coulomb-repels the channel carriers, shifting the Fermi level / threshold, and the transistor's transconductance amplifies that shift into a channel-current change. Because the nanoparticle network leaks charge over seconds, the conductance — the synaptic weight — relaxes on its own, giving volatile, history-dependent weighting of a spike train.

## Intuition

The nanoparticles are the neurotransmitter vesicles: spikes fill them, leakage empties them, and the drain current reads out how full they are. The transistor supplies two things a bare memory element does not have — gain (a few stored charges move the whole channel current) and multiplication (I_DS = G(V_history)·V_DS, i.e. the synapse's w·s product). Volatility, which would be a defect in a memory, is precisely what makes the device a *short-term* synapse: depression is charge accumulating faster than it leaks (spike period ≪ discharge time), facilitation is the particles emptying between spikes (period ≫ discharge time).

## Variants

- **Programmed mode**: an initial gate pulse charges (facilitating) or discharges (depressing) the nanoparticles before the spike train; the same device shows either behaviour.
- **Unprogrammed / pseudo two-terminal mode**: gate and drain receive the same train, so the train writes its own state — closer to an autonomous biological synapse.
- **Geometry-tuned variants**: channel length 200 nm–20 µm and particle diameter 5–20 nm set the discharge time constant (≈0.9–20 s) and hence the 0.01–10 Hz operating band.
- **Later "Synapstor"/NOMFET follow-ups**: the same charge-storage channel used for spike detection and hybrid NOMFET/CMOS associative circuits (Bichler, Zhao, Alibart et al., referenced as in-preparation in the 2009 paper).
- **vs. non-volatile nanoparticle memories**: identical stack, but retention engineered to persist — a memory, not a synapse (the group's own APL 2008 precursor).

## Comparison

- vs. **`[[proton-conductor-artificial-synapse]]`**: both are three-terminal gate-written volatile transistor synapses; the protonic device's weight is a distributed interfacial ion profile (millivolt-scale EDL gating, humidity-dependent), the NOMFET's is trapped electronic charge in discrete capacitors (self-assembled, no electrolyte, but tens-of-volts gating).
- vs. **`[[volatile-memristive-synapse]]`**: both get short-term plasticity from a state that decays on its own, but the volatile memristor's state is a single stochastic conductive filament in a two-terminal resistor, whereas the NOMFET's is distributed charge read out through a transistor — analog and amplifiable, at the cost of a three-terminal device and large operating voltages.
- vs. **CMOS synapse circuits**: one device replaces the ≥7 transistors per emulated synapse and is assembled bottom-up on plastic-compatible organic films; costs are high write voltage, low mobility and no demonstrated learning rule.

## Known limitations

- Operating voltages of tens of volts for programming and spike trains.
- Nanoparticles and SAMs disorder the organic film: mobility falls from ~0.13 to ~10^-3 cm^2 V^-1 s^-1 with much larger device dispersion.
- Discharge time constant is only indirectly controllable (set by channel resistance, particle count, and an uncontrolled ligand/tunnel barrier), so the frequency band is a fabrication outcome, not a calibrated knob.
- Short-term only — no long-term weight; no array-scale, learning-rule or energy-per-event demonstration.

## Open problems

- Independent engineering of the discharge time constant (ligand-barrier design) to make the timescale a settable parameter.
- Low-voltage realization of the same charge-storage mechanism (electrolyte/EDL-assisted gating).
- Hardware learning rules (STDP, rate-coded Hebbian) and network-level tasks on arrays of these devices.
- Settling the device-taxonomy question the paper raises: charge-controlled memristor vs. memcapacitor.
- Yield and variability across arrays; energy per synaptic event versus volatile memristors.

## Relationship to foundations

Stands on organic field-effect transistor physics (disordered pentacene channel, percolation transport as described by Vissenberg–Matters) plus floating-gate-like charge storage in nanoscale capacitors, and maps it onto the standard short-term-plasticity models of computational neuroscience (Tsodyks/Markram resource models, Varela/Abbott iterative facilitation–depression equations). It sits at the junction where the artificial-synapse literature and the memristor debate of 2008–2009 met.

## Realized by

- None recorded yet.

## My understanding

The concept's core is a reinterpretation: leaky charge storage in a transistor channel is not a poor memory but a good synapse, because a synapse's defining property *is* a weight that fades with its own timescale. From that follow the two signatures the paper demonstrates — frequency-dependent depression/facilitation and programmability of polarity — and the device taxonomy debate. What keeps it from being a general-purpose artificial synapse is that everything the concept needs (gain, volatility, multiplier) comes packaged with everything organic electronics in 2009 struggled with (high voltage, disorder, variability).
