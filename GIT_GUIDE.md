# Git 操作手冊

本手冊適用於本專案的版本管理，以及 GitHub 遠端的設定與日常操作。

## 目前狀態

本專案的主要分支為 `main`，目前綁定以下 GitHub 遠端：

```text
https://github.com/Alex5025/youtube_novel_and_photo.git
```

可用以下指令確認：

```bash
git branch --show-current
git log --oneline -5
git remote -v
```

`git remote -v` 應顯示 `origin` 的 fetch 與 push 網址。

## 綁定新的遠端倉庫

本專案已完成綁定，不需要再次執行 `git remote add`。若在另一份尚未設定遠端的本機倉庫操作，可執行：

```bash
git remote add origin https://github.com/Alex5025/youtube_novel_and_photo.git
git branch -M main
git push -u origin main
```

GitHub 常見網址格式：

```text
SSH:   git@github.com:Alex5025/youtube_novel_and_photo.git
HTTPS: https://github.com/Alex5025/youtube_novel_and_photo.git
```

確認設定：

```bash
git remote -v
git remote get-url origin
```

若網址設錯，不必移除歷史，直接修改：

```bash
git remote set-url origin <正確網址>
```

## 日常提交流程

```bash
git status
git diff
git add README.md GIT_GUIDE.md
git commit -m "文件：更新專案與 Git 操作說明"
git push
```

使用 `git add .` 前先執行 `git status`，避免把大型影音、憑證或暫存檔一起提交。提交訊息應簡短說明目的，例如：

- `內容：新增黑雨斷城第一章`
- `設定：補充角色與時間線`
- `文件：更新作品目錄規則`
- `修正：調整第三章時間順序`

## 取得與同步變更

第一次下載倉庫：

```bash
git clone https://github.com/Alex5025/youtube_novel_and_photo.git
cd youtube_novel_and_photo
```

開始工作前同步遠端：

```bash
git pull --rebase origin main
```

`--rebase` 可避免產生不必要的合併提交，但執行前應先提交或暫存本機變更。

## 分支作業

較大的作品或結構調整建議使用獨立分支：

```bash
git switch -c content/black-rain-ch001
git push -u origin content/black-rain-ch001
```

完成審查與合併後，切回主分支並同步：

```bash
git switch main
git pull --rebase origin main
git branch -d content/black-rain-ch001
```

## 暫存未完成工作

```bash
git stash push -m "暫存第一章修改"
git stash list
git stash pop
```

使用 `stash pop` 後應立即檢查 `git status`，確認是否發生衝突。

## 衝突處理

拉取或 rebase 時若發生衝突：

1. 執行 `git status` 查看衝突檔案。
2. 編輯檔案並移除 `<<<<<<<`、`=======`、`>>>>>>>` 標記。
3. 執行 `git add <檔案>` 標記為已解決。
4. rebase 流程執行 `git rebase --continue`；一般合併則執行 `git commit`。

需要取消尚未完成的 rebase，可執行：

```bash
git rebase --abort
```

## 常用檢查與修復

```bash
git diff --check             # 檢查多餘空白
git log --oneline --graph    # 查看提交歷史
git restore --staged <檔案>  # 取消暫存，不刪除修改
git commit --amend           # 修正最近一次尚未分享的提交
```

不要對已分享的 `main` 使用 `git push --force`。若確實需要改寫個人分支歷史，優先使用 `git push --force-with-lease`，並先確認不會覆蓋他人的工作。

## 大型檔案與機密

- 音訊、影片與大量生成圖片建議使用 Git LFS 或外部儲存服務。
- 不得提交 API Key、Token、密碼、Cookie、私鑰或 `.env`。
- 若機密已提交，僅刪除檔案不足以清除歷史；應立即撤銷憑證並進行 Git 歷史清理。
