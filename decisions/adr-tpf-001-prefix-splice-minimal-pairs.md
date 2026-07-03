# Use prefix-splice minimal pairs as the causal instrument

**Status**: `accepted`
**Date**: 2026-07-03
**Related**: ADR-TPF-002 (endpoint definition), ADR-TPF-003 (judging)

---

## Context

The study tests whether a precision-implying token selected stylistically and inaccurately
(canonical case: loose "orthogonal") causes downstream damage in continued generation. This
requires a counterfactual in which *only the token differs* and everything else is held
fixed. Candidate instruments: observational corpus comparison, instructed usage, activation
steering, and prefix splicing.

## Decision

Generate analytical prose across ~5 domains until the target token occurs naturally in
loose usage. For each such prefix, construct minimal-pair variants by splicing the token
span out for register-matched honest paraphrases (e.g., "largely separate concerns").
Sample continuations from both arms as prefills under identical decoding parameters.

## Rationale

The instrument's validity is *entailed by the mechanism under study rather than assumed*:
causal masking guarantees that a spliced prefix conditions the continuation identically to
a sampled one — token provenance is unrepresentable in the forward pass, so the splice is a
perfect token-level counterfactual. Both arms are prefills, so the weak recalled-intention
channel documented in introspection research (prefill-vs-own-output discrimination) is
symmetric between conditions and cancels. Note the division of labor: provenance-erasure is
mathematically guaranteed and is *not* under test; only its downstream consequences are.

### Positive Consequences
- Exact counterfactual at the token level; no off-manifold perturbation.
- Works on closed-weight models via API; cross-family replication is cheap.
- Natural elicitation preserves the ecological distribution of tic-hosting contexts.

### Negative Consequences
- Cannot identify *which internal pathway* mediates any observed effect (token-as-evidence
  is the only manipulated channel — by design).
- Paraphrase choice is a nuisance parameter; mitigated by marginalizing over k variants
  per prefix (see loose-ends ledger for k).

## Alternatives Considered

### Option A: Activation steering
**Why rejected:** Perturbs the residual stream directly, changing more than the token
(off-manifold artifacts, strength calibration problems documented in the steering
literature); requires open weights, blocking cross-family replication on frontier models.
Remains the right tool for a *mechanism-localization* follow-up, not for the causal
existence question.

### Option B: Instructed usage ("use the word X in your answer")
**Why rejected:** Demand effects — the instruction itself enters the context and plausibly
alters register and self-monitoring, confounding the token's effect with the instruction's.

### Option C: Observational corpus comparison
**Why rejected:** Contexts that naturally elicit the tic differ systematically from those
that don't; no amount of matching recovers the counterfactual.

## Open Questions

- [ ] Natural-only vs. mixed natural+synthetic prefixes — **Resolution:** pilot confound
  check on prefix position/length (see loose-ends entry, elicitation strategy).
- [ ] Prefill-symmetry assumption — **Resolution:** manipulation check comparing
  continuation statistics of un-spliced prefill vs. live generation of the same prefix
  before the main run.

## Supersession Relationships

**Supersedes:** none (first record)
**Superseded by:** TBD (a mechanism-localization study using steering would extend, not
replace, this design)
