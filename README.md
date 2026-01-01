# Mastering Git CLI Skill

Production-ready Git workflows and automation for modern development (2025).

## Overview

This skill provides comprehensive guidance for Git CLI operations in modern development. It covers:

- **Repository Management**: Clone, init, remote configuration
- **Branching Strategies**: Feature branches, release branches, hotfixes
- **Merge Operations**: Merge vs rebase vs cherry-pick decision trees
- **Worktrees**: Parallel development with isolated working directories
- **Submodules**: Multi-repo project architecture
- **Recovery**: Lost commits, broken merges, corrupted repos
- **Modern Defaults**: 2025 recommended Git configuration

## Quick Start

```bash
# Clone and start working
git clone <url> && cd <repo>
git checkout -b feature-x

# Commit workflow
git add -A && git commit -m "feat: description"
git push -u origin feature-x

# Merge feature to main
git checkout main && git pull
git merge --no-ff feature-x
git push
```

## When to Use This Skill

Use when:
- Working with Git repositories and version control
- Setting up branching strategies and workflows
- Resolving merge conflicts
- Creating parallel agent workflows with worktrees
- Managing multi-repo projects with submodules
- Recovering from Git disasters (lost commits, broken merges)
- Configuring Git for modern development (2025 defaults)

## Installing with Skilz (Universal Installer)

The recommended way to install this skill across different AI coding agents is using the **skilz** universal installer.

### Install Skilz

```bash
pip install skilz
```

This skill supports [Agent Skill Standard](https://agentskills.io/) which means it supports 14+ coding agents including Claude Code, OpenAI Codex, Cursor and Gemini.

### Git URL Options

You can use either `-g` or `--git` with HTTPS or SSH URLs:

```bash
# HTTPS URL
skilz install -g https://github.com/SpillwaveSolutions/mastering-git-cli-agent-skill

# SSH URL
skilz install --git git@github.com:SpillwaveSolutions/mastering-git-cli-agent-skill.git
```

### Claude Code

Install to user home (available in all projects):
```bash
skilz install -g https://github.com/SpillwaveSolutions/mastering-git-cli-agent-skill
```

Install to current project only:
```bash
skilz install -g https://github.com/SpillwaveSolutions/mastering-git-cli-agent-skill --project
```

### OpenCode

Install for [OpenCode](https://opencode.ai):
```bash
skilz install -g https://github.com/SpillwaveSolutions/mastering-git-cli-agent-skill --agent opencode
```

Project-level install:
```bash
skilz install -g https://github.com/SpillwaveSolutions/mastering-git-cli-agent-skill --project --agent opencode
```

### Gemini

Project-level install for Gemini:
```bash
skilz install -g https://github.com/SpillwaveSolutions/mastering-git-cli-agent-skill --agent gemini
```

### OpenAI Codex

Install for OpenAI Codex:
```bash
skilz install -g https://github.com/SpillwaveSolutions/mastering-git-cli-agent-skill --agent codex
```

Project-level install:
```bash
skilz install -g https://github.com/SpillwaveSolutions/mastering-git-cli-agent-skill --project --agent codex
```

### Install from Skillzwave Marketplace
```bash
# Claude to user home dir ~/.claude/skills
skilz install SpillwaveSolutions_mastering-git-cli-agent-skill/mastering-git-cli

# Claude skill in project folder ./claude/skills
skilz install SpillwaveSolutions_mastering-git-cli-agent-skill/mastering-git-cli --project

# OpenCode install to user home dir ~/.config/opencode/skills
skilz install SpillwaveSolutions_mastering-git-cli-agent-skill/mastering-git-cli --agent opencode

# OpenCode project level
skilz install SpillwaveSolutions_mastering-git-cli-agent-skill/mastering-git-cli --agent opencode --project

# OpenAI Codex install to user home dir ~/.codex/skills
skilz install SpillwaveSolutions_mastering-git-cli-agent-skill/mastering-git-cli --agent codex

# OpenAI Codex project level ./.codex/skills
skilz install SpillwaveSolutions_mastering-git-cli-agent-skill/mastering-git-cli --agent codex --project

# Gemini CLI (project level) -- only works with project level
skilz install SpillwaveSolutions_mastering-git-cli-agent-skill/mastering-git-cli --agent gemini
```

### Other Supported Agents

Skilz supports 14+ coding agents including Claude Code, OpenAI Codex, OpenCode, Cursor, Gemini CLI, GitHub Copilot CLI, Windsurf, Qwen Code, Aidr, and more.

For the full list of supported platforms, visit [SkillzWave.ai/platforms](https://skillzwave.ai/platforms/) or see the [skilz-cli GitHub repository](https://github.com/SpillwaveSolutions/skilz-cli)

<a href="https://skillzwave.ai/">Largest Agentic Marketplace for AI Agent Skills</a> and
<a href="https://spillwave.com/">SpillWave: Leaders in AI Agent Development.</a>

## Skill Contents

- **SKILL.md** - Main skill documentation with decision trees and quick patterns
- **references/** - Detailed reference documentation
  - `foundations.md` - Git internals, object model, DAG concepts
  - `daily-usage.md` - Clone, commit, log, branch basics
  - `worktrees.md` - Parallel development and agent workflows
  - `merge-operations.md` - Merge strategies and conflict resolution
  - `submodules.md` - Multi-repo project management
  - `advanced-operations.md` - Reset, revert, restore, interactive rebase
  - `recovery.md` - Disaster recovery and troubleshooting
- **scripts/** - Utility scripts
  - `setup-agent-worktrees.sh` - Create isolated worktrees for parallel agents
  - `cleanup-agent-worktrees.sh` - Remove agent worktrees
  - `submodule-report.sh` - Get readable submodule status
  - `git-health-check.sh` - Diagnose repository issues

## License

MIT

## Author

Richard Hightower - [SpillWave Solutions](https://spillwave.com/)
