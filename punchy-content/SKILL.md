---
name: punchy-content
description: >
  Craft punchy, engaging short-form content in a first-person, opinionated
  voice, in English or Swedish. Use this skill whenever the user wants social
  or audience-facing content: LinkedIn posts, X/Twitter posts or threads,
  newsletter issues, post hooks, captions, or short promotional copy. Trigger
  it for phrases like "write a LinkedIn post", "make this into a post", "skriv
  ett LinkedIn-inlägg", "turn this into a thread", "newsletter about...", or
  when repurposing a report/article into social content. For reports, emails
  and other long-form prose, use the general-writing skill instead.
---

# Punchy content

Write posts a real person with real opinions would publish. The enemy is twofold: sounding like AI, and sounding like every other creator chasing engagement. Both lose the reader.

## When to activate

- User wants a LinkedIn post, X post, thread, newsletter issue, caption, or hook
- User says: "write a LinkedIn post", "make this into a post", "skriv ett LinkedIn-inlägg", "turn this into a thread", "newsletter about..."
- User wants to repurpose a report, article, or idea into social content
- For long-form prose (reports, emails, memos), use general-writing instead

## Language

Write natively in English or Swedish depending on the request and the audience. For Swedish, keep the same directness; Swedish LinkedIn tolerates less hype than American LinkedIn, so dial the intensity down a notch further. Read `references/banned-patterns.md` before finalizing any post; it includes Swedish tells.

## The voice

- First person, opinionated. "I shipped this and it broke" beats any thought-leadership abstraction.
- Take a stance. A post without a stance is a press release.
- Specifics carry everything: numbers, names, dates, what actually happened. "We cut onboarding from 14 days to 3" beats "we dramatically improved onboarding."
- Admit uncertainty and mess where true. "I'm honestly not sure this scales" reads human.
- Contractions, spoken rhythm, sentences starting with And/But/So.
- Humor from unexpected precision, never from forced jokes.

## Core mechanics

**The hook is 80% of the post.** The first line decides whether anyone reads line two.
- Short, strong, declarative. A claim, a number, a tension, or a confession.
- Concrete beats clever: "I deleted half our codebase last week" > "Sometimes less is more."
- Never open with meta ("I want to share some thoughts on...") or scene-setting ("In today's fast-paced world...").

**The 1/3/1 cadence.** One punchy opening line. A 2–3 sentence paragraph carrying the substance. One punchy closer. Use it as a default shape for openings, not a straitjacket for the whole post.

**Rate of revelation.** Every line must give the reader something new. The moment a line restates the previous one, cut it. Short-form lives or dies on information density per second of reading.

**The Tequila Test.** Before writing, list what everyone says about this topic. Use none of it. If your post could have been written by anyone in the niche, it says nothing.

**One idea per post.** Two ideas = two posts. Depth on one point beats coverage of five.

**Ending.** End on the strongest concrete point or a genuine question you actually want answered. No "Agree?", no "Thoughts?", no recap of the post, no generic "exciting times ahead."

## Rhythm and formatting

- One to two sentences per paragraph. White space is pacing.
- Vary line length aggressively. Short. Then longer. A fragment. Then a sentence that earns its length.
- No em dashes. Periods, commas, colons, parentheses.
- Bold almost never (LinkedIn doesn't render it natively anyway; unicode-bold is a spam signal).
- Emojis: none, or one where it does actual work. Never as bullet decoration.
- Numbers as digits: 3 tools, 14 days, 500 users.

## What kills a post (beyond banned-patterns.md)

Read `references/banned-patterns.md` first — it covers negative parallelisms, dead vocabulary, structural tells, and formatting tells that apply to all prose including posts. The items below are short-form specific:

- **Engagement bait:** "Let that sink in", "Read that again", "This changes everything", "You're not ready for this", "Agree?" Banned outright.
- **Fake vulnerability:** the humblebragging "I failed" story that's really a victory lap with a sad first line. If you write a failure, the failure has to actually cost something and the lesson has to be specific.
- **Guru abstractions:** "consistency compounds", "your network is your net worth". Anything that fits on a mug.
- **Broetry inflation:** 40 one-line paragraphs saying nothing. White space is pacing, not content.
- **Hashtag spam.** 0–3 hashtags on LinkedIn, at the very end, only if genuinely useful for reach in a niche. None mid-text.

## Process

1. **Find the one idea.** Write it as a single sentence. If you can't, you don't have a post yet.
2. **Tequila Test the angle.** What would everyone else say? Cross it out.
3. **Draft 3 hooks**, evaluate them against the fold and the Tequila Test, keep the strongest, then write the body.
4. **Cut 30%.** Every post survives losing a third. Cut abstract lines first; keep the specifics.
5. **Scan against `references/banned-patterns.md`.** One violation = rewrite the line, not patch it.
6. **Evaluate as a scroller.** Line by line: does line 1 stop the scroll? Does each following line add new information and pull to the next? Any line that fails gets fixed or cut.

## Platform specifics

Read `references/platforms.md` for format rules per platform (LinkedIn, X/Twitter, threads, newsletters): lengths, fold lines, structure, and what each algorithm punishes. Read it whenever the target platform is known.

## Worked examples

**Hook rewrite — LinkedIn:**

> User: "Write a post about why we switched from microservices to a monolith."
>
> Bad (AI-tell + engagement bait): "Most people don't realize that microservices aren't always the answer. Here's the part nobody talks about... 🧵"
>
> Good: "We just deleted 47 microservices and moved everything into one repo. On purpose."

**Full post — X/Twitter single:**

> User: "Post about finding a critical bug in production."
>
> Bad (guru abstraction + fake vulnerability): "Failure isn't the opposite of success. It's part of the journey. Last week, I learned this lesson the hard way when a bug taught me the importance of robust testing..."
>
> Good: "Pushed a config change at 4pm Friday. Took down payments for 6 hours. Root cause: a missing comma in a JSON file. The lesson isn't 'test more' — it's 'don't deploy at 4pm Friday.'"

**Thread opener:**

> User: "Thread about pricing psychology."
>
> Bad (table of contents hook): "A thread on pricing psychology 🧵"
>
> Good: "We raised prices 40% last quarter. Churn went down. Here's what actually happened."

**Swedish LinkedIn — repurposed report:**

> User: "Gör ett LinkedIn-inlägg av säkerhetsrevisionen."
>
> Bad (Swedish AI-tell + Jantelagen violation): "Otroligt stolt över att få dela resultaten från vår senaste säkerhetsrevision. Det är inte bara en checklista — det är ett strategiskt steg mot en mer robust säkerhetslösning..."
>
> Good: "Säkerhetsrevisionen hittade 214 aktiva konton som tillhör personer som slutat för mer än ett år sedan. Tre av dem hade fortfarande adminrättigheter. Vi stängde av dem samma dag."

## Failure modes

- **Weak hook above the fold.** The LinkedIn preview shows a generic opener and the reader never clicks "see more". Fix: the first line must be a claim, number, tension, or confession that only makes sense if you read on.
- **Skipped Tequila Test.** The post says what everyone else says about the topic. Fix: literally list the conventional takes, then write none of them.
- **Broetry by default.** The agent turns every post into 40 one-line paragraphs because "white space is pacing". Fix: white space serves information density, not replaces it. One to two sentences per paragraph, not one sentence per paragraph.
- **Wrong platform shape.** A thread written as a LinkedIn post (long paragraphs, no open loops) or a LinkedIn post written as a thread (choppy, no substance paragraphs). Fix: read `references/platforms.md` before drafting when the platform is known.
- **Skipped banned-patterns scan.** The draft contains dead vocabulary, negative parallelisms, or engagement bait. Fix: step 5 of the process is mandatory, not optional. One violation = rewrite the line.
- **Generic closer.** The post ends with "Thoughts?" or restates the opening. Fix: end on the strongest concrete point or a genuine question you actually want answered.

## The litmus test

Apply to the finished post:

> Would a sharp, busy person stop scrolling for this, and would they believe a human wrote it?

If either answer is no, revise before delivering.

## Reference files

| File | When to read it |
|------|----------------|
| `references/banned-patterns.md` | Always, before finalizing. AI tells and banned language, English and Swedish. |
| `references/platforms.md` | When the target platform is known. Format, length, and structure rules per platform. |
