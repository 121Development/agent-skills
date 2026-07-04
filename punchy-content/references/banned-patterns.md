# Banned patterns

If even one hard-banned item appears in the final text, the output fails. Rewrite the sentence, don't patch it.

Based on Wikipedia's "Signs of AI writing" field guide (WikiProject AI Cleanup) plus peer-reviewed detection research.

## 1. THE BIG ONE: negative parallelisms (fatal)

The single most reliable tell of AI text. Any sentence that negates one framing and then asserts a corrected one:

- "This isn't X. This is Y."
- "It's not just about X, it's about Y."
- "Not only X, but also Y."
- "Forget X. This is Y."
- "You don't need X. You need Y."
- "The question isn't X. The question is Y."
- "X is dead. Y is the future."
- "Less X, more Y." / "No X, no Y, just Z."
- "Stop thinking X. Start thinking Y."

Sneaky disguised versions, equally banned:
- "While X might seem right, Y is actually..."
- "Sure, X works. But Y is where the real..."
- "X gets all the attention, but Y is what actually..."

Swedish versions, equally banned:
- "Det handlar inte om X. Det handlar om Y."
- "Det är inte bara X, det är Y."
- "Glöm X. Det här är Y."
- "Frågan är inte X. Frågan är Y."

**The fix:** delete everything before the positive claim. "It's not about the prompt, it's about the context" → "It's about the context." The negation adds zero information.

## 2. Dead AI vocabulary (English)

Never use: delve, realm, harness, unlock, tapestry, paradigm, cutting-edge, revolutionize, landscape (abstract), intricate/intricacies, showcase/showcasing, crucial, pivotal, meticulously, vibrant, unparalleled, underscore (verb), leverage, synergy, game-changer, testament, commendable, highlight (verb), emphasize, boast, groundbreaking, foster, enhance, holistic, garner, seamless, robust, empower, streamline, elevate, effortless, transformative, redefine, unleash, trailblazing, pioneering, visionary, disruptive, unprecedented, state-of-the-art, supercharge, future-proof, enduring, interplay, captivate, journey (figurative), navigate (figurative), evolving, ever-changing.

"Serves as", "stands as", "marks a", "represents a", "boasts a", "features a", "offers a" as dodges for "is"/"has": banned. Just say is.

## 3. Dead AI vocabulary (Swedish)

Never use: spännande (as filler praise), unik (unless literally true), banbrytande, sömlös, robust (figurative), skräddarsydd, holistisk, dynamisk, innovativ (as filler), främja, belysa, understryka (figurative), möjliggöra, optimera, nyckelroll, avgörande roll, central roll, landskap (abstract: "det digitala landskapet"), resa (figurative: "vår digitala resa"), navigera (figurative), ta del av (when "läsa"/"se" works), i framkant, spjutspets, kraftfull (about software/ideas), ett kvitto på (as testament-dodge), vittnar om.

Copula dodges: "utgör", "fungerar som", "står som", "tjänar som" when "är" works. Skriv "är".

## 4. Dead phrases

English:
- "In today's [anything]..."
- "It's important to note that..." / "It's worth noting..."
- "In order to" (say "to")
- "Let's dive in / explore / unpack"
- "At the end of the day"
- "Moving forward"
- "In other words..."
- "What makes this particularly interesting is..."
- "Here's the thing" / "Here's the part nobody talks about"
- Anything with "nobody" or "most people don't realize"
- "In this article/report, I will..." (all meta-commentary about what you're about to do)
- "Despite its [positives], [subject] faces challenges..."
- "Challenges and Future Prospects" as a heading

Swedish:
- "I dagens samhälle / digitala värld..."
- "Det är viktigt att notera/poängtera att..."
- "Låt oss dyka ner i / utforska..."
- "I slutändan..."
- "Framåt / framgent..." as filler
- "Med det sagt..."
- "Värt att nämna är att..."
- "I den här rapporten kommer jag att..." (meta-commentary)

## 5. Dead transitions

Furthermore, Additionally, Moreover, "That said", "That being said", "With that in mind", "It is also worth mentioning", "On top of that". Swedish: Vidare, Dessutom (as mechanical paragraph opener), Därutöver, Sammanfattningsvis (as reflex ending). Use natural connections or none.

## 6. Structural tells

- **Rule of three.** "Speed, efficiency, and innovation." Three adjectives, three phrases, three bullets, every time. Use 2. Or 4. Or the one that matters.
- **False ranges.** "From ancient traditions to modern innovations." If there's no meaningful middle between X and Y, the range is fake. Delete it.
- **Superficial -ing analysis.** "...highlighting its importance", "...ensuring reliability", "...reflecting broader trends". Swedish equivalent: "...vilket understryker/belyser/speglar...". Delete the phrase. If the analysis matters, give it its own sentence with a specific claim.
- **Significance inflation.** "A pivotal moment in the evolution of...", "setting the stage for...", "en milstolpe i utvecklingen av...". State the fact; let the reader judge significance.
- **Elegant variation.** The protagonist → the main character → the central figure → the hero. Just repeat the name. Forced synonyms are worse than repetition.
- **Vague attribution.** "Experts argue", "industry reports suggest", "observers have noted", "många menar att". Name the source or cut the claim.
- **Metronome rhythm.** Every sentence medium, every paragraph 3–4 sentences. Real writing breathes unevenly.
- **Generic positive conclusions.** "The future looks bright...", "Exciting times ahead", "Framtiden ser ljus ut". End on the last concrete point instead.

## 7. Formatting tells

- Em dashes. Banned. Use commas, periods, colons, parentheses.
- Bold on every other phrase. Bold 1–2 moments per section, max.
- Bolded-header bullet lists ("**Performance:** Performance has been enhanced..."). Write prose or plain bullets.
- Title Case Headings. Use sentence case.
- Emoji decoration (🚀💡✅).
- Curly quotes. Use straight quotes.

## 8. Chat leakage

Never in published text: "I hope this helps", "Certainly!", "Of course!", "Great question", "Would you like me to...", "Let me know if...", "As of my last update...", "While specific details are limited...". Swedish: "Hoppas det hjälper!", "Självklart!", "Hör av dig om...".

## Self-check before delivering

1. Any negative parallelism, in any disguise? → rewrite the sentence from scratch.
2. Grep mentally for the vocabulary lists (sections 2–3).
3. Count em dashes. Should be zero.
4. Count triads. More than one rule-of-three per page is suspicious.
5. Read the opening and closing. If either could be pasted onto any other document about any other topic, it's generic. Rewrite.
