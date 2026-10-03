---
{"dg-publish":true,"permalink":"/papers/tunable-synaptic-working-memory-volatile-memristive/","title":"Tunable Synaptic Working Memory with Volatile Memristive Devices","tags":["neuromorphic","artificial-synapse","memristor","volatile-memristor","working-memory","short-term-plasticity"],"dg-note-properties":{"title":"Tunable Synaptic Working Memory with Volatile Memristive Devices","slug":"tunable-synaptic-working-memory-volatile-memristive","arxiv":"2306.14691","venue":"Neuromorphic Computing and Engineering","year":2023,"tags":["neuromorphic","artificial-synapse","memristor","volatile-memristor","working-memory","short-term-plasticity"],"importance":3,"date_added":"2026-09-30","source_type":"tex","tldr":"A C/HfO2/Ag threshold-switching memristive device whose retention time (1 ms to 10 s) and switching probability are both electrically tunable is used as a volatile synapse for working memory: a five-device hardware store/recall demo reaches >90% classification accuracy, and device-measured parameters drive simulations of a Mongillo-style biological working-memory network and an associative symbolic working memory.","contribution_type":["method","application"],"datasets":[],"cited_by":[]}}
---

## Problem & Context

Working memory holds information for seconds and must forget it again on a matching timescale: real tasks — visual processing, language comprehension, episodic planning — need time constants spanning milliseconds to minutes, and a memory that never fades saturates its capacity and cannot accept new items. In hardware, that flexibility is expensive. CMOS neuromorphic circuits synthesize temporal dynamics by charging and discharging a capacitor with a constant current, so at biologically relevant time constants the capacitor area becomes non-negligible and the circuit keeps burning power; digital (GPU/FPGA) and subthreshold-ASIC alternatives add clock latency or complexity. On the device side, non-volatile memristive synapses had already shown promising results, but they need extra reset circuitry (area + power) to forget, and volatile memristive devices — which could supply the forgetting natively — had been explored mainly for reservoir computing and selector/security applications, with short-term-memory systems "still at its infancy". What was missing was a volatile synapse whose timescale is not fixed by fabrication but can be reconfigured per task.

## Key idea

Use the volatility itself as the memory. In an Ag-based threshold-switching (diffusive) memristor the stored item *is* the conductive filament: a pulse above threshold forms it, and below the hold voltage it dissolves on its own. Because the filament's lifetime grows with the compliance current that sets its diameter, and because the probability of forming it grows with pulse amplitude/width and with pulse-burst number, both defining parameters of the "memory" — how long it lasts and how easily it is written — are electrical knobs rather than material constants. So one device replaces a bank of reconfigurable capacitors: retention time tunes from ~1 ms to 10 s, write probability tunes per pulse, and the resulting stochastic, decaying trace reproduces the short-term-plasticity dynamics that synaptic theories of working memory assume — with device noise cast as a resource (biological synapses are themselves unreliable) rather than a defect.

## Method

- **Device**: one-transistor/one-resistor cell on a foundry MOS transistor; 70 nm × 70 nm graphitic-carbon bottom electrode, 10 nm HfO2 active layer and 100 nm Ag top electrode e-beam-evaporated at room temperature without breaking vacuum. No electroforming step (a 0 → 1.5 V quasi-static sweep sets the device); ON/OFF ratio ~10^8; operating voltages < 3 V (CMOS compatible). The series NMOS gate sets the compliance current I_CC, which controls filament diameter and hence retention.
- **Device characterization**: DC sweeps on a HP 4156C; pulsed experiments on a TTI TGA12104 waveform generator with a LeCroy Waverunner 640Zi reading the drop across a 50 Ω resistor (MATLAB control). Retention measured after a 10 ms / 5 V triangular set pulse, monitored at −150 mV, for I_CC = 10–70 µA, 100 repetitions per setting in random order. Switching probability P_ON measured over 100 pulses per (amplitude, width) combination and fit with an error-function CDF; burst statistics fit with P_ON(N) = 1 − (1 − P_ON(1))^N.
- **Small-scale hardware working memory**: five volatile 1T1R synapses wired in parallel into one integrating neuron; each color/pattern is encoded by stimulating a 3-of-5 device combination; the neuron fires when summed LRS current crosses a threshold. I_CC = 17 µA (≈28 ms median retention), store/recall at f_stim = 50 Hz and P_ON = 5%, each condition repeated 10 times.
- **Synapse model for simulation**: a phenomenological STP model — binary state x_i ∈ {0,1}, per-synapse switching probability ρ_i, and lognormal retention times (µ = 7.24, σ = 0.82 ⇒ mean ≈ 1.5 s) fitted to the measured distributions — implemented as a custom NEST 2.14 synapse in Python 3.8, 1 ms time step.
- **Biologically inspired working-memory network**: the Mongillo et al. (2008) recurrent model adapted to that synapse: 8000 excitatory + 2000 inhibitory LIF neurons, five memory items of 800 strongly connected excitatory neurons each, static inhibition, 1000 item-specific input neurons at 0.1 Hz baseline, and Gaussian noise tuned (as in Mongillo) to make the network multistable.
- **Associative symbolic working memory**: 8 LIF memory neurons over three categories (shape, texture, color) with bidirectional associative links, one model memristive device per association plus series input/output threshold gates for routing, and one lateral inhibitory neuron per category to enforce item exclusivity.

## Experiment & Results

- **Device knobs work as claimed**: median retention time grows exponentially with I_CC and is tunable from ms to seconds; P_ON rises with pulse amplitude (µ fitting from 2.31 V at 50 ns width down to 0.59 V at 5 ms) and with the number of pulses in a burst, i.e. burst stimulation accelerates the store phase.
- **Hardware store/recall**: with P_ON = 5% and f_stim = 50 Hz the network classifies stored vs. non-stored patterns with > 90% accuracy over a test sequence; after ~1 s without stimulation all devices switch off and the pattern is forgotten. Accuracy degrades at higher P_ON (non-cued devices switch on spuriously) and, at low P_ON, at low spike rates (cued devices decay too early); average current mismatch over 100 patterns quantifies progressive forgetting for each (P_ON, f_stim) condition.
- **Large-scale simulation**: a stored item is recalled ~1 s after store with strongly elevated firing in its 800-neuron ensemble, while the network stays silent during timeouts and can then store an item without interference. Recall SNR (item-specific vs. other population firing rate) drops sharply for retention times below ~1 s, and P_ON ≈ 0.05 is optimal because it avoids spurious device activation — matching the hardware optimum.
- **Associative symbolic memory**: after storing an object ("smooth, red cylinder"), cueing with any single feature reactivates the other features; decoding error versus store-to-recall delay gives a reliable recall window of ~600 ms, corresponding to I_CC = 70 µA.
- **Headline**: one device family covers task-specific working-memory lifetimes from 1 ms to 10 s by selecting I_CC and pulse amplitude, with no change of materials or extra reset circuitry.

## Limitations

- The only physical demonstration is five devices into one threshold neuron — no array-scale hardware, no on-chip learning, and the neuron/recognition logic is external; every larger result is a simulation driven by measured device parameters.
- Store and recall pull P_ON in opposite directions: higher P_ON shortens the store phase but raises recall errors, so operating point must be hand-matched to stimulation rate; during two consecutive stores only the second item is safely retained.
- Strong stochasticity is both the feature and the cost: retention distributions are broad (lognormal), devices within the same pattern do not switch together, and retention < ~1 s collapses network recall SNR.
- Device parameters must be re-tuned when the expected spike rate changes; adaptive/co-on-line tuning of retention and P_ON is suggested but not implemented.
- Fabrication and evidence gaps: device-to-device variability across the five cells is not systematically characterized, endurance/cycling is not reported, and the simulation code is only "available upon publication".

## Open questions

- Can the (I_CC, P_ON) operating point be adapted online to the observed stimulation statistics instead of being set per task in advance?
- Does the >90% five-device accuracy and the simulated SNR survive array-scale device-to-device variability and interconnect parasitics?
- Can the same volatile synapses support on-chip learning rules (e.g. STDP) rather than fixed store/recall protocols?
- Is the noise-as-computational-resource claim quantifiable — does stochastic filament switching improve capacity or robustness versus an ideal deterministic volatile synapse?
- What is the energy per store/recall event compared with the CMOS capacitor alternative the paper argues against?

## My take

The clean move is reframing volatility from a defect into a reconfigurable resource: the filament's diameter becomes a time constant and its stochastic formation becomes a write probability, so "forgetting" is engineered the same way ordinary device parameters are. The paper is unusually honest about the coupling between store speed and recall accuracy — that trade-off, not raw retention, is the real design variable, and it is exactly what a capacitor bank cannot tune cheaply. The evidence chain is the weak part: the interesting claims (biological working memory, symbolic association) live in NEST simulations parameterized by five devices, so the paper demonstrates plausibility of the technology rather than a working neuromorphic system. As an existence proof that volatile memristors can carry the timescale-matching role that synaptic theories of working memory demand, it is a solid anchor for the volatile-synapse line of work.

## Related

- [[concepts/volatile-memristive-synapse\|volatile-memristive-synapse]]
