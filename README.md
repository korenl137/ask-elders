# ask-elders

An agent skill for the question "how did experts, seniors or others do this?"

It surveys how practitioners and earlier builders handled what you are about to
do, including adjacent fields that solved the same kind of problem, and gives
approach candidates plus a recommendation fitted to your situation.

What it does differently from a plain search:

- Works with rich session context (one recommendation) and with almost none
  (states its assumptions, gives branches by condition).
- Labels each point as Verified (the page was read), Reported (summary or
  snippet) or Judgment (the agent's own).
- Says what it could not read and what it did not find. It does not invent
  sources, people or quotes.
- Skips the process for questions one search can settle.

It is read-only. Nothing is edited, installed or published.

Status: draft 0.1.0. A first comparison (2026-11-07) ran the four cases in
`skills/ask-elders/evals/scenarios.json` once each against a plain prompt that
also searched the web, with sub-agents following `SKILL.md` and a blind grader.
The skill answers were preferred in the three research cases, with no invented
sources in either arm. One run per case and no native skill loading, so treat
it as a first check, not proof.

## Install

The skill is the folder `skills/ask-elders/`. It works with any agent that
reads `SKILL.md` skills (Claude Code, Codex, and others).

```bash
git clone https://github.com/korenl137/ask-elders.git ~/src/ask-elders
ln -s ~/src/ask-elders/skills/ask-elders ~/.claude/skills/ask-elders    # Claude Code
ln -s ~/src/ask-elders/skills/ask-elders ~/.agents/skills/ask-elders    # Codex
```

## Use

Ask in plain words: "how did experts do this?", "has anyone built this?",
"what's the standard way to show this?"
