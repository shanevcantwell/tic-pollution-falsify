# Require a cross-family judge ensemble with human subsample

**Status**: `accepted`
**Date**: 2026-07-03
**Related**: ADR-TPF-002 (endpoints being judged)

---

## Context

Continuations must be scored for PCR and register drift at scale, which in practice means
LLM judges. But the study's own thesis predicts the contamination: judge models are
descendants of the same preference-optimization pipeline whose surface taste is under
measurement, and AI-feedback pipelines launder rather than remove that taste. A judge from
the generator's family plausibly shares its prestige-lexeme preferences (biasing register
measurement) and its charitable reading of precision tokens (biasing PCR in an unknown
direction). This is the rare case where the hypothesis under test disqualifies the default
measurement apparatus.

## Decision

- Judge ensemble of models from **at least two families other than the generator's**.
- Judges are **blind to arm** and score **continuation text only** (prefix stripped).
- **~5% human subsample**, double-rated, with inter-rater agreement (κ) reported for both
  human–human and human–ensemble pairs.
- Judge prompts never mention vocabulary, precision, or the manipulated token.
- **Scope:** this apparatus governs *behavioral* endpoints only (PCR, register drift,
  earned-ness). Mechanistic endpoints — activation-level measurements in the ADR-TPF-001
  follow-up tier — are measured, not judged; no ensemble, κ gate, or human subsample
  applies to them.

## Rationale

Reflexive consistency: a study arguing that surface-selected tokens deceive downstream
readers cannot use a downstream reader with the same training lineage as its measurement
instrument without independent validation. The human subsample anchors the ensemble;
disagreement between anchor and ensemble is itself a reportable finding about judge
contamination.

### Positive Consequences
- Measurement error decorrelated from the generator's taste.
- Human anchor converts "judges might share the bias" from a threat into a measured quantity.

### Negative Consequences
- Cost and rubric-adherence variance across families.
- Cross-family judges may be weaker at the rubric; mitigated by the κ gate in ADR-TPF-002.

## Alternatives Considered

### Option A: Single same-family LLM judge
**Why rejected:** Cheapest and standard practice, but reflexively invalid here — correlated
measurement error with unknown sign on the primary endpoint.

### Option B: Human-only evaluation
**Why rejected:** Cost at the required N (10³–10⁴ continuations per arm), and — the
decisive irony — time-constrained human evaluation is precisely the channel shown to be
vulnerable to surface persuasion (false-positive rates rising ~18–24% post-RLHF in the
sophistry literature). Reproducing the original failure mode inside the instrument would
be self-defeating.

## Open Questions

- [ ] Which judge families — **Resolution:** fixed at pre-registration, after checking
  training-lineage independence claims for candidate models.
- [ ] Is 5% human subsample sufficient — **Resolution:** pilot κ confidence intervals
  determine final fraction before main run.

## Supersession Relationships

**Supersedes:** none
**Superseded by:** TBD
