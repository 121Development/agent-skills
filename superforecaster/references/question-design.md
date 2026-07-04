# Designing resolvable forecasting questions

The rewrite step is where most of a forecast's value is created or destroyed.
This file gives patterns for turning vague questions into scoreable ones while
preserving what the asker actually cares about.

## The intent-preservation rule

A rewrite is good only if the asker, on resolution day, would agree the answer
settles *their* question. "Will AI take over jobs?" rewritten as "Will US
unemployment exceed 10% by 2030?" fails this — unemployment could stay low
while job *composition* changes radically. Always ask: what observation would
the user themselves accept as "yes, that's what I meant"?

When intent is genuinely ambiguous, offer rewrites that span the plausible
intents rather than variants of one interpretation.

## Common failure modes and their fixes

| Failure | Example | Fix |
|---|---|---|
| No deadline | "Will fusion power become viable?" | Add a horizon: "...will a fusion plant deliver net electricity to a commercial grid before 2036-01-01?" |
| Undefined term | "Will the economy crash?" | Replace with a measurable proxy + threshold: "Will S&P 500 close ≥20% below its prior all-time high at any point before...?" |
| No resolution source | "Will remote work decline?" | Name the series: "...according to BLS/SCB survey X, will the share of remote workers fall below Y% in...?" |
| Opinion-resolvable | "Will the product launch be a success?" | Convert to observables: units sold, revenue, retention at date D |
| Compound question | "Will X win and immediately do Y?" | Split into separate questions, or make the conjunction explicit and forecast each part |
| Value question in disguise | "Should I take this job?" | Not forecastable as asked. Extract the forecastable sub-questions ("Will this startup raise a Series B within 18 months?") and say the decision needs the user's values on top — then use the decision ladder below |

## Decision ladder for "should I / should we" questions

A probability alone doesn't answer a decision question — the same 30% justifies
some actions and forbids others. After forecasting the extracted question, map
the probability to action with a **reversibility × required-confidence ladder**:

| Commitment type | Roughly needs | Example |
|---|---|---|
| Cheap, reversible prep | ~15–25% | draft the mobilisation plan, sketch the hire profile |
| Forgoing alternatives | ~50–60% | turning down conflicting work, reserving capacity |
| Irreversible commitments | ~80%+ | hiring, capex, signing leases — and often not before the outcome is *formally* locked in (award + appeal window, contract signed) |

Calibrate the thresholds to the user's actual stakes (a cheap option with a
huge payoff justifies acting at lower probability — expected value, not the
raw probability, drives the ladder). Present this ladder with the forecast so
the user gets a decision tool, not just a number.

## Threshold and horizon selection

The threshold/deadline you pick often determines the answer, so:

- Offer the user a **spread** when the natural threshold is unclear (e.g.,
  "below 1.75%" vs "below 1.50%"; "by end of 2026" vs "by end of 2027").
- Prefer round, checkable dates (quarter-ends, year-ends) and officially
  published series over ad-hoc cutoffs.
- Match the horizon to the user's decision. A forecast that resolves after
  the decision must be made is useless to them.

## Worked example

**Original**: "Is crypto going to make a comeback?"

Gaps: "crypto" (which asset/metric?), "comeback" (vs what baseline?), no
deadline, no source.

Candidate rewrites (spanning intents):

1. *Price intent*: "Will BTC-USD close above its current all-time high on any
   day before 2027-01-01 (Coinbase daily close)?"
2. *Adoption intent*: "Will total crypto market capitalization (CoinGecko)
   exceed $5T at any point before 2027-01-01?"
3. *Institutional intent*: "Will net inflows into US spot-BTC ETFs over 2026
   exceed those of 2024 (issuer filings)?"

Present all three, let the user pick.

## Multi-outcome and quantity questions

- "Who will win X?" → enumerate the outcome space explicitly, including
  "someone else / no one", and make probabilities sum to 100%.
- "How many / how much / when?" → forecast a distribution: report P10/P50/P90
  and state the resolution source for the eventual number. For "when",
  the percentiles are dates.
