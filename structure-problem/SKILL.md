---
name: structure-problem
version: 1.0.0
description: |
  Write a decision memo by running two independent analyses and comparing them on one page.
  Top-down: derive possible answers from general principles without looking at evidence.
  Bottom-up: let grouped evidence speak for itself without forcing a conclusion.
  Then align the two, surface conflicts, and present the conclusion first with a reversal condition.
  Use when facing a complex decision, writing a decision memo, or needing team alignment on direction.
triggers:
  - "decision memo"
  - "structure a problem"
  - "top-down and bottom-up"
  - "decision document"
  - "product decision"
  - "write a memo"
  - "stakeholder alignment"
  - "pricing decision"
  - "should we"
  - "need to decide"
tools:
  - search_files
mutating: false
---

# Structure Problem

## Contract
- Transforms a vague subject into a specific, answerable decision with an owner and a deadline
- Runs top-down and bottom-up analyses independently; never lets one pollute the other
- Surfaces alignments, conflicts, and evidence gaps explicitly on a single comparison page
- States the conclusion first with a clear condition that would reverse it
- Never buries disagreements or forces premature resolution

## Phases

1. **State the decision.**
   - Write the exact decision as a yes/no or choice question
   - Name who must approve it
   - Set a hard deadline
   - If the prompt is a subject ("pricing"), convert it to a decision ("Should we switch to per-seat pricing before renewal season, and who approves?")
   - *Completion:* one sentence that could be answered with "yes," "no," or "Option A"

2. **Top-down analysis: principles to possibilities.**
   - Before touching any evidence, list the few potential answers that pure logic suggests
   - Consider ideal circumstances: what would make sense if resources, politics, and legacy were not constraints?
   - Write 2 to 4 candidate solutions
   - For each, state the principle or reasoning that supports it
   - *Rule:* do not look at data, tickets, or conversations during this step. Objectivity depends on this separation.
   - *Completion:* a short list of logically derived options with their supporting reasoning

3. **Bottom-up analysis: evidence to findings.**
   - Gather available evidence: support tickets, user conversations, usage data, sales notes, team stand-up comments, competitor moves, market signals
   - Group evidence by type, not by which option it favors
   - Let each group present its own findings without forcing them into a preferred conclusion
   - Note contradictions within the evidence itself
   - *Rule:* evidence groups must not be framed as "pro" or "con" for any option. They report what they see.
   - *Completion:* grouped findings, each standing on its own

4. **Combine on a single page.**
   - Place top-down possibilities and bottom-up findings side by side
   - Mark three things explicitly:
     - **Alignments:** where logic and evidence point the same way
     - **Conflicts:** where logic suggests one thing and evidence suggests another
     - **Gaps:** potential solutions with no supporting evidence, or evidence that supports no stated option
   - Do not resolve conflicts yet. Document them.
   - *Completion:* a one-page comparison with labeled alignments, conflicts, and gaps

5. **Present conclusion first, with a reversal condition.**
   - State the decision in the first sentence
   - Provide supporting evidence below
   - Explicitly explain any conflicts rather than omitting them
   - End with one sentence: the specific evidence that would lead to a different decision
   - *Completion:* a memo where the first sentence is the decision, the body is the reasoning, and the last sentence is the reversal trigger

## Output Format
A structured decision memo containing:
- **Decision statement** (one sentence, answerable, with owner and deadline)
- **Top-down possibilities** (2 to 4 options derived from principles, no evidence)
- **Bottom-up findings** (grouped evidence, self-reporting, no forced conclusion)
- **Comparison** (alignments, conflicts, gaps)
- **Conclusion** (decision first, conflicts explained, reversal condition stated)

## Anti-Patterns
- Letting the conclusion drive the evidence gathering. This produces confirmation bias dressed as analysis.
- Resolving conflicts during step 4. Discrepancies are data. Document them, do not bury them.
- Writing a subject instead of a decision. "Pricing" is not a decision. "Should we switch to per-seat pricing?" is.
- Skipping the reversal condition. Without it, the memo is a verdict, not a living decision.
- Letting the overall summary override detailed analysis. The summary is the entry point; the detail is the substance.

## Why this works
Two independent analyses produce a tension that one analysis alone cannot. The top-down keeps you honest about what should be true. The bottom-up keeps you honest about what is true. The comparison surface is where real judgment happens: deciding which findings are consistent enough to form a basis and which contradictions matter.
