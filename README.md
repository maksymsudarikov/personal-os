# Personal OS — Your AI operating system for Claude Code and Codex

A free, MIT-licensed starter kit that turns Claude Code or Codex into a personal operating system for your business. Built for entrepreneurs, creators, and operators running one or more projects who want AI that actually does work — not just answers questions.

---

## The test

> **"While you're away from your desk, your Personal OS handles something faster and more accurately than you would have."**

If that's not happening yet, this kit gives you the structure to get there.

---

## What you get

Three skills that compound over time:

| Skill | When to run | What it does |
|---|---|---|
| `/setup` | Day 1 — right after clone | 7-question interview. Learns your business, voice, priorities, tools. Generates your operating files. |
| `/review` | Day 7, then weekly | Scores your OS across four layers. Shows exactly what's missing and what to fix first. |
| `/build` | Day 14, then weekly | Finds one manual task worth automating. Scopes it. Helps you ship it. One per week. |

---

## Quick start

1. Clone this repo to a folder on your machine
2. Open it in Claude Code or Codex
3. Run `/setup` — answer 7 questions honestly. Takes 10-15 minutes.
4. Use it for a week with real questions and real decisions
5. Day 7: run `/review` to see your score
6. Day 14: run `/build` to ship your first automation

---

## Repo layout

```
personal-os/
├── README.md
├── CLAUDE.md                  ← operating manual for Claude Code (filled by /setup)
├── AGENTS.md                  ← operating manual for Codex and other agents (filled by /setup)
├── intake.md                  ← source of truth for /setup — edit and re-run any time
├── connections.md             ← every tool your OS can reach
├── setup-guide.md             ← detailed setup instructions
├── EXPANSIONS.md              ← what to add as you grow
├── context/                   ← about you and your business (filled by /setup)
├── references/                ← API guides, voice samples, SOPs
├── decisions/log.md           ← append-only record of decisions and why
└── .claude/skills/            ← /setup, /review, /build
```

---

## License

MIT License. © 2026 Maksym Sudarikov.
