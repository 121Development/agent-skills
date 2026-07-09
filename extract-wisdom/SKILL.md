---
name: extract-wisdom
description: >
  Extract structured, high-density wisdom from any content: articles, transcripts,
  podcasts, papers, books. Use when the user says "extract wisdom from this",
  "distill this into insights", "synthesize this content", "summarize this into
  key takeaways", or feeds you long-form content and wants structured output.
  Also trigger when the user pastes a transcript, article, or document and asks
  for insights, quotes, habits, facts, or a structured summary.
---

# Extract Wisdom

Transform any content into a high-density knowledge asset. The goal is not summarization. It is extraction: pulling out the ideas, quotes, habits, and insights that survive independent of the original medium.

## When to activate

- User says: "extract wisdom from this", "distill this into insights",
  "synthesize this content", "summarize this into key takeaways"
- User pastes a transcript, article, paper, book chapter, or long-form text
  and asks for insights, quotes, habits, facts, or structured output
- User references Daniel Miessler's Fabric pattern or "extract wisdom" workflow
- Another skill needs a content-decomposition step

## Worked example

User input: a 2,000-word article on deep work by Cal Newport.

Phase 1 output:
- Title: Deep Work Rules for Focus
- Author: Cal Newport
- Medium: article
- Date: 2016-01-05

Phase 2 sample (ideas):
- Deep work is cognitively demanding activity done without distraction.
- The ability to perform deep work is becoming rare and therefore valuable.
- Schedule every minute of your day in blocks to protect focus time.
- Quit social media for 30 days, then evaluate which tools you actually miss.

Phase 3 sample (insights):
- Scarcity of attention drives value of focused work in knowledge economy.
- Willpower is unreliable; systems and scheduling protect intent better.

Phase 4 sample (quote):
- "Clarity about what matters provides clarity about what does not."
  — Cal Newport, on saying no
  *Why it matters: The criterion for elimination is the criterion for focus.*

Phase 7 (takeaway):
- In a world of shallow distraction, deep focus creates work that truly outlasts the noise.
  (15 words)

## Input

The user provides content in one of these forms:

1. Raw text pasted directly into chat
2. A URL to an article, transcript, or document
3. A file path to a document on disk

If a URL or file path is given, read it first. Do not extract from a URL
without fetching the content.

## Extraction workflow

Run these phases in order. Each phase produces one section of the final output.

### Phase 1: Capture metadata

Record the source:
- Title (if known) or a 6-word descriptive label
- Author or speaker
- Medium (article, podcast transcript, book chapter, lecture, etc.)
- Date (if known)

### Phase 2: Extract high-impact ideas

Pull 20-50 ideas from the content. An idea is a discrete claim, observation,
technique, or piece of knowledge that stands on its own.

Rules:
- One idea per bullet
- Maximum 16 words per bullet
- Preserve the author's framing where it matters
- Include page markers or timestamps if the source has them
- Skip filler, repetition, and throat-clearing

### Phase 3: Extract abstract insights

Distill 10-20 broader insights from the ideas. These are patterns, principles,
or mental models that transcend the specific content.

Rules:
- One insight per bullet
- Maximum 16 words per bullet
- Frame as transferable knowledge, not content summary
- Connect to domains outside the source where natural

### Phase 4: Extract verbatim quotes

Capture 3-10 quotes that are especially sharp, surprising, or precisely worded.

Rules:
- Quote exactly. Do not paraphrase inside quotation marks
- Keep each quote to 2 sentences max
- Attribute to speaker/author
- Include a 1-sentence note on why this quote matters

### Phase 5: Extract practical habits and facts

- **Habits:** Actions, routines, or behaviors recommended or demonstrated
  in the content. 5-15 items. 16 words max each.
- **Facts:** Concrete, checkable world-knowledge stated in the content.
  5-15 items. 16 words max each.

### Phase 6: Extract references and tools

- **References:** Books, papers, people, or concepts cited by the source.
  3-10 items.
- **Recommended tools:** Software, frameworks, or methods mentioned.
  3-10 items.

### Phase 7: One-sentence takeaway

Synthesize the entire content into a single sentence of exactly 15 words.
This is the compressed essence. Every word must earn its place.

## Output format

Follow the schema in `references/output-format.md`. Use the exact section
headings and ordering listed there.

## Quality checks

Before delivering:

1. Count the words in every bullet. Any bullet over 16 words gets cut or
   split until it complies.
2. Verify every quote is verbatim. If you are uncertain, downgrade it to a
   paraphrased idea in Phase 2 instead.
3. Check the 15-word takeaway. Exactly 15. Not 14. Not 16.
4. Remove duplicate ideas. One concept should not appear in both Phase 2
   and Phase 3 unless the Phase 3 version is genuinely abstracted.
5. Strip meta-commentary. Do not include phrases like "the author argues"
   or "this section discusses." State the claim directly.

## Failure modes

- **Bloated bullets:** Bullets creep past 16 words because the extractor
  tries to preserve nuance. Fix: split into two bullets or delete the
  weaker half.
- **Summary masquerading as wisdom:** The output restates what happened
  in the content rather than extracting durable knowledge. Fix: ask
  "would this idea be useful to someone who has never read the source?"
- **Empty quotes:** Quotes chosen because they sound important but say
  nothing specific. Fix: prefer the surprising over the noble.
- **Phase 3 duplicates Phase 2:** Abstract insights just reword the ideas
  without elevating them. Fix: Phase 3 should name patterns the original
  author never explicitly stated.
