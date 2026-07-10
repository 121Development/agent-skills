---
name: extract-wisdom
description: >
  Extract structured, high-density wisdom from any content: articles, transcripts,
  podcasts, papers, books, lectures. Use when the user says "extract wisdom from this",
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
  and asks for insights, quotes, habits, facts, or a structured summary
- User references Daniel Miessler's Fabric pattern or "extract wisdom" workflow
- Another skill needs a content-decomposition step

## Input

The user provides content in one of these forms:

1. Raw text pasted directly into chat
2. A URL to an article, transcript, or document
3. A file path to a document on disk

If a URL or file path is given, read it first. Do not extract from a URL
without fetching the content.

**If fetching fails:** Browser, web_extract, API calls, and file reads can all
fail on paywalled or restricted content. Try these in order:
1. `web_extract_plus` with `render_js=true` and provider `firecrawl`
2. `browser_navigate` followed by `browser_console` to extract innerText
3. `web_search` for quoted phrases or threadreader copies
4. Ask the user to paste the text directly

If the full source text remains unreachable after these attempts, state the
blocker clearly and stop. Do not fabricate extraction output from search
snippets or metadata.

## Extraction workflow

Run these phases in order. Each phase ends on a completion criterion.

### Phase 1: Capture metadata

Record the source:
- Title (if known) or a 6-word descriptive label
- Author or speaker
- Medium (article, podcast transcript, book chapter, lecture, etc.)
- Date (if known)

**Done when:** All four metadata fields are filled. Use "unknown" for missing fields.

### Phase 2: Extract high-impact ideas

Pull 20-50 ideas from the content. An idea is a discrete claim, observation,
technique, or piece of knowledge that stands on its own.

Rules:
- One idea per bullet
- Maximum 16 words per bullet
- Preserve the author's framing where it matters
- Include page markers or timestamps if the source has them
- Skip filler, repetition, and throat-clearing

**Done when:** You have 20-50 bullets and every bullet is 16 words or fewer.

### Phase 3: Extract abstract insights

Distill 10-20 broader insights from the ideas. These are patterns, principles,
or mental models that transcend the specific content.

Rules:
- One insight per bullet
- Maximum 16 words per bullet
- Frame as transferable knowledge, not content summary
- Connect to domains outside the source where natural

**Done when:** You have 10-20 bullets, each 16 words or fewer, and none merely
reword a Phase 2 idea.

### Phase 4: Extract verbatim quotes

Capture 3-10 quotes that are especially sharp, surprising, or precisely worded.

Rules:
- Quote exactly. Do not paraphrase inside quotation marks
- Keep each quote to 2 sentences max
- Attribute to speaker/author
- Include a 1-sentence note on why this quote matters

**Done when:** You have 3-10 attributed quotes with why-it-matters notes.
If uncertain about verbatim accuracy, downgrade to a Phase 2 paraphrase.

### Phase 5: Extract practical habits and facts

- **Habits:** Actions, routines, or behaviors recommended or demonstrated
  in the content. 5-15 items. 16 words max each.
- **Facts:** Concrete, checkable world-knowledge stated in the content.
  5-15 items. 16 words max each.

**Done when:** Both lists have 5-15 items, all under 16 words.

### Phase 6: Extract references and tools

- **References:** Books, papers, people, or concepts cited by the source.
  3-10 items.
- **Recommended tools:** Software, frameworks, or methods mentioned.
  3-10 items.

**Done when:** Both lists have 3-10 items.

### Phase 7: One-sentence takeaway

Synthesize the entire content into a single sentence of exactly 15 words.
This is the compressed essence. Every word must earn its place.

**Done when:** The sentence is exactly 15 words. Count twice.

## Output format

Follow the schema in `references/output-format.md`. Use the exact section
headings and ordering listed there.

## Quality checks

Before delivering, run this checklist. Do not skip it.

- [ ] Every Phase 2 bullet is 16 words or fewer.
- [ ] Every Phase 3 bullet is 16 words or fewer.
- [ ] Every Phase 5 bullet is 16 words or fewer.
- [ ] Every quote is verbatim or has been downgraded to Phase 2.
- [ ] The takeaway is exactly 15 words. Not 14. Not 16.
- [ ] No concept appears in both Phase 2 and Phase 3 unless Phase 3 genuinely abstracts it.
- [ ] No meta-commentary ("the author argues", "this section discusses") in bullets.
- [ ] The word count audit table at the bottom of the output shows zero violations.

If any box is unchecked, fix the violation before delivering.

## Worked example

**Input:** A 2,000-word article on deep work by Cal Newport.

**Phase 1:**
- Title: Deep Work Rules for Focus
- Author: Cal Newport
- Medium: article
- Date: 2016-01-05

**Phase 2 (4 of 32 ideas):**
- Deep work is cognitively demanding activity done without distraction.
- The ability to perform deep work is becoming rare and therefore valuable.
- Schedule every minute of your day in blocks to protect focus time.
- Quit social media for 30 days, then evaluate which tools you actually miss.

**Phase 3 (2 of 14 insights):**
- Scarcity of attention drives value of focused work in knowledge economy.
- Willpower is unreliable; systems and scheduling protect intent better.

**Phase 4 (1 of 6 quotes):**
- "Clarity about what matters provides clarity about what does not."
  — Cal Newport, on saying no
  *Why it matters: The criterion for elimination is the criterion for focus.*

**Phase 7:**
- In a world of shallow distraction, deep focus creates work that truly outlasts the noise.
  (15 words)

## Failure modes

| Smell | Diagnosis | Fix |
|-------|-----------|-----|
| Bullets creep past 16 words | The extractor tries to preserve nuance in one bullet | Split into two bullets or delete the weaker half |
| Output restates what happened in the content | Summary masquerading as wisdom | Ask: "Would this idea be useful to someone who has never read the source?" |
| Quotes sound important but say nothing specific | Empty quotes | Prefer the surprising over the noble |
| Phase 3 rewords Phase 2 without elevating | Insights lack abstraction | Phase 3 should name patterns the original author never explicitly stated |
| Full source remains unreachable after all fetch attempts | Source inaccessible | State the blocker clearly, list attempted tools, ask user to paste text directly |
