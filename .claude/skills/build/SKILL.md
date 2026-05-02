## What this skill does

Weekly build session. Finds one manual task worth automating, scopes it, and helps you ship it. One run = one shipped artifact.

Run on Day 14, then weekly. After `/review` shows you what's structurally missing, `/build` finds what capability to add next.

## When to run

- "What should I automate next?"
- "Find me leverage this week"
- Weekly Friday ritual
- After closing a gap from `/review`

## Execution

### Phase 1: Find the candidate

Ask: "What's the most repetitive thing you did this week that you wish you hadn't?"

If they can't name one, prompt with their Q7 pain point from `context/about-me.md`.

Push for specifics:
- How often does it happen?
- How long does it take each time?
- What's the input and what's the output?

Goal: one clearly scoped manual task. Stop at one.

### Phase 2: Scope it

Before building, answer four questions together:

1. **Input** — what triggers this? (email arrives, time of day, you ask manually)
2. **Process** — what steps happen between input and output?
3. **Output** — what does done look like? (a drafted reply, a logged entry, a summary)
4. **Autonomy level** — pick one:
   - *Assisted*: you do it, OS helps (draft, summarize, suggest)
   - *Semi-auto*: OS does it, you approve before it sends/saves
   - *Autonomous*: OS does it, you review after

Ask: "Does this work today if you do it manually?" If no — fix the manual process first. Don't automate chaos.

### Phase 3: Build it

Based on the scoped automation, build one artifact:

**Option A — New skill**
Write `.claude/skills/{name}/SKILL.md`. Structure:
- What it does (one line)
- When to run it
- Step-by-step execution
- Output format

**Option B — API script**
Write `scripts/{tool}_action.py`. Save `references/{tool}-api.md` if it doesn't exist yet.

**Option C — Prompt template**
Write `references/{name}-prompt.md`. A reusable prompt the user pastes or invokes.

Pick the simplest option that achieves the autonomy level from Phase 2.

### Phase 4: Close

After the artifact is built:

1. Suggest logging: "Want to append this to `decisions/log.md`? I can draft the entry — what you built, why, what you expect it to save per week."
2. Set a reminder: "Run `/build` again next week. We'll see if this one stuck and find the next one."

## Rules

- One automation per session. Finish one before considering the next.
- Don't build what doesn't work manually first.
- No framework names or methodology labels. Just: find it, scope it, ship it.
- If MCP is the right answer, say so. If a script is simpler, use a script.
