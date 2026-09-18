---
name: skills-sync
description: Sync the user's Claude Code skills (~/.claude/skills) with GitHub repo Hank581/skill - pull the latest skills and push local changes. Use when the user says "sync skills", "同步skill", "更新skill", "push skills", "拉取skill", or right after creating or editing a skill they want on GitHub.
---

# Skills sync

`~/.claude/skills` is a git clone of https://github.com/Hank581/skill. Hooks already sync it on
session start and after each reply; this skill forces a sync right now.

## Run

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File "$env:USERPROFILE\.claude\scripts\skills-sync.ps1" -Mode sync
```

Report the one-line result to the user. On failure, show the tail of
`~/.claude/scripts/skills-sync.log`:

- **push failed (auth)**: the stored GitHub credential is missing or expired. Ask the user to run
  `git -C "$env:USERPROFILE\.claude\skills" push` in a terminal; Git Credential Manager opens a
  browser to sign in. Never handle tokens or passwords yourself.
- **rebase conflict**: local commits are kept, nothing was pushed. Show `git -C ~/.claude/skills status`
  and help the user resolve it.

## Creating a new skill

Put it in `~/.claude/skills/<skill-name>/SKILL.md` with `name` and `description` frontmatter,
then run the sync above so it lands on GitHub.
