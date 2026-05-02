# Setup Guide

Everything you need to get Personal OS running in 15 minutes.

## Prerequisites

- [Claude Code](https://claude.ai/code) installed, OR Codex configured in your editor
- A Claude or OpenAI account

## Step 1: Clone the repo

```bash
git clone https://github.com/maksymsudarikov/personal-os ~/projects/personal-os
```

Or download as ZIP and unzip to a folder on your machine.

## Step 2: Open in Claude Code or Codex

**Claude Code:**
```bash
cd ~/projects/personal-os
claude .
```

**Codex / VS Code:** Open the folder in your editor and use your configured coding agent.

## Step 3: Run /setup

Type `/setup` in the agent prompt. Answer the 7 questions.

**One rule:** Q2 asks for writing samples. Paste real, unedited text — don't type something fresh. Open a real email or post in another tab and paste it. This is the only rule that matters.

Takes 10-15 minutes. At the end, your operating files are generated.

## Step 4: Use it

Bring real questions. Make real decisions. Log them:

```
Append this to decisions/log.md:
## 2026-05-02 — [Short title]
Decision: [what you decided]
Why: [the reasoning]
```

## Step 5: Day 7 — run /review

```
/review
```

See your four-layer score. Pick one gap to close.

## Step 6: Day 14 — run /build

```
/build
```

Find one automation worth building. Build it. One per week from here.
