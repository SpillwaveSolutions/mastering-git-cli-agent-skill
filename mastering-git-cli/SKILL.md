---
name: mastering-git-cli
description: Git CLI operations, workflows, and automation for modern development (2025). Use when working with repositories, commits, branches, merging, rebasing, worktrees, submodules, or multi-repo architectures. Includes parallel agent workflow patterns for isolated worktree development, comprehensive merge strategy selection, conflict resolution, and recovery procedures. Triggers on git commands, version control questions, merge conflicts, worktree setup, submodule management, repository troubleshooting, branch strategy, rebase operations, cherry-pick decisions, and CI/CD git integration.
---

# Git CLI Skill (2025 Edition)

Production-ready Git workflows and automation for modern development.

## Quick Start

### Most Common Patterns

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

### Modern Git Config (2025 Defaults)

```bash
git config --global pull.rebase true
git config --global push.autoSetupRemote true
git config --global merge.conflictStyle zdiff3
git config --global diff.algorithm histogram
git config --global rerere.enabled true
git config --global rebase.autoStash true
```

## Decision Trees

### Merge vs Rebase vs Cherry-pick

```
Need to integrate changes?
│
├─ All commits from a branch?
│  ├─ Shared branch (pushed/collaborative) → MERGE
│  └─ Local-only branch → REBASE (cleaner) or MERGE
│
└─ Specific commits only?
   └─ CHERRY-PICK
      ├─ Hotfix to release branch → cherry-pick -x
      └─ Backport to old version → cherry-pick -x
```

### Worktrees vs Branches vs Stash

```
Need to switch context?
│
├─ Quick switch, will return soon → STASH
├─ Parallel work on same files → Not possible
├─ Parallel work on different features?
│  ├─ Short-lived (minutes) → STASH or COMMIT WIP
│  └─ Long-running or parallel builds → WORKTREE
│
└─ Multiple agents working simultaneously → WORKTREE (essential)
```

### Submodules vs Subtree vs Monorepo

```
External code dependency?
│
├─ Need to modify and contribute back → SUBMODULE
├─ Just embedding, no upstream → SUBTREE
├─ Tight coupling, single team → MONOREPO
└─ Standard library/package → PACKAGE MANAGER
```

### Reset vs Revert vs Restore

```
Undo something?
│
├─ Discard file changes (not staged) → git restore <file>
├─ Unstage files → git restore --staged <file>
├─ Undo commits (not pushed)?
│  ├─ Keep changes staged → git reset --soft HEAD~1
│  ├─ Keep changes unstaged → git reset HEAD~1
│  └─ Discard everything → git reset --hard HEAD~1
│
└─ Undo commits (already pushed) → git revert <sha>
```

## Merge Easy Buttons

### Integrate feature into main
```bash
git checkout main
git merge --no-ff feature    # Always creates merge commit
```

### Update feature with latest main
```bash
git checkout feature
git merge main               # Safe for shared branches
# OR
git rebase main              # Only if branch not shared
```

### Resolve all conflicts using theirs
```bash
git checkout --theirs .
git add .
git commit
```

### Resolve all conflicts using ours
```bash
git checkout --ours .
git add .
git commit
```

### Abort a broken merge
```bash
git merge --abort
```

### Undo a pushed merge
```bash
git revert -m 1 <merge-sha>
git push
```

### Merge multiple branches at once
```bash
git merge feature-a feature-b feature-c  # Octopus merge (no conflicts allowed)
```

## Script Usage

### Agent Worktree Setup
Create isolated worktrees for parallel agent development:
```bash
scripts/setup-agent-worktrees.sh [num_agents] [base_branch]
# Example: scripts/setup-agent-worktrees.sh 3 main
# Creates: ../agent-1, ../agent-2, ../agent-3, ../integration
```

### Agent Worktree Cleanup
Remove all agent worktrees and optionally delete branches:
```bash
scripts/cleanup-agent-worktrees.sh [--delete-branches] [--force]
```

### Submodule Status Report
Get readable status of all submodules:
```bash
scripts/submodule-report.sh
```

### Git Health Check
Diagnose common repository issues:
```bash
scripts/git-health-check.sh [--verbose]
```

## Reference Navigation

Read the appropriate reference file based on your task:

| Task | Reference File |
|------|----------------|
| Understand Git internals, object model, DAG | [references/foundations.md](references/foundations.md) |
| Configure Git, set up 2025 defaults | [references/foundations.md](references/foundations.md) |
| Clone, commit, log, branch basics | [references/daily-usage.md](references/daily-usage.md) |
| Create/manage worktrees | [references/worktrees.md](references/worktrees.md) |
| Set up parallel agent workflows | [references/worktrees.md](references/worktrees.md) |
| Choose merge strategy | [references/merge-operations.md](references/merge-operations.md) |
| Resolve merge conflicts | [references/merge-operations.md](references/merge-operations.md) |
| Use rerere for conflict resolution | [references/merge-operations.md](references/merge-operations.md) |
| Add/update/manage submodules | [references/submodules.md](references/submodules.md) |
| Multi-repo project architecture | [references/submodules.md](references/submodules.md) |
| Reset, revert, restore operations | [references/advanced-operations.md](references/advanced-operations.md) |
| Interactive rebase, squashing | [references/advanced-operations.md](references/advanced-operations.md) |
| Stashing, tags, hooks | [references/advanced-operations.md](references/advanced-operations.md) |
| Recover lost commits/branches | [references/recovery.md](references/recovery.md) |
| Troubleshoot common errors | [references/recovery.md](references/recovery.md) |
| Command cheat sheet | [references/recovery.md](references/recovery.md) |

## Critical Knowledge

### The `-X ours` vs `-s ours` Trap

```bash
# -X ours: Prefer our changes ONLY IN CONFLICTS
git merge -X ours feature
# ↑ Merges all non-conflicting changes from feature

# -s ours: IGNORE EVERYTHING from other branch
git merge -s ours feature
# ↑ Keeps our tree exactly, just records the merge
```

### Conflict Style Recommendation

```bash
git config --global merge.conflictStyle zdiff3
```

Shows base version in conflicts, making resolution clearer:
```
<<<<<<< HEAD
our version
||||||| merged common ancestor
original version
=======
their version
>>>>>>> feature
```

### Branch Can Only Exist in One Worktree

A branch can only be checked out in ONE worktree. To work on it elsewhere:
```bash
git worktree add -b feature-copy ../feature-copy feature  # Create copy
```

### Submodules Default to Detached HEAD

After `git submodule update`, always checkout a branch before making changes:
```bash
cd submodule-dir
git checkout main  # Then make changes
```
