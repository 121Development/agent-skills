# Facilitation principles and technique details

Reference for running the clarify-project-intent skill well. Load this when the session is high-stakes, contested, or the user is stuck.

## Principles

1. **Get the user's starting point first.** Before any technique, ask where they are in their thought process, their experience with the problem and the codebase/domain, and what "done" would look like. Their answers determine which techniques are worth running. Skip this only if the conversation already makes it obvious.

2. **One question at a time.** Never dump a questionnaire. Ask, wait, adapt. Prioritize questions whose answers would change the architecture or scope; drop questions the user's earlier answers already settled.

3. **Prefer showing over asking.** For taste-shaped unknowns (unknown knowns), a prototype or 3–4 contrasting options the user can react to beats ten questions. People are far better at recognizing than describing.

4. **Do your homework before asking theirs.** If you have access to the codebase, files, or the web, search first. Come to the user with "I found X and Y; which matches your intent?" rather than open-ended questions you could have answered yourself.

5. **Be willing to reframe.** Sometimes clarifying the unknowns reveals the problem should be solved a different way entirely. Say so explicitly rather than optimizing the original framing.

6. **Right-size the process.** A small, cheap, reversible task might need one interview question. A large migration might need every phase. Tell the user which phases you recommend and why, and let them skip.

7. **Capture as you go.** Every resolved unknown goes into the Intent Brief. Don't rely on the user remembering the conversation.

## Technique details

### Blindspot Pass

Research the domain/codebase yourself, then teach the user what they don't know to ask. Cover:

- The questions an expert would raise
- What "good" looks like in this domain
- Historical decisions and conventions in this codebase
- Common failure modes

End with: "Given this, here's how I'd rewrite your original request — does this match your intent?" This both educates the user and improves the prompt.

### Brainstorm & Prototypes

Before committing to a direction:

- Brainstorm a range of approaches spanning cheapest → most ambitious. Let the user say which resonate. This sets scope with intent.
- For anything visual or taste-dependent, build throwaway mockups with fake data (an HTML file with 3–4 genuinely different design directions). The point is cheap disagreement now instead of expensive disagreement mid-implementation.

### References

If the user struggles to articulate what they want, ask for references in this priority:

1. Source code (a library, module, or component they like — even in another language)
2. Designs, docs, diagrams
3. Screenshots

Read the reference and play back what you extracted: "so the semantics you want are X, Y, Z." Get confirmation.

### Interview

One question at a time about remaining ambiguities. Order by blast radius:

1. Architecture-changing decisions
2. Data model
3. UX flows
4. Cosmetics

Stop when remaining questions wouldn't change what gets built. If the user says "you decide" — decide, but record the assumption in the Intent Brief.

### Implementation Plan

Write a plan that leads with the decisions the user is most likely to want to change: data model changes, new type interfaces, anything user-facing. Put mechanical/boring work at the bottom. Ask the user to review the top section only. This surfaces last unknowns cheaply.

## Anti-patterns

| Pattern | Why it fails | Fix |
|---|---|---|
| Dumping a questionnaire | Overwhelms the user; answers are shallow | One question at a time, adapt after each answer |
| Skipping Phase 0 | You run techniques the user doesn't need, or miss ones they do | Always situate first: task, position, stakes |
| Building one mockup | Gives the user nothing to compare against; they can't articulate what's wrong | Build 3–4 genuinely different directions |
| Asking before researching | Wastes the user's time on questions you could answer yourself | Search codebase/web first, then ask |
| Optimizing the wrong framing | The real problem is different from what the user asked | Be willing to reframe explicitly |
| Forgetting to capture | Decisions are lost; next session repeats the same ground | Every resolved unknown goes into the Intent Brief immediately |
| Implementation plan led by boilerplate | The user reviews boring work and misses the critical decisions | Lead with architecture, data model, user-facing changes |

## Example session openings

**Unknown unknowns dominate:** "I want to add multi-tenancy to my app but I've never done it before."
→ Blindspot Pass → Interview → Implementation Plan

**Unknown knowns dominate:** "I need a landing page. I can't describe design, I just know it when I see it."
→ Brainstorm & Prototypes → References → Brief

**Known unknowns dominate:** "Help me get clear on intent for rebuilding our shift-scheduling module. I know the domain cold but haven't picked a data model."
→ Interview (data model first) → Implementation Plan
