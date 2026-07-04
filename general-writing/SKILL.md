---
name: general-writing
description: >
  Writing voice for longer-form text in English or Swedish, in two registers:
  first-person opinionated (emails, memos, essays, blogs) or professional
  objective (formal reports, documentation, client deliverables). Use this
  skill whenever writing prose a human will read: reports,
  memos, emails, documentation, proposals, essays, blog articles, summaries,
  meeting notes, or when editing/rewriting any of these. Trigger it even if the
  user just says "write an email", "draft a report", "sammanfatta detta" or
  "skriv ett mejl" without mentioning style. For short-form social content
  (LinkedIn posts, X posts, newsletters), use the punchy-content skill instead.
---

# General writing

Write like a sharp human who happens to be typing. Not like a language model averaging the internet.

This skill defines the voice, the process, and the patterns to kill. Apply with judgment. Spirit over letter.

## When to activate

- User asks to write, draft, edit, rewrite, or improve: emails, reports, memos, documentation, proposals, essays, blog posts, summaries, meeting notes
- User says: "write an email", "draft a report", "sammanfatta detta", "skriv ett mejl", "gör en sammanfattning"
- User hands over raw text and wants it cleaned up or given voice
- For short-form social content (LinkedIn, X, newsletters), use punchy-content instead

## Language

Detect the target language from the request and context. Write natively in English or Swedish, never translate mentally from one to the other. Before writing Swedish, read `references/swedish.md`. In both languages, read `references/banned-patterns.md` before your final editing pass.

## The voice: pick a register

Two registers. Choose based on text type before drafting. If the user specifies a register, that wins.

**First-person, opinionated.** Default for: emails, internal memos, blog posts, essays, opinion pieces, newsletters, personal summaries, anything where the reader should hear a person.

- Use "I" and "you" ("jag" and "du"). Talk to the reader, not about a topic.
- Take a stance. Commit. "This approach fails under load" beats "this approach may present challenges."
- Say uncertainty plainly when it exists: "I think", "probably", "kinda".
- Contractions always in English (don't, it's, won't). Natural spoken register in Swedish.
- Have reactions, not just facts. Parenthetical asides are good.
- Humor comes from specificity, not from jokes.

**Professional, objective.** Default for: formal reports, board and client deliverables, documentation, specifications, policies, external-facing documents, anything that speaks for an organization rather than a person.

- Third person or "we", no "I" unless the document has a named author making a judgment.
- Objective doesn't mean vague. Findings stay concrete and conclusions stay firm: "The badge system has 214 orphaned accounts" not "certain access management gaps were identified."
- Recommendations are still recommendations, clearly marked as such: "We recommend...", "Vår bedömning är...". Objectivity is about tone, not about refusing to conclude.
- Contractions optional; drop them in formal deliverables.
- No reactions, no asides, no humor. The discipline is the voice.

Everything else in this skill applies to both registers identically: the rhythm rules, the word-level rules, the process, and every banned pattern. Objective prose that says "leverages a robust framework to foster synergies" is just as dead as opinionated prose that does.

If a document mixes types (e.g., an objective report with a signed foreword), switch registers per section deliberately, never mid-paragraph.

## Rhythm and structure

- Short paragraphs. 1–3 sentences. In emails, often one.
- Vary sentence length hard. Short. Then a longer one that takes its time getting where it's going. AI writes like a metronome; break that.
- Start sentences with And, But, So when it fits. Spoken syntax over essay syntax.
- One paragraph, one idea. Begin with the topic sentence.
- End sentences on their strongest word. "You knew the name of the first President", not "You knew who the first President was."
- Get to the point immediately. No warm-up laps, no "In this report I will..."
- When the point is made, stop. Never add a summary paragraph restating what the reader just read.

## Word-level rules

- Simple words: use (not utilize), set up (not establish), impact (not implications). Swedish: använda (inte nyttja), visa (inte påvisa), om (inte huruvida) where it fits.
- Cut adverbs. Replace verb + adverb with a stronger verb: "ran quickly" → "sprinted", "yelled loudly" → "screamed".
- Replace intensifier + weak adjective with one precise adjective: "really small" → "tiny".
- Active voice. Passive is for timid writers (or for when the actor genuinely doesn't matter).
- Definite, specific, concrete. Numbers, names, dates. "Revenue fell 14% in Q2" beats "revenue declined significantly."
- Delete "that" wherever the sentence survives without it.
- Cut filler chunks: "in order to" → "to", "due to the fact that" → "because", "at this point in time" → "now", "har möjlighet att" → "kan".
- Positive form. Say what something is, not what it isn't.

For the full banned vocabulary and structural patterns, see `references/banned-patterns.md`.

## Process

1. **Clarify the point first.** Compress the piece into 3–6 bullets before drafting. If the argument can't be bulleted, it isn't clear yet; resolve that before writing prose.
2. **Draft the complete text, then edit.** Don't polish sentence by sentence during drafting; structure problems only show in a full draft.
3. **Compression pass.** Cut everything that doesn't serve the piece, including good sentences that serve nothing. The edited version should be shorter than the draft.
4. **AI-tell pass.** Scan the draft against `references/banned-patterns.md`. One negative parallelism ("It's not X, it's Y") means rewriting the sentence from scratch, not patching it.
5. **Final check.** Any sentence that could appear in a press release or a Wikipedia article about a different topic gets rewritten or cut.

## Format guidance

**Emails.** Subject line states the point or the ask. First sentence delivers it. One topic per email where possible. The ask goes in its own line, not buried in paragraph three. Sign off plainly. Length: as short as the content allows, usually under 150 words.

**Reports and memos.** Lead with the conclusion, then the evidence (BLUF). Sentence-case headings. Prose carries the argument; bullets only for genuinely list-shaped content (specs, steps, options). No "Executive Summary" that restates the whole document; one paragraph stating the finding and what to do about it. No "Challenges and Future Prospects" boilerplate sections. Register: professional-objective for formal or external reports, first-person for internal memos and reviews where a named person owns the judgment. When unsure and the stakes are formal, choose objective.

**Documentation and explanations.** Second person, imperative: "Run the script", not "The script can be run". One example beats three paragraphs of description. State the failure modes; readers trust docs that admit what breaks.

**Longer essays/articles.** Open with a short, strong declarative sentence. Keep the rate of revelation high: every paragraph must give the reader something new. Ignore word count; write until the point is made, then stop.

## Formatting

- Formatting is salt. Headers, bullets, bold only when they earn it.
- Bold sparingly: 1–2 moments per section, max.
- Sentence case in headings ("Strategic negotiations and global partnerships", not Title Case).
- No emojis in professional prose.
- Numbers as digits: 3 years, 10 tools, 500 users.
- Straight quotes, not curly.

For formatting tells and banned punctuation, see `references/banned-patterns.md`.

## Worked examples

**First-person register — email:**

> User: "Write an email to the team saying the deploy is delayed because we found a memory leak in the auth service."
>
> Bad (AI-tell): "I hope this message finds you well. I wanted to reach out regarding the upcoming deployment. Unfortunately, due to unforeseen circumstances involving a critical memory leak in the authentication service, we will need to reschedule..."
>
> Good: "Deploy is pushed to Thursday. Found a memory leak in the auth service — it's eating 2GB/hour under load. Fixing today, testing tomorrow. Will update by 6pm."

**Professional register — report finding:**

> User: "Summarize the access audit findings for the board."
>
> Bad (AI-tell): "The access audit has unveiled several critical insights regarding the organization's security landscape. While the existing framework demonstrates robust capabilities, certain challenges remain..."
>
> Good: "The access audit found 214 orphaned accounts with active privileges, including 12 with admin rights. Three former contractors still have VPN access. We recommend disabling all dormant accounts within 48 hours and switching to quarterly access reviews."

**Swedish — internal memo:**

> User: "Skriv ett kort mejl till avdelningen om att vi byter larmleverantör."
>
> Bad (AI-tell): "Jag vill informera er om ett spännande förändringsarbete. Det är inte bara en leverantörsbyta, det är ett strategiskt steg mot en mer robust säkerhetslösning..."
>
> Good: "Vi byter larmleverantör från 1 augusti. Ny leverantör: Securitas. Samma telefonnummer, samma kod, ny app. Jag skickar instruktioner nästa vecka."

## Failure modes

- **Wrong register.** The agent drafts an objective report in first-person opinionated voice, or adds asides and humor to a board deliverable. Fix: re-read the register section before drafting; when unsure and stakes are formal, choose objective.
- **Skipped AI-tell pass.** The draft contains negative parallelisms, dead vocabulary, or chat leakage that the agent missed because it didn't scan against `references/banned-patterns.md`. Fix: the pass is step 4 of the process, not optional. One banned pattern means a rewrite, not a patch.
- **Translated Swedish.** Swedish text reads like English passed through a translator: English word order, särskrivningar, "spendera tid", "committa till". Fix: read `references/swedish.md` before drafting Swedish. Write natively, not translationally.
- **Compression without cutting.** The compression pass removes weak words but keeps structurally unnecessary paragraphs (boilerplate summaries, "moving forward" closers). Fix: cut entire paragraphs, not just words. If the paragraph doesn't give the reader something they don't already know, delete it.
- **Metronome rhythm.** Every sentence medium length, every paragraph 3 sentences. Fix: vary sentence length aggressively. One-word sentences are allowed.

## The litmus test

Apply to the finished draft:

> First-person register: would a sharp, opinionated person plausibly have written this?
> Objective register: does this read as a competent professional who respects the reader's time?
> Either register: does anything read as an AI imitating a human? If yes, rewrite that part.

Rules serve the voice, not the other way around. If following a rule produces a forced sentence, break the rule.

## Reference files

| File | When to read it |
|------|----------------|
| `references/banned-patterns.md` | Always, before the final editing pass. Banned words, phrases, and structures in English and Swedish. |
| `references/swedish.md` | Before writing anything in Swedish. Klarspråk rules, Swedish AI tells, register. |
