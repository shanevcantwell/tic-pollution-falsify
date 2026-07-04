# The primary instrument probes selection-policy behavior, on-policy

**Status**: `accepted`
**Date**: 2026-07-03
**Provenance**: Operator-decided in session 2026-07-03 ("probing at Opus 4.8
*behavior*, not performing neurosurgery through torch"); handoff §2.
**Related**: ADR-TPF-005 (provenance), ADR-TPF-001 (splice — demoted by this
record), ADR-TPF-004/PR #1 (rework-as-primary is the live disposition option)

---

## Context

The study's original spark was an on-policy A/B: everything fixed but seed and
one system-prompt directive ("Orthogonal has a textbook meaning that must be
respected") — an intervention on the *writer*. The machine-drafted methodology
rejected that design (ADR-TPF-001 §Option B, "demand effects") and substituted
an off-policy prefix splice — an intervention on the *text*, probing only
reader damage. The two designs answer different questions.

## Decision

1. The **directive-conditioned on-policy A/B** is the study's primary
   instrument: the model authors every token of both arms; only seed and the
   standing directive vary. The question is whether one constraint re-anchors
   the selection policy.
2. The **prefix splice is demoted to secondary** — a reader-pass follow-up if
   the primary shows an effect, not the study's frame.
3. Cross-family apparatus is on notice: the Qwen3.6 lazy-"orthogonal" specimen
   (distillation-heredity) breaks ADR-TPF-003's family-independence
   assumption; its verdict rides the ADR-TPF-005 ratification pass.

## Consequences

- Positive: the instrument matches the operator's actual question and evidence
  (the A/B seed transcripts, `../notes/orthogonal-directive-ab-transcripts.md`);
  no constructed counterfactuals; the demand-effects concern is handled by
  measuring continuations directive-absent (the two-phase shape ADR-TPF-004
  proposes).
- Negative: gives up the splice's exact token-level counterfactual as the
  headline claim; scope question (one critter version-pinned vs. cross-family
  phenomenon) remains open — handoff §4.2.

## Open Questions

- [ ] Scope: Opus 4.8 version-pinned characterization vs. general phenomenon.
      **Resolution:** operator, cleaner-context session.
- [ ] PR #1 disposition (rework ADR-TPF-004 as the primary-instrument record).
      **Resolution:** same session, after ADR-TPF-005 verdicts.

## Supersession Relationships

**Supersedes:** the instrument *priority* implied by ADR-TPF-001 (the splice
description itself remains valid as a secondary instrument, pending its
ADR-TPF-005 ratification verdict)
**Superseded by:** TBD
