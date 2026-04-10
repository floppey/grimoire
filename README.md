# grimoire

Claude Code skills, hooks, and settings I use across projects.

## What's in here

### Skills

Copy to `~/.claude/skills/` to make them available globally.

- **[review-pr](skills/review-pr/SKILL.md)** — Senior engineer design review of a PR. Evaluates the approach, not the code style. Posts review as a GitHub comment, fetches Jira context if linked, refuses to review PRs with no description. `/review-pr <number>`
- **[plan-issues](skills/plan-issues/SKILL.md)** — Analyzes open GitHub issues and creates a prioritized implementation plan. Groups related issues, identifies quick wins and blockers, estimates scope by reading actual code. `/plan-issues [max]`
- **[clean-worktrees](skills/clean-worktrees/SKILL.md)** — Removes all git worktrees except the main working tree. `/clean-worktrees`

### Hooks

Copy to `~/.claude/hooks/`.

- **[block-quoted-flags.sh](hooks/block-quoted-flags.sh)** — PreToolUse hook that prevents bash commands triggering the "quoted characters in flag names" warning in Claude Code. Blocks compound commands, quoted flag values, and echo/printf with quoted strings.

### Settings

- **[settings.json](settings.json)** — Global permissions, plugins, and hooks config. Merge into `~/.claude/settings.json`. Key decisions:
  - Broad allow for git, gh, pnpm, dotnet + common shell utilities
  - Hard deny on `npx` and `gh repo delete`
  - Explicit ask-every-time for package install/add/remove and PR merge/close
  - MCP tools for Atlassian and Splash UI auto-allowed

- **[CLAUDE.md](CLAUDE.md)** — Global instructions. Copy to `~/.claude/CLAUDE.md`. Covers communication style (direct, no sycophancy), code standards (native APIs, no hacks, a11y), and package management (pnpm only, no npx, manual approval for new deps).

## Install

```bash
# Skills
cp -r skills/* ~/.claude/skills/

# Hooks
cp hooks/* ~/.claude/hooks/
chmod +x ~/.claude/hooks/block-quoted-flags.sh

# Settings and instructions — merge manually, don't overwrite
# Your settings.json may have other config you want to keep
```
