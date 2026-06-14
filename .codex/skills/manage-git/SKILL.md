---
name: manage-git
description: Safely inspect and operate Git repositories, including status review, staging, commits, branches, remotes, pull/rebase, push, conflict resolution, and history inspection. Use when the user asks to commit or push changes, connect or replace a remote, create or switch branches, synchronize repositories, explain Git state, resolve conflicts, undo staging, or diagnose Git errors.
---

# Manage Git

## Operating Principles

- Inspect the repository before changing it.
- Preserve user changes and unrelated work.
- Match the user's requested scope; do not stage everything by default.
- Prefer non-interactive commands.
- Explain consequential operations in Traditional Chinese unless the user requests another language.
- Never expose credentials embedded in remote URLs or configuration output.

## Inspect First

Run the relevant read-only checks before acting:

```bash
git status --short
git branch --show-current
git remote -v
git log -8 --oneline
git diff --stat
git diff --cached --stat
```

Also inspect `README.md`, `AGENTS.md`, `GIT_GUIDE.md`, or repository-specific contribution files when they exist. Determine:

1. Which changes belong to the request.
2. Whether unrelated or user-authored changes are present.
3. Whether the branch tracks a remote branch.
4. Whether the requested operation rewrites shared history.

## Stage and Commit

Review changes before staging. Stage explicit paths:

```bash
git add path/to/file another/file
git diff --cached --check
git diff --cached --stat
git commit -m "類型：簡短說明"
```

Follow the repository's existing commit style. For this project, prefer concise Traditional Chinese messages:

- `內容：新增第一章正文`
- `設定：更新角色與時間線`
- `文件：補充 Git 操作說明`
- `修正：調整章節順序`

Do not amend an existing commit unless the user asks or the commit was created during the current task and has not been shared.

## Manage Remotes

Inspect before adding or changing a remote:

```bash
git remote -v
git remote get-url origin
```

Use the operation matching the current state:

```bash
git remote add origin <url>
git remote set-url origin <url>
git remote remove origin
```

Clarify that removing a remote only disconnects the local repository. It does not delete local history or the cloud repository.

## Branch and Synchronize

Create focused branches with descriptive names:

```bash
git switch -c content/ch001
git push -u origin content/ch001
```

Before pulling, ensure local work is committed or intentionally stashed. Prefer:

```bash
git pull --rebase origin main
```

Do not rebase a shared branch without checking its state and the user's intent. Push with upstream setup when needed:

```bash
git push -u origin main
```

## Handle Conflicts

When a merge or rebase conflicts:

1. Run `git status` and identify every conflicted file.
2. Read both sides and preserve intended user changes.
3. Remove conflict markers only after resolving content correctly.
4. Stage resolved files with `git add <path>`.
5. Continue with `git rebase --continue` or complete the merge commit.
6. Run project validation before pushing.

Use `git rebase --abort` or `git merge --abort` when cancellation is safer than guessing.

## Undo Safely

Use non-destructive commands for routine correction:

```bash
git restore --staged <path>
git stash push -m "工作說明"
git stash list
```

Never run `git reset --hard`, `git clean -fd`, destructive `git restore`, branch deletion, or force push without explicit user approval and a clear explanation of what would be lost. Prefer `git push --force-with-lease` over `--force` when rewriting a personal branch is explicitly required.

## Verify and Report

After modifications, run appropriate checks:

```bash
git diff --check
git status --short
git log -3 --oneline
git remote -v
```

For a push, report the remote, branch, and commit hash. State clearly if authentication, network access, conflicts, hooks, or CI prevented completion.
