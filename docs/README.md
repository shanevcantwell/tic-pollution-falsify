# Decision Records — Tic-Pollution Falsification Study

Decision records for the experimental protocol testing the "forged credential"
hypothesis: that precision-implying tokens selected stylistically (e.g., loose
"orthogonal") cause measurable downstream damage in LLM generation.

Provenance discipline: per ADR-TPF-005, a record carries decision authority
only from operator conversation turns, cited in the record. Machine-drafted
records are marked as such until ratified.

| # | Title | Status | Date |
|---|-------|--------|------|
| [ADR-TPF-001](adr-tpf-001-prefix-splice-minimal-pairs.md) | Prefix-splice minimal pairs as the causal instrument | model-drafted; ratification pending (ADR-TPF-005) | 2026-07-03 |
| [ADR-TPF-002](adr-tpf-002-pcr-primary-endpoint.md) | Premise-consumption rate (PCR) as primary endpoint | model-drafted; ratification pending; endpoint superseded by ADR-TPF-007 | 2026-07-03 |
| [ADR-TPF-003](adr-tpf-003-cross-family-judge-ensemble.md) | Cross-family judge ensemble with human subsample | model-drafted; ratification pending; independence assumption challenged (ADR-TPF-006 §3) | 2026-07-03 |
| ADR-TPF-004 | (reserved — directive-conditioned prefix generation, unmerged PR #1) | proposed; held | 2026-07-03 |
| [ADR-TPF-005](adr-tpf-005-conversation-turn-provenance.md) | Decision records carry authority only from conversation-turn provenance | accepted | 2026-07-03 |
| [ADR-TPF-006](adr-tpf-006-on-policy-behavior-probe-primary.md) | Primary instrument probes selection-policy behavior, on-policy | accepted | 2026-07-03 |
| [ADR-TPF-007](adr-tpf-007-earned-lazy-substitution-endpoint.md) | Earned-vs-lazy (substitution test) replaces PCR as primary endpoint | accepted | 2026-07-03 |

Tactical decisions that failed the ADR three-part test are tracked in
[`../loose-ends.md`](../loose-ends.md) (also model-drafted; ratification
pending per ADR-TPF-005).
