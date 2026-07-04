---
name: clarify-project-intent
description: Run a guided intent-clarification session before, during, or after a project or coding task. Use when the user wants to get clear on intent, clarify requirements, figure out what they actually want, plan a project, mentions unknowns or blindspots, starts a new feature and seems unsure of scope, or asks you to interview them about a task. Also trigger on vague, high-stakes, or large tasks where guessing wrong would be expensive.
---

# Clarify Project Intent

Close the gap between the user's **map** (their prompt, context, assumptions) and the **territory** (real codebase, real constraints, real preferences) before expensive work happens. Produce a concrete **Intent Brief** the user can hand to a fresh implementation session.

## When to activate

- User says: "get clear on intent", "clarify requirements", "figure out what I actually want", "plan a project with me"
- User mentions: unknowns, blindspots, ambiguity, "I don't know what I don't know"
- User starts a new feature or project and seems unsure of scope
- User asks you to interview them about a task
- User hands over a vague, high-stakes, or large task where guessing wrong would be expensive

## The unknowns matrix

Diagnose which quadrant dominates before choosing techniques:

| | User knows they know it | User doesn't know they know it |
|---|---|---|
| **Known** | **Known knowns** — what's in the prompt | **Unknown knowns** — "I'll recognize it when I see it" (taste, implicit conventions) |
| **Unknown** | **Known unknowns** — open questions the user is aware of | **Unknown unknowns** — questions the user doesn't know to ask |

**Quadrant → technique:**

- Many **unknown unknowns** (new domain, new codebase area) → Blindspot Pass
- Many **unknown knowns** (taste, design, "I'll know it when I see it") → Brainstorm & Prototypes, References
- Many **known unknowns** (open decisions the user is aware of) → Interview
- Mostly **known knowns** (user is confident) → Implementation Plan, with Implementation Notes as insurance

## Workflow

### Phase 0 — Situate

1. Establish three things conversationally: the task (in their own words), their position (familiarity with domain and codebase), and the stakes (how expensive is a wrong guess?).
2. Diagnose which quadrants dominate.
3. Propose a lightweight plan: name the phases you recommend, justify why, and let the user skip. Get agreement before proceeding.

**Completion criterion:** User agrees to a phase plan, or explicitly declines all phases and asks for the Intent Brief from what you have.

### Phase 1 — Pre-implementation

Run the techniques the diagnosis calls for, in this order:

1. **Blindspot Pass** (unknown unknowns). Research the domain/codebase yourself, then teach the user what they don't know to ask. End with a reframed request for confirmation.
2. **Brainstorm & Prototypes** (unknown knowns). Brainstorm approaches spanning cheapest to most ambitious. For taste-dependent work, build 3–4 throwaway mockups with genuinely different directions for the user to react to.
3. **References** (when words fail). Ask for source code, designs, docs, or screenshots the user likes. Read them and play back extracted semantics for confirmation.
4. **Interview** (known unknowns). One question at a time, ordered by blast radius: architecture first, then data model, then UX flows, then cosmetics. Stop when remaining questions wouldn't change what gets built.
5. **Implementation Plan** (final check). Write a plan that leads with decisions the user is most likely to want to change. Ask the user to review the top section only.

**Completion criterion:** For each technique run, the user has confirmed or corrected the output, and you have captured the resolution in the running Intent Brief.

### Phase 2 — During implementation

If you are implementing, or instructing another session: keep a running `implementation-notes.md` with a **Deviations** section. When an edge case forces departure from the plan, take the conservative option, log it with a one-line rationale, and keep going.

If a deviation is large enough to invalidate the plan's premise, stop and return to Phase 1.

**Completion criterion:** Notes document exists and every deviation is logged with rationale.

### Phase 3 — Post-implementation

Offer two deliverables:

1. **Pitch / Explainer.** Package the prototype, spec, and implementation notes into one document a reviewer can absorb quickly.
2. **Quiz.** Produce a report of what actually changed, ending in a short quiz the user should pass before merging/shipping. If they miss questions, explain and re-quiz.

**Completion criterion:** User passes the quiz or explicitly waives it.

## Output: Intent Brief

Finish every session with this document. Save as markdown by default; HTML if the user prefers.

```markdown
# Intent Brief: [project name]
## Goal
One paragraph, in the user's own words where possible.
## Decisions made
Each resolved unknown: the question, the decision, why.
## Assumptions (unvalidated)
Things you decided or the user delegated — flagged for later review.
## Out of scope
Explicitly excluded, so future sessions don't drift.
## References
Code, designs, docs pointed to during the session, and what to take from each.
## Open questions
Known unknowns deliberately deferred, and the trigger for revisiting them.
## Suggested implementation prompt
A ready-to-paste prompt for a fresh session, incorporating everything above.
```

The "Suggested implementation prompt" is the payoff: the user should be able to open a new session, paste it (plus the brief), and get work aligned with their actual intent.

## Worked examples

**Example 1 — Unknown unknowns dominate**

User: "I want to add multi-tenancy to my app but I've never done it before."

- Phase 0: Task = add multi-tenancy; position = new to the concept; stakes = high (data isolation). Diagnosis = unknown unknowns dominate.
- Phase 1: Run Blindspot Pass on multi-tenancy patterns (row-level security vs schema-per-tenant vs application-level), then Interview on which pattern fits their scale, then Implementation Plan led by data model changes.
- Output: Intent Brief with chosen pattern, deferred auth decisions, and a paste-ready implementation prompt.

**Example 2 — Unknown knowns dominate**

User: "I need a landing page. I can't describe design, I just know it when I see it."

- Phase 0: Task = landing page; position = strong taste, weak vocabulary; stakes = reversible. Diagnosis = unknown knowns dominate.
- Phase 1: Skip Interview. Build 4 contrasting HTML mockups (minimal, bold, editorial, playful). Iterate on reactions. Ask for 2–3 reference sites. Write brief.
- Output: Intent Brief with chosen direction, reference semantics extracted, and a paste-ready build prompt.

**Example 3 — Known unknowns dominate**

User: "Help me get clear on intent for rebuilding our shift-scheduling module. I know the domain cold but haven't picked a data model."

- Phase 0: Task = rebuild shift-scheduling; position = domain expert, architecture undecided; stakes = medium. Diagnosis = known unknowns dominate.
- Phase 1: Brief Interview ordered by blast radius (data model first, then scheduling algorithm, then UX flows). Implementation Plan led by data model section.
- Output: Intent Brief with chosen data model, deferred UI decisions, and a paste-ready implementation prompt.

## Deeper reference

For facilitation principles, technique details, and anti-patterns: [`references/facilitation.md`](references/facilitation.md)
