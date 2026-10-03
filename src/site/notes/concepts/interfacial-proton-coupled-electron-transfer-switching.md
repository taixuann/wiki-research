---
{"dg-publish":true,"permalink":"/concepts/interfacial-proton-coupled-electron-transfer-switching/","title":"Interfacial proton-coupled electron transfer switching","tags":["neuromorphic","memristor","volatile-memristor","proton-conductor","pcet","molecular-electronics"],"dg-note-properties":{"title":"Interfacial proton-coupled electron transfer switching","aliases":["interfacial PCET switching","field-driven PCET switch","proton-coupled electron transfer memristor","double-layer dipole injection switch"],"tags":["neuromorphic","memristor","volatile-memristor","proton-conductor","pcet","molecular-electronics"],"maturity":"emerging","definition":"Volatile threshold switching in an asymmetric solid-state junction where the applied field drives proton-coupled electron transfer across a sub-nanometer electrode/organic contact, so that interfacial deprotonation builds a compact double-layer-like dipole that transiently lowers the carrier-injection barrier and relaxes back when the bias is removed.","key_papers":["[[papers/electric-field-driven-interfacial-proton-coupled]]"],"related_concepts":["[[concepts/volatile-memristive-synapse]]","[[concepts/proton-conductor-artificial-synapse]]"],"first_introduced":"2026 (Nguyen et al., JACS submitted)","date_updated":"2026-09-30"}}
---

## Definition

A two-terminal switching mechanism in which proton motion and electron transfer occur as one coupled interfacial event: under field, a protonated site at the electrode/organic contact (e.g. PDA-H+ at ITO) transfers its proton onto electrode surface hydroxyls while the electron stays in the injection circuit, producing a localized charged species (ITO-OH2+) whose compact dipole lowers the injection barrier. The junction therefore jumps into a low-resistance state above a threshold field, and — because the interfacial protonation is unstable without bias — it relaxes spontaneously to the high-resistance state, giving volatile (self-resetting) threshold switching. No conductive filament and no long-range bulk ion drift are required.

## Intuition

Bulk proton conductors move charge by pushing ions through a matrix — slow, high-voltage, fatigue-prone. Filamentary memristors get volatility from a metal wire that dissolves on its own. This concept puts the ionic event exactly where the potential drop already is: a ~1–2 Å Helmholtz contact sustains ~1 V/Å at sub-volt bias, so the proton transfer that would need 4.6 eV field-free becomes barrierless-ish (~0.4 eV) exactly at the interface, and the resulting dipole is thin enough to shift an injection barrier by the few hundred meV needed for an orders-of-magnitude current jump. Volatility then falls out of thermodynamics — the interfacial protonation state is only stable under field — rather than out of filament geometry or an external reset.

## Variants

- **Protonated-polydopamine/ITO junctions** (the introducing paper): electropolymerized PDA-H+ between ITO and eC/Cu; unipolar switching under positive top bias, slope ≈ 23.6, Vth 0.5–1.1 V, ~10³ rectification, ~300 pJ/event, >10⁶ cycles; charge accounting ties the transient to the electrochemical proton dose.
- **Molecular PCET switches with NDR**: single-molecule / molecular-monolayer junctions where proton-coupled electron transport produces hysteretic negative differential resistance gated by local pH — same interfacial PCET physics, but a static NDR fingerprint instead of a volatile threshold switch.
- **pH-/redox-gated molecular junctions**: chemically tuned acceptor/donor groups at the contact that shift barriers with protonation state, without the field-driven sub-µs dynamics.

## Comparison

- vs. **volatile memristive (filamentary) synapses** (`[[volatile-memristive-synapse]]`): same device phenotype (steep SET, compliance-set ON state, spontaneous reset), but the state variable is an interfacial dipole rather than a dissolving metallic filament — no stochastic filament nucleation, polarity-selective by construction, and the switching charge can be reconciled with an independently measured proton inventory.
- vs. **proton-conductor artificial synapses** (`[[proton-conductor-artificial-synapse]]`): both rely on mobile protons, but there the proton is a *gate* charge that modulates a channel through an electric double layer in a three-terminal transistor; here it is part of the *source-drain injection event itself* in a two-terminal junction, which is why the response is threshold-like and sub-microsecond instead of analog and ms-scale.
- vs. **bulk protonic memristors / VCM devices**: no long-range ion drift through a disordered matrix and no oxygen-vacancy migration, so no fatigue-driven cycle-to-cycle drift — endurance holds at ~10³ ON/OFF over 10⁶ cycles.

## Known limitations

- Demonstrated only in µm-scale (200 × 200 µm²) shadow-mask junctions so far; density and interconnect are untested.
- Threshold-voltage spread of 0.4–1.1 V across junctions/batches; yield is good (~92/100 devices switch for ≥50 cycles) but not array-grade.
- The mechanism is inferred from charge accounting, polarity asymmetry, relaxation kinetics and a cluster-model DFT field argument — no operando observation of the interfacial dipole yet.
- Inherently unipolar in the demonstrated form: the asymmetric contact chemistry that enables switching on one polarity forbids it on the other.
- Volatility time constants are fast (ns-scale turn-on, ~100 ns interfacial transfer) and not yet shown to be tunable into synapse-relevant bands.

## Open questions

- Can the relaxation timescale be tuned (protonation density, hydration, cross-linking, top-contact chemistry) without losing the steep slope and low threshold?
- Can the contact be engineered to make the effect bipolar or complementary, or is asymmetry fundamental to the mechanism?
- Does the same mechanism survive at nanometer contact areas, where the Helmholtz-field argument and the proton/site-density bookkeeping must still hold?
- Can the interfacial dipole be observed directly under bias (operando XPS/IR/Raman)?
- What role do the specific catechol/amine sites of polydopamine play — is PDA a special case, or is any protonatable, hydrogen-bond-rich organic contact sufficient?

## Relationship to foundations

Builds on proton-coupled electron transfer as a general chemistry mechanism (concerted/sequential proton-electron translocation modulating redox potentials), on electric-double-layer/Helmholtz-contact physics at electrode/organic interfaces, and on threshold switching in asymmetric (rectifying) molecular junctions. The new ingredient is using PCET as a *device action* — a field-triggered, self-resetting injection-barrier modulator — rather than as a chemical transformation to be catalyzed or a static transport pathway.

## Realized by

- None recorded yet.

## My understanding

What makes this concept worth its own page rather than a bullet under volatile memristors is the accounting identity at its core: the charge that flows in the switching transient is the same charge that was electrochemically installed as protons, normalized against the electrode's own surface site density. That turns "protons are involved" from a slogan into a measurable conservation law, and it fixes the state variable's location (interface, not bulk) and its capacity (a sub-monolayer). If the identity survives scaling and operando verification, it gives the volatile-switching family a mechanism whose ON/OFF, polarity and endurance can be reasoned about chemically instead of only statistically.
