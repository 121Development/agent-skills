---
name: crafting-effective-readmes
description: Use when writing, improving, reviewing, or adding to README files. Trigger when the user mentions README, documentation, project setup instructions, or asks for help making their repo presentable. Provides audience-matched templates and a three-step process.
---

# Crafting Effective READMEs

## When to activate

- User wants to write, improve, review, or add to a README
- User mentions README, documentation, "make this repo presentable", or project setup instructions
- User hands over a project with missing or stale README
- User asks for help documenting code, a tool, or a config folder

## Process

### Step 1 — Identify the task

Ask: "What README task are you working on?"

| Task | When |
|------|------|
| **Creating** | New project, no README yet |
| **Adding** | Need to document something new |
| **Updating** | Capabilities changed, content is stale |
| **Reviewing** | Checking if README is still accurate |

**Completion criterion:** User names a task, or you have enough context to select one yourself.

### Step 2 — Run task-specific questions

**Creating initial README:**
1. Identify the project type (see Project Types below)
2. Ask: what problem does this solve in one sentence?
3. Ask: what's the quickest path to "it works"?
4. Ask: anything notable to highlight?
5. Load the matching template from `templates/`

**Adding a section:**
1. Ask: what needs documenting?
2. Read the current README to find where it belongs
3. Ask: who needs this info most?
4. Draft the section and propose insertion point

**Updating existing content:**
1. Ask: what changed?
2. Read the current README, identify stale sections
3. Propose specific edits

**Reviewing/refreshing:**
1. Read the current README
2. Check against actual project state (package.json, main files, etc.)
3. Flag outdated sections
4. Update "Last reviewed" date if present

**Completion criterion:** For creating: template loaded and user confirmed type. For adding/updating/reviewing: specific edits identified and user confirmed.

### Step 3 — Draft and verify

Draft the README or edits. Then ask: **"Anything else to highlight or include that I might have missed?"**

Iterate on feedback until the user is satisfied.

**Completion criterion:** User confirms the README is complete or explicitly signs off.

## Project types

| Type | Audience | Key Sections | Template |
|------|----------|--------------|----------|
| **Open Source** | Contributors, users worldwide | Install, Usage, Contributing, License | `templates/oss.md` |
| **Personal** | Future you, portfolio viewers | What it does, Tech stack, Learnings | `templates/personal.md` |
| **Internal** | Teammates, new hires | Setup, Architecture, Runbooks | `templates/internal.md` |
| **Config** | Future you (confused) | What's here, Why, How to extend, Gotchas | `templates/xdg-config.md` |

Ask the user if unclear. Don't assume OSS defaults for everything.

## Essential sections (all types)

Every README needs at minimum:

1. **Name** — Self-explanatory title
2. **Description** — What + why in 1–2 sentences
3. **Usage** — How to use it (examples help)

## Worked examples

**Example 1 — Creating an OSS README**

User: "I just published a CLI tool for formatting JSON. Can you write the README?"

- Step 1: Task = Creating
- Step 2: Project type = Open Source. Problem = "format JSON from the command line". Quickest path = `npm install -g jsonfmt && jsonfmt file.json`. Notable = supports stdin, pretty/minify modes. Load `templates/oss.md`.
- Step 3: Draft README with install, usage examples for both file and stdin, contributing section. User adds "also supports YAML input". Update and confirm.

**Example 2 — Updating a stale README**

User: "My README says the API is v1 but we shipped v2 last month."

- Step 1: Task = Updating
- Step 2: What changed = API v2. Read current README, identify all v1 references, authentication section that changed, and new endpoint list. Propose specific edits.
- Step 3: Draft edits. User confirms. Note "Last reviewed: [date]" added.

## Deeper reference

- [`references/section-checklist.md`](references/section-checklist.md) — Which sections to include by project type
- [`references/style-guide.md`](references/style-guide.md) — Common README mistakes and prose guidance
- [`references/using-references.md`](references/using-references.md) — Guide to deeper reference materials
