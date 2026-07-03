# Use directive-conditioned prefix generation as the H0₄ instrument

**Status**: `proposed`
**Date**: 2026-07-03
**Related**: ADR-TPF-001 (splice instrument; §Option B is the conflict this record resolves),
ADR-TPF-002 (H0₄ statement), `reviews/2026-07-03-h0-family-review.md` (findings 1, 3, 5),
`notes/metadiscussion-of-h0-generation.md` L60 (the fold-vs-split call this record reopens)

---

## Context

H0₄ tests whether a textbook-meaning preference line generalizes beyond the target token.
As folded into ADR-TPF-002 it rode an instrument this study had already rejected:
ADR-TPF-001 §Option B refuses instructed usage because the instruction enters the context
and confounds the token's effect with its own. No record documented H0₄'s instrument or
reconciled the contradiction; the genesis transcript offered the split (L60) and it was
declined at distillation. The H0-family review found the fold buried a real structural
conflict (finding 1) and that H0₄'s "emission frequency" wording has no cell for the effect
its own seed demonstrates (finding 5: in the A/B transcripts the token appears in *both*
arms; what changed is whether it was earned).

## Decision

A two-phase instrument, distinct from the splice but sharing its measurement mechanics:

1. **Prefix generation — directive present.** Arm L (lazy): natural elicitation, no
   directive, per ADR-TPF-001. Arm D (directed): identical elicitation with the
   textbook-meaning directive in the system prompt. Harvest prefixes containing the target
   token from both arms.
2. **Continuation measurement — directive absent.** All continuations are sampled as
   prefills conditioned on the prefix token sequence alone. The directive is never present
   at measurement time in either arm.

H0₄ is restated across three levels (replacing the single "target-token emission" wording
in ADR-TPF-002 §Decision.3):

- **H0₄a — frequency:** emission rate of the target token is equal across arms.
- **H0₄b — earned-ness:** conditional on emission, the token is locally cashed out
  (grounded by its surrounding tokens) at equal rates across arms.
- **H0₄c — generalization:** precision on dimensions unrelated to the target token is
  equal across arms.

Factorial controls: the register-neutral arbitrary-ban arm (retained from ADR-TPF-002)
**plus** a content-relevant specificity-matched arm (e.g. a bare "use 'orthogonal'
precisely" without the textbook-meaning framing), per review finding 5's
attention-salience confound.

**Downstream contrast (the core question, stated at emission level):** PCR measured on
lazy-arm vs directed-arm occurrences of the *same token* discriminates whether the token's
inferential license is provenance-blind. Equal PCR: downstream computation cannot tell
earned from decorative — the token injects the same separability features into emission
regardless, with nothing behind it in the lazy arm — forged credential in its sharpest
form. Lazy < earned: the surrounding justification, not the token, carries the license.
Lazy > earned: cashed-out usage arms the reader against over-reading; a distinct mechanism
warranting its own follow-up.

## Rationale

At measurement time nothing exists but a token sequence conditioning a forward pass.
Causal masking (ADR-TPF-001's own foundation) guarantees the continuation cannot be
affected by a directive that is not among the prefix tokens. ADR-TPF-001 §Option B
rejected instructed usage because the instruction contaminates the **measured** context;
in this instrument the instruction touches only the **generation** of the manipulated
material and is structurally absent from the measured context. The rejection stands
exactly where it was made; this design does not breach it — it routes around it on the
same causal-masking grounds that validate the splice.

The directed arm additionally serves as the **correct-usage arm** the review found missing
(finding 3): earned occurrences are contexts where the literal claim is locally grounded,
separating "damage because misused" from "precision vocabulary licenses premises
regardless."

### Positive Consequences
- Resolves the review's highest structural finding; the fold-vs-split call at genesis L60
  is now decided in the record.
- H0₄b targets the effect the A/B seed actually shows, instead of a frequency proxy.
- One arm closes two findings (misuse-vs-presence discriminator rides for free).

### Negative Consequences
- Directed-arm prefixes may differ from natural ones in position/length distribution —
  same confound class as the natural-elicitation loose-end; the same pilot check covers it.
- Earned-ness requires its own judge rubric (below), adding one rubric to the κ-freeze
  pipeline.

## Alternatives Considered

### Option A: Keep H0₄ folded in ADR-TPF-002 with a reconciling footnote
**Why rejected:** The instrument carries its own threat model (demand effects at
generation, salience confounds, arm-matching) and is hard to reverse after
pre-registration. A footnote cannot carry that; burying it was the original defect.

### Option B: Drop H0₄ entirely
**Why rejected:** The lazy-vs-directed contrast is the study's origin observation
(`notes/orthogonal-directive-ab-transcripts.md`). Dropping it unmoors the design from its
motivating evidence.

## Open Questions

- [ ] Earned-ness rubric (what counts as "locally cashed out") — **Resolution:** same
  pilot-iterate-until-κ-then-freeze procedure as the PCR rubric (ADR-TPF-002).
- [ ] Whether arm-D prefixes need explicit length/position matching to arm L —
  **Resolution:** shared pilot confound check with the natural-elicitation loose-end.

## Supersession Relationships

**Supersedes:** the H0₄ wording in ADR-TPF-002 §Decision.3 (amended same date to point here)
**Superseded by:** TBD
