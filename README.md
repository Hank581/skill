# Claude Code skills

Personal skills for Claude Code. This repo is cloned to `~/.claude/skills` and kept in sync automatically:

- **SessionStart hook**: commits local changes, pulls from GitHub, pushes.
- **Stop hook** (after each Claude reply, in the background): pushes if anything under `~/.claude/skills` changed.
- Claude Code hot-reloads skills when their files change, so pulled updates apply without a restart.

Layout: one folder per skill, each with a `SKILL.md`:

```
<skill-name>/
  SKILL.md        # frontmatter: name, description
  ...             # optional scripts / references
```

Sync script: `~/.claude/scripts/skills-sync.ps1` (log: `~/.claude/scripts/skills-sync.log`).
