---
name: ste-writing
version: 1.0.0
description: |
  Rewrite prose (docs, READMEs, PR descriptions, error messages, release notes, comments — never code)
  into ASD-STE100 Simplified Technical English to remove "AI slop".
  Use when asked to make writing not sound like AI, make docs clear or plain,
  enforce a controlled writing style, or write technical documentation that reads human.
  Two modes — strict (procedures/safety) and STE-flavored (general prose).
triggers:
  - "make this not sound like AI"
  - "remove AI slop"
  - "simplify this text"
  - "STE rewrite"
  - "plain English"
  - "technical writing"
  - "README rewrite"
  - "PR description"
  - "error message rewrite"
  - "release notes"
  - "docs rewrite"
  - "controlled language"
tools:
  - write_file
mutating: false
---

# ste-writing

## Contract
- Rewrites any prose into ASD-STE100 Simplified Technical English on the first pass
- Returns only the requested text: no preamble, no summary, no closing remarks
- Applies the correct mode (strict or STE-flavored) based on the document type
- Strips marketing language, nominalizations, passive voice, and phrasal verbs
- Enforces one name per thing, one meaning per word, active voice, and short sentences

## Rules

WORDS
- Use one name for one thing. Do not call the same item by two different names.
- Use the short common word: start (not begin/commence/initiate), use (not utilize/leverage), help (not facilitate), make sure (not ensure), before (not prior to), after (not subsequent to), about (not regarding/concerning), get (not obtain/acquire), show (not demonstrate), also (not additionally/furthermore/moreover).
- Give each word one meaning. "fall" means to move down, not to decrease.
- No marketing adjectives: seamless, robust, powerful, cutting-edge, effortless, world-class, next-generation, revolutionary.
- American spelling.

VERBS
- Active voice. "the parser reads the file", not "the file is read by the parser".
- Use a verb for an action. "analyze the log", not "perform an analysis of the log".
- No stacked auxiliaries. Not "it is important to note that this may help to improve". Write "this improves X".
- No "-ing" main verb where a simple tense works.

SENTENCES
- One instruction per sentence. Max 20 words (instruction), max 25 (descriptive).
- No contractions. Use articles: a, an, the, this, these.

PUNCTUATION
- No semicolons. Write two sentences.
- No em dashes. Use a period or parentheses instead.

STRUCTURE
- One topic per paragraph, max six sentences. For steps, use a numbered vertical list, one action per item, imperative form. Put a condition before its command.

Write only the requested text. No preamble, no summary, no closing remarks.

## Modes

- **strict** — procedures, runbooks, safety text, error messages: apply every rule and both length caps.
- **STE-flavored** — general prose (READMEs, PR descriptions, docs): apply the sentence, paragraph, active-voice, and no-phrasal-verb discipline; relax the ~900-word dictionary lockdown so the text keeps enough range to read naturally.

## Self-lint (run before returning text)

1. Any sentence over 20 words? Split it.
2. Any semicolon? Replace with a period.
3. Any em dash? Replace with a period or parentheses.
4. Any contraction? Expand it.
5. Any passive voice with a known actor? Make it active.
6. Any "-ing" main verb, nominalization ("perform an analysis"), or phrasal verb ("spin up")? Replace with a plain verb.
7. Same thing named two ways? Pick one name.

## Output Format
Clean rewritten text only. No preamble, no framing, no markdown code fences around the output unless the user explicitly requests them. The text itself follows ASD-STE100 rules: short declarative sentences, active voice, no marketing language, one name per thing.

## Anti-Patterns
- Applying STE to code, identifiers, or command syntax. This skill is for prose only.
- Using STE for marketing copy, essays, or anything that needs a voice. STE strips voice on purpose.
- Trying to complete all five drafts in one sitting. Writing is iterative, not linear.
- Letting the user edit during the brain-dump phase. This kills momentum and produces thin drafts.
- Returning the text wrapped in explanations like "Here is the rewritten version:" Just return the text.
- Preserving em dashes because they "look nice." They are a slop marker. Remove them.

The mechanical rules above are lintable and are what removes slop. Full STE also needs human judgment (the right technical noun, whether a sentence "makes good sense") — a checker cannot certify that, and slop is not about that. This skill fixes the FORM of slop. It cannot make a hollow paragraph true.

Free official standard (do not paste it in full; it is copyrighted): https://asd-ste100.org
