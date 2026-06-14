---
name: audit-serial-continuity
description: Audit serialized audiobook chapters for continuity, pacing, hooks, payoffs, character progression, timeline consistency, unresolved foreshadowing, resource tracking, narration readiness, and one-chapter-per-file compliance. Use when reviewing chapters, checking every ten chapters, diagnosing weak retention, finding contradictions, or preparing a revision plan.
---

# 連載品質與連續性檢查

## 檢查來源

讀取作品 Bible、角色、時間線、劇情大綱、相關章節及既有製作檔。以檔案中的明確設定為證據，不憑印象判斷。發現衝突時指出檔案與內容，不直接改寫，除非使用者要求修正。

## 單章檢查

- 前 300 字內是否有鉤子或明確問題？
- 主角是否承受具體壓力並作出選擇？
- 中段是否持續增加衝突、資訊或代價？
- 是否有可辨識的情緒回報與狀態變化？
- 反派和配角是否具備合理動機與行動能力？
- 是否避免長篇設定說明與角色無腦降智？
- 章末是否產生下一章需求？
- 內容是否可直接朗讀，且沒有不應被讀出的製作註記？
- `chapters/chXXX.md` 是否只包含一章，且不存在重複的閱讀版、完整合併稿或 TTS 複本？

## 連載檢查

每十章或每卷整理：

- 主角能力、資源、身份與關係的最新狀態
- 已埋、已回收、逾期未處理的伏筆
- 敵人狀態、配角立場與未完成承諾
- 時間、地點、傷勢、道具和資源數量矛盾
- 爽點或衝突是否重複，升級幅度是否失衡
- 下一階段是否需要新目標、場景、敵人或代價

## 回報格式

先列最嚴重且可行動的問題，再列一般改善項目：

```markdown
# 檢查結果
## 嚴重問題
## 節奏與留存
## 設定與時間線
## 角色與伏筆
## 製作完整性
## 建議修正順序
```

每項問題說明「現象、影響、證據、建議」。若沒有發現問題，明確說明已檢查範圍與仍存在的風險，不虛構缺陷。
