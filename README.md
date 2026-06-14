# YouTube 有聲書與影像內容專案

本專案用於製作適合 YouTube 發布的繁體中文連載有聲書，整合作品設定、可直接朗讀的分章文字稿、AI 生圖提示詞、縮圖素材與影片包裝資料。

## 專案內容

- `AGENTS.md`：專案共通規則與作品目錄標準。
- `GEMINI.md`：Gemini CLI 專案指引與技能路由。
- `黑雨斷城/`：獨立有聲書作品，包含故事 Bible、分章稿、角色、時間線與製作資料。
- `末日重生_我的庇護所無限升級/`：依章拆分的末日系統流有聲書作品。
- `.gitlab-ci.yml`：既有 GitLab CI 安全檢查設定。若改用其他 Git 平台，可依需求保留、調整或移除。
- `.codex/skills/`、`.gemini/skills/`：企劃、寫作、生圖、YouTube 包裝與品質檢查技能。

## 作品目錄規範

每部作品應使用獨立目錄，避免角色、設定與素材互相混用：

```text
作品名稱/
  README.md
  novel-bible/       # 世界觀、角色、劇情大綱、時間線
  chapters/
    ch001.md         # 第一章可直接朗讀的正式稿
    ch002.md         # 第二章可直接朗讀的正式稿
  image-prompts/
    ch001-prompts.md
  youtube/
    ch001-youtube.md
  assets/
    thumbnails/
    generated-images/
    audio/
    video/
```

每部作品直接放在專案根目錄。`chapters/` 必須一章一檔，每個 `chXXX.md` 只能包含一章，且該檔就是可直接用於 TTS 或錄音的正式稿。不建立閱讀版、完整合併稿或重複的朗讀稿。

檔名使用小寫英文與三位數章號，例如 `ch001.md`、`ch001-prompts.md`。大型影音檔不宜直接提交至一般 Git 儲存庫，建議使用 Git LFS 或外部物件儲存服務。

## 建議工作流程

1. 在 `novel-bible/` 完成作品定位、角色與主線大綱。
2. 在 `chapters/` 逐章撰寫可直接朗讀的正式稿，不合併多章。
3. 將生圖提示詞與 YouTube 資料按章保存於各自目錄。
4. 使用專案技能檢查鉤子、爽點、懸念、連續性與朗讀流暢度。
5. 提交前執行：

```bash
git status --short
git diff --check
git diff
```

## GitHub 倉庫

本專案目前使用以下 GitHub 遠端倉庫：

```text
https://github.com/Alex5025/youtube_novel_and_photo
```

第一次下載專案：

```bash
git clone https://github.com/Alex5025/youtube_novel_and_photo.git
cd youtube_novel_and_photo
```

既有本機倉庫可使用以下指令確認連線：

```bash
git remote -v
git branch --show-current
```

提交、同步、分支與衝突處理可使用專案內的 `manage-git` 技能。

## 內容與安全注意事項

- 不要提交 API Key、密碼、Token、Cookie 或未公開的私人資料。
- 正式發布求生、急救或災害應變內容前，應以可靠官方來源再次查證。
- 提交前確認素材授權，避免加入來源不明的圖片、音樂、字型或影片。
