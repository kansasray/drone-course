# drone-course

**`kansasray/gym-course`(自有框架 fork)的 clone,放一門課:`courses/drone/`「無人機之路」。** 框架負責建置稽核驗證部署;課程內容全在 `courses/drone/`;`courses/gym/` 是上游對照範例不要動。

課程:台灣民航局操作證導向,3 部 9 章(法規與考證/飛行操作/空拍與應用)、21 單元 57 支影片、6 小時 19 分。中文主軸,災防應用章(CH9)全英文(中文搜救熱像/測繪為零)。不建 citations、不宣告 grades。

## 指令
```bash
COURSE=courses/drone make build audit verify
COURSE=courses/drone COOKIES_BROWSER= uv run python src/build/fetch_meta.py
```

## 這門課的特殊紀律(改動前必讀)

1. **法規正在活動中**:策展期間就遇到 2026-07-18 禁航區大幅擴增。每支法規影片標上傳日期+「以民航局現況為準」;CH2 直接收了那則新聞當時效教材。補片時延續這個紀律。
2. **民航局官方素材**:官方頻道「宣導短片」的 10 支術科示範是 CH3 骨幹(kind: official)。
3. **唯一留白**:禁飛區查詢工具教學全網查無介面現行版本(CH2-u2),note 記錄了 DJI 地理圍籬與政府禁航系統是兩套的區別。
4. **低觀看刻意收錄**:CH3 一支 14 次觀看的學科指南(全網僅存的系統性內容之一),audit 警告已知。
5. **DJI 內容的過時對策**:教操作邏輯不背選單位置;每支標示範機型與年代;產品模式名(QuickShots/Sport)保留英文不自譯。
6. **中國內容界線**:制度類(CAAC/實名登記)排除;純操作技術(HeyDrones 等)可收,HeyDrones 全課佔 14% 在門檻內。
7. **倫理線**:真實災難新聞畫面不收(一支含颶風倖存者證詞的候選被棄用)。

## 派工陷阱(本課踩過)
- config 的 unitTypes 我最初只定義 reg/skill/application,派工 prompt 卻寫了 concept → agent 自行加了 `concept:"原理"` 並回報;requireAssessment 已補 concept。**派工前 unitTypes 與 prompt 要對齊。**
- tight/weak 欄位再次被誤用(CH3),已併回 assessment;所有 prompt 現在都帶明確禁令。

## 框架陷阱
同 atak/pilot/firstaid/hamradio 清單。

## 狀態(2026-08-10 完成)
- **verify 57/57、audit 0 錯誤 2 警告(留白+低觀看,皆已知)、89 tests**;零跨章重複;HeyDrones 最高 14%
- **已上線 https://drone-course.pages.dev**(Pages 專案 drone-course)
- **GitHub**:kansasray/drone-course(public,Discussions 已開,giscus 已填待裝 App)
