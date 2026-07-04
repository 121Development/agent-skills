# Superforecasting methodology — deeper reference

Load this for high-stakes, contested, or unusually uncertain forecasts.

## Tetlock's Ten Commandments (adapted for practice)

1. **Triage.** Spend effort where it pays: questions in the "Goldilocks zone"
   of difficulty. Don't grind on near-certainties or pure coin flips — say so
   and move on.
2. **Break seemingly intractable problems into tractable sub-problems.**
   Fermi-ize. Even crude decompositions expose which assumption drives the answer.
3. **Strike the right balance between inside and outside views.** Outside view
   first (base rate), inside view as adjustment. Novel events still have
   reference classes — find the "comparison class of one-of-a-kind events".
4. **Balance under- and overreacting to evidence.** Many small updates beat
   rare dramatic ones. But when a genuine regime change happens, don't cling
   to the old anchor — ask "is this news the kind of thing that changes the
   mechanism, or just the mood?"
5. **Seek out clashing causal forces.** For every argument, look for a
   counter-argument. Synthesize a "dragonfly view" from multiple perspectives
   rather than averaging away disagreement.
6. **Granularity pays.** Distinguish 55 from 60 from 65. Vague-verbiage
   forecasts ("distinct possibility") can't be scored and can't be improved.
7. **Balance under- and overconfidence.** Both prudence (never committing) and
   decisiveness (premature certainty) are failure modes. The betting test
   catches both.
8. **Look for errors behind mistakes — own them.** When a forecast misses,
   find the flawed step (wrong reference class? overweighted a vivid signal?)
   rather than excusing it ("I was almost right").
9. **Bring out the best in others** (panel context): when aggregating multiple
   forecasts or opinions, weight track records and independence, and beware
   information cascades.
10. **Master the error-balancing bicycle.** Calibration comes from practice
    with feedback, not from reading about calibration. Encourage the user to
    log forecasts and score them (Brier score) on resolution.

## Bias checklist (run during Step 5)

- **Anchoring on the inside story** — the vivid narrative crowds out the base rate.
- **Recency / availability** — last week's headline feels like a trend.
- **Confirmation** — searching only for evidence that supports the initial hunch.
  Antidote: spend one search query explicitly on the opposing case.
- **Scope insensitivity** — same probability for "within 1 year" and "within 5
  years". Recompute at a doubled horizon; if the number doesn't move, it's wrong.
- **Wishful / dreadful thinking** — desirability leaking into likelihood. Ask:
  "if I wanted the opposite outcome, would I read this evidence the same way?"
- **Hindsight-proofing** — vague terms chosen so any outcome can be claimed as
  a hit. The Step 0 gate exists to prevent this.
- **Overcorrection theater** — hedging to 50% to avoid being wrong. 50% is a
  claim (maximal uncertainty), not a refuge.
- **Conjunction sloppiness** — multiplying chain probabilities that aren't
  independent, or forgetting that a 5-link chain at 80% each is already ~33%.

## Aggregation and markets

- A liquid prediction-market price is an aggregate of motivated forecasters.
  Treat it as a strong prior; beating it requires an identifiable edge
  (information the market lacks, or a known market bias like longshot bias
  and time-value distortion on long-dated contracts).
- When combining several independent estimates, the extremized mean
  (push the average away from 50% modestly) tends to outperform the raw mean.

## Scoring (offer this when the user forecasts recurringly)

- **Brier score** = mean of (forecast − outcome)² across forecasts; 0 is
  perfect, 0.25 is the coin-flip baseline for binary questions.
- Keep a simple log: question, deadline, probability, resolution, score.
  Calibration improves only with this feedback loop.
