# YouTube 小說與影像內容專案

本專案用於製作適合 YouTube 發布的繁體中文連載小說，整合故事設定、章節正文、TTS 朗讀稿、AI 生圖提示詞、縮圖素材與影片包裝資料。

## 專案內容

- `AGENTS.md`：章回爽文生產規格，包含節奏、格式、品質檢查與 YouTube 包裝原則。
- `novels/`：已整合或輸出的完整小說與有聲書文字檔。
- `黑雨斷城/`：獨立作品目錄，包含故事 Bible、角色、時間線、求生知識與章節規劃。
- `.gitlab-ci.yml`：既有 GitLab CI 安全檢查設定。若改用其他 Git 平台，可依需求保留、調整或移除。
- `GIT_GUIDE.md`：本專案的 Git 日常操作與更換遠端教學。

## 作品目錄規範

每部作品應使用獨立目錄，避免角色、設定與素材互相混用：

```text
作品名稱/
  README.md
  novel-bible/       # 世界觀、角色、劇情大綱、時間線
  chapters/          # 小說正文，例如 ch001.md
  audio-scripts/     # TTS 朗讀稿，例如 ch001-tts.md
  image-prompts/     # AI 生圖提示詞
  youtube/           # 標題、簡介、縮圖文字、Hashtags
  assets/
    thumbnails/
    generated-images/
    audio/
    video/
```

檔名使用小寫英文與三位數章號，例如 `ch001.md`、`ch001-prompts.md`。大型影音檔不宜直接提交至一般 Git 儲存庫，建議使用 Git LFS 或外部物件儲存服務。

## 建議工作流程

1. 在 `novel-bible/` 完成作品定位、角色與主線大綱。
2. 將正文、朗讀稿、生圖提示詞與 YouTube 資料分開保存。
3. 依 `AGENTS.md` 的品質清單檢查鉤子、爽點、懸念與 TTS 可讀性。
4. 提交前執行：

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

提交、同步、分支與衝突處理方式請閱讀 [GIT_GUIDE.md](GIT_GUIDE.md)。

## 內容與安全注意事項

- 不要提交 API Key、密碼、Token、Cookie 或未公開的私人資料。
- 正式發布求生、急救或災害應變內容前，應以可靠官方來源再次查證。
- 提交前確認素材授權，避免加入來源不明的圖片、音樂、字型或影片。
