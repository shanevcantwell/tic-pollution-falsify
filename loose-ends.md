# Loose Ends Log

Tactical decisions from the tic-pollution falsification protocol that didn't qualify for
ADR treatment but are worth remembering.

**Created:** 2026-07-03
**Last updated:** 2026-07-03

---

## 2026-07-03 — Decoding temperatures fixed at {0.7, 1.0}

**Category:** provisional
**Related ADR:** ADR-TPF-001
**Graduation trigger:** If effect sizes diverge materially across temperatures, temperature
becomes a design factor and the choice gets ADR'd with a trade-off analysis.

### Context
Continuations need fixed decoding parameters; two temperatures give a cheap robustness
check without a full sweep.

### Decision
Sample all continuation arms at T=0.7 and T=1.0, analyzed separately.

### Why Not an ADR?
- [x] Hard to reverse? → No; trivially changed any time before pre-registration.
- [x] Real trade-off? → Not analyzed in depth; conventional values chosen for coverage.

---

## 2026-07-03 — k = 3 paraphrase variants per prefix

**Category:** convenience
**Related ADR:** ADR-TPF-001
**Graduation trigger:** If paraphrase-level variance dominates prefix-level variance in the
mixed model, formalize a paraphrase-generation procedure as a design decision.

### Context
Paraphrase choice is a nuisance parameter in the splice arm (ADR-TPF-001); marginalizing over
variants is the mitigation. The *principle* is in the ADR; the count is tactical.

### Decision
Three register-matched honest paraphrases per prefix, authored before any continuations
are sampled.

### Why Not an ADR?
- [x] Hard to reverse? → No; k is a knob.
- [x] Real trade-off? → Cost-vs-variance intuition only; no formal analysis.

---

## 2026-07-03 — Prestige lexicon seeded from the 21 published focal words

**Category:** single-option
**Related ADR:** ADR-TPF-002 (register endpoint)
**Graduation trigger:** Unlikely; lexicon composition is measurement detail, not architecture.

### Context
The register-drift endpoint needs a pre-registered prestige-lexeme list. The
excess-vocabulary literature provides the only published, method-derived list of
LLM-overused focal words.

### Decision
Seed the lexicon with the 21 focal words from the excess-vocabulary work; extend with
generator-specific tics measured from the generator's own base rates during pilot.

### Why Not an ADR?
- [x] Surprising without context? → No; it's the obvious available instrument.
- [x] Real trade-off? → No credible alternative seed list exists.

### Open Questions
- [ ] Which generator-specific extensions make the cut — **Resolution trigger:** pilot
  corpus statistics, frozen at pre-registration.

---

## 2026-07-03 — Power planning assumes baseline PCR of 1–3%

**Category:** provisional
**Related ADR:** ADR-TPF-002
**Graduation trigger:** None; the assumption is designed to be replaced.

### Context
Sample-size math (10³–10⁴ continuations per arm for a 2–3× rate ratio) currently rests on
a guessed base rate for premise consumption.

### Decision
Plan against 1–3% baseline PCR; treat as placeholder.

### Why Not an ADR?
- [x] Hard to reverse? → No; pilot estimate replaces it mechanically at pre-registration.
- [x] Real trade-off? → It's a guess, not a choice among alternatives.

### Open Questions
- [ ] Pilot PCR estimate — **Resolution trigger:** pilot completion; power analysis re-run
  before main data collection.

---

## 2026-07-03 — Natural elicitation first; synthetic prefixes only if confounds appear

**Category:** provisional
**Related ADR:** ADR-TPF-001
**Graduation trigger:** If pilot reveals position/length confounds in naturally elicited
prefixes, prefix-construction strategy becomes a design decision and gets ADR'd.

### Context
Prefixes can be harvested from natural generation (ecological validity) or constructed
synthetically (position/length control). Both are compatible with the splice instrument.

### Decision
Run natural elicitation only; hold synthetic construction in reserve as a contingency.

### Why Not an ADR?
- [x] Hard to reverse? → No; adding a synthetic arm later doesn't invalidate natural data.
- [ ] Surprising without context? → Mildly, but the ADR-TPF-001 rationale covers it.
- [x] Real trade-off? → Deferred rather than decided.

---

## 2026-07-03 — Instrument-validation controls: explicit-claim positive, inert-synonym negative

**Category:** convenience
**Related ADR:** ADR-TPF-002
**Graduation trigger:** Unlikely; standard assay validation.

### Context
The PCR instrument needs sensitivity and specificity checks before results are interpretable.

### Decision
Positive control: prefixes asserting the independence claim explicitly and plainly (must
yield high PCR). Negative control: inert synonym splice, e.g. "large"→"big" (must yield
null on both endpoints).

### Why Not an ADR?
- [x] Surprising without context? → No; obvious once the endpoint exists.
- [x] Hard to reverse? → No; controls can be added or swapped freely pre-registration.

---
