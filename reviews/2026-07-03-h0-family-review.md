# Review: does the H0 family follow from the genesis material?

**Date:** 2026-07-03
**Reviewer:** adversarial methodological review (frontier-model pass, dispatched from the
curator seat at operator request — "make sure the H0 follows")
**Inputs:** ADR-TPF-001/002/003, loose-ends.md, notes/metadiscussion-of-h0-generation.md
(genesis transcript, cited by transcript line L#), notes/orthogonal-directive-ab-transcripts.md
(A/B seed)
**Verdict:** **Yes, with named repairs.** All four H0 trace to the genesis transcript
(L41–L44); H0₁ and H0₂ are sound as operationalized. Three repairs are load-bearing
before pre-registration freeze.

---

## Load-bearing findings

### 1. H0₄ smuggles an instrument ADR-TPF-001 rejected (STRUCTURAL — highest)
H0₁–H0₃ run on the splice instrument. H0₄ does not — it manipulates a **system-prompt
directive** (textbook-meaning line + arbitrary-ban control), i.e. an *instructed-context*
manipulation, which ADR-TPF-001 §Option B rejects for demand effects ("the instruction
itself enters the context and plausibly alters register and self-monitoring"). No record
documents H0₄'s instrument or reconciles the contradiction. The genesis transcript offered
the split ("stand alone as 0004… a clean split", L60) and it was folded into 002 —
**folding was not fully correct**: co-locating the hypothesis (shares PCR) was fine;
burying the distinct directive-manipulation instrument was not.
**Repair:** mint ADR-TPF-004 for the directive-manipulation instrument; resolve the
ADR-001 §Option B conflict explicitly (why instructed usage is admissible for H0₄ but
not H0₁).

### 2. H0₃'s register-only comparator is ill-defined and near-redundant with H0₁
(a) PCR counts inferences licensed *only by the literal reading* of the manipulated token;
a register-only tic ("delve") has no literal reading that licenses a precision inference,
so its PCR delta ≈ 0 **by construction** — H0₃ collapses into H0₁. (b) "Same position"
is not operationalizable across syntactic slots (adjective vs verb).
**Repair:** re-specify the comparator — see finding 3.

### 3. The misuse-vs-mere-presence discriminator was entertained and dropped (COVERAGE GAP)
Genesis L29 proposed a correct-usage arm (context where orthogonality genuinely holds)
and/or a different misused precision token ("isomorphic"). Neither survived. Without one,
the design cannot distinguish "the tic licenses false premises *because misused*" from
"precision vocabulary licenses premises *regardless*" — close to the core claim.
**Repair:** re-admit the correct-usage arm and/or the "isomorphic" arm; this also gives
H0₃ a well-defined, non-redundant comparator.

### 4. Factual-error-rate endpoint dropped without recorded rationale (COVERAGE GAP)
Genesis L28–L30 listed it co-equal with PCR/register-drift; ADR-002 keeps neither it nor
a demotion rationale. (The latent-probe drop is clean — explicitly optional, deferred to
the mechanism-localization follow-up.)
**Repair:** re-admit as tertiary confirmatory endpoint, or record the demotion.

### 5. H0₄'s "emission frequency" framing contradicts its own seed
In the A/B seed, "orthogonal" appears in **both** arms; the directive changed
**within-token precision on the target concept** (decorative → earned/cashed-out), not
emission frequency. H0₄'s wording has no cell for that middle category — the one the seed
actually demonstrates. Genesis L10 predicted this ("precision instructions tend to
generalize"). Secondary confound: the crux-ban control is content-*irrelevant* while the
textbook-meaning directive is content-*relevant*; arms can differ on attention-salience,
not precision-demand generalization.
**Repair:** reword H0₄ across three levels — (i) target-token frequency, (ii)
target-concept precision when used, (iii) unrelated-dimension precision — and add a
specificity-matched control arm.

### 6. Seed fidelity (confirmation with limits)
orthogonal-directive-ab-transcripts.md is n=1 per arm, one model, one domain, sampling
unknown, and the two
runs have different search trajectories (retrieved-evidence confound, genesis L9). The
ADRs correctly quarantine it as motivation, not evidence; the single over-read is
finding 5.

### 7. Interpretation matrix leans silently on the time-signature prediction (minor)
If PCR and register drift covary, the "reject H0₂ only" (bleached) cell is not cleanly
reachable; the actual identifying assumption is the divergent time-signature
(ADR-002 §Decision.4). **Repair:** state that dependence explicitly at pre-registration.

### 8. H0₁ hinges on paraphrase construction (minor, largely mitigated)
Paraphrase authoring can move PCR in either direction; mitigated by k=3 marginalization
and the positive/negative controls (loose-ends). Worth one pre-registration sentence
naming the bidirectional threat.

## Confirmations
- **H0₁** traces to genesis L21 (forged-credential mechanism) + L41; testable; follows.
- **H0₂** traces to L9/L14/L20 (drift, bleaching, equilibrium) + L42; follows.
- **ADR-001's splice rationale** (validity entailed by causal masking; provenance-erasure
  not under test) is sound per L11/L24/L34; the prefill-symmetry manipulation check
  correctly internalizes the introspection caveat (L27).

## Disposition
Repairs 1–3 (ADR-TPF-004 mint + H0₄ reword; H0₃ comparator; misuse-vs-presence arm) are
pre-registration blockers. Repairs 4, 7, 8 are one-paragraph record fixes. All are
operator decisions — this review changes no decision records itself.
