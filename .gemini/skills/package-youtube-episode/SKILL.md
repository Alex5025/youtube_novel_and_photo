---
name: package-youtube-episode
description: Package serialized fiction episodes for YouTube with compelling Traditional Chinese titles, thumbnail text, descriptions, hashtags, pinned comments, and next-episode hooks. Use when preparing an episode upload, improving click-through presentation, creating metadata variants, or turning a chapter into publish-ready YouTube copy.
---

# YouTube 小說分集包裝

## 工作流程

1. 一次讀取一個 `作品名稱/chapters/chXXX.md` 與作品定位，找出本集最大衝突、身份反差、情緒回報與下一集懸念。
2. 包裝必須準確反映內容，不承諾章節中不存在的事件。
3. 使用繁體中文，避免堆砌關鍵字、過度驚嘆號與誤導式標題。

## 標題

提供三至五個候選，結合衝突、反差、回報及懸念。優先把最具體的事件或代價放在前半段。系列名稱與集數格式依作品既有規則保持一致。

## 縮圖文字

提供三個版本，每個約四至八個中文字。文字要短、可辨識、有情緒，但不要完整重複標題。同步給出畫面主體、表情與留白位置建議。

## 簡介與互動

影片簡介包含：本集看點、主角困境、主要回報、下一集鉤子及自然的訂閱提醒。避免提前揭露結尾全部答案。

Hashtags 使用少量且直接相關的標籤，例如作品名、題材、有聲小說與小說連載。置頂留言提出一個與本章選擇或懸念相關的具體問題，引導留言，不使用空泛誘導。

## 輸出格式

```markdown
# 第 XXX 章 YouTube 包裝
## 標題候選
## 縮圖文字與畫面建議
## 影片簡介
## Hashtags
## 置頂留言
```

完成後檢查標題、縮圖與簡介是否一致，並確認沒有劇透錯章、角色名錯誤或不實宣稱。

將結果存為同章號的 `作品名稱/youtube/chXXX-youtube.md`，不要把多章包裝合併在同一文件。
