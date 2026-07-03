# Use premise-consumption rate (PCR) as the primary endpoint

**Status**: `accepted`
**Date**: 2026-07-03
**Related**: ADR-TPF-001 (instrument), ADR-TPF-003 (judging)

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
   H0₂ register inertness; H0₃ class equivalence (precision-implying vs. register-only
   tic swaps produce equal PCR deltas); H0₄ instruction locality (the textbook-meaning
   preference line affects only target-token emission), tested in a factorial that
   includes a register-neutral arbitrary-ban control arm.
4. **Pre-registered time-signature prediction:** PCR effects grow with continuation length
   (coherence debt compounds); register effects appear immediately. Divergence of these
   two curves is evidence no single-channel alternative explains easily.

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
