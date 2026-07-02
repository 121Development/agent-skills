# Agent Skills

Custom Hermes Agent skills curated by 121Development.

## Skills

### cia-red-team
Run a 4-phase hostile stress-test on any idea, plan, or decision using techniques from the CIA's declassified Tradecraft Primer (2009). Use when you want to kill a weak idea before investing months into it.

**Triggers:** `cia red team`, `red team my idea`, `stress test this plan`, `kill my idea`, `hostile review`

### ogilvy-writing-coach
Audit any piece of writing against David Ogilvy's 10 rules from his 1982 internal memo. Diagnoses what's broken, what's working, and gives specific fixes so you learn the rules by doing the rewriting yourself.

**Triggers:** `ogilvy check`, `audit this`, `writing audit`, `review my copy`, `ogilvy writing`

### x-sentiment-analyzer
Analyze the comment/reply section of an X/Twitter post to extract overall sentiment and summarize the main arguments for and against. Tells you if a post is well-received, poorly received, or polarizing.

**Triggers:** `sentiment check`, `what do people think`, `is this well received`, `x sentiment`, `analyze replies`

### visual-explainer
Generate self-contained HTML visual explanations for systems, concepts, and architectures. Installed from [nicobailon/visual-explainer](https://github.com/nicobailon/visual-explainer).

### here-now
Publish static sites to live URLs at {slug}.here.now and store private files in cloud Drives. Use for "publish this", "host this", "deploy this", "share this on the web", "make a website", "put this online", or "save this to my Drive".

### premortem
Run a premortem on any plan, launch, product, hire, strategy, or decision. Assumes it already failed 6 months from now and works backward to find every reason why. Produces a revised plan with blind spots exposed.

**Triggers:** `premortem this`, `premortem my`, `run a premortem`, `what could kill this`, `future-proof this`, `stress test this plan`, `what am i missing here`, `find the blind spots`

### teach (from mattpocock/skills)
Structured learning and teaching skill. Defines glossary, mission, learning record, and resources formats for teaching the user new skills within the workspace.

### wayfinder (from mattpocock/skills)
Navigational decision-making for large investigations. Plan a huge chunk of work as a shared map of investigation tickets on your issue tracker, and resolve them one at a time until the way to the goal is clear.

### writing-great-skills (from mattpocock/skills)
A meta-skill for writing great agent skills. Covers prompt engineering, trigger design, context gathering, anti-patterns, and output formatting for maximum agent usefulness.

### humanizer/voice-dna
Source of truth for writing voice. Rules for pacing, rhythm, banned vocabulary, AI pattern avoidance, and anti-overfitting guidance. Apply with judgment. Spirit over letter.

## Installation

Copy any skill folder to your Hermes skills directory:

```bash
cp -r skill-name ~/.hermes/skills/
```

Or for categorized skills:

```bash
cp -r skill-name ~/.hermes/skills/<category>/
```

## Sources

- **Created:** cia-red-team, ogilvy-writing-coach, x-sentiment-analyzer
- **Forked:** visual-explainer ([nicobailon/visual-explainer](https://github.com/nicobailon/visual-explainer))
- **From mattpocock/skills:** teach, wayfinder
- **From Google Doc:** premortem
- **From message.txt:** humanizer/voice-dna

## License

MIT
