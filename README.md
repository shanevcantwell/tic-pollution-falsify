# tic-pollution-falsify

Experimental protocol for the **Tic-Pollution Falsification Study**: testing the
"forged credential" hypothesis — that precision-implying tokens selected stylistically
and inaccurately (canonical case: loose "orthogonal") cause measurable downstream
propositional damage in LLM generation — against the "bleached equilibrium" null
(register contagion without propositional consequence).

- **ADR repo-code:** `TPF` (registered in `design-docs/adr-refactor/codes.txt`)
- **Decision records:** [`decisions/`](decisions/README.md) — instrument (ADR-TPF-001),
  endpoints (ADR-TPF-002), judging (ADR-TPF-003)
- **Tactical decisions:** [`loose-ends.md`](loose-ends.md) — sub-ADR choices with
  graduation triggers
- **Working notes:** [`notes/`](notes/README.md) — raw provenance (genesis transcript,
  inspiring source material), subordinate to `decisions/` and `loose-ends.md`
- **Phases (implicit in the ADRs; roadmap doc TBD):** pilot → pre-registration freeze
  (rubric κ gate, power re-plan, judge-family fixation) → main run

Established 2026-07-03 from the `incoming-ideas` bundle `it_isnt_orthogonal_dammit.zip`
(archived with provenance at `design-docs/established/tic-pollution-falsify/`).
