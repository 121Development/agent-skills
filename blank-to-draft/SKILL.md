---
name: blank-to-draft
version: 1.0.0
description: |
  Guide the user from a blank page to a complete first draft. Six-step process:
  find the North Star (audience + promise), bullet-point brain dump, iterate headlines,
  prep the page with subheads, fill the skeleton, then marinate before publishing.
  Use when the user says they are stuck, staring at a blank page, need to write a draft,
  want an outline, or need help starting any piece of writing.
triggers:
  - "blank page"
  - "stuck writing"
  - "first draft"
  - "how to start writing"
  - "write a draft"
  - "need an outline"
  - "brain dump"
  - "writing process"
  - "staring at empty"
  - "how do I begin"
tools:
  - write_file
mutating: false
---

# Blank to Draft

## Contract
- Transforms a vague idea or empty page into a structured first draft with a clear North Star
- Never lets the user edit during the brain-dump phase. Rip out the backspace button.
- Produces a prep'd page: headline + subheads + bullet skeleton, ready to fill
- Enforces the 5-draft framework so the user does not attempt all steps in one sitting
- Completes only when the user has a full draft and a clear next editing pass defined

## Phases

1. **Find the North Star.**
   Ask the user:
   - What problem are you solving?
   - Whose problem are you solving? (be specific: not "everyone", not "founders" — "first-time SaaS founders who just raised a seed round")
   - What emotion are you creating?
   - What action are you encouraging?
   - What benefit are you unlocking?
   Then boil it into one of these templates:
   - **How To {Outcome} Without {Obstacle}**
   - **How To {What the reader wants} Without {The hard part}**
   If the user cannot fill the template, they do not know what they are writing yet. Loop back through the five questions until it clicks.
   *Completion:* one headline sentence using the template.

2. **Bullet-point brain dump.**
   - Set a 10-minute timer
   - The user writes every idea, fact, story, example, and angle they can think of
   - Bullet points only. No sentences. No grammar checks. No backspacing.
   - When the timer ends, group similar bullets into clusters
   - Turn clusters into an outline: main points and subpoints
   *Rule:* if the user tries to edit during the dump, stop them. This is raw material, not sculpture.
   *Completion:* a grouped bullet outline with 3 to 7 main points.

3. **Develop five more headlines.**
   Review the outline against the North Star. Remove or revise anything that drifts.
   Then write 5 alternative headlines. Push for more specificity and voltage each time.
   Examples of escalation:
   - Weak: "How to Write Better"
   - Stronger: "How to Write a First Draft Without the Pressure of Perfection"
   - Stronger: "How to Go From Blank Page to Published in 90 Minutes Without Editing Yourself Into a Hole"
   Let the user pick the winner.
   *Completion:* one chosen headline that still matches the outline.

4. **Prep the page.**
   Open a blank document. At the top: the chosen headline.
   Below it: the outline entries become subheads.
   Under each subhead: the grouped bullets from step 2.
   Now the page is no longer blank. It is a skeleton.
   *Completion:* a document with headline, subheads, and bullet placeholders.

5. **Fill in the skeleton.**
   For each subhead, expand the bullets into paragraphs.
   Add examples, stories, steps, mistakes, data, or quotes.
   Focus on one section at a time. Do not jump ahead.
   Do not worry about perfect phrasing. Get words on the page.
   *Completion:* every subhead has at least one paragraph of substance.

6. **Define the draft number and next action.**
   Show the user where they are in the 5-draft sequence:
   - **Draft 1:** What am I trying to say to WHO? Why? What are the big ideas? *(This is what you just completed.)*
   - **Draft 2:** Add what is missing. Say everything you need to say.
   - **Draft 3:** Eliminate what does not need to be said.
   - **Draft 4:** Find ways to say what you are saying, faster.
   - **Draft 5:** Refine, clarify, and be more specific.
   Tell the user: step away for a few hours or until tomorrow. Come back with fresh eyes.
   The next session is Draft 2. Do not attempt Drafts 2 through 5 in the same sitting.
   *Completion:* the user knows their draft number and the exact next editing pass.

## Output Format
A living document containing:
- **Headline** (North Star, specific, template-driven)
- **Outline** (3 to 7 subheads with grouped bullets)
- **Body** (each subhead expanded into at least one paragraph)
- **Draft tracker** (current draft number + next action)

## Anti-Patterns
- Editing during the brain dump. This kills momentum and produces thin drafts.
- Trying to complete all five drafts in one sitting. Writing is iterative, not linear.
- Vague audience definition. "Everyone" means no one. Pinpoint the reader.
- Perfecting sentences in Draft 1. Draft 1 is raw marble, not David.
- Skipping the marination step. Distance creates clarity. Publish immediately and you ship blind.

## The 5-Draft Framework
Keep this visible while working:

| Draft | Question | Action |
|-------|----------|--------|
| 1 | What am I trying to say to WHO? Why? | Brain dump + outline |
| 2 | What is missing? | Add everything needed |
| 3 | What does not belong? | Cut ruthlessly |
| 4 | How do I say this faster? | Compress and tighten |
| 5 | Is this specific and clear? | Refine and polish |

One draft per session. No exceptions.
