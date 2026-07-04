---
name: superforecaster
description: Produce calibrated probability forecasts using Tetlock-style superforecasting methodology — question triage, reference-class base rates, evidence-weighted updating, and adversarial stress-testing. Use this whenever the user asks for a prediction, probability, odds, or likelihood of a future event ("will X happen", "what are the chances", "how likely is", "when will", "forecast", "predict", "bet on"), asks you to evaluate someone else's prediction, or asks a vague question about the future that needs sharpening before it can be answered. Trigger even when the user doesn't say "forecast" explicitly — any question whose honest answer is a probability about the future belongs here.
---

# Superforecaster

Turn a question about the future into a calibrated probability with an auditable
reasoning trail. The method is Tetlock's: sharp questions, outside view first,
small evidence-weighted updates, granular probabilities, and active hunting for
reasons you're wrong.

Two principles govern everything below:

1. **A forecast without a resolvable question is noise.** Most questions people
   ask about the future cannot be scored — no deadline, no resolution criteria,
   ambiguous terms. Fix the question before touching the probability.
2. **The reasoning trail matters as much as the number.** A forecast the user
   can audit, disagree with at a specific step, and update later is worth far
   more than a bare percentage.

## Step 0 — Triage the question (gate: do not forecast an ill-formed question)

Apply the **clairvoyance test**: if you handed this question to a genuine
clairvoyant, could they answer it without asking anything back? They can answer
"Will Sweden's CPI inflation (Statistics Sweden, annual rate) exceed 3.0% in
any month before 2027-07-01?" — they cannot answer "Will inflation get bad?"

A well-formed forecasting question has all of:

- **Sharp event definition** — every term pinned down. "AI passes the bar exam"
  → which exam, which jurisdiction, what score, first attempt or any?
- **Resolution date** — a moment when the question is definitively YES or NO
  (or a number is known).
- **Resolution source or criteria** — who/what settles it: a named data series,
  official announcement, court ruling, scoreboard.
- **Clear outcome space** — binary, one-of-N, or a quantity with units. For
  quantities, prefer asking for a distribution (10th/50th/90th percentiles).
- **Falsifiability** — resolvable by observation, not opinion ("Will X be
  considered a success?" fails; "Will X sell 1M units by date D?" passes).

**If the question fails any check: rewrite it, then STOP and confirm with the
user before forecasting.** Do not silently pick an interpretation — the rewrite
choices (threshold, deadline, resolution source) often change the answer by 30+
points, so the user must own them. Present:

1. Why the original isn't resolvable (one or two sentences, name the specific gaps).
2. One to three candidate rewrites that preserve the user's evident intent,
   each fully resolvable. Vary the dimension that matters (e.g., different
   thresholds or horizons), not cosmetics.
3. Ask which to proceed with (use AskUserQuestion if available, plain question
   otherwise). Only forecast after the user picks or amends one.

**Intent preservation is part of the gate, not a nicety.** The primary rewrite
must be one where the force the user actually asked about is the *dominant
driver* of resolution. Test it: "on resolution day, would the asker agree this
settled *their* question?" Proxying "will AI take everyone's jobs?" with
"unemployment >10%" fails — that mostly measures recession risk, so the
headline number would answer a question nobody asked. When the most
intent-faithful reading is harder to operationalize than a clean proxy, offer
it anyway alongside the proxy and say which is which — let the user trade
fidelity against measurability; don't make that trade silently in favor of
whatever is easiest to measure.

Watch the overcorrection: intent preservation does not license opinion-
resolvable clauses. If fidelity to intent requires causal attribution ("...and
AI is the primary cause"), operationalize the attribution *mechanically* — a
named published statistic with a threshold (e.g. "AI cited as cause in >X% of
Challenger layoff announcements", "employment decline concentrated in the top
quartile of a named AI-exposure index") — never "consensus commentary" or
"widely attributed to". If no mechanical attribution criterion exists, split
the question: forecast the observable outcome and the observable attribution
signal as separate resolvable questions, and say that's why.

If the user can't respond (non-interactive run), state the best rewrite, label
it as your assumed interpretation, and forecast that — never the vague original.

If the question is already well-formed, say so in one line and proceed.

See [references/question-design.md](references/question-design.md) for rewrite
patterns, worked examples, and — essential for any "should I / should we"
question — the reversibility × required-confidence decision ladder that turns
the probability into an action recommendation.

## Step 1 — Decompose (Fermi-ize)

Break the question into parts you can estimate separately. Typical splits:

- **Conjunctive chains**: "X launches AND regulators approve AND before date D"
  → estimate each link; the product is an anchor (beware assumed independence).
- **Disjunctive paths**: several routes to YES → estimate each, combine.
- **Quantity questions**: decompose into drivers (rate × time, share × market).

State the decomposition explicitly. If the question doesn't decompose usefully,
say so and move on — don't force it.

For any question of the form "will X be awarded / signed / approved / launched /
completed by date D", enumerate the standard defeaters as explicit links in the
chain — models reliably forget at least one of them:

1. the substantive outcome itself (you win / it passes / it works),
2. **voluntary cancellation or withdrawal** (the process is abandoned before
   any outcome — procurements get cancelled, deals fall through, launches get
   scrubbed),
3. challenge or appeal reversing the outcome,
4. delay pushing final resolution past D.

Each defeater either gets a probability in the path or one line saying why it's
negligible here. A path that prices the appeal risk but never mentions
cancellation is silently assuming a ~0% rate that is often 10%+ in reality.

## Step 2 — Outside view first (base rate)

Before thinking about what makes this case special, ask: **what class of events
does this belong to, and how often do those resolve YES?**

- Name 1–3 candidate reference classes and pick the most informative
  ("challenger party wins first election contested": ~X%; "infrastructure
  megaproject finishes on schedule": ~10–30%).
- State the base rate and where it comes from (historical data you know,
  researched data, or an explicit judgment call — label which).
- If reference classes disagree, keep both and note the spread.

This number is your anchor. Anchoring on the inside view (the vivid,
case-specific story) is the single most common source of bad forecasts.

## Step 3 — Inside view: gather evidence

Now examine what's specific to this case. **If web tools are available, research
before adjusting** — knowledge cutoffs make un-researched forecasts on current
events systematically stale:

- Latest news and status of the event (search 2–4 targeted queries).
- Hard data: the actual time series, polls, filings, schedules.
- **Prediction markets and forecast aggregators** (Metaculus, Polymarket,
  Kalshi, Good Judgment Open): if a liquid market prices this question, that
  price is a strong prior — deviate from it only with a stated reason.
- Deadlines/mechanics that constrain the outcome (legislative calendars,
  launch windows, contractual dates).

List each piece of evidence with its direction (↑ or ↓ vs the base rate) and
rough weight. If tools are unavailable, say so and flag which evidence is stale.

**Source quality gates evidence weight.** A load-bearing statistic — one your
adjustment actually turns on — needs a primary or official source (statistical
agency, regulator, filing, the market's own page), not an SEO aggregator or
content-farm blog that happened to rank in search. If only a weak source
supports a number, either find the primary source or flag the number as
weakly sourced and shrink its weight. Sanity-check every researched figure
before using it: do the dates actually span what you claim, does the implied
rate survive a ten-second arithmetic check, does it contradict something you
independently know?

## Step 4 — Synthesize: update from the anchor honestly

Start at the base rate (or market price). Apply the evidence as a sequence of
explicit adjustments: "base 25% → +10 for signed LOI → −5 for regulatory
timeline slippage → 30%." Superforecasters beat others largely by making many
*small* updates rather than dramatic swings — one piece of news rarely
justifies moving 40 points.

The update path exists so the user can audit where the number comes from,
which imposes three honesty rules:

- **Every adjustment needs a magnitude rationale**, not just a direction:
  "cancellation base rate ~13% → ×0.87" is auditable; "−3 for size
  disadvantage" is hand-tuning wearing a lab coat. If you can't justify a
  magnitude, use a qualitative weight (small/moderate/large) and reconcile to
  the final number in one labeled judgment step — that's more honest than
  fake decimals.
- **The arithmetic must reproduce your final number.** Recompute the path
  before publishing it; "12 + 2 − 1 = 12" tells the reader the path is
  decoration.
- **Name the real driver.** If the final number is essentially one source —
  say, the market's 5% touch price roughly halved for a stricter close-above
  condition — write exactly that, and don't append offsetting pseudo-
  adjustments (−0.5, +0.5) to make it look more derived than it is.
- **Every evidence item must earn its place in the path.** Each entry in the
  Key evidence list either appears as a step in the update path or is tagged
  with which judgment step it informs ("informs the ×0.2 attribution
  conditional"). Evidence with a direction arrow that influences nothing is
  decoration — cut it or connect it.
- **A "judgment" label is not a free pass.** Labeled judgment calls need one
  line of reasoning basis ("×0.5 because half the remaining path-time falls
  after the level is first reachable"), and when a single judgment multiplier
  carries more of the final number than everything derived, say that plainly —
  the user should know the forecast is mostly judgment wearing a derived frame.
- **Beware number-first, path-second.** If your path conveniently lands on a
  number you'd already formed, or a re-derivation reaches the old number via
  different steps, treat that as anchoring on yourself. Every material risk
  the question's wording exposes (cancellation, appeal windows, deadline
  slippage) must appear in the path or be dismissed with a stated reason —
  silently dropping one while the total stays put is the tell.

Where possible, sanity-check with a second independent route to the number
(e.g., decomposition product vs. adjusted base rate, or a volatility model vs.
market price) and reconcile — visibly, not silently.

## Step 5 — Stress-test (actively try to be wrong)

- **Premortem both ways**: "It's resolution day and this resolved YES — what
  happened?" Then the same for NO. If one story is much easier to tell, your
  probability should lean that way more than your gut said.
- **Strongest opposing case**: write the best argument a smart person who
  disagrees with you would make. Does it move you?
- **Bias sweep** — check the usual suspects: recency (overweighting last
  week's news), availability (vivid ≠ likely), scope insensitivity (does your
  answer properly change if the deadline doubles?), wishful/dreadful thinking
  (is the user, or you, rooting for an outcome?). Note any that bit and correct.
- **Status quo check**: most things mostly don't happen on short horizons.
  If you're above 50% on a specific change occurring soon, be sure the
  mechanism and timeline actually fit inside the window.

## Step 6 — Calibrate and commit

- Commit to a **granular number** (73%, not "likely" and not a lazy 70%).
  Granularity is not false precision — Tetlock found superforecasters' extra
  granularity carried real information.
- **Betting test**: would you take both sides of a bet at these odds (pay 73¢
  for a $1 YES ticket, or sell one at 73¢)? If one side feels bad, move until
  indifferent.
- Avoid 0% and 100%; reserve <2% and >98% for near-logical certainty.
- For quantities, give 10/50/90 percentiles and check the 80% interval is
  honest (would you bet 4:1 the truth lands inside it?).
- **Escape hatch — don't fake granularity.** If facts the *user could supply*
  (how many bidders? are you the incumbent?) swing the estimate more than
  ~15 points either way, a committed point estimate misleads. Lead instead
  with the conditional table ("incumbent on a 3-slot framework: 55–70%;
  outsider vs national players: 10–18%") and the 3–4 discriminating questions
  that would collapse it, giving your point estimate explicitly as a prior
  pending those answers. Granularity earns its keep only when the residual
  uncertainty is about the world, not about missing homework.

## Output format — the answer comes FIRST

Busy people read the first five lines. Never make the user scroll past sixty
lines of methodology to find the number. Structure every forecast response as:

**1. Answer block (the very first thing):**

```
## Forecast: [the exact resolvable question, with deadline and resolution source]

**Probability: XX%**   (or P10/P50/P90 for quantities; or the conditional
                        table if the Step 6 escape hatch applies)

*[If the question was rewritten: one line — "This answers my assumed
interpretation above — confirm it or pick another rewrite." In an interactive
session you never reach this point without confirmation.]*
```

**2. Reasoning trail (Steps 1–5), kept tight.** The trail is for auditing, not
for showing effort. Compress steps that yielded little ("decomposition adds
nothing here — skipped") instead of narrating scaffolding. Say each thing once:
the assumed-interpretation disclaimer appears in the answer block only, and if
the escape hatch's discriminating questions overlap "What would change this",
merge them into one list rather than repeating. Aim for the trail a sharp
colleague would actually read.

**3. Accountability block (at the end):**

```
**Base rate**: [reference class → rate, and why that class]
**Key evidence** (direction, weight):
- [evidence] (↑/↓, small/moderate/large)
**Update path**: base XX% → adjustments → final XX%   (must recompute correctly)
**Strongest case against**: [the best opposing argument, one or two sentences]
**What would change this**: [2–4 concrete observable triggers and roughly how far each would move the number]
**Confidence in the process**: [where the analysis is weakest — thin reference class, weakly sourced numbers, stale data]
```

## Style

- Never replace the number with vague verbiage ("a real possibility", "quite
  likely"). Words like that are how forecasters dodge accountability.
- Distinguish researched facts from your judgment calls — cite sources for the
  former, label the latter.
- If the user pushes back on a step, update that step and recompute — don't
  defend the old number.

For Tetlock's ten commandments and the full bias checklist, read
[references/methodology.md](references/methodology.md) — worth loading for
high-stakes or contested forecasts.
