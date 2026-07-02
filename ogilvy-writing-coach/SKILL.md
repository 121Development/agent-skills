---
name: ogilvy-writing-coach
description: |
  Audit any piece of writing against David Ogilvy's 10 rules from his 1982 internal memo. Use when the user says "audit this", "ogilvy check", "writing audit", "review my copy", or wants feedback on emails, social posts, newsletters, landing pages, memos, or any business writing. The skill does NOT rewrite the text. It diagnoses what's broken, what's working, and gives specific fixes so the user learns the rules by doing the rewriting themselves.
triggers:
  - "ogilvy check"
  - "audit this"
  - "writing audit"
  - "review my copy"
  - "ogilvy writing"
mutating: false
---

# Ogilvy Writing Coach

Audit any piece of writing against David Ogilvy's 10 rules from his 1982 internal memo to Ogilvy & Mather staff. The memo opened with: "The better you write, the higher you will go in Ogilvy & Mather. People who think well, write well. Good writing is not a natural gift. You have to learn to write well."

## Contract

- The user pastes the text they want audited.
- The skill diagnoses against all 10 rules. No rule is skipped.
- Violations are sorted by severity: Critical, Moderate, Minor.
- Every violation includes the exact offending quote, why it breaks the rule, and a specific fix.
- The skill also surfaces what is WORKING so the user does not edit away the good stuff.
- The skill does NOT rewrite the text. The user does the rewriting to internalize the rules.
- Output is a calibrated audit, not generic "tighten it up" feedback.

## The 10 Rules

**Rule 1: Read the Roman-Raphaelson book on writing. Read it 3 times.**
- This is meta: the skill itself embodies those principles. Not audit-able in a single piece.
- Instead, flag if the writing shows signs of someone who has NOT internalized basic readability principles.

**Rule 2: Write the way you talk. Naturally.**
- Look for: stilted phrasing, corporate voice, sentences no human would say aloud.
- The fix is usually to record yourself saying it, then transcribe.

**Rule 3: Use short words, sentences, and paragraphs.**
- Flag: sentences over 25 words, paragraphs over 4-5 lines, multi-syllable words where a short one works.
- Readability test: if you get caught up reading it aloud, it needs simplifying.

**Rule 4: Never use jargon.**
- Flag: industry jargon, buzzwords, acronyms without expansion, abstractions that hide meaning.
- Test: would an 8th grader understand this sentence?

**Rule 5: Never write more than 2 pages on any subject.**
- Flag: length without density. Rambling. Points that could be shorter.
- Not a hard page limit in digital, but the principle is: if it can't be said briefly, it hasn't been thought through clearly.

**Rule 6: Check your quotations.**
- Flag: unsourced quotes, misattributed quotes, quotes that don't add value.
- If there are no quotes, this is a pass.

**Rule 7: Never send a letter or memo on the day you write it. Read it aloud the next morning, then edit it.**
- This is process advice. The skill flags things that a fresh read would catch: typos, awkward transitions, emotional heat, unclear logic.
- Simulate the "next morning" read.

**Rule 8: If it is something important, get a colleague to improve it.**
- Meta rule. The skill itself IS the colleague. Flag things a colleague would catch that the writer missed.

**Rule 9: Before you send your letter or memo, make sure it is crystal clear what you want the recipient to do.**
- Flag: no clear CTA, buried ask, multiple competing asks, the reader finishes and doesn't know what to do next.
- Put yourself in the reader's shoes.

**Rule 10: If you want ACTION, don't write. Go tell the guy what you want.**
- Flag: situations where writing is the wrong medium entirely. Urgent action items, sensitive conversations, anything that needs real-time negotiation.
- Ask: would a 2-minute conversation solve this faster and better?

## Phases

### Phase 1: Capture the Text

Ask the user to paste the text they want audited. Accept any format: email, social post, newsletter, landing page copy, memo, thread.

### Phase 2: Overall Read

Give a one-line verdict on whether the piece is working and what the single biggest issue is.

Format:
> **Verdict:** [Working / Needs work / Broken] — [single biggest issue in 10-15 words]

### Phase 3: Rule-by-Rule Audit

For each of the 10 rules, state:
- **Status:** PASS / MINOR / MODERATE / CRITICAL
- **Evidence:** Exact quote from the text that violates (or exemplifies) the rule.
- **Why:** 1-2 sentences on why this breaks the rule.
- **Fix:** 1 sentence on the specific change to make. Not a rewrite. A direction.

If a rule passes with no issues, say PASS briefly and move on.
If a rule is not applicable (e.g. no quotes to check for Rule 6), say N/A and explain why.

### Phase 4: What's Working

List 2-5 things the writer should NOT change. Be specific. Quote the good lines.

This prevents the common failure mode where a writer over-edits and kills their own voice or strong points.

### Phase 5: Priority Fix List

Sort all violations by severity. Present as:

| Priority | Rule | Issue | Fix |
|---|---|---|---|
| Critical | #3 | Sentence is 47 words | Break into 2-3 sentences |
| Moderate | #4 | "Leverage our core competencies" | Replace with "use what we're good at" |

Limit to the top 5-7 fixes. The user should not be overwhelmed.

### Phase 6: Final Note

One paragraph summarizing the biggest leverage point: the one change that would improve this piece the most.

## Output Format

```
## Ogilvy Audit: [Piece type]

**Verdict:** [Working / Needs work / Broken] — [single biggest issue]

---

### Rule 2: Write the way you talk
**Status:** [PASS / MINOR / MODERATE / CRITICAL]
**Evidence:** "[exact quote]"
**Why:** [1-2 sentences]
**Fix:** [1 sentence direction]

### Rule 3: Short words, sentences, paragraphs
... (repeat for all 10 rules)

---

### What's Working (Don't Edit These Away)
1. "[good quote]" — [why it's strong]
2. ...

---

### Priority Fix List
| Priority | Rule | Issue | Fix |
|---|---|---|---|
| Critical | #3 | ... | ... |
| Moderate | #4 | ... | ... |

---

### Biggest Leverage Point
[1 paragraph]
```

## Anti-Patterns

- Rewriting the text for the user. The skill diagnoses; the user rewrites. That's how the rules stick.
- Generic feedback like "tighten it up" or "this isn't quite working." Every violation must name the exact rule, quote the exact text, and give a specific fix direction.
- Skipping rules. All 10 are checked even if some are N/A.
- Only listing what's wrong. Always surface what's working to prevent over-editing.
- Ranking everything Critical. Be honest about severity. A single long sentence is Moderate, not Critical. Three pages of jargon is Critical.
