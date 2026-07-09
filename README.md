# Agent Skills

Agent skills that pass review. Each one follows the [`writing-great-skills`](writing-great-skills/) standard: trigger sections, imperative instructions, checkable completion criteria, worked examples, and explicit failure modes.

## What this is

An agent skill is a deterministic process wrapped in markdown. It tells an AI agent how to do one thing well, the same way every time. These skills cover writing, reasoning, analysis, visual explanation, and workflow operations. Most are model-invoked (the agent can fire them autonomously); some are user-invoked (you type the name).

## Skills

### Writing and voice

| Skill | What it does |
|-------|-------------|
| [`general-writing`](general-writing/) | Long-form prose in English or Swedish. Two registers: first-person opinionated (emails, memos, essays) and professional objective (reports, documentation, client deliverables). |
| [`punchy-content`](punchy-content/) | Short-form social content: LinkedIn posts, X/Twitter posts and threads, newsletters, hooks. First-person opinionated with anti-AI-tell mechanics. |
| [`ogilvy-writing-coach`](ogilvy-writing-coach/) | Audit any text against David Ogilvy's 10 rules from his 1982 internal memo. Diagnoses what's broken and what's working; you do the rewriting. |
| [`humanizer`](humanizer/) | Source of truth for writing voice. Rules for pacing, rhythm, banned vocabulary, AI pattern avoidance, and anti-overfitting guidance. User-invoked; type the skill name to load it. |

### Reasoning and analysis

| Skill | What it does |
|-------|-------------|
| [`superforecaster`](superforecaster/) | Calibrated probability forecasts using Tetlock-style methodology. Question triage, base rates, evidence-weighted updating, adversarial stress-testing. |
| [`cia-red-team`](cia-red-team/) | 4-phase hostile stress-test on any idea, plan, or decision. Based on the CIA's declassified Tradecraft Primer and Red Cell methodology. |
| [`premortem`](premortem/) | Assume your plan already failed 6 months from now and work backward to find every reason why. Based on Gary Klein's method. |
| [`clarify-project-intent`](clarify-project-intent/) | Guided intent-clarification session before expensive work. Walks through the known/unknown matrix and produces an Intent Brief. |
| [`extract-wisdom`](extract-wisdom/) | Transform any content into a high-density knowledge asset. 7-phase extraction: ideas, insights, quotes, habits, facts, references, and a 15-word takeaway. |

### Visual explanation

| Skill | What it does |
|-------|-------------|
| [`visual-explainer`](visual-explainer/) | Self-contained HTML visual explanations for systems, concepts, code changes, plans, data, and architectures. Single file, no build step, no dependencies. |

### Operations and workflow

| Skill | What it does |
|-------|-------------|
| [`handoff`](handoff/) | Compact a conversation into a handoff document for another agent. Summarises context, references existing artifacts, redacts sensitive info. |
| [`wayfinder`](wayfinder/) | Plan a large chunk of work as a shared map of investigation tickets, resolve them one at a time until the path to the goal is clear. |
| [`here-now`](here-now/) | Publish static sites to live URLs and store private files in cloud Drives. Drop HTML, images, PDFs, videos, or documents and get back a shareable link. |
| [`teach`](teach/) | Structured learning and teaching within the workspace. Defines glossary, mission, learning record, and resources formats. |

### Social and monitoring

| Skill | What it does |
|-------|-------------|
| [`x-sentiment-analyzer`](x-sentiment-analyzer/) | Read the reply section of an X/Twitter post and extract sentiment. Classifies replies, surfaces strongest arguments on each side, delivers a verdict. |

### Meta

| Skill | What it does |
|-------|-------------|
| [`writing-great-skills`](writing-great-skills/) | How to write agent skills well. Covers invocation design, shape, instruction voice, information hierarchy, leading words, and failure modes. |
| [`crafting-effective-readmes`](crafting-effective-readmes/) | Write or improve README files matched to audience and project type. Templates, section checklists, and a three-step process. |

## Installation

Each skill is a self-contained folder. Copy any skill to your agent's skills directory.

```bash
cp -r skill-name ~/.hermes/skills/
```

Or for categorized installs:

```bash
cp -r skill-name ~/.hermes/skills/<category>/
```

## Structure

Every skill follows the same layout:

```
skill-name/
├── SKILL.md              # Required. Frontmatter + body with triggers, process, examples.
├── references/           # Optional. Deep docs the agent loads on demand.
│   └── topic.md
├── templates/            # Optional. Reusable artifacts.
│   └── template.md
└── scripts/              # Optional. Executable helpers.
    └── helper.py
```

Read [`writing-great-skills/SKILL.md`](writing-great-skills/SKILL.md) for the full standard.

## Contributing

1. Write the skill following the [`writing-great-skills`](writing-great-skills/) standard.
2. Include worked examples and explicit failure modes.
3. Test it on real data before submitting.
4. Open a PR with a description of what gap the skill fills.

## License

MIT
