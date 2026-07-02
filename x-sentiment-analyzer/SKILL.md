---
name: x-sentiment-analyzer
description: |
  Analyze the comment/reply section of an X/Twitter post to extract overall sentiment and summarize the main arguments for and against. Use when the user shares an X URL and asks "what do people think", "is this well received", "sentiment check", "are people agreeing", or wants to know if a post/article is considered good or bad by its audience. The skill fetches the post and top replies, classifies sentiment, counts positive/negative/neutral, surfaces the strongest pro and con arguments, and delivers a verdict.
triggers:
  - "sentiment check"
  - "what do people think"
  - "is this well received"
  - "x sentiment"
  - "analyze replies"
mutating: false
---

# X Sentiment Analyzer

Read the reply section of an X/Twitter post and extract: overall sentiment (positive/negative/mixed), a verdict on whether the post is well-received, and a summary of the strongest arguments on each side.

## Contract

- The user provides an X/Twitter URL.
- The skill fetches the post content and its replies using available tools.
- Sentiment is classified per reply: Positive / Negative / Neutral / Mixed.
- A count and percentage breakdown is provided.
- The skill surfaces 3-5 strongest pro arguments and 3-5 strongest con arguments, each with representative quotes.
- A verdict states whether the post is generally well-received, poorly received, or polarizing.
- If replies are sparse or unavailable, the skill reports that honestly and analyzes what is available.

## Phases

### Phase 1: Capture the URL

Ask the user for the X URL if not already provided. Accept both x.com and twitter.com links.

### Phase 2: Fetch Post and Replies

Use the best available tool to retrieve:
- The original post text and engagement stats (likes, reposts, replies, bookmarks)
- Top-level replies (aim for 50-100 if available)
- Quote posts if accessible (these often carry stronger sentiment)

**Tool priority:**

**1. `xurl` CLI (primary, highest fidelity)**
- Extract the tweet ID from the URL. Example: `https://x.com/jayagup10/status/2052870394093408558` → ID is `2052870394093408558`.
- Fetch replies: `xurl search "conversation_id:<ID>" -n 100`
  - Returns up to 100 replies per call. Paginate with `next_token` if present in the response.
  - Filter out replies from the original author if they are just acknowledgements ("thanks", "agreed", etc).
- Fetch quote tweets: `xurl search "url:<tweet_url>" -n 100` or `xurl search "quoted_tweet_id:<ID>" -n 100`
  - Quote tweets often carry stronger sentiment than plain replies.
- Fetch the original post: `xurl read <ID>`
- Combine all unique tweets into the analysis set.

**2. Browser automation (fallback when xurl unavailable or rate-limited)**
- Navigate to the post URL with `browser_navigate`.
- Scroll down with `browser_scroll` repeatedly (3-8 times) to load more replies via X's lazy loader.
- Use `browser_snapshot(full=true)` or JavaScript evaluation to extract reply text and author handles.
- Limit: slower, but can capture replies that the API misses due to visibility settings.

**3. `web_extract` / `web_extract_plus` (last resort)**
- Use only if both xurl and browser are unavailable.
- Note explicitly that the sample is limited to top-level visible replies.

**4. `web_search` (augmentation)**
- Search for the post URL or key phrases to find discussions on Hacker News, Reddit, LinkedIn, or quote-tweet threads.
- Include only if the discussion adds meaningful sentiment not captured by X-native replies.

If tool access is limited, surface what you can reach and note the gap.

### Phase 3: Sentiment Classification

For each reply, classify:
- **Positive:** Agrees with, praises, supports, or expands positively on the post
- **Negative:** Disagrees with, criticizes, mocks, or attacks the post
- **Neutral:** Asks a question, shares information, or is tangential with no clear stance
- **Mixed:** Both praises and criticizes, or is sarcastic/ambiguous

Count each bucket. Calculate percentages. Note if one side dominates or if it is split.

### Phase 4: Extract Arguments

**Pro side (supporting the post):**
- Identify 3-5 distinct arguments or themes from positive replies
- For each: summarize the argument in one sentence, include a representative quote

**Con side (against the post):**
- Identify 3-5 distinct arguments or themes from negative replies
- For each: summarize the argument in one sentence, include a representative quote

If one side is dominant, still surface the best 1-2 arguments from the minority so the user sees what the opposition is saying.

### Phase 5: Verdict

State clearly:
- **Well-received** if positive significantly outweighs negative (e.g. 70%+ positive)
- **Poorly received** if negative significantly outweighs positive (e.g. 70%+ negative)
- **Polarizing** if roughly split or if strong emotions exist on both sides
- **Quiet/Low engagement** if reply volume is too low to judge

Add one sentence on *why* the sentiment is what it is: what about the post triggers this reaction?

## Output Format

```
## X Sentiment Analysis

**Post:** [Title or first 100 chars of post]
**Author:** @handle
**Engagement:** X likes / Y reposts / Z replies / W bookmarks
**Replies analyzed:** N

---

### Sentiment Breakdown
- 👍 Positive: N (X%)
- 👎 Negative: N (X%)
- ⚪ Neutral: N (X%)
- 💭 Mixed: N (X%)

**Verdict:** [Well-received / Poorly received / Polarizing / Quiet]
**Why:** [1 sentence on the trigger]

---

### Pro Arguments (People agreeing)
1. **[Theme]** — [1-sentence summary]
   > "[representative quote]"
2. ...

---

### Con Arguments (People disagreeing)
1. **[Theme]** — [1-sentence summary]
   > "[representative quote]"
2. ...

---

### Notable Replies
- [Any reply that is especially funny, viral, or insightful]

---

### Confidence
[High / Medium / Low] — [reason: sample size, data quality, access limitations]
```

## Anti-Patterns

- Judging sentiment by likes/reposts alone. Replies are the signal; likes are noise.
- Skipping the minority side. Even a 90/10 split deserves one strong counter-argument.
- Counting bot/spam replies as genuine sentiment. Flag suspicious patterns.
- Presenting sarcastic replies at face value. Sarcasm reads as mixed or negative, not positive.
- Declaring a verdict with fewer than 10 replies. Report "Quiet/Low engagement" instead.
- Rewriting replies in the user's voice. Quote replies verbatim to preserve tone.
