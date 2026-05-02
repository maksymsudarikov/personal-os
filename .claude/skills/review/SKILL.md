## What this skill does

Runs the four-layer audit on the current project. Reads (never writes) project files. Scores each of the four layers out of 25. Surfaces strengths and the top 3 gaps with concrete next steps.

**Scope is structural — "is the OS built right?"** Capability planning ("what could I automate?") belongs to `/build`.

First run is the baseline. Re-run weekly to watch the score climb.

## The four layers (25 pts each = 100 total)

| Layer | Test |
|---|---|
| **Context** | Knows the business — identity, voice, priorities, decisions, references |
| **Connections** | Reaches your tools — MCPs, scripts, API keys |
| **Capabilities** | Knows how to work — skills and agents |
| **Cadence** | Runs without being asked — schedules, hooks, rituals |

## Execution

### Step 1: Read the project

Check for:
- `CLAUDE.md` or `AGENTS.md` — operating manual
- `MEMORY.md` or `memory/` — persistent memory
- `.claude/skills/*/SKILL.md` — skill count
- `.claude/agents/*.md` — agent count
- `connections.md` — tool registry
- `references/` — reference docs
- `decisions/log.md` — decisions
- `.claude/settings.json` — hooks, MCPs
- `templates/` — templates

### Step 2: Score each layer

**Context (25 pts)**
- Operating manual exists and is >200 words: 5 pts
- Identity, role, voice captured: 5 pts
- Memory exists with >3 entries: 5 pts
- Reference docs exist: 5 pts
- Decisions log has ≥1 entry: 5 pts

**Connections (25 pts)**

Seven domains. A domain counts as "reachable" via any mechanism: MCP, script, `.env` key + reference doc.

Domains: (1) Revenue/Financials, (2) Customer interactions, (3) Calendar, (4) Communication, (5) Tasks, (6) Meeting intelligence, (7) Knowledge/files.

- Domain coverage: 1.4 pts per reachable domain, cap 10 pts
- Reference guide per connected tool: 5 pts (-1 per connected tool missing a `references/{tool}-api.md`, floor 0)
- Freshness: 5 pts (-1 per stale/broken connection, floor 0)
- Connections registry documented: 3 pts (0 missing, 1 sparse, 2 most, 3 complete)
- At least one write-capable connection: 2 pts (0 if all read-only)

**Capabilities (25 pts)**
- 3+ skills installed: 10 pts
- 1+ user-built skill (not setup/review/build): 10 pts
- 1+ agent defined: 5 pts

**Cadence (25 pts)**
- 1+ recurring trigger (hook or named daily-*/weekly-* skill): 10 pts
- Recent activity (skill files modified within 30 days OR decisions entry within 30 days): 10 pts
- Templates folder populated: 5 pts

### Step 3: Top 3 gaps by leverage

For each criterion that lost points, leverage = points lost × multiplier:
- 0 domains reachable: 4×
- Operating manual thin/missing: 3×
- ≤2 domains reachable: 3×
- 0 skills: 2×
- No recurring trigger: 2×
- All connections read-only: 2×
- No reference guides for connected tools: 1.5×
- No decisions log: 1.5×
- All others: 1×

Sort by leverage descending. Take top 3. For each, write a concrete one-line next step.

### Step 4: Output

```
# Personal OS Review — {date}
**Score: {total}/100** ({stage})

Stage: 0-39 Foundation | 40-69 Built | 70-89 Compounding | 90-100 Autonomous

## Scoreboard
Context        {bar}  {n}/25  {label}
Connections    {bar}  {n}/25  {label}
Capabilities   {bar}  {n}/25  {label}
Cadence        {bar}  {n}/25  {label}

(bar = ## per 5 pts | Strong ≥20 | Solid 15-19 | Thin 8-14 | Missing <8)

## Strengths
- [1-3 bullets from highest-scoring criteria]

## Top 3 Gaps
1. **{gap}** (-{pts} × {multiplier}×) → {concrete next step}
2. **{gap}** (-{pts} × {multiplier}×) → {concrete next step}
3. **{gap}** (-{pts} × {multiplier}×) → {concrete next step}

## Suggested next: {single most leveraged action}

---
Structural gaps only. To find automation opportunities, run /build after closing your top gap.
```

After output, offer to save the report to `audits/review-{date}.md`.

## Rules

- Read-only. Never modify project files. The only allowed write is the optional audit report.
- Be honest, not generous. 95/100 is rare. Most fresh setups land 30-50.
- Structural gaps only. Capability gaps belong to `/build`.
