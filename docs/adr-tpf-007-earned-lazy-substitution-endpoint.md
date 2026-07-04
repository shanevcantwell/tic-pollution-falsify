# Earned-vs-lazy (substitution test) replaces PCR as primary endpoint

**Status**: `accepted`
**Date**: 2026-07-03
**Provenance**: Operator's hypothesis restatement, session 2026-07-03
(handoff §3): "orthogonal… most often lazily to mean 'non-parallel,' which is
a massive difference to conflate."
**Related**: ADR-TPF-006 (instrument), ADR-TPF-002 (endpoint it supersedes)

---

## Context

The construct is a specific, judgeable semantic error: conflating
**orthogonal** (zero projection — improving one axis moves nothing on the
other) with **non-parallel** (true of almost anything), by an
authority-reaching term in contexts where the textbook meaning is live.
PCR (premise-consumption rate) was the machine-drafted proxy; it measures
downstream inference licensing, not the conflation itself.

## Decision

1. Primary endpoint: **earned/lazy classification per occurrence** via the
   substitution test — does the surrounding context cash out zero-projection,
   or does the sentence survive substituting "different / unrelated /
   non-parallel" with no loss of content?
2. PCR survives, if at all, as a secondary downstream-damage measure.
3. Classification is **procedural-first**: substitution rubric + embedding
   separability (768-d store complete; 4096-d nv-embed store byte-complete,
   87,004/87,004) before any LLM judge — LLM judges carry the mirrored
   register deformations under study (handoff §5, §8).

## Supersession Relationships

**Supersedes:** the endpoint choice in ADR-TPF-002 §Decision (whatever
ADR-TPF-002's own ratification fate under ADR-TPF-005 — the endpoint question
is settled regardless)
**Superseded by:** TBD

## Open Questions

- [ ] Rubric calibration set: the 293 model-side corpus occurrences, classified
      first. **Resolution:** Phase 0, handoff §9.3.
- [ ] Does embedding separability reproduce rubric labels well enough to
      retire the LLM judge entirely? **Resolution:** Phase 0 separability test.
