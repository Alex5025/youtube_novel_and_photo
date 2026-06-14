---
name: create-story-image-prompts
description: Create consistent AI image prompts from serialized fiction chapters, including scene selection, character appearance, composition, lighting, camera language, aspect ratio, and negative prompts. Use when generating story illustrations, episode visuals, thumbnails, character sheets, scene prompts, or maintaining visual continuity across chapters.
---

# 小說生圖提示詞

## 準備

一次讀取一個 `作品名稱/chapters/chXXX.md`、角色設定與既有視覺規範。輸出至對應的 `作品名稱/image-prompts/chXXX-prompts.md`。為主要角色整理固定特徵：年齡感、髮色、瞳色、臉型、服裝、武器或標誌物、氣質與主色調。後續每張圖都沿用，不因場景任意漂移。

## 選圖原則

每章預設至少四張：

1. 開場危機或鉤子
2. 主角關鍵行動或高光
3. 反派、衝突或重要轉折
4. 章末懸念

長影片可增加場景轉場、角色半身、道具、地圖、勢力或縮圖專用畫面。避免多張圖只更換背景而沒有敘事功能。

## 每張提示詞

包含場景、角色固定外觀、姿態、情緒、關係、重要道具、光影、鏡頭、構圖、畫風、色調、細節程度與比例。預設影片畫面使用 `16:9`，縮圖需預留短文字區域。

```markdown
### 圖 X：畫面用途
- 中文描述：
- English Prompt：
- Negative Prompt：low quality, blurry, bad anatomy, extra fingers, text, watermark, logo
```

英文 prompt 應是可直接使用的完整描述，不只是中文逐字翻譯。負面提示詞依模型與畫面調整。

## 安全與一致性

不要指定模仿在世藝術家的獨特風格，不使用未授權角色或商標。避免露骨性內容、過度血腥或危險行為教學畫面。完成後比對所有人物特徵、服裝時代、時間、天氣、傷勢與道具是否符合章節。
