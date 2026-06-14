# Gemini Project Instructions

## 專案目的

本專案製作可發布至 YouTube 的繁體中文連載有聲書。主要產出包含作品設定、可直接朗讀的分章稿、生圖提示詞、影片包裝與影音素材。

## 基本規則

- 開始工作前，先閱讀目標作品的 `README.md` 與 `novel-bible/`。
- 每部作品直接放在專案根目錄的獨立 `作品名稱/`。
- `chapters/chXXX.md` 是唯一正式文字稿，必須可直接用於 TTS 或錄音。
- `chapters/` 一章一檔；不得建立閱讀版、完整合併稿或重複的朗讀稿。
- 生圖提示詞與 YouTube 包裝依章分別保存，例如 `ch001-prompts.md` 與 `ch001-youtube.md`。
- 不擅自修改既有角色設定、時間線、能力限制或使用者變更。

## 標準結構

```text
作品名稱/
  README.md
  novel-bible/
  chapters/
    ch001.md
    ch002.md
  image-prompts/
  youtube/
  assets/
    thumbnails/
    generated-images/
    audio/
    video/
```

## 編碼與安全

- 所有文字檔使用 UTF-8，預設語言為繁體中文。
- 章號使用三位數；每個章節檔只能有一個章節。
- 不提交密碼、Token、API Key、Cookie、私鑰或 `.env`。
- 大型影音檔使用 Git LFS 或外部儲存服務。
- 專業、求生、急救或災害資訊在正式發布前必須查證可靠來源。

## Gemini Skills

依任務載入 `.gemini/skills/` 中的對應技能：

- `plan-serial-novel`：作品企劃與大綱
- `write-serial-chapter`：可直接朗讀的單章稿
- `create-story-image-prompts`：每章生圖提示詞
- `package-youtube-episode`：每章 YouTube 包裝
- `audit-serial-continuity`：連載品質與設定檢查
- `manage-git`：安全執行 Git 操作
