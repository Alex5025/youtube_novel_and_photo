---
name: manage-git
description: Safely inspect and operate Git repositories, including status review, staging, commits, branches, remotes, pull/rebase, push, conflict resolution, and history inspection. Use when the user asks to commit or push changes, connect or replace a remote, create or switch branches, synchronize repositories, explain Git state, resolve conflicts, undo staging, or diagnose Git errors.
---

# Git 版本管理

## 核心原則

- 執行任何變更前，先檢查倉庫狀態。
- 保留使用者現有修改，不撤銷與任務無關的內容。
- 只暫存本次任務涉及的明確路徑，不預設執行 `git add .`。
- 優先使用非互動式 Git 指令。
- 除非使用者指定其他語言，使用繁體中文說明操作與結果。
- 不輸出遠端網址或設定中可能包含的密碼、Token 或其他憑證。

## 操作前檢查

依任務執行必要的唯讀檢查：

```bash
git status --short
git branch --show-current
git remote -v
git log -8 --oneline
git diff --stat
git diff --cached --stat
```

若存在 `README.md`、`AGENTS.md`、`GEMINI.md`、`GIT_GUIDE.md` 或貢獻指南，先閱讀相關規則。確認：

1. 哪些變更屬於本次任務。
2. 是否存在使用者或其他工作留下的修改。
3. 目前分支是否追蹤遠端分支。
4. 操作是否會改寫已分享的歷史。

## 暫存與提交

先檢閱差異，再暫存明確路徑：

```bash
git add path/to/file another/file
git diff --cached --check
git diff --cached --stat
git commit -m "類型：簡短說明"
```

沿用倉庫既有提交風格。本專案優先使用簡短的繁體中文訊息：

- `內容：新增第一章正文`
- `設定：更新角色與時間線`
- `文件：補充 Git 操作說明`
- `修正：調整章節順序`

除非使用者要求，或提交是本次任務剛建立且尚未分享，否則不要 amend 既有提交。

## 遠端管理

新增或修改遠端前先檢查：

```bash
git remote -v
git remote get-url origin
```

依目前狀態選擇正確操作：

```bash
git remote add origin <url>
git remote set-url origin <url>
git remote remove origin
```

說明移除 remote 只會解除本機連線，不會刪除本機提交歷史或雲端倉庫。

## 分支與同步

使用描述性名稱建立工作分支：

```bash
git switch -c content/ch001
git push -u origin content/ch001
```

拉取前，先確認本機修改已提交或已明確暫存。一般情況優先使用：

```bash
git pull --rebase origin main
```

不要在未確認狀態與使用者意圖前 rebase 共用分支。首次推送並設定 upstream：

```bash
git push -u origin main
```

## 衝突處理

發生 merge 或 rebase 衝突時：

1. 執行 `git status` 找出所有衝突檔案。
2. 閱讀衝突雙方內容，保留正確的使用者修改。
3. 完成內容整合後才移除衝突標記。
4. 使用 `git add <path>` 標記已解決。
5. 執行 `git rebase --continue` 或完成 merge commit。
6. 推送前執行專案驗證。

無法可靠判斷時，使用 `git rebase --abort` 或 `git merge --abort`，不要猜測內容。

## 安全復原

一般修正優先使用非破壞性指令：

```bash
git restore --staged <path>
git stash push -m "工作說明"
git stash list
```

沒有使用者明確同意與遺失範圍說明時，不得執行 `git reset --hard`、`git clean -fd`、破壞性 `git restore`、刪除分支或強制推送。確實需要改寫個人分支時，優先使用 `git push --force-with-lease`，不要使用 `--force`。

## 驗證與回報

操作完成後執行適當檢查：

```bash
git diff --check
git status --short
git log -3 --oneline
git remote -v
```

若有推送，回報遠端、分支與 commit hash。若因驗證、身分認證、網路、衝突、hook 或 CI 無法完成，清楚說明實際阻礙。
