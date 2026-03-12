# /learn — Interactive Coding Tutor for Claude Code

A Claude Code skill that turns your own projects into a personalized coding curriculum. Instead of generic tutorials, it reads your actual codebase and teaches you how your code works through Socratic questioning.

Built for people who've been vibe coding — building real projects with AI help — and want to understand what's actually happening under the hood.

## What it does

- **Reads your projects** and builds a curriculum around your actual code
- **Asks questions** instead of lecturing — draws understanding out of you
- **Tracks progress** across sessions with a structured curriculum (6 modules, 24 topics)
- **Adapts to feedback** — tell it to slow down, change style, or focus on specific areas
- **Creates exercises** using your own code patterns

## Curriculum

| Module | Topics |
|--------|--------|
| 1. Programming Fundamentals | Variables, functions, control flow, imports |
| 2. Web Fundamentals | HTML/JSX, CSS/Tailwind, client vs server, HTTP |
| 3. React & Components | Props, state/hooks, composition, server components |
| 4. Data & Databases | Schemas, queries, ORMs, API integration |
| 5. App Architecture | Project structure, routing, auth, background jobs |
| 6. APIs & Integrations | REST routes, third-party APIs, env vars, error handling |
| 7. Debugging & Verification | Reading errors, print debugging, devtools, testing, verifying features |

Modules are automatically skipped if your projects don't use those technologies. You can also add custom topics anytime with `/learn add-topic [name]`.

### After completing all modules

The learning doesn't stop. You can choose from: deep dives into specific topics, full code reviews of your projects, building something from scratch, reading open-source code, or onboarding new projects as fresh learning material.

## Setup

### 1. Install the skill

Copy `SKILL.md` into your Claude Code skills directory:

```bash
mkdir -p ~/.claude/skills/learn
cp SKILL.md ~/.claude/skills/learn/SKILL.md
```

### 2. Clone this repo (or create a working directory)

The skill needs a working directory to store your progress and exercises:

```bash
mkdir ~/learning-to-code
cd ~/learning-to-code
```

### 3. Make sure your projects are accessible

The skill works best when your projects are in a sibling or nearby directory. On first run, it scans for projects and asks you to confirm what it found.

### 4. Start learning

```
cd ~/learning-to-code
claude
> /learn
```

## Commands

| Command | What it does |
|---------|-------------|
| `/learn` | Continue from last session (or start fresh) |
| `/learn assess` | Run/re-run the skills assessment |
| `/learn progress` | Show your progress dashboard |
| `/learn topic [name]` | Jump to a specific topic |
| `/learn review` | Quiz on previously covered material |
| `/learn feedback` | Share feedback to improve the experience |
| `/learn add-topic [name]` | Add a custom topic to the curriculum |

## How it works

**First run:** The skill scans nearby directories for projects, identifies their tech stacks, and builds a curriculum map. Then it runs an assessment — showing you snippets from your code and asking what you think they do — to gauge your starting level.

**Each session:** Review a prior concept → Explore new code → Get feedback → Go deeper → Try a challenge → Wrap up with progress saved.

**Feedback loop:** At the end of each session, it asks about pacing. You can also run `/learn feedback` anytime. Adjustments are tracked in `adaptations.md` so the teaching style evolves with you.

## Files created at runtime

These are created in your working directory and excluded from git:

| File | Purpose |
|------|---------|
| `progress.json` | Your level, topic statuses, session history |
| `config.json` | Discovered projects and curriculum mapping |
| `feedback.md` | Raw feedback log |
| `adaptations.md` | Active teaching adjustments |
| `exercises/` | Scratch files for coding challenges |

## Tips

- **`/clear` between sessions** is fine — all progress is saved to files
- **Finish the wrap-up step** before clearing, so your progress gets saved
- **Be honest** when you don't understand something — the skill gives hints, not answers
- **Correct the tutor** if it assumes you know more than you do

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI
- One or more coding projects to learn from
