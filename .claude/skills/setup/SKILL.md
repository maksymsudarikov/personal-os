## What this skill does

Single combined wizard. Reads or writes `intake.md` (the canonical intake), conducts the 7-question interview if the file isn't filled, then scaffolds the Day-1 file set at the end. One flow, no separate steps.

**The closing prompt:** at the end, suggest — *"Try this: ask me what's the one thing I should move forward this week?"* That's the moment the OS becomes real.

## When NOT to run this

- User already onboarded and wants to refresh: still run, but skip questions already answered.
- User wants to add a new connection: point them to `connections.md` directly, or run `/build` Phase 2.

## Execution

### Step 1: Read the intake

Read `intake.md`. Check which Q1-Q7 sections have content vs. `[Your answer here]` placeholders.

- **All filled** → skip to Step 3 (scaffold).
- **Some filled** → tell the user which questions are answered and ask if they want to fill the rest or scaffold from what's there.
- **None filled** → run Step 2.

### Step 2: The interview (7 questions, hard cap)

Ask one at a time. Write each answer into `intake.md` as you go.

**Q1 — Who are you and what do you run?**
Name, role, businesses or projects, ICP. One paragraph each.

If they run more than one project or business, ask as a follow-up: *"Which one needs the most attention right now — or are you splitting focus?"* Note the answer as `primary_focus`. This shapes every `/build` session and the priorities scaffold.

**Q2 — Paste 1-2 things you've written recently. Don't edit them.**
Voice samples MUST be pasted, not typed mid-conversation. If the user starts typing fresh prose, stop them:

> *"Pause — paste it raw. If you type it here while we're talking, the sample is already shaped by our conversation. Open a real email or post in another tab and paste the unedited text. This is the one rule."*

Ask for two samples. One email, one post. Or two of either.

**Q3 — What are your top 2-3 priorities this quarter?**
Push back on vague answers ("grow my business"). Make them name a number, a deadline, or a deliverable.

**Q4 — Where does revenue land and how do you track it?**
Multiple answers OK. Map to Domain 1 (Revenue/Financials).

**Q5 — Where do you talk to clients, teammates, and the world?**
Email (Gmail/Outlook), messaging (Slack/Telegram/iMessage), DMs. Map to Domains 2 + 4. Infer calendar from email provider (Gmail → Google Cal; Outlook → Outlook Cal).

**Q6 — Where do notes, recordings, and docs live?**
Map to Domains 6 + 7.

**Q7 — What's the one task that eats your week, and where do you track work?**
Top pain point + task system. Map to Domain 5.

### Step 3: Scaffold Day-1 files

Once intake is complete, generate these files in one batch. Back up originals to `archives/setup-{YYYY-MM-DD-HHMM}/` if re-running.

1. **`context/about-me.md`** — from Q1 (identity, role) + Q7 (top pain). One short paragraph each.
2. **`context/about-business.md`** — from Q1 (offer, ICP) + Q4 (revenue). One paragraph. If multiple businesses: one paragraph per business, with a "Current focus" line at the top naming the `primary_focus` from Q1.
3. **`context/projects.md`** — only if the user runs 2+ projects. List each project with: name, one-line description, status (active / building / paused), and current priority level (primary / secondary). This is the map `/build` uses to stay on-target.
4. **`context/priorities.md`** — from Q3. Numbered list, one line per priority.
4. **`references/voice.md`** — from Q2. Paste samples verbatim with a short header on how to use them.
5. **`connections.md`** — populate the 7-row table from Q4-Q7 answers. Each row: `mechanism: not yet connected`, `auth: —`, `last checked: —`.
6. **`CLAUDE.md` and `AGENTS.md`** — fill all `{{...}}` placeholders with the user's name, priority, voice summary, and connections summary. Write identical content to both files. If multi-project: add a "Projects" section listing all businesses with their focus level.

### Step 4: Closing

Print one screen:

```
✓ Setup complete. Your Personal OS knows who you are, what you run, what matters this quarter, and how you sound.

Today: ask me — "what's the one thing I should move forward this week?"
Tomorrow: pick one tool from connections.md and wire it up.
Day 7: run /review to see your score.
```

When the user runs the closing prompt ("what's the one thing I should move forward this week?"), respond using only the new context files:
- 3-bullet priority list in their voice register from Q2
- Each bullet ties back to a Q3 priority
- Final line: "If I had to pick one — [X], because [reason]. Want me to draft the first step? And — where could AI take more of this off your plate?"

## Rules

1. **7 questions, hard cap.** No Q8.
2. **Voice paste cannot be skipped.** Typed samples get refused.
3. **Scaffold in one batch** after Q7. No confirmation loop.
4. **Idempotent.** Re-running refreshes files; backs up originals. Skips answered questions.
5. **No .env writes.** Don't ask for API keys during setup.
6. **No extra skills.** Don't create new skills during this run.
