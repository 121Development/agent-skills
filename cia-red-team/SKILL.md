---
name: cia-red-team
description: |
  Run a 4-phase hostile stress-test on any idea, plan, or decision using techniques from the CIA's declassified Tradecraft Primer (2009). Use when the user says "cia red team", "red team my idea", "stress test this plan", or wants to kill a weak idea before investing months into it. Works on startups, product launches, pitches, hires, investments, tweets, life decisions. The user must paste their idea first; then invoke the 4 prompts in order. No skipping. Each finds something the others miss.
triggers:
  - "cia red team"
  - "red team my idea"
  - "stress test this plan"
  - "kill my idea"
  - "hostile review"
mutating: false
---

# CIA Red Team

Run a 4-phase hostile stress-test on any idea using techniques from the CIA's declassified Tradecraft Primer. Adapted from the CIA Red Cell, Army Red Team University, and Pentagon Joint Doctrine Note 1-16.

## Contract

- The user pastes their idea in plain language first: what is it, who is it for, what is the goal, what would success look like in 6 months.
- Run all four prompts in order. Do not skip any. Each targets a different blind spot.
- Each prompt produces sharp, specific, hostile critique. No softening. No "here are the pros and cons." Attack only.
- The final output is a calibrated assessment: either the idea is dead (saved you 6 months) or it survives with a specific fix list.

## Phases

### Phase 0: Capture the Idea

Ask the user to paste their idea if they haven't already. One paragraph is enough:
- What is it?
- Who is it for?
- What is the goal?
- What would success look like in 6 months?

### Phase 1: Key Assumptions Check

> **Prompt:** You are a CIA analyst running a Key Assumptions Check. The user has presented an idea/plan below. Your ONLY job is to find the load-bearing assumptions — the things this plan depends on being true, which the user has not questioned and cannot point to evidence for.
>
> List every assumption you can find. For each, state:
> 1. The assumption in one sentence.
> 2. Why it is load-bearing (what collapses if it is wrong?).
> 3. What evidence, if any, supports it.
> 4. A severity rating: CRITICAL / MAJOR / MINOR.
>
> If an assumption has NO evidence behind it, flag it in red. If the plan depends on 3+ critical assumptions with no evidence, say so explicitly.
>
> Do NOT offer encouragement. Do NOT suggest fixes yet. Just surface the assumptions.

### Phase 2: Pre-Mortem

> **Prompt:** You are running a Pre-Mortem. It is 6 months from now. The idea below has FAILED. It is over. It did not work.
>
> Your job: explain exactly WHY it failed. Not "what could go wrong" — it ALREADY failed. You are writing the post-mortem now.
>
> Structure your answer:
> 1. **The headline failure:** one sentence on what killed it.
> 2. **The root cause:** the single deepest reason it died. Not a symptom. The root.
> 3. **The warning signs we missed:** 3-5 specific signals that should have told us this was coming.
> 4. **Who saw it coming:** which stakeholder group (customers, investors, team, competitors) knew first and why.
>
> At the end, state clearly:
> - If the root cause is PREVENTABLE, give a 1-paragraph prevention roadmap.
> - If the root cause is UNPREVENTABLE, say so in bold. The idea may be wrong.
>
> Be brutal. This already failed. There is no hope to protect.

### Phase 3: Hostile Competitor

> **Prompt:** You are a hostile competitor. Not "a competitor" — a SPECIFIC, motivated, funded enemy with a deadline and a grudge. You have 6 months and $500K to kill the user's idea below.
>
> Your job: write the exact playbook you would use to destroy them.
>
> Structure:
> 1. **Who you are:** name your company, your funding, your team size, your edge.
> 2. **Your attack vector:** the ONE weakness in the user's plan that lets you win. Be specific.
> 3. **Your 90-day playbook:** week-by-week what you do to exploit that weakness.
> 4. **The kill shot:** the exact moment or move that ends them.
> 5. **Why they can't stop you:** what about their model, positioning, or execution makes them vulnerable to this specifically.
>
> At the end, extract the "weakness that lets me win" into one bolded line. Then tell the user:
> - If the weakness is fixable in 30 days: say FIX IT NOW and say how.
> - If the weakness is structural/unfixable: say THEY NEED A MOAT and explain what kind.

### Phase 4: The 1-Star Review

> **Prompt:** You are the customer who just used the product/service described below. You are ANGRY. You feel CHEATED. You are writing a 1-star review that will be the top review on every platform.
>
> Your job: write that review. Not an abstract critique. The ACTUAL emotional voice of betrayal.
>
> Structure:
> 1. **The headline:** the review title that makes everyone scroll.
> 2. **The promise vs reality gap:** what they SAID they would deliver vs what you GOT. Be specific.
> 3. **The moment of betrayal:** the exact interaction or missing feature that made you realize this was a scam/waste.
> 4. **Who you told:** who you warned and what you said.
> 5. **The one thing that would have saved it:** the smallest change that would have turned your 1-star into a 4-star.
>
> At the end, extract the "made me feel cheated" line into one bolded sentence. Then tell the user:
> - If the betrayal is in the PROMISE: change the messaging.
> - If the betrayal is in the DELIVERY: change the product.
> - If both: fix both or kill the idea.
>
> Do not hold back. This is the review that kills brands.

## Output Format

After all four prompts, synthesize into a final calibration:

```
## Red Team Verdict

**Status:** DEAD / SURVIVES WITH FIXES / SURVIVES CLEAN

**Why:** 1-2 sentences

**Assumptions at risk:** [list critical assumptions with no evidence]
**Pre-mortem root cause:** [the failure mode]
**Competitor's kill shot:** [the weakness]
**Customer betrayal:** [the gap]

**Fix list (if survives):**
1. [specific fix + owner + timeline]
2. ...

**Kill reasons (if dead):**
1. [specific reason]
2. ...
```

## Anti-Patterns

- Skipping prompts. Each finds something the others miss.
- Softening the critique. The point is hostile stress-testing, not "balanced feedback."
- Running the prompts without the user's idea pasted first. Garbage in, garbage out.
- Suggesting fixes during Phase 1-4. Critique first, fixes only in the synthesis.
- Stopping at 2-3 prompts because "this is enough." It isn't.
