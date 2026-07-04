# Agent Skills

A collection of agent skills for reasoning, writing, analysis, and visual explanation.

## Skills

### cia-red-team
Run a 4-phase hostile stress-test on any idea, plan, or decision. Based on the CIA's declassified Tradecraft Primer (2009) and Red Cell methodology. Designed to find the holes before you commit.

### clarify-project-intent
Run a guided intent-clarification session before, during, or after a project or coding task. Walks the user through discovering their unknowns using the known/unknown matrix so agent and user align on intent before expensive work begins. Produces an Intent Brief with a paste-ready implementation prompt. From Matt Pocock's skill library.

### ogilvy-writing-coach
Audit any piece of writing against David Ogilvy's 10 rules from his 1982 internal memo. Not a rewrite tool. It diagnoses what's broken, what's working, and gives specific fixes so you learn the rules by doing the rewriting yourself.

### x-sentiment-analyzer
Read the reply section of an X/Twitter post and extract overall sentiment. Classifies replies as positive, negative, neutral, or mixed. Surfaces the strongest arguments on each side and delivers a verdict: well-received, poorly received, or polarizing.

### visual-explainer
Generate self-contained HTML visual explanations for systems, concepts, code changes, plans, data, and architectures. Output is a single HTML file with embedded CSS and optionally embedded Mermaid diagrams. No build step. No dependencies.

### here-now
Publish static sites to live URLs and store private files in cloud Drives. Drop HTML, images, PDFs, videos, or documents and get back a shareable link. Or use Drive storage for agent memory, context, plans, and assets that persist across sessions.

### handoff
Compact the current conversation into a handoff document for another agent to pick up. Summarises context, references existing artifacts instead of duplicating them, redacts sensitive info, and suggests skills the next agent should invoke. From Matt Pocock's skill library.

### premortem
Assume your plan already failed 6 months from now and work backward to find every reason why. Based on Gary Klein's method (Harvard Business Review) and Daniel Kahneman's most valued decision-making technique. Produces a revised plan with blind spots exposed.

### superforecaster
Produce calibrated probability forecasts using Tetlock-style superforecasting methodology. Question triage, reference-class base rates, evidence-weighted updating, adversarial stress-testing, and granular probability commitment. Turns vague "will X happen" questions into auditable, scoreable predictions.

### teach
Structured learning and teaching skill. Defines glossary, mission, learning record, and resources formats for teaching the user new skills within the workspace. From Matt Pocock's skill library.

### wayfinder
Plan a huge chunk of work as a shared map of investigation tickets on your issue tracker, and resolve them one at a time until the way to the goal is clear. Built for work that doesn't fit in one session. From Matt Pocock's skill library.

### writing-great-skills
A meta-skill for writing great agent skills. Covers prompt engineering, trigger design, context gathering, anti-patterns, and output formatting. Draws from Matt Pocock's skill design patterns and Daniel Miessler's PAI skill creation framework, adapted to a harness-agnostic vocabulary of determinism, progressive disclosure, and leading words.

### humanizer/voice-dna
Source of truth for writing voice. Rules for pacing, rhythm, banned vocabulary, AI pattern avoidance, and anti-overfitting guidance. Apply with judgment. Spirit over letter.

## Installation

Copy any skill folder to your agent's skills directory.

```bash
cp -r skill-name /path/to/your/skills/
```

Or for categorized installs:

```bash
cp -r skill-name /path/to/your/skills/<category>/
```

## License

MIT
