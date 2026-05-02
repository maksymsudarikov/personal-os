# Personal OS — Testing Guide

Run this before sharing the kit with anyone. Each section is a scenario to walk through manually. Mark gaps as you find them.

---

## How to use this guide

1. Open `~/projects/personal-os` in a **fresh Claude Code session** (no context from this conversation)
2. Work through each scenario below in order
3. Mark ✅ when it passes, ❌ when it breaks or feels off
4. Fix gaps before distributing

---

## Scenario 1: Cold clone — first-time user experience

Simulate what a buyer does on Day 1.

- [ ] Open the repo in Claude Code with zero prior context
- [ ] Read `README.md` — does the hook land? Is it clear what to do next?
- [ ] Read `setup-guide.md` — can you follow it without help?
- [ ] Run `/setup` — does it start the interview without needing explanation?

**What to watch for:**
- Does it ask Q1 immediately, or does it do something unexpected first?
- Does it write Q1 answers into `intake.md` before moving to Q2?
- Is the language clear for someone who's never seen this before?

**Gap signals:**
- Confusion about what to type to start
- Skill doesn't read `intake.md` first
- Asks multiple questions at once instead of one at a time

---

## Scenario 2: Q2 voice paste enforcement

This is the one rule that must hold.

- [ ] When `/setup` asks Q2, start typing a fresh paragraph instead of pasting
- [ ] Verify: does it refuse and ask you to paste raw text?
- [ ] Then paste a real email or post verbatim
- [ ] Verify: does it accept it and write it to `intake.md`?

**Gap signals:**
- Accepts typed fresh prose without pushing back
- Refuses paste as well (over-strict)
- Doesn't save to `intake.md` after accepting

---

## Scenario 3: Full interview + scaffold

Complete all 7 questions with realistic answers.

- [ ] Answer Q1-Q7 with real or realistic data (use your own or invent a persona: "Sarah, runs a freelance design studio")
- [ ] After Q7, verify `/setup` scaffolds all files in one batch without asking for confirmation:
  - [ ] `context/about-me.md` created
  - [ ] `context/about-business.md` created
  - [ ] `context/priorities.md` created
  - [ ] `references/voice.md` created with pasted samples verbatim
  - [ ] `connections.md` populated with real tools from Q4-Q7
  - [ ] `CLAUDE.md` — all `{{placeholders}}` replaced
  - [ ] `AGENTS.md` — identical to `CLAUDE.md`
- [ ] Verify the closing screen appears (3-line format, not a menu)

**Gap signals:**
- Any `{{placeholder}}` still visible in CLAUDE.md or AGENTS.md after setup
- connections.md still shows `_filled by /setup_` placeholders
- voice.md contains paraphrased samples instead of verbatim paste
- AGENTS.md differs from CLAUDE.md

---

## Scenario 4: Closing prompt

Right after `/setup` finishes, run the suggested prompt.

- [ ] Ask: *"what's the one thing I should move forward this week?"*
- [ ] Verify the response:
  - Uses the Q2 voice register (matches the pasted samples)
  - References Q3 priorities specifically (not generic advice)
  - Ends with the "If I had to pick one" line
  - Asks "where could AI take more of this off your plate?"

**Gap signals:**
- Generic response that could apply to anyone
- Doesn't reference the specific priorities from Q3
- Sounds like AI, not like the user's voice register
- Missing the closing question about AI leverage

---

## Scenario 5: Idempotency — re-running /setup

Test that re-running doesn't break anything.

- [ ] Edit `context/priorities.md` manually — change one priority
- [ ] Re-run `/setup`
- [ ] Verify: it detects that Q1-Q7 are already answered and asks what to do
- [ ] Choose to refresh — verify it creates a backup in `archives/setup-{timestamp}/`
- [ ] Verify: only the changed priority updates; other files stay intact

**Gap signals:**
- Re-running overwrites everything without asking
- No backup created in `archives/`
- Doesn't detect already-answered questions

---

## Scenario 6: /review on a fresh setup

Run the audit immediately after `/setup` to get the Day-1 baseline score.

- [ ] Run `/review`
- [ ] Verify the scoreboard appears with all four layers scored
- [ ] Verify: score is in the 30-55 range (fresh setup should not score above 60)
- [ ] Verify: top 3 gaps are concrete — each has a specific next step, not vague advice
- [ ] At the end, say yes to saving the report
- [ ] Verify: `audits/review-{date}.md` is created

**Gap signals:**
- Score above 60 on a fresh install (scoring is too generous)
- Gaps say "improve your connections" without a specific action
- Report file not created despite saying yes
- Skill modifies any project file (it should be read-only)

---

## Scenario 7: /build — find and scope one automation

- [ ] Run `/build`
- [ ] When asked "what's the most repetitive thing you did this week?", name something real (e.g. "I copy-paste client inquiry emails into a spreadsheet")
- [ ] Verify it asks the four scoping questions: input, process, output, autonomy level
- [ ] Verify it recommends ONE artifact type (skill, script, or prompt template) — not all three
- [ ] Verify it builds or drafts the artifact in the same session
- [ ] Verify it suggests logging to `decisions/log.md` at the end

**Gap signals:**
- Jumps to building without scoping
- Tries to build multiple automations at once
- Doesn't offer to log the decision
- Builds something complex when a simple prompt template would do

---

## Scenario 8: AGENTS.md — Codex compatibility

- [ ] Open the repo in a Codex-compatible editor (VS Code with Codex, or similar)
- [ ] Verify `AGENTS.md` is read as the operating manual
- [ ] Verify contents are identical to `CLAUDE.md` (run `diff CLAUDE.md AGENTS.md` — should show no output)
- [ ] Confirm `/setup`, `/review`, `/build` are referenced in `AGENTS.md`

**Gap signals:**
- diff shows differences between CLAUDE.md and AGENTS.md
- Skills not referenced in AGENTS.md

---

## Scenario 9: Edge case — empty answers

- [ ] Run `/setup` fresh
- [ ] At Q3, give a vague answer: "I want to grow my business"
- [ ] Verify: it pushes back and asks for a number, deadline, or deliverable
- [ ] Give a real answer and verify it proceeds

**Gap signals:**
- Accepts "grow my business" without pushing back
- Pushes back so hard it won't proceed even with a reasonable answer

---

## Scenario 10: README sanity check

- [ ] Read the README as if you've never heard of this product
- [ ] Can you answer these questions just from the README?
  - What is Personal OS?
  - Who is it for?
  - What do you get?
  - How do you start?
- [ ] Is there any mention of Nate Herk, AIS-OS, or "AI Automation Society"? (should be zero)
- [ ] Is there any mention of "second brain"? (should be zero)

---

## Gap log

Use this section to track issues found during testing:

| Scenario | Issue | Severity (High/Med/Low) | Fixed? |
|---|---|---|---|
| | | | |

**Severity guide:**
- **High** — blocks the user from completing setup or getting value
- **Med** — confusing or incomplete but workaround exists
- **Low** — polish issue, minor wording, cosmetic

Fix all High issues before distributing. Fix Med issues before charging money for it.

---

## Sign-off checklist

Before sharing with anyone:

- [ ] Scenarios 1-5 passed (core flow works end-to-end)
- [ ] Scenario 6 passed (audit scores correctly)
- [ ] Scenario 7 passed (build ritual works)
- [ ] Scenario 10 passed (no third-party branding in README)
- [ ] Zero `{{placeholders}}` visible after a full `/setup` run
- [ ] `diff CLAUDE.md AGENTS.md` returns empty
- [ ] Gap log has no unfixed High issues
