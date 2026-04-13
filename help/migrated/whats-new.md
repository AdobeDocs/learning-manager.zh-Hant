---
description: 在 2026 年 4 月版本的 Adobe Learning Manager 中，了解新功能與增強功能，包括 API 與 webhook 的變更
jcr-language: en_us
title: Adobe Learning Manager 2026 年 4 月發布的新內容
exl-id: da46f186-3ff3-422a-af49-31c7405fd584
source-git-commit: 971a9c79fc2b831b990e30a44a2eeab5d5c5ce63
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 0%

---

# Adobe Learning Manager 2026 年 4 月發布的新內容

**給學習者：** 流體玩家現在會顯示下一個模組名稱和一個清晰的退出按鈕。 玩家語言可以透過 LTI 設定，以實現跨平台的一致體驗。 自訂參數名稱為「locale」，並接受區域代碼。 例如，locale=fr-FR。 Captivate 內容包含統一的目錄、投影片層級的完成記號，以及可靠的筆記匯出。 提供多語言支援，涵蓋工作輔助工具、檢查清單問題及視訊文字軌（VTT）。 AI 助理幫助學習者在學習過程中獲得答案。

**給管理員和作者：** Zoom 連接器支援多個並行的 VILT 會話。 同儕帳號中的共享課程會顯示真正的作者，而不是「外部作者」。 管理員可以限制模組的啟動時間。 學習物件的到期日會在學習者 API 中揭露。 檢查清單模組支援加權評分、多語言題目文本及可選的評審意見。 自訂憑證提供拖放編輯器，具備動態欄位與 AI 生成背景。 未登入的經驗建構器讓你可以在不登入的情況下建立公開學習頁面。

**給講師：** 產生 QR 碼，例如報名和出席次數。 在檢查清單評估時加入意見或回饋。

**報告與分析：** SCORM 內容現在可以在 L2 報告中回報多次小考嘗試。 學習者成績單的學習時間計算有所提升。 管理員的學習成績單報告已更新。 提供進階搜尋增強功能。

**登入方式：** 學習 Adobe Learning Manager 中 OpenID Connect 登入的運作方式，供學習者、作者與管理員使用。 OpenID Connect（OIDC）是一種基於網路標準建立的常見登入方式。 許多組織使用一個身份提供者（例如 Okta、Google Workspace 或 Microsoft Entra ID），供員工與合作夥伴使用。

欲了解更多資訊，請參閱 [使用 OIDC](/help/migrated/oidc.md) 登入。

## 網路鉤子與替代與等價裝置中的遷移

### Webhook

當學習者透過替代或關聯完成課程時，ALM 會觸發一個與標準課程完成 webhook 不同的 webhook 事件。 這確保整合能在需要時以不同方式回應替代完成。 當出現追溯性完成或追溯性未完成時，也會觸發 Webhook 事件，涵蓋歷史更新及關係變更。

欲了解更多資訊，請參閱 [Webhooks](/help/migrated/integration-admin/feature-summary/webhooks.md#webhooks-for-alternates) 。

### 遷徙

基於 CSV 的資料模型及引入學習對象（LO）等價性的遷移行為，詳見 [Webhooks](/help/migrated/integration-admin/feature-summary/migration-manual.md#migration-for-alternates-and-equivalents)。

## 自動清除已刪除使用者

自動清除已刪除使用者的功能，是用來清除已在 ALM 中刪除的使用者的資料。 清除是在可設定的保留期之後進行，重點放在批量作業上，讓大型客戶帳戶能有效率地處理而不影響效能。

更多資訊請參閱 [自動清除已刪除用戶](/help/migrated/administrators/feature-summary/purge-users.md#auto-purge-of-deleted-users) 。

## 設定模組存取時間控制

這項增強功能讓作者和管理員在 Adobe Learning Manager 中設定一個允許學習者開始模組的時間窗口。 在設定的開始/結束視窗之外，模組仍可見於課程結構中，但學習者無法啟動。

欲了解更多資訊，請參閱 [Set 模組存取時間控制](/help/migrated/administrators/feature-summary/module-access-time-control.md) 。

## 學習者成績單變更

此發布強化了學習成績單（LT）報告，提供更明確的審計性與合規支持。

* 管理員 LT 中的新完成方法欄位顯示完成是直接完成、替代或撤銷，而替代完成則依繼承來源訓練日期影響狀態、完成日期及完成來源，並在來源被撤銷或直接完成時更新。
* 撤銷的備用會在所有合格關係被移除且啟用追溯未完成時，自動調整狀態、完成日期及完成來源。
* 檢查清單模組的評審回饋已標準化於管理員與學習者 LT 及所有匯出管道中，統一於更名後的評審意見欄。
* 最後，學習時間計算現在能更好地區分活躍時間與閒置時間，提升參與度與合規報告的準確性。

欲了解更多資訊，請參閱 [學習者成績單報告](/help/migrated/administrators/feature-summary/reports/changes-in-learner-transcript.md) 變更。

## 附有評論功能給審稿人的檢查清單

此功能讓審稿人在檢查清單評估時能加入評論或回饋。 你可以為每位學習者提供個人化且可執行的回饋。 你也可以選擇在留言中顯示你的名字以保持透明。 所有備註都會儲存在學習者的成績單中，並包含在檢查表報告中。

查看 [配置檢查清單並附](/help/migrated/authors/feature-summary/courses.md#checklist-with-commenting) 註解以獲取更多資訊。

## 多語言清單支援

此功能允許您建立並管理多種語言的檢查清單模組。 每個檢查清單問題、教學與評量標準都能翻譯，讓審查者與學習者以偏好語言與檢查表互動。 系統以使用者選擇的內容語言顯示檢查清單，提升全球團隊的無障礙性與合規性。

檢視 [建立多語言清單 在模組中](/help/migrated/authors/feature-summary/courses.md#create-a-multi-language-checklist)

## 教師評鑑的檢查題權重清單

此功能允許你為每個檢查表問題分配不同的最高分數（權重）。 你可以反映每題重要性或難度的不同，這有助於更準確且有意義的評估。 系統會根據你的輸入計算總分，並根據你設定的標準判斷學習者是否通過或不及格。

檢視 [建立加權清單問題](/help/migrated/authors/feature-summary/courses.md#how-to-create-a-weighted-checklist)

## 自訂憑證

Adobe Learning Manager （ALM） 中的自訂憑證讓管理員與作者設計、管理並發行個人化的學習者憑證。

此功能包含拖放編輯器、動態欄位、多語言支援及 AI 生成背景，使組織能在不需技術專業的情況下建立品牌證書。

查看 [設計自訂證書](/help/migrated/administrators/feature-summary/create-customize-certificate.md)

## 未登入經驗建構器

Experience Builder 的非登入體驗讓組織能向所有訪客（包括尚未登入者）展示其學習內容與入口頁面。 此功能旨在吸引、告知並吸引潛在學習者，透過在要求他們登入或註冊前，提供流暢且具品牌特色的培訓預覽。

在 Experience Builder 中查看 [未登錄的經驗](/help/migrated/administrators/feature-summary/experience-builder/non-logged-in-experience.md)

## 進階搜尋增強功能

進階搜尋的搜尋結果現在更準確且相關。 精確的關鍵字匹配在內容內搜尋和元資料中排名較高，讓學習者更容易找到他們真正想要的內容。

學習者現在也能在搜尋結果中看到已註冊的學習物件，即使它們不屬於無障礙目錄，確保不會遺漏相關內容。 此外，Job Aid 在進階搜尋與內容內搜尋的排名也有所提升，能更快呈現最相關的資源。

## 多語言工作輔助工具

Adobe Learning Manager （ALM） 中的多語言工作輔助工具，讓作者與管理員能在同一工作輔助工具條目中，以多種語言提供支持文件、指南或資源。 不同地區的學習者都能以偏好語言取得相關教材，提升理解力、合規性及使用者體驗。

查看 [新增多語言工作輔助工具](/help/migrated/authors/feature-summary/job-aids.md#create-a-multilingual-job-aid) 以獲取更多資訊。

## 多語言影片文字軌（VTT）支援（作者使用）

Adobe Learning Manager 的多語言影片文字軌（VTT）支援，讓作者能為多語言的影片與音訊內容提供字幕與字幕。 此功能簡化了在地化流程，使培訓對全球受眾開放，並確保符合無障礙標準。 作者可直接在平台上自動生成、翻譯、審查及編輯 VTT 檔案。

欲了解更多資訊，請參閱 [多語言 VTT 支援](/help/migrated/authors/feature-summary/content-library.md#multi-lingual-vtt-support) 。

## 在同儕帳號中顯示共享課程的原始作者

當課程透過目錄分享給同儕帳號時，Adobe Learning Manager 目前會在接收帳號的學習者、管理員和作者檢視中，將作者標示為「外部作者」。 這對學習者與管理者來說，尤其在大型企業中，會帶來挑戰，因為當出現問題或問題時，很難辨識並聯繫適當的內容擁有者。

此強化確保作者資訊能被保留並顯示於同儕帳號中的共享課程，而非被通用的佔位符取代。

### 有什麼新鮮事

在同儕帳號中顯示共享課程的實際作者名稱

對於透過外部或同儕目錄分享的課程，接收帳號中會顯示原始作者名稱，而非「外部作者」。

這適用於：

* 學習者應用程式（課程卡或課程詳情）。
* 作為學習者預覽時的管理員與作者觀點。

查看 [共用課程](/help/migrated/administrators/feature-summary/peer-account.md#author-name-display-for-shared-courses-including-previously-acquired-courses) 的作者名稱顯示以獲取更多資訊。

## 對應與替代

提供無阻礙的學習體驗，並消除ALM中等價與替代課程的重複訓練。 這項新功能允許管理員設定單向（替代）或雙向（等效）規則，完成一個訓練會自動授予另一個訓練的替代完成。 此功能旨在簡化大型學習生態系統，確保學習者繞過已掌握的內容，組織大幅減少管理員支援工單，消除手動覆蓋，並維持更乾淨且準確的學習者紀錄。

欲了解更多資訊，請參閱[&#128279;](/help/migrated/administrators/feature-summary/alternates-equivalence.md)等效與替代。

## 講師的 QR 碼，例如報名和參加課程

教師可以自行產生 QR 碼用於：

* 課程實例註冊，
* 會議出席率，或
* 註冊人數+出席人數合計

在會議層級。 它設計用於學習者進入實體或混合教室，需要快速自助方式註冊並使用 QR 碼記錄出勤的情況。

請參閱 [下載QR碼，以獲取學習者註冊及出席](/help/migrated/instructors/feature-summary/learners.md#download-qr-codes-for-learner-enrollment-and-attendance) 資訊。

## 具有會議連結的行事曆邀請（ICS）

Adobe Learning Manager 直接在發送給學習者和講師的行事曆邀請（ICS 檔案&#x200B;**）中加入**&#x200B;會話連結。這讓參與者能直接從行事曆加入會議，無需搜尋會議電子郵件。

這項改進提升了 Gmail **和** Outlook **等行事曆用戶端**&#x200B;的使用體驗。

請參閱 [帶有會議連結](/help/migrated/instructors/feature-summary/learners.md#joining-a-session-from-gmail) 的行事曆邀請函以獲取更多資訊。

## 學習者的 AI 助理

AI 助理（Beta）幫助學習者快速從指定的學習內容中找到答案，無需瀏覽整門課程。 你可以用淺顯易懂的語言提問，並獲得準確且聚焦的回答，並附有相關課程內容的來源連結。

隨著功能演進，功能、支援情境及限制可能會有所變化。 AI 助理是 Adobe Learning Manager 中由 AI 驅動的生成聊天夥伴，能利用您信賴的學習內容快速且準確地回答。 它包含引用，讓你隨時知道資訊來源。

查看 [學習者 AI 助理](/help/migrated/learners/feature-summary/learner-ai-assistant.md)


## API 版本中的變更

2026 年 4 月的 Adobe Learning Manager 版本針對公開 API 進行了針對替代方案與等效功能的專注強化，包括內容時窗存取、內容導向測驗嘗試、非登入體驗，以及職業輔助處理。 這些變更設計上大致向下相容，同時允許更精確的整合。

查看 [四月版本中的 API 變更](/help/migrated/api-changes-alm.md)

## 系統需求

查看 [Adobe Learning Manager 系統需求](/help/migrated/system-requirements.md)。

## 發行說明

請 [查看最新發行公告](/help/migrated/release-note/release-notes.md) 。

## Adobe Learning Manager 先前版本

* [Adobe Learning Manager 2025 年 10 月版本](/help/migrated/whats-new-october-2025.md)
* [Adobe Learning Manager 2025 年 5 月版本](/help/migrated/whats-new-may-2025.md)
