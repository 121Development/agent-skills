---
name: humanizer
description: >
  Source of truth for writing voice. Rules for pacing, rhythm, banned
  vocabulary, AI pattern avoidance, and anti-overfitting guidance. Apply with
  judgment. Spirit over letter.
disable-model-invocation: true
---

# Humanizer

Write like a sharp human who happens to be typing. Not like a language model averaging the internet.

This skill defines the voice, the banned vocabulary, and the patterns to kill. Apply with judgment. Spirit over letter.

## When to activate

- User asks to humanize, rewrite, or voice-check any text
- User says: "make this sound less like AI", "humanize this", "check the voice"
- Before finalizing any published writing (posts, emails, reports, documentation)
- As a reference while writing with general-writing or punchy-content

## Writing rules

**Pacing and rhythm:**

- Short paragraphs. 1–2 sentences default. 3 max.
- Get to the point. No warm-up laps.
- Vary sentence length hard. Short punchy lines mixed with longer ones. AI writes like a metronome; break that rhythm.
- Start sentences with And, But, Like, So. Write as you speak.
- If you've made your point, stop. Don't summarize what someone just read.

**Voice and tone:**

- Use contractions naturally (don't, can't, won't, it's).
- Use "I" and "you." Direct address. Active voice.
- Be specific. Numbers, names, concrete details. Specific writing is sharp writing.
- When uncertain, say so plainly ("I think," "probably," "maybe," "kinda").
- Never pad output to seem thorough. Shorter and accurate beats longer and fluffy.
- Take a stance. Commit. Avoid "may," "could," "often considered."
- Give real examples. Point to something that actually happened.
- Use physical verbs for abstract processes: "sanded down," "bolted on," "stripped back."
- Humor comes from specificity. Be unexpectedly precise.
- Parenthetical asides are good (for editorial commentary, honest reactions).
- Natural transitions only. No mechanical connectors.

## Formatting rules

- Short paragraphs (1–2 sentences default, 3 max).
- Numbers as digits: 3 years, 10 tools, 500 users.
- Contractions always.
- No em dashes. Use commas, periods, colons, semicolons, or parentheses.
- Bold sparingly: 1–2 key moments per section.
- Code blocks for specific prompts, commands, or tool outputs.
- Use formatting like salt. Headers, bullets, numbered lists: only when they earn it.
- If you've made your point, stop. Don't add a summary paragraph restating everything.

## Banned vocabulary

If even one of these appears, the output fails. Rewrite the sentence, don't patch it.

**Dead AI vocabulary (English):**

delve, realm, harness, unlock, tapestry, paradigm, cutting-edge, revolutionize, landscape (abstract), intricate/intricacies, showcasing, crucial, pivotal, surpass, meticulously, vibrant, unparalleled, underscore (verb), leverage, synergy, innovative, game-changer, testament, commendable, meticulous, highlight (verb), emphasize, boast, groundbreaking, align, foster, showcase, enhance, holistic, garner, accentuate, pioneering, trailblazing, unleash, versatile, transformative, redefine, seamless, optimize, scalable, robust, breakthrough, empower, streamline, frictionless, elevate, adaptive, effortless, data-driven, insightful, proactive, mission-critical, visionary, disruptive, reimagine, unprecedented, intuitive, leading-edge, synergize, democratize, accelerate, state-of-the-art, dynamic, immersive, predictive, transparent, proprietary, integrated, plug-and-play, turnkey, future-proof, paradigm-shifting, supercharge, enduring, interplay, valuable, captivate.

Also banned: "serves as," "stands as," "marks a," "represents a," "boasts a," "features a," "offers a" when used to avoid "is" or "has." Just say "is."

**Dead phrases:**

- "In today's [anything]..."
- "It's important to note that..." / "It's worth noting..."
- "In order to" (just say "to")
- "I'd be happy to help"
- "Straightforward"
- "Let's dive in" / "Let's explore" / "Let's unpack" / "Delve into"
- "At the end of the day"
- "Moving forward"
- "To put this in perspective..."
- "What makes this particularly interesting is..."
- "The implications here are..."
- "In other words..."
- "It goes without saying..."
- "Here's the part nobody's talking about" / "What nobody tells you"
- Anything with "nobody" or "most people don't realize"
- "In this article, I will..." (all meta commentary about what you're about to do)
- "Despite its [positive words], [subject] faces challenges..."
- "Challenges and Future Prospects" as a section header

**Dead transitions:**

- "Furthermore" / "Additionally" / "Moreover"
- "That said" / "That being said"
- "With that in mind"
- "It is also worth mentioning"
- "On top of that"
- Any mechanical connector that reads like a college essay

**Engagement bait:**

- "Let that sink in" / "Read that again" / "Full stop"
- "This changes everything"
- "Are you paying attention?" / "You're not ready for this"

**Hype language:**

- "Supercharge" / "Unlock" / "Future-proof"
- "10x your [anything]"
- "Game-changer" / "Cutting-edge"
- Any promise of superpowers, easy riches, or overnight transformation

## The fatal pattern: negative parallelisms

The single most reliable tell of AI-generated text. Any sentence that negates one framing and then asserts a corrected one:

- "This isn't X. This is Y."
- "Not X. Y."
- "Forget X. This is Y."
- "Less X, more Y."
- "Not only X, but also Y."
- "It's not just about X, it's about Y."
- "No X, no Y, just Z."
- "X? No. Y."
- "Stop thinking X. Start thinking Y."
- "It's not about X. It's about Y."
- "X is dead. Y is the future."
- "The question isn't X. The question is Y."
- "You don't need X. You need Y."
- "X is overrated. Y is what matters."
- ANY sentence that negates one framing then asserts a corrected one.

**Sneaky versions, equally banned:**

- "While X might seem right, Y is actually..."
- "Sure, X works. But Y is where the real..."
- "X gets all the attention, but Y is what actually..."

**The fix:** delete everything before the positive claim. "It's not about the prompt, it's about the context" → "It's about the context." The negation adds zero information.

## Structural tells to avoid

**Puffery and significance inflation.** AI inflates the importance of everything. "A pivotal moment in the evolution of..." "Setting the stage for..." State the fact. Let the reader judge significance.

**Rule of three.** AI loves listing 3 things: "speed, efficiency, and innovation." Use 2. Or 4. Or just say the one thing that matters.

**False ranges.** "From ancient traditions to modern innovations." Sounds impressive, means nothing. If there's no meaningful middle ground, the range is fake. Delete it.

**Elegant variation.** AI swaps terms to avoid repetition: "the protagonist," then "the key player," then "the eponymous figure." Just use the name again. Forced synonyms are worse than repetition.

**Meta commentary.** "In this section, we will discuss..." "Let me walk you through..." Say the thing. Don't announce that you're about to say the thing.

**Superficial analysis via participle phrases.** "...highlighting its importance," "...underscoring its significance," "...reflecting broader trends." Delete the participle phrase. If the analysis matters, give it its own sentence with a specific claim.

**Knowledge-cutoff disclaimers.** "As of my last update..." "While specific details are limited..." Never include these.

**Collaborative communication leakage.** "I hope this helps!" "Would you like me to..." "Certainly!" "Great question!" These belong in chat. Strip them from published writing.

**Metronome rhythm.** Every sentence same length. Every paragraph same number of sentences. Real writing breathes unevenly. Short. Then longer. Then a fragment. Then a 30-word sentence that earns its length.

**Copulative avoidance.** AI replaces "is" and "has" with bloated alternatives: "serves as," "stands as," "represents," "marks a." Just say "is."

**Title case in headers.** Use sentence case.

## Anti-overfitting guide

This document captures taste. It is a guide. Apply it with judgment.

**Frequency guidance:**

- **HARD RULE:** Never violate. Banned words, structures, phrases. Absolute.
- **STRONG TENDENCY (70–80%):** Short sentences, direct address, active voice, specific details, varied rhythm.
- **LIGHT PREFERENCE (context decides):** Specific word choices, particular structures, humor placement.

**Natural variation matters:**

- Don't use the same opening formula every time just because it works.
- Don't avoid a word forever just because it's on a banned list (sometimes it's genuinely the right word).
- Let the content dictate structure.

## The litmus test

> Does this sound like something I would actually write, or does it sound like an AI trying very hard to imitate me?

If it feels forced, pull back. Inhabit the voice.

## Failure modes

- **Rule-following becomes the voice.** The agent applies every rule mechanically, producing prose that sounds like it's checking boxes rather than communicating. Fix: the litmus test overrides every rule. If a rule produces a forced sentence, break the rule.
- **Banned-word false positives.** A word on the banned list is genuinely the right word in context (e.g., "landscape" in a photography essay). Fix: the banned list applies to abstract filler usage, not literal denotation. Use judgment.
- **Overcorrection to fragments.** The agent breaks every sentence into one-word fragments to "vary rhythm." Fix: variation means real variation, not uniform shortness. Some sentences should be long and complex if they earn it.
- **Anti-AI voice becomes its own cliché.** The agent overuses parenthetical asides, sudden fragments, and "kinda" to signal humanity. Fix: these devices work because they're sparse. If every sentence has an aside, it's just a different kind of machine voice.
