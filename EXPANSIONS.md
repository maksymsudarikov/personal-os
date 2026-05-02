# Expansions

What to add as your Personal OS grows. Start with the basics. Add layers when the previous one is working.

## Layer 1 — Foundation (Day 1-7)
Already in place after `/setup`:
- `context/` — who you are, your business, your priorities
- `references/voice.md` — your voice baseline
- `connections.md` — tool registry

## Layer 2 — Connections (Day 2-14)
Wire your tools:
- Add `.env` with API keys (copy `.env.example` if it exists)
- Write `scripts/{tool}_api.py` for each connection
- Save `references/{tool}-api.md` after wiring each tool
- Update `connections.md` — change mechanism from `not yet connected`

## Layer 3 — Capabilities (Week 2-4)
Build custom skills:
- Create `.claude/skills/{skill-name}/SKILL.md`
- Start with one skill that automates your top pain point from Q7

## Layer 4 — Agents (Month 2+)
Automate recurring work:
- Create `.claude/agents/{agent-name}.md`
- Wire to a schedule or trigger

## Layer 5 — Scale (When ready)
- `projects/{project-name}/` — sub-OS for each business
- `templates/` — repeatable document structures
- `.claude/agents/` — autonomous agents for recurring tasks
