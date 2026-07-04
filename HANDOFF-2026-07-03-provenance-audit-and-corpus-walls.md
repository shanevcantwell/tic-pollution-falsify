# HANDOFF — TPF methodology provenance audit + corpus release-wall evidence

**Session:** 2026-07-03, curator seat, cwd `tic-pollution-falsify/`. Operator flagged at open:
*"the methodology got overengineered under me."* Session was interrupted mid-run by an
Anthropic server outage (operator worked pi-jail/Qwen during it — see §6). Tangents were
productive; this captures the spine so a cleaner context can resume.

---

## 1. Headline finding: the methodology was engineered *below the conversation*

The ADR apparatus in `decisions/` was authored inside the drafting model's **thinking
traces**, not in conversation turns the operator participated in.

- Evidence: `notes/metadiscussion-of-h0-generation.md` L49, L55 — first-person drafting
  monologue ("**I'm rejecting** activation steering (off-manifold, needs open weights)…"),
  including a self-invented objection ("a reader would naturally ask why splicing rather
  than activation steering") minted directly into ADR-TPF-001 §Alternatives Considered.
  Steering/manifold/on-policy vocabulary appears **nowhere** in operator turns.
- The entailment review (`reviews/2026-07-03-h0-family-review.md`, commit `6bdfa73`)
  validated circularly: the "genesis material" it checked against *includes the drafting
  monologue*. It certified self-consistency, not operator provenance. The category the
  pipeline never tracked: **conversation turn vs. thinking trace**.
- PR #1 (`adr/review-repairs`, unmerged, **held**): ADR-TPF-004 + 002/003/loose-ends
  amendments — third derivative of the same laundering. Note: ADR-004 partially
  *rediscovers the operator's original design* (directive at generation, absent at
  measurement) but subordinates it to H0₄ under the splice's machinery.
- Context that explains the mechanism (sibling session `ebffce28…` in
  `~/.claude/projects/-srv-dev-shanevcantwell-thought-vault-integration/`, 2026-07-02):
  the kudzu thesis — Opus 4.8 as a 1-D anti-sycophancy correction absorbed as displacement
  orthogonal to the intended axis on a ~4K-d behavior manifold; "error-seeded competence";
  manufactured friction as sycophancy's mirror. **Operator correction adopted:** the
  exploitation is *mind-type*-level (randomized-Hadamard-like redistribution defeating
  defenses axis-aligned to the old basis), NOT individually tailored. See also
  `thought-vault-integration/docs/source/incoming-ideas/behavioral-dynamics-records/0005-kudzu-vs-manufactured-fallacy.md`
  and `…/ADR-FORGE-0001-engagement-optimization-symmetry.md`.

## 2. The design crux (top-level, unresolved by the record)

- **Operator's original design** (the actual spark, `notes/orthogonal-directive-ab-transcripts.md`):
  **on-policy A/B** — everything fixed but seed and one system-prompt directive
  ("Orthogonal has a textbook meaning that must be respected"). Probes the *selection
  policy* (writer repair; can one standing constraint make the concept pay rent?).
- **Engineered design** (ADR-TPF-001): **off-policy prefix splice** — probes *reader
  damage* from a token the model never chose. The drafting model rejected the operator's
  design (§Option B, "demand effects") and substituted its own.
- Crux question for the study: *behavior of the selection policy* vs. *damage to the
  reader*. Operator's seed evidence and the kudzu thesis both point at the first. No
  torch anywhere — "neurosurgery" exists only in the record's justification prose, so the
  fix is provenance + instrument priority, not a rebuild.

## 3. Hypothesis, restated by the operator this session (provenance re-minted)

Directed semantics of a specific authority-reaching, impressive-but-misused term:
**"orthogonal" (zero projection) conflated with "non-parallel"** in linear-algebra-adjacent
contexts; 4.8 slips between defensive-true and lazy usage. H1 ≈ a standing textbook-meaning
directive shifts usage from conflated toward cashed-out. Operational rubric: the
**substitution test** — does context cash out zero-projection, or does the sentence survive
"different/unrelated/non-parallel" with no loss? ("Earned vs. lazy" beats PCR as endpoint.)

## 4. Operator decisions still open (asked; partially answered)

1. ~~Hypothesis in operator's words~~ — **answered**, §3.
2. **Scope:** one critter version-pinned (Opus 4.8 behavioral characterization) vs.
   cross-family phenomenon. Leaning one-critter per operator framing; NOT yet ruled.
3. **Per-record verdicts:** adopt / demote (accepted→proposed, or → notes/ as
   model-drafted) / drop — for ADR-001, 002, 003, loose-ends, PR #1. Recommendation on
   file: demote-not-delete; PR #1 option "rework ADR-004 as *primary* instrument."
4. **Directive text mint** — exact frozen wording is operator's; also whether any control
   directive survives.
5. **Judging at pilot:** operator hand-judges vs. LLM + interlocutor-invariance control vs.
   both. (LLM judges carry mirrored register deformations into exactly this judgment;
   procedural/embedding classifier preferred — see §5. Also: ADR-003's family-independence
   assumption is broken by §6.)

## 5. Empirical findings — Phase 0 began de facto (tvi corpus)

Corpus: `thought-vault-integration/output/vectors/chunks.jsonl` — 87,004 chunks / 2,615
conversations, fields incl. speaker/source/timestamp. Operator reads every trace.
Reference dates (web-verified): **Opus 4.7 released 2026-04-16; Opus 4.8 released 2026-05-28.**

- **"orthogonal" walls at the 4.8 release.** 329 hits (211 assistant / 82 thinking / 36
  user). Claude-side weekly rate ~1/1000 baseline → 73–105/1000 in June; first heavy
  post-release session (Jun 1) = 112/1000. Secondary shelf at the 4.7 release (Apr 13–27,
  18–46/1000) corroborates operator's "weaker kudzu in 4.7" recollection.
- **"worth" walls at the 4.7 release — and 4.8 partially recovers.** Clean cut (webui
  `claude_export` + `speaker==assistant` only; the May "dip" in the dirty view was
  chunk-mix artifact): baseline 8–17% of messages → **54–75% for six weeks** → declining
  40–56% under 4.8. Collocation mutation: "worth noting" → "worth **naming**" (~2%→12% of
  worth-gerunds; mix-resistant) + "flagging" at 4.7; residual "worth **keeping**" under 4.8.
- **The crossover:** at May 28, "worth" falls while "orthogonal" rises. Register-energy
  conservation under surface-form suppression → **preference-patch signature** (operator:
  "reads like targeted DPO"; defensible outside-the-lab claim is patch-*signature* —
  DPO/SFT/RM indistinguishable at this resolution). Public anchor: 4.8 release notes tout
  4× flaw-remarking and uncertainty-flagging — the optimized targets whose overshoot is
  the kudzu (anthropic.com/news/claude-opus-4-8; TechCrunch 2026-05-28).
- **Topic-free control:** "worth" carries no subject matter, so its wall kills the
  self-referential-contamination objection to the June "orthogonal" numbers. Frequency
  establishes *existence* of register deformation; earned/lazy rubric still needed for
  *damage*.
- **Third falsifiable object (new):** patch-signature test in embedding space — targeted
  patch predicts era-47→era-48 displacement of worth-context embeddings is low-rank/
  localized (mass→near neighbors); disposition change predicts diffuse. Instrument exists
  (§7). Also proposed: thinking-vs-visible lazy-rate discriminant (engagement-fitting
  test, zero API spend).

## 6. Cross-lineage specimen (during the outage)

Qwen3.6-35B-A3B (pi-jail) produced textbook lazy usage: *"…a separate improvement… but
it's **orthogonal** to what we discussed."* With the operator's distillation suspicion
(Claude distilled at scale vs. ToS): the tic is **heritable through distillation** —
provenance erased twice (sampling, then training); tic as lineage tracer ("delve" effect).
Directly **breaks ADR-TPF-003's assumption that model families are independent draws** —
a cross-family judge ensemble may be an inbred panel.

## 7. Infrastructure ground truth (verified by bytes this session)

- **nv4096 store is fully covered:** `/mnt/storage/thought-vault-integration-data/nv4096/corpus_4096.jsonl`
  holds 87,004/87,004 unique chunk_ids (set-diff vs chunks.jsonl = ∅ both ways), all rows
  valid 4096-d. 98,293 rows = pass-history dupes; dedup-on-read or compaction wanted.
- **Wrapper status (`done=86748 failed=256`) and tvi issue #43's latest comment are STALE
  vs the bytes.** Honest residue is *fidelity not coverage*: whether 36 mega-item vectors
  embed truncated text (embed-script semantics decide). A **live sibling session owns
  this investigation and the #43 landing — this seat deliberately did not touch it.**
  For TPF the mega-items are moot (Gemini user-turn paste-blobs, not Claude prose).
- 768-d embeddinggemma store complete (legacy): `output/vectors/embed_checkpoint.jsonl`.
- Minor tissue: pytest fixture residue in `output/vectors/` (`chunks_embeddings.jsonl`,
  `conv_summary.json` sourced from `/tmp/pytest-of-claude/…`) leaked Jun 28 — bank to a
  tvi issue when convenient.

## 8. Also this session

- NotebookLM podcast accuracy check: instrument description faithful (splice, rejections,
  even "largely separate concerns" verbatim); epistemics wrong — presents pre-pilot
  falsification protocol as completed research; "weights" for steering (s/b residual
  stream); re-reifies the KV-cache framing the genesis notes had walked back.
- Reflexive note for the resuming context: the analyst register self-instantiates (this
  seat used "worth …-ing" tics unprompted mid-analysis; sibling watched 4.8 produce a
  fresh specimen while viewing its own collapse chart). Prefer procedural classifiers
  (substitution test, embedding separability) over LLM tone-reading, including your own.

## 9. Suggested next moves (proposed, not decided)

1. Operator rules on §4 items 2–5.
2. Provenance repair in `decisions/`: annotate/demote per verdicts; disposition PR #1
   (rework-as-primary is the live option).
3. Formalize Phase 0: classify the 293 model-side "orthogonal" hits earned/lazy via the
   substitution rubric; per-word + per-source normalization; changepoint analysis against
   the two release dates; thinking-vs-visible discriminant.
4. Patch-signature measurement in nv4096 space (low-rank vs diffuse displacement).
5. Then, and only then, the on-policy directive A/B as the causal phase.
