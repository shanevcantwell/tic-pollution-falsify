# The "Literally" Arc: Semantic Bleaching, Prestige Borrowing, and Why a Word Mid-Decay Is More Dangerous Than a Word Fully Decayed

*Status: presentation source — a self-contained essay tying the study's motivation to its
sociolinguistic frame, written 2026-07-03 for NotebookLM audio synthesis. Not a decision
record; the operative claims live in `../decisions/`.*

---

Everyone has a word they mourn. For many English speakers it is "literally," which now
routinely means its own opposite: "I literally died" is uttered by the visibly living.
The complaint feels modern — people like to blame MTV, or the internet — but the process
it names is one of the oldest and best-documented phenomena in linguistics, and the
complaint itself is centuries late. Dickens, Twain, and Joyce all used "literally" as a
mere intensifier. What the word underwent is called **semantic bleaching**: the gradual
loss of a word's specific content as it gets recruited for emphasis. It is the same
process that long ago hollowed out "very" — which once meant "true," from the same root
as "verify" — and "really," and "awfully," and "terribly." Intensifiers wear out the way
currency inflates: each speaker spends a little more meaning than the word has left, and
the aggregate effect is devaluation. Linguists treat this as ordinary drift, not decay.
Language survives it. Nobody today is misled by "very."

But there is a second, less discussed process that interacts with bleaching:
**prestige borrowing**. Speakers reach for words that carry the register of expertise —
Latinate vocabulary over plain English, technical jargon outside its home domain —
because the word's *credentials* transfer even when its content does not. "Quantum leap,"
"exponential," "paradigm shift," and lately "orthogonal" all migrated from technical
registers where they had precise meanings into general prose where they mostly signal
sophistication. This is different from bleaching in one crucial way: a bleached word has
*lost* its claim to precision, and everyone knows it. A prestige-borrowed technical word
still *carries* its claim to precision — that is exactly why it was borrowed.

This distinction matters because of where the danger sits on the arc. A fully bleached
word is epistemically harmless: when someone says "literally died," no listener updates
their beliefs about mortality, because the community has finished renegotiating what the
word does. The common ground repairs the utterance automatically. The dangerous position
is the **middle of the transition**, when usage has already come unmoored from the
technical meaning but the word's credential still cashes. "Exponential" is arguably
there now: it is used loosely to mean "a lot," yet listeners still sometimes infer
actual compounding growth — a real inference, licensed by a word that was chosen for its
sound. The word writes checks; the context has no funds; the reader honors the check
anyway. Call this the **forged credential**: a token that was selected for register but
is consumed as evidence.

"Orthogonal" is a candidate for exactly this position. In its home register it makes a
strong, specific claim: two things are independent — improving one cannot interfere with
the other. Used loosely, it usually means only "somewhat unrelated." A human reader in
conversation can challenge the usage: *do you mean actually independent?* But language
models now produce a large and growing fraction of the technical prose in circulation,
and they occupy a strange double position in this story. As *speakers*, they are heavy
prestige borrowers — preference-trained models measurably overuse a small set of focal
words, and "orthogonal" appears at rates far above human baselines, including in
contexts where it is not the topic and not earned. As *readers*, they are uniquely
defenseless: a model continuing a text cannot ask the clarifying question. The next
token is conditioned on the words that precede it, and the words that precede it include
a precision claim that nobody meant. If the model treats that claim as a premise —
"since the two systems are orthogonal, we can tune one without regressing the other" —
then a stylistic tic has been converted into a false belief, mechanically, inside a
single pass of computation.

The honest counterargument deserves its full weight. Language has always changed;
complaints about degeneration are as old as writing, and every generation's corruption
is the next generation's standard usage. Perhaps "orthogonal" is simply doing what
"literally" did, and will land where "literally" landed: bleached, conventional, and
harmless, with the community's expectations adjusting to match. On this view the
fist-shaking is aesthetic, not epistemic — a taste preference dressed up as a warning.

The right response to that counterargument is not rhetorical but empirical, because the
two stories make different predictions. If "orthogonal" is merely bleaching — call it
the **bleached equilibrium** — then a loose usage should propagate *style* downstream
(more prestige vocabulary, more borrowed register) while propagating no *propositions*:
continuations should not contain inferences that depend on the word's literal meaning.
If the credential is forged and still cashing, the signature reverses: the literal
meaning should leak into downstream reasoning as consumed premises — and that leakage
should compound with distance, the way a false assumption compounds through an argument,
while mere style-matching appears immediately and stays flat. Two channels, two
time-signatures, separable by experiment: hold everything fixed, swap the single word
for its honest paraphrase, and measure what the continuation *believes* versus what it
*wears*.

That experiment is what this repository exists to run. The sociolinguistics frames the
question but cannot answer it, because the arc from precision to bleach is only visible
in hindsight for human speech communities, which renegotiate meaning over generations.
Machine text is different in both directions: the damage, if real, is faster — models
consume their own dialect at training time and each other's output at inference time —
and the measurement, unlike with human communities, is actually available. We do not
have to wait a century to see where on the "literally" arc "orthogonal" sits. We can
splice the word in and out of otherwise identical contexts and watch what the forward
pass does with it. Either the word has bleached into harmless decoration, in which case
the fist-shaking can relax into mourning — or the credential still cashes, in which case
every loosely spent "orthogonal" is quietly writing premises into machine reasoning, and
the mourning is premature because the patient is not yet dead. He is, at worst, only
literally dying.
