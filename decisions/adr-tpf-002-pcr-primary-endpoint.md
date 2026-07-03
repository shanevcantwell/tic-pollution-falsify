# Use premise-consumption rate (PCR) as the primary endpoint

**Status**: `accepted`
**Date**: 2026-07-03
**Revised**: 2026-07-03 — H0₃ comparator re-specified; H0₄ split out to ADR-TPF-004;
matrix dependence and endpoint disposition recorded — per
`reviews/2026-07-03-h0-family-review.md`
**Related**: ADR-TPF-001 (instrument), ADR-TPF-003 (judging), ADR-TPF-004 (H0₄ instrument)

---

## Context

"Downstream damage" needs operationalization. Broad holistic quality scores are noisy,
judge-taste-contaminated, and cannot discriminate between the two live readings of the
thesis: *forged credential* (the tic licenses false downstream inferences) vs.
*bleached equilibrium* (the tic is register-contagious but propositionally inert).

## Decision

1. **Primary endpoint — PCR:** fraction of continuations containing at least one inference
   licensed *only* by the literal reading of the manipulated token (separability,
   non-interaction, "can be optimized independently") and unsupported by other prefix
   content. A mere echo of the token never counts toward PCR.
2. **Secondary endpoint — register drift:** prestige-lexeme density per 100 tokens
   (pre-registered lexicon) and lexical-diversity measures. Token echoes count here.
3. **Hypothesis family:** H0₁ propositional inertness (PCR equal across arms);
   H0₂ register inertness; H0₃ class equivalence (swaps of the target token vs. a second
   *misused precision-implying* token — e.g. "isomorphic" — produce equal PCR deltas;
   the earlier register-only comparator ("delve") is retired: it has no literal reading
   to license a precision inference, so its PCR delta is ≈0 by construction and the
   comparison collapses into H0₁, besides not filling the same syntactic slot); H0₄
   instruction locality, restated across three levels (frequency / earned-ness /
   generalization) with its own instrument — **see ADR-TPF-004**, which also supplies
   the correct-usage arm separating misuse from mere presence. Factorial includes the
   register-neutral arbitrary-ban control arm and ADR-TPF-004's specificity-matched arm.
4. **Pre-registered time-signature prediction:** PCR effects grow with continuation length
   (coherence debt compounds); register effects appear immediately. Divergence of these
   two curves is evidence no single-channel alternative explains easily. **This is also
   the interpretation matrix's identifying assumption, not merely a prediction:** if PCR
   and register drift covary at all lengths, the "reject H0₂ only" (bleached) cell is not
   cleanly reachable, and matrix conclusions must be conditioned on the observed
   separation.

## Rationale

The endpoint is derived from the theory it tests: the forged-credential claim is
specifically that inference-licensing tokens convert to false premises downstream, so the
measurement must isolate premise consumption from stylistic contagion. The interpretation
matrix depends on this separation — rejecting H0₂ alone *downgrades* the thesis from
epistemic to stylistic, which is a reportable result against the theory and must remain
distinguishable.

### Positive Consequences
- Maximal discriminative power between the two readings; each cell of the H0 matrix has a
  distinct interpretation fixed in advance.
- Narrow rubric supports high inter-judge agreement and cross-family judging.

### Negative Consequences
- Diffuse damage not captured by either endpoint is missed by the confirmatory analysis
  (accepted; exploratory analyses permitted but must be labeled as such).
- **Factual-error-rate scoring** (a co-equal candidate in the genesis material) is
  deliberately demoted to labeled exploratory analysis: it overlaps PCR on the
  confirmatory question while importing the holistic-judging noise Option A was rejected
  for. Recorded so the demotion is a decision, not an omission.
- PCR contrasts inherit paraphrase-construction risk **in both directions** — a poorly
  authored honest paraphrase can manufacture or mask an effect; bounded by the
  explicit-claim positive and inert-synonym negative controls (loose-ends ledger).
- PCR base rates are unknown; power planning is provisional pending pilot (see
  loose-ends ledger).

## Alternatives Considered

### Option A: Holistic quality / error-rate scoring
**Why rejected:** Cannot separate propositional from register channels; vulnerable to
judge surface-taste; would render the interpretation matrix undecidable.

### Option B: Perplexity or embedding-drift measures only
**Why rejected:** Sensitive to register by construction; blind to whether a false premise
was *consumed* — the one thing the thesis is about.

## Open Questions

- [ ] Exact rubric wording for "licensed only by the literal reading" — **Resolution:**
  iterate in pilot until inter-rater κ meets pre-registered threshold; freeze before main run.
- [ ] Baseline PCR estimate — **Resolution:** pilot replaces the 1–3% assumption at
  pre-registration (see loose-ends entry, power planning).

## Supersession Relationships

**Supersedes:** none
**Superseded by:** TBD
