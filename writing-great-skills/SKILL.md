---
name: writing-great-skills
description: Reference for writing and editing skills well — the vocabulary and principles that make a skill predictable.
disable-model-invocation: true
---

A skill exists to wrangle determinism out of a stochastic system. **Predictability** — the agent taking the same _process_ every run, not producing the same output — is the root virtue; every lever below serves it.

**Bold terms** are defined in [`GLOSSARY.md`](GLOSSARY.md); look them up there for the full meaning.

## First principles

These six principles sit above every section that follows. Use them to resolve trade-offs when the rules below conflict.

1. **Trigger from the description.** The frontmatter `description` is the only part read before the skill loads. Say what the skill does and the concrete situations that should trigger it. Do not hide trigger rules in the body.
2. **Spend tokens like they are scarce.** Assume the agent is already good at general reasoning. Keep only non-obvious workflow, domain constraints, tool choices, failure modes, and validation rules. Delete background, motivation, and generic advice.
3. **Write procedures, not essays.** Prefer imperative rules, decision points, and small examples. A good skill changes behavior in the next turn; it does not merely explain the topic. Match the procedure to the deliverable's shape: a catalog of techniques with "pick what fits" produces tool-picking, not a flow. If the job is a shaped interaction (an interview, a staged walk, a staged review), the workflow must *be* that shape, with the techniques demoted to steps inside it.
4. **Use progressive disclosure.** Keep the main skill file short. Push long schemas, examples, provider docs, or variant-specific guidance out into linked `references/` files, reached by a pointer that fires only when needed. Put repeatable fragile operations in `scripts/`. Put reusable output material in `assets/`.
5. **Validate by use.** A skill is good when a fresh agent applies it correctly on a realistic task — run it blind, and on the weakest model that will run it. After editing, read it as if you had no conversation history and remove anything that would not affect action.
6. **Examples document the problem, not the solution.** An example earns its tokens by teaching the agent to *recognise a recurring problem* — the smell, the symptom, how you knew it was wrong. The fix you happened to apply is not durable. Write the failure mode and its tell; let the agent derive the fix fresh.

## Invocation

Two choices, trading different costs:

- A **model-invoked** skill keeps a **description**, so the agent can fire it autonomously _and_ other skills can reach it (you can still type its name too). It contributes to **context load** — the description sits in the window every turn. Mechanics: omit `disable-model-invocation`, and write a model-facing description with rich trigger phrasing ("Use when the user wants…, mentions…").
- A **user-invoked** skill strips the description from the agent's reach: only you, typing its name, can invoke it — and no other skill can. Zero context load, but it spends **cognitive load**: _you_ are the index that must remember it exists. Mechanics: set `disable-model-invocation: true`; the `description` becomes human-facing — a one-line summary, trigger lists stripped.

Pick model-invocation only when the agent must reach the skill on its own, or another skill must. If it only ever fires by hand, make it user-invoked and pay no context load.

When user-invoked skills multiply past what you can remember, that piled-up cognitive load is cured by a **router skill**: one user-invoked skill that names the others and when to reach for each.

## Skill shape

Skills come in two shapes. Picking the wrong one is the most common structural mistake.

**Simple** — a single `SKILL.md`, no subdirectories, no disclosed references. Appropriate when the skill is one focused capability, the instructions fit comfortably under ~100 lines, and every user of the skill needs every line every time. The cost of simplicity is that everything lives in the context window whenever the skill loads.

**Compound** — `SKILL.md` plus one or more disclosed reference files (methodology docs, component libraries, templates) reached by **context pointers**. Appropriate when the workflow has multiple phases, when different runs need different depths of context, or when the full material would bloat the window for quick-reference use. The cost of compounding is the indirection: the agent must follow pointers correctly, and you must maintain the split boundary.

The decision is not about total line count; it is about **branch divergence**. If every run walks the same path, keep it simple. If some runs need the quick reference and others need the deep methodology, split by branch and push the deep material behind a pointer.

## Directory layout

The host system decides the root path, but the internal layout is standard:

```
skills/<name>/
├── SKILL.md                 # always present
├── references/              # disclosed reference (optional)
│   └── methodology.md
├── templates/               # reusable templates (optional)
│   └── report.md
└── scripts/                 # executable helpers (optional)
    └── validate.py
```

Keep the top level flat. Three subdirectories are enough: `references/` for deep reading, `templates/` for reusable artifacts, `scripts/` for executable helpers. Name every file for what it holds, not for its type (`methodology.md`, not `reference-1.md`).

## Writing the description

A model-invoked **description** does two jobs — state what the skill is, and list the **branches** that should trigger it. Every word increases **context load**, so a description earns even harder pruning than the body:

- **Front-load the skill's leading word** — the description is where it does its invocation work.
- **One trigger per branch.** Synonyms that rename a single branch are **duplication** — "build features using TDD … asks for test-first development" is one branch written twice. Collapse them; keep only genuinely distinct branches.
- **Cut identity that's already in the body.** Keep the description to triggers, plus any "when another skill needs…" reach clause.

## Trigger section

The body needs an explicit trigger section — typically titled "When to activate" or similar — that repeats the branches in the description with more detail. The description is for the model's router; the trigger section is for the model once the skill loads. Both must exist: the description fires the skill, the trigger section confirms the skill was the right choice.

List trigger conditions as concrete user phrases or task shapes, not abstractions. "User asks for a forecast, probability, odds, or likelihood" is better than "statistical queries".

## Instruction voice

Instructions must be imperative: verb-first, direct, actionable. The agent is not being persuaded; it is being directed.

- ✅ "Run the test suite before committing."
- ✅ "Search 2–4 targeted queries before adjusting the base rate."
- ❌ "You should run the test suite before committing."
- ❌ "We will search for relevant information."

The test for instruction voice: can you prepend the word "Agent," and does it still read like an order, not a conversation? If not, rewrite.

Be specific about quantities and limits. "Search 2–4 queries" is better than "do some research" because it sets a **completion criterion** the agent can check.

Match the procedure to the deliverable's shape. A catalog of techniques with "pick what fits" produces tool-picking, not a flow. If the job is a shaped interaction (an interview, a staged walk, a staged review), the workflow must *be* that shape, with the techniques demoted to steps inside it.

## Information hierarchy

A skill is built from two content types — **steps** and **reference** — that mix freely: a skill can be all steps, all reference, or both. The core decision is which to use and where each sits on the **information hierarchy**, a ladder ranked by how immediately the agent needs the material:

1. **In-skill step** — an ordered action in `SKILL.md`, the primary tier: what the agent does, in order. Each step ends on a **completion criterion**, the condition that tells the agent the work is done. Make it _checkable_ (can the agent tell done from not-done?) and, where it matters, _exhaustive_ ("every modified model accounted for", not "produce a change list") — a vague criterion invites **premature completion**.
2. **In-skill reference** — a definition, rule, or fact in `SKILL.md`, consulted on demand. Often a legitimately flat peer-set (every rule of a review on one rung) — a fine arrangement, not a smell. _This skill is all reference._
3. **External reference** — reference pushed out of `SKILL.md` into a separate file, reached by a **context pointer**, loaded only when the pointer fires. (Spans _disclosed_ reference — a sibling file like `GLOSSARY.md`, still part of the skill — through fully **external reference** that lives outside the skill system and any skill can point at.)

A demanding completion criterion drives thorough **legwork** — the digging the agent does within the work — whether the skill has steps or not, since "every rule applied" binds flat reference just as "every step done" binds a sequence.

Push too little down and the top bloats; push too much and you hide material the agent actually needs. That tension is the whole decision.

**Progressive disclosure** is the move down the ladder — out of `SKILL.md` into a linked file — so the top stays legible. Mechanics: a linked `.md` file in the skill folder, named for what it holds (this skill discloses its full definitions to `GLOSSARY.md`). Some skills are used in more than one way, and each distinct way is a **branch** — different runs taking different paths through the skill. Branching is the cleanest disclosure test: inline what every branch needs, and push behind a pointer what only some branches reach. A **context pointer**'s _wording_, not its target, decides when and how reliably the agent reaches the material.

Where the ladder decides _how far down_ a piece sits, **co-location** decides _what sits beside it_ once there: keep a concept's definition, rules, and caveats under one heading rather than scattered, so reading one part brings its neighbours with it.

## When to split

**Granularity** is how finely you divide skills, and each cut spends one of the two loads, so split only when the cut earns it. Two cuts:

- **By invocation** — split off a **model-invoked** skill when you have a distinct **leading word** that should trigger it on its own, or another skill must reach it. You pay **context load** for the new always-loaded **description**, so that independent reach has to be worth it.
- **By sequence** — split a run of **steps** when the steps still ahead (a step's **post-completion steps**) tempt the agent to rush the one in front of it (**premature completion**). Keeping them out of view encourages the agent to do more **legwork** on the current task.

## Pruning

Keep each meaning in a **single source of truth**: one authoritative place, so changing the behaviour is a one-place edit.

Check every line for **relevance**: does it still bear on what the skill does?

Then hunt **no-ops** sentence by sentence, not just line by line: run the no-op test on each sentence in isolation, and when one fails, delete the whole sentence rather than trim words from it. Be aggressive — most prose that fails should go, not be rewritten.

## Leading words

A **leading word** is a compact concept already living in the model's pretraining that the agent thinks with while running the skill (e.g. _lesson_, _fog of war_, _tracer bullets_). Repeated throughout the text (though not necessarily — a strong leading word might only be needed once), it accumulates a distributed definition and anchors a whole region of behaviour in the fewest tokens, by recruiting priors the model already holds.

It serves predictability twice. In the body it anchors _execution_: the agent reaches for the same behaviour every time the word appears. In the description it anchors _invocation_: when the same word lives in your prompts, docs, and code, the agent links that shared language to the skill and fires it more reliably.

Hunt for opportunities to refactor skills to use leading words. A triad spelled out at three sites (**duplication**), a description spending a sentence to gesture at one idea — each is a passage begging to **collapse** into a single token. Before and after:

| Before | After | What changed |
|---|---|---|
| "fast, deterministic, low-overhead" | _tight_ | One quality restated across a phase collapses into a single pretrained word (a _tight_ loop). |
| "a loop you believe in" | _red_ | A fuzzy gate becomes a binary observable state (the loop goes _red_ on the bug, or it doesn't). |
| "be thorough" | _relentless_ | A weak leading word that the agent already obeys by default is upgraded to a stronger one that actually changes behavior. |

You win twice over: fewer tokens, _and_ a sharper hook for the agent to hang its thinking on. Assume every skill is carrying restatements that leading words retire — go find them.

## Worked examples

Every skill that does something should show something. A worked example is not decoration; it is a compressed test case that validates the skill's instructions against reality. The agent reading the skill uses it as a reference point; the user reading the skill uses it to judge whether the skill fits their need.

An example earns its tokens by teaching the agent to *recognise a recurring problem* — the smell, the symptom, how you knew it was wrong. The fix you happened to apply is not durable. Write the failure mode and its tell; let the agent derive the fix fresh.

> *Example of durable teaching:* "A directional question gated on a centroid distance read wrong from every bearing" teaches; "so we keyed it on FRONT_ARC" rots.

Include at least one concrete example that walks through a full invocation: the user's input, the skill's response shape, and the key decision points. If the skill has branches, show one example per major branch. Keep examples tight — they should demonstrate the skill's process, not reproduce its full output.

If a skill has no examples, that is a signal that either the skill is purely reference (legitimate, but rare) or the author has not actually exercised it.

## Failure modes

Use these to diagnose issues the user may be having with the skill.

- **Premature completion** — ending a step before it's genuinely done, attention slipping to _being done_. Defence, in order: sharpen the completion criterion first (cheap, local); only if it is irreducibly fuzzy _and_ you observe the rush, hide the post-completion steps by splitting (the sequence cut).
- **Duplication** — the same meaning in more than one place. Costs maintenance and tokens, and inflates a meaning's prominence on the ladder past its real rank.
- **Sediment** — stale layers that settle because adding feels safe and removing feels risky. The default fate of any skill without a pruning discipline.
- **Sprawl** — a skill simply too long, even when every line is live and unique. Hurts readability and maintainability and wastes tokens. The cure is the ladder: disclose **reference** behind pointers, and split by **branch** or sequence so each path carries only what it needs.
- **No-op** — a line the model already obeys by default, so you pay load to say nothing. The test: does it change behaviour versus the default? A weak leading word (_be thorough_ when the agent is already thorough-ish) is a no-op; the fix is a stronger word (_relentless_), not a different technique.

## Concrete anti-patterns

Copy-level mistakes that show up in review:

| Pattern | Why it fails | Fix |
|---|---|---|
| Vague description | "A skill for web development" gives the model nothing to match on | State what it does, name the tools, list trigger phrases |
| Missing trigger section | The description fires the skill, but the body never confirms the skill was the right choice | Add an explicit "When to activate" section with concrete user phrases |
| Conversational instructions | "You should create a directory" sounds like advice, not an order | Imperative voice: "Create the directory" |
| No completion criteria | Steps end with narrative, not a checkable gate | Every step ends on a condition the agent can verify |
| No examples | The user cannot tell if the skill fits their need | Include one tight worked example per major branch |
| Broken context pointers | A reference to `references/methodology.md` that does not exist | Verify every pointer before committing |
| Duplicating external context | Copying global rules or environment setup into the skill | Reference by name; assume the host system provides it |
| Duplicating between body and references | Banned patterns, vocab lists, or formatting rules restated in both SKILL.md and a disclosed reference | Single source of truth; point from body, keep detail in reference |
| Over-splitting | A 20-line skill with three disclosed reference files | Keep it simple unless branch divergence justifies the split |
| Under-splitting | A 400-line SKILL.md with no disclosed references | Push deep methodology behind pointers; keep the top as quick reference |

## Pre-flight checklist

Before a skill is ready:

- [ ] **Shape is correct** — simple or compound, justified by branch divergence
- [ ] **Description earns its load** — model-facing triggers are specific and exhaustive; user-facing description is stripped to identity
- [ ] **Trigger section exists** — body confirms the branches listed in the description
- [ ] **Instructions are imperative** — every directive is verb-first and actionable
- [ ] **Completion criteria are checkable** — every step ends on a verifiable condition
- [ ] **Examples are present** — at least one worked example per major branch
- [ ] **Pointers resolve** — every linked file exists and is reachable
- [ ] **No duplication** — every meaning lives in a single source of truth
- [ ] **No-ops removed** — every sentence changes behaviour versus the default
- [ ] **Leading words recruited** — restated concepts are collapsed into pretrained terms
- [ ] **Tested with realistic input** — the skill was exercised, not just written

For a table-form version of this checklist with common failures, see `references/review-checklist.md`.
