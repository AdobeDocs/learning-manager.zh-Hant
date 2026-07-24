---
description: 在 2026 年 4 月版本的 Adobe Learning Manager 中，了解新功能與增強功能，包括 API 與 webhook 的變更
jcr-language: en_us
title: Adobe Learning Manager 2026 年 8 月版本的新內容
exl-id: da46f186-3ff3-422a-af49-31c7405fd584
source-git-commit: 558b239bd393c175384e6559559929d4d21ee131
workflow-type: tm+mt
source-wordcount: '2747'
ht-degree: 0%

---

# 2026 年 8 月版 Adobe Learning Manager 的新內容

>[!IMPORTANT]
>
>本文所述的功能已包含在測試版中。 Adobe Learning Manager 測試版功能僅供評估用途，且可在正式發行前進行修改、限制或移除。 功能名稱、行為及設定選項可能會隨時更改，恕不另行通知。


## 適應性課程

自適應課程讓你能根據學習者所屬的使用者群組，控制每個學習者看到哪些模組及哪些模組是必需的，來提供個人化訓練。 單一課程會自動動態地將正確的內容呈現給正確的人。

作者會為使用者群組規則設定每個模組 **為可選** 與 **強制** 。 不同使用者群的學習者可以完成完全不同的模組組合，但仍能完成相同的課程。 課堂與虛擬課堂課程的名額限制現已在模組層級強制執行，因此學習者可在特定課程的候補名單中註冊課程。 欲了解更多資訊，請參閱 [《適應性課程-作者》。](/help/migrated/authors/feature-summary/adaptive-course-author.md)

主要能力：

* 各使用者群組的模組層級可見性與完成規則
* OR 合併邏輯：如果任何一組將模組定為必修，該模組對該學習者來說就是必修的
* 課堂與虛擬課堂課程的模組層級候補名單
* 當學習者的個人資料變更時，會觸發刷新完成
* 在學習路徑與認證上獲得支持，並附有定期認證的書面限制

了解更多關於適應性課程的資訊。

## 成績簿

Adobe Learning Manager 中的成績簿為課程新增加權分數，讓作者能為每個評分模組分配貢獻百分比，並設定課程完成的最低總分。 學習者可在課程期間追蹤成績，管理員也能查看期末成績並下載相關成績單。

### 成績簿的功能

啟用成績簿的課程會根據各模組分配的權重百分比，將各個模組的分數合併計算，計算每位學習者的最終成績。 這提供了一個精確且加權的績效衡量，而非僅以成績加總或通過/不通過的標準。

Gradebook 支援兩種完成模式：

* **僅限**&#x200B;必修模組：課程在所有必修模組完成後即完成。 成績簿分數仍會計算並可見，但總分數不會影響及格標準。

* **必修模組加總分**：學習者必須完成所有必修模組，並取得達最低及格門檻或以上的總分。 這兩個條件都必須符合，才能通過。

### 課程成績的計算方式

每個可評分模組，對課程總分的貢獻為：

（取得的分數÷最高分）× 權重百分比 = 模組貢獻

課程總分為所有模組貢獻的總和。 所有可評分模組的權重百分比必須加起來正好為100。 在符合此條件之前，成績簿配置無法儲存。

課程總分為所有模組貢獻的總和。 所有可評分模組的權重百分比必須加起來正好為100。 在符合此條件之前，成績簿配置無法儲存。

評分標準不必在各模組間保持一致。 一個課堂課程（滿分100分）和一個SCORM模組（滿分10分）可以同時存在於同一本成績冊中。 公式在施加權重前會對每個貢獻進行正規化。

**可評分模組與不可評分模組**

只有產生分數的模組才有權重資格。 可評分模組類型包括：

* SCORM、AICC 和 xAPI 內容並啟用評分
* Captivate 內容包
* Adobe Learning Manager 中的原生測驗
* 課堂與虛擬課堂課程，由講師或行政人員輸入分數
* 由講師或行政人員評分的活動模組

非評分模組類型、PDF 檔案、影片檔案、音訊檔案、PowerPoint簡報、Word文件、Excel檔案及HTML內容，無法分配權重百分比，且不計入總分。 這些模組仍可能是完成課程的必要條件。 當啟用「包含不計入最終成績」的模組時，這些模組會出現在成績簿中，但不會有權重值。

欲了解更多資訊，請參閱 [作者成績冊](/help/migrated/authors/feature-summary/alm-author-gradebook.md)

## 階層式內容資料夾

內容庫現支援最多三層的私密資料夾階層。 管理員負責建立資料夾結構，並控制哪些自訂角色可以存取哪些第一層資料夾。 存取會自動串接到第一級資料夾內的所有子資料夾。

作者可以在資料夾間複製和移動內容，依資料夾篩選內容庫，並在新增模組時瀏覽層級結構。

主要能力：

* 最多可有三層巢狀（每個父層最多 25 個子資料夾）
* 僅在第一級時分配基於角色的存取權限
* 內容可以出現在多個資料夾中，且不會重複
* 公共資料夾與私人資料夾結構是互斥的
* 在課程編寫中選擇模組時，瀏覽資料夾的經驗

欲了解更多管理員層級功能的資訊，請參閱 [階層式內容資料夾](/help/migrated/administrators/feature-summary/settings/advanced-settings.md#content-folder)。 欲了解更多作者層級功能，請參閱 [階層式內容資料夾](/help/migrated/authors/feature-summary/content-library.md#add-content-to-a-folder)。

## 直播中心

Live Hub 是 Adobe Learning Manager 內建的 AI 虛擬培訓體驗，協助組織提供引人入勝且具影響力的即時學習。 透過 AI 投票、分組討論室協調、持續學習空間及 AI 輔助等智慧功能，Live Hub 大幅提升講師生產力，同時降低課程進行的複雜度。

重點摘要：

* 透過原生的 Adobe Learning Manager 體驗提升即時學習，提升教學品質與學習成果。
* 為你的講師提供一位由 AI 驅動的共同主持人，透過智慧投票、問答支持及分組討論區的洞見，推動參與度。
* 透過 AI 生成的摘要和可依主題搜尋的課程錄影，幫助學習者從每堂課中獲得更多收穫。
* 透過超越出席率、揭示真實學習參與度的參與度分析，衡量哪些重點。
* 協助作者使用AI驅動的教師搜尋器，依技能、可用時間、偏好時間、時區及目前使用情況匹配合適的教師。

## 元件式電子郵件範本建構器

組織現在可以使用現代的所見即所得元件編輯器，在 Adobe Learning Manager 中建立企業級的品牌電子郵件通知。 管理員可以一次建立全域版面，包含可重複使用的頁首、頁尾和品牌元素，並在帳號層級套用到所有電子郵件範本。 個別範本可在課程或實例層級自訂，預設繼承父版面，僅在需要時覆寫。

主要能力：

* WYSIWYG 編輯器，內建可重用元件庫（文字、圖片、按鈕、分隔符、頁頭、頁尾）
* 變數支援：插入動態欄位，如學習者姓名、課程名稱及截止日期
* 連結與非連結模板階層結構：連結模板的變更會傳播到所有子範本;未連結模板可獨立編輯
* 多語言範本支援
* 發佈前預覽與測試傳送
* 向下相容性：現有的電子郵件範本仍可正常使用

欲了解更多資訊，請參閱 [元件式電子郵件建構器](/help/migrated/administrators/feature-summary/email-builder.md)

## 外部學習支援

學習者現在可以直接從學習者儀表板提交非平台培訓，如認證、工作坊、會議及外部課程，讓管理者審核。 核准的提交會顯示在學習者成績單中。

主要能力：

* 可設定提交表單，包含標準與自訂欄位
* 經理審查與核准工作流程，並附有意見支援
* 核准的提交會顯示在學習者成績單中，並附有完整元資料
* 管理員可以設定必填欄位，包括自訂欄位
* 行政與學習者成績單新增欄位：外部學習名稱、完成評論、自訂欄位欄位
* API 支援：新增五個學習者範圍的端點，用於建立、檢索及更新提交

欲了解更多管理層級資訊，請參閱 [外部學習支援](/help/migrated/administrators/feature-summary/settings/basic-settings.md)。 欲了解更多經理層級資訊，請參閱 [外部學習支援](/help/migrated/managers/feature-summary/review-external-learning-requests.md)。 欲了解更多學習者層級資訊，請參閱 [外部學習支援](/help/migrated/learners/feature-summary/submit-external-learning.md)。

## AI 功能

### 學習者的 AI 助理

學習者 AI 助理現在除了回答指定學習內容的問題外，還支援四項新功能：

* **課程摘要**：使用 / 指令選擇目錄項目並產生摘要，無需開啟課程
* **學習物件比較**：使用/指令選擇最多兩個學習物件，並請助理進行比較
* **Adobe Experience League 回答**：助理現在能從 Adobe Learning Manager 的說明文件中獲取操作問題的答案
* **第三方內容查詢**：Go1 與 LinkedIn Learning 目錄內容可查詢（僅中繼資料;僅限英文;目錄新增後需 1–2 小時擷取）

欲了解更多資訊，請參閱 [學習者](/help/migrated/learners/feature-summary/learner-ai-assistant.md)專用的 AI 助理。

### 學習路徑代理

學習者現在可以與 AI 助理進行引導對話，根據目標、背景及可用時間，生成客製化且有序的學習路徑。 學習路徑會自動建立，學習者也會註冊。

主要能力：

* 多回合對話引導學習者選擇主題、複習課程及路徑確認
* 每場對話最多可建議五個學習主題
* 課程選擇來自指定課程目錄
* 學習者首頁最多可顯示 10 條個人化學習路徑
* 完成的路徑可以與同事分享

欲了解更多資訊，請參閱 [學習者](/help/migrated/learners/feature-summary/learning-path-agent.md)專用的 AI 助理。

### Insights 代理

Insights Agent 協助管理員透過自然語言查詢分析學習資料。 詢問有關入學趨勢、完成率、學習者參與度及技能缺口的問題。 代理會產生報告與視覺化以回應。

欲了解更多資訊，請參閱 [Insights Agent](/help/migrated/administrators/feature-summary/insights-agent.md)

### 生成式人工智慧的製作團隊

Adobe Learning Manager 整合了透過與代理協調器授權連結的基於信用系統管理的 AI 驅動功能。 此系統要求管理員啟用功能、設定信用額度，並透過帳單頁面監控使用情況。 將 Adobe Learning Manager 帳號連結到擁有有效代理協調器授權的 Adobe 管理控制台組織，對於啟用生成式 AI 功能至關重要。

更多資訊請參見 [生成式人工智慧（Gen AI）成就](/help/migrated/administrators/feature-summary/billing-management.md#genaicredits)

## 管道

頻道提供一種集中式的方式，讓人們能組織、發布及發現來自網頁及 Confluence 頁面的影片內容。 管理員可以透過連接支援的網頁或 Confluence 頁面來建立和管理頻道，設定頻道設定、控制可見性，並同步來源內容。 學習者可以瀏覽可用頻道、訂閱感興趣的頻道，並從單一地點觀看精選影片內容。

欲了解更多資訊，請參閱 [「建立頻道」](/help/migrated/administrators/feature-summary/create-channels.md)

## 報表建置器

Report Builder 為管理員提供一個靈活且自助的報告工具，超越 Adobe Learning Manager 其他固定報告類型。 管理員不再受限於預先定義的報告結構，而是可以將多個資料集的欄位（如使用者、使用者群組、課程與學習路徑、模組、逐字稿、目錄等）合併成一份符合組織特定資料需求的客製化報告。

報告只建立一次，並儲存以供重複使用。 每次下載都不需要重建篩選器、重新套用分組或重新連接資料集。 儲存的報告可隨時下載、與其他管理員分享，或透過訂閱設定，讓收件人能定期自動收到更新報告。

欲了解更多資訊，請參閱 [報表建單](/help/migrated/administrators/feature-summary/alm-report-builder.md)器。

## 自訂角色變更

自訂管理員現在可以透過自訂角色定義中的「使用者」進階權限層級，獲得擴充的使用者管理能力。

有兩個進出層級可供選擇：

| 通行層 | 自訂管理員能做什麼 |
|---|---|
| **僅讀** | 查看所有自訂角色、匯入日誌及已刪除使用者;下載自訂角色報告 |
| **完全控制** | 所有唯讀功能，並可建立、編輯、刪除及指派自訂角色;透過 CSV 匯入使用者;清除已刪除的使用者 |

了解更多關於自訂角色變更的資訊。 欲了解更多資訊，請參閱 [「進階使用者權限解鎖內容」](/help/migrated/administrators/feature-summary/custom-role.md#whatadvanceduserpermissionunlocks)

## LTI 深度連結

整合管理員現在可以啟用 LTI 深度連結，讓課程作者能直接從外部 LMS 瀏覽並嵌入 Adobe Learning Manager 課程，無需手動複製課程網址。

啟用後，作者會在外部 LMS 活動設定中看到 **「選擇內容** 」按鈕。 他們可以瀏覽核准的課程目錄、選擇課程並確認選擇——所有欄位都會自動填入。

欲了解更多資訊，請參閱 [LTI深度連結](/help/migrated/integration-admin/feature-summary/lti-deep-links.md)。

## 教室地點

教室地點現支援結構化 **的四領域地點格式**，包括國家、州/省/地區、城市及地點名稱，方便跨區域管理與組織訓練地點。 這次更新包含一次性遷移，從舊有的單一欄位格式轉移，並新增多語言支援 **地點名稱** 與 **教室資訊** 欄位，讓學習者能取得在地化的教室細節。

欲了解更多資訊，請參閱 [教室位置](/help/migrated/administrators/feature-summary/classroom.md)

## 即將推出：Adobe Learning Manager 內容撰寫器

Adobe Learning Manager 內容撰寫器是即將推出的 Adobe Learning Manager AI 課程撰寫工具，能幫助你快速建立可發佈的課程。

## 發布變更報告

想了解更多關於 Adobe Learning Manager](/help/migrated/reporting-changes-august-2026.md) 2026 年 8 月版本的[報告變更。

## API 版本中的變更

在 2026 年 8 月發布的 Adobe Learning Manager](/help/migrated/api-changes-august-2026.md) 中，了解更多關於 [API 變更的資訊。

## 本版本的其他增強內容

| 強化 | 說明 |
|---|---|
| **MQA：最新分數與最高分數** | 對於多次嘗試的模組，作者現在可以選擇將最新或最高嘗試分數記錄在學習者成績單中，並用於成績簿計算。 最新是現有的預設值，設定未設定時仍維持不變。 欲了解更多資訊，請參閱 [作者](/help/migrated/authors/feature-summary/alm-author-gradebook.md#configurescoresettingsmultipleattempts)成績冊。 |
| **內容庫中的內容預覽** | 作者現在可以在內容庫中預覽已上傳的內容檔案，再將它們加入課程。 欲了解更多資訊，請參閱 [預覽內容庫](/help/migrated/authors/feature-summary/content-library.md#previewcontentlibrary)。 |
| **增量用戶回報** | 新的基於 API 的使用者報告僅回傳自上次請求以來所建立或修改的使用者，減少使用自動化使用者同步工作流程的大型帳號資料傳輸。 欲了解更多資訊，請參閱 [增量用戶報告](/help/migrated/incremental-user-report.md)。 |
| **流體玩家中的11種新語言** | 流體式播放器現在支援 11 種額外語言，包括從右到左（RTL）腳本支援。 更多資訊請參見 [流體演奏](/help/migrated/learners/feature-summary/fluidic-player.md)者。 |
| **LTI 模組遷移** | 現有的 LTI 1.1 模組現在可以透過遷移工具遷移到 LTI 1.3。 欲了解更多資訊，請參閱 [模組](/help/migrated/integration-admin/feature-summary/migration-manual.md#migrationofltimodules)的 LTI 遷移。 |
| **電子郵件建構器：富文本編輯器支援** | Adobe Learning Manager 中的電子郵件範本現在支援富文字格式、附件及自訂自動化。 欲了解更多資訊，請參閱 [電子郵件建構器](/help/migrated/administrators/feature-summary/email-builder.md)。 |
| **電子郵件建構器：預覽功能** | 你可以使用預覽選項查看已撰寫的電子郵件，看看收件人端會呈現什麼樣子。 欲了解更多資訊，請參閱 [電子郵件建構器](/help/migrated/administrators/feature-summary/email-builder.md)。 |
| **Webhook 時間戳標準化** | webhook 有效載荷物件中 `data` 的所有日期與時間欄位現在都設定為 `00`秒數，提供與學習者逐字稿報告一致的分鐘級精確度。 |
| **連接強化** | Azure Data Lake Storage （ADLS） 連接器更新;持續支援重複虛擬教室課程的教室名稱;基於錄影檢視的出席追蹤。 |
| **球員表現提升** | 流暢的賽道玩家經過優化，以加快載入時間與模組間更順暢的銜接。 |
| **退役賽道/LP前的撞擊警告** | 管理員現在會看到警告，列出所有有效註冊及依賴的學習路徑，才能在課程或學習路徑退休前列出。 |
| **CR/VC 模組：預期時長** | 作者現在可以設定課堂與虛擬教室模組的預期時長，與排定的場次時間分開。 此數值會出現在報告及面向學習者的課程資訊中。 |
| **編輯已取得課程前的確認** | 同儕帳號的管理員現在在編輯透過目錄共享取得的課程前會看到確認對話框，防止對共享內容的意外變更。 |
| **帶有實例 ID 的會話 URL** | Microsoft Teams、Adobe Connect 和 Zoom 課程的啟動網址現在包含實例 ID，確保當多個實例存在時，學習者能被導向正確的會話。 |
| **警告：大眾觀眾公告** | 當臨時發送公告郵件給超過可設定的收件人數量時，管理員現在會在發送前看到音量警告。 |
| **電子郵件範本：外部學習者的帳號網址** | 電子郵件通知範本現在可以包含專門為外部學習者設置的帳號網址，並將他們導向正確的登入體驗。 |
| **AEM 網站** | 現在&#x200B;**在你的個人檔案**>你的興趣領域區塊中，只有一個&#x200B;**編輯**&#x200B;按鈕，可以編輯你對產品、職務和技能的偏好設定。這也是 Native Learning Manager 的一部分。 |
| **AEM 網站** | 過去只有兩個&#x200B;**編輯**&#x200B;按鈕，但現在編輯&#x200B;****&#x200B;按鈕是整合後的按鈕，用來修改產品、角色和技能的偏好設定。 |
| **時區** | 在登入使用者的個人資料設定中，時區欄位下方新增了一個搜尋框。 搜尋框可以直接搜尋時區，而不必捲動整個可用時區清單。 如果你想更改現有時區，請選擇新的時區並選擇儲存。 新時區被保存下來。 儲存按鈕只會在你選擇時區時出現。 |

## 系統需求

查看 [Adobe Learning Manager 系統需求](/help/migrated/system-requirements.md)。

## 發行說明

請 [查看最新發行公告](/help/migrated/release-note/release-notes.md) 。

## Adobe Learning Manager 先前版本

* [Adobe Learning Manager 2026 年 4 月版本](/help/migrated/whats-new-april-2026.md)
* [Adobe Learning Manager 2025 年 10 月版本](/help/migrated/whats-new-october-2025.md)
