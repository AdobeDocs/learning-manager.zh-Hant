---
description: 了解 Adobe Learning Manager 2026 年 8 月版本中的新功能與增強功能
jcr-language: en_us
title: Adobe Learning Manager 2026 年 8 月版本的新功能
exl-id: da46f186-3ff3-422a-af49-31c7405fd584
source-git-commit: 123ab618e2e052ef63800463be939de93b5eb99f
workflow-type: tm+mt
source-wordcount: '2644'
ht-degree: 0%
---
# Adobe Learning Manager 2026 年 8 月版本的新功能

## 成績簿

Adobe Learning Manager 中的成績簿為課程新增加權分數，讓作者能為每個評分模組分配貢獻百分比，並設定完成課程的最低總分。 學習者可以在課程期間追蹤成績，管理員則可查看期末成績並下載相關成績單。

### 成績簿的功能

支援成績簿的課程會依據各模組所分配的權重百分比，將個別模組的分數合併計算，計算每位學習者的最終成績。 這提供精確且加權的績效衡量，而非單純的分數加總或僅以完成度為標準的通過/不合格評分。

成績簿支援兩種完成模式：

* **僅限**&#x200B;必修模組：當所有必修模組完成後，課程即告結束。 成績簿分數仍會計算並可見，但總分不會影響及格標準。

* **必修模組加上總分**：學習者必須完成所有必修模組，並取得達到或超過最低及格門檻的總分。 這兩個條件必須同時符合，才能取得及格成績。

### 課程成績的計算方式

每個可評分模組對課程總分的貢獻為：

（得分÷最高分）× 權重百分比 = 模組貢獻

課程總分數為所有模組貢獻的總和。 所有可評分模組的權重百分比加起來必須正好為 100。 在未符合此條件之前，無法儲存成績簿設定。

課程總分數為所有模組貢獻的總和。 所有可評分模組的權重百分比加起來必須正好為 100。 在未符合此條件之前，無法儲存成績簿設定。

評分標準不必在不同模組間保持一致。 一個滿分 100 分的課堂課程，以及一個 10 分滿分的 SCORM 模組，可以同時存在在同一本成績冊裡。 公式會在套用權重前對每個貢獻進行標準化。

**可評分與不可評分模組**

只有產生分數的模組才有資格獲得加權。 可評分模組類型包括：

* 啟用評分的 SCORM、AICC 與 xAPI 內容
* Captivate 內容套件
* Adobe Learning Manager 中的原生測驗
* 由講師或行政人員輸入分數的教室與虛擬課堂課程
* 由講師或管理員評分的活動模組

不可評分的模組類型、PDF 檔案、影片檔案、音訊檔案、PowerPoint 簡報、Word 文件、Excel 檔案及 HTML 內容，無法分配權重百分比，且不計入總分。 這些模組仍可能是完成課程的必修科目。 當啟用「包含不對最終成績有貢獻的模組」選項時，這些模組會在成績簿中顯示，但不會顯示權重值。

了解更多關於 [作者](/help/migrated/authors/feature-summary/alm-author-gradebook.md)用成績簿的資訊。

## 階層式內容資料夾

內容庫現在支援最多三層的私有資料夾階層結構。 管理員負責建立資料夾結構，並控制哪些自訂角色可以存取哪些第一級資料夾。 自動層級資料夾內所有子資料夾存取級串接。

作者可以在資料夾間複製和移動內容、依資料夾篩選內容庫，並在新增模組到課程時瀏覽階層結構。

主要功能：

* 最多可有三個層級的巢狀（每個父層最多 25 個子資料夾）
* 僅在第一級指派角色式存取
* 內容可以出現在多個資料夾中而不重複
* 公用資料夾與私人資料夾結構互斥
* 在課程撰寫中選擇模組時，瀏覽資料夾的體驗

進一步了解 [階層式內容資料夾——管理員層級的功能](/help/migrated/administrators/feature-summary/settings/advanced-settings.md#content-folder)。 進一步了解 [階層式內容資料夾——作者](/help/migrated/authors/feature-summary/content-library.md#add-content-to-a-folder)層級的功能。

如果您正將學習內容從其他平台遷移至 Adobe Learning Manager，並希望保留現有的資料夾組織，您可以使用 CSV 檔案建立階層式資料夾結構，並將內容檔案與適當的資料夾關聯。 在「遷移內容資料夾階層[&#128279;](/help/migrated/integration-admin/feature-summary/migration-manual.md#migratecontentfolderhierarchy)」中了解更多關於遷移的資訊。

## Live Hub（測試版）

Live Hub 是 Adobe Learning Manager 內建的 AI 虛擬訓練體驗，協助組織提供引人入勝且具影響力的即時學習。 透過人工智慧投票、分組討論室協調、持續學習空間及 AI 輔助等智慧功能，Live Hub 大幅提升講師生產力，同時降低課程進行的複雜度。

主要亮點：

* 透過原生的 Adobe Learning Manager 體驗提升線上學習，提升教學品質與學習成果。
* 為你的講師提供一位由 AI 驅動的共同主持人，透過智慧投票、問答支援以及分組討論室的洞見，推動參與度。
* 透過 AI 生成的摘要與可依主題搜尋的課程錄影，幫助學習者從每堂課中獲得更多收穫。
* 透過參與度分析來衡量什麼重要，不僅只看出席，還能揭示真正的學習參與。
* 協助作者利用 AI 驅動的講師搜尋器，依技能、時間、偏好時間、時區及現用情況配對合適的講師。

了解更多關於 [Live Hub](./getting-started-with-live-hub/getting-started-live-hub.md) 入門的資訊。

## Adobe Learning Manager 內容撰寫器（測試版）

Adobe Learning Manager 現在內建 Content Composer，這是一款原生 AI 課程撰寫工具，能在數分鐘內將你從簡單的提示詞帶到結構化、準備好發佈的課程。

主要特色：

* 對話式 AI 會引導作者完成訓練目標、資源來源與學習目標，生成完整的課程簡報與大綱。
* 文件為基礎的生成將 AI 輸出限制在上傳的檔案上，這對於合規、法規及程序訓練至關重要。
* 完整課程生成一次完成，例如課程、主題、文字、圖片、知識檢定及評分測驗。
* 視覺主題系統，具備亮色與深色模式、字型控制、頁首與頁尾支援，以及可進行進階自訂的 JSON 匯出。
* 可在發佈前設定完成條件、成功條件、測驗設定及 SCORM 版本。
* 以及更多。

進一步了解 [Adobe Learning Manager 內容撰寫器](/help/migrated/authors/feature-summary/content-composer/content-composer-help.md)。


## 基於元件的電子郵件範本建構器

組織現在可以使用現代化所見即所得元件編輯器，在 Adobe Learning Manager 中建立企業級、具品牌特色的電子郵件通知。 管理員只需建立一次全域版面配置，包含可重複使用的頁首、頁尾及品牌元素，並套用至帳戶層級的所有電子郵件範本。 個別範本可在課程或實例層級自訂，預設繼承父版面配置，僅在需要時覆寫。

主要功能：

* WYSIWYG 編輯器，內建可重複使用的元件庫（文字、圖片、按鈕、分隔線、頁首、頁尾）
* 支援變數：插入動態欄位，如學習者姓名、課程名稱及截止日期
* 連結與未連結範本階層結構：連結範本的變更會傳播至所有子範本;未連結範本可獨立編輯
* 多語言範本支援
* 發佈前預覽並測試傳送
* 向下相容性：現有電子郵件範本仍能正常運作

進一步了解 [元件式電子郵件建置器](/help/migrated/administrators/feature-summary/email-builder.md)。

## 外部學習支援

學習者現在可以直接從學習者儀表板提交平台外的培訓，如認證、工作坊、會議及外部課程，以供主管審核。 已核准的提交會顯示在學習者成績單中。

主要功能：

* 可設定的提交表單，包含標準與自訂欄位
* 具備備註支援的經理審查與核准工作流程
* 已核准的提交會顯示在學習者成績單中，並附上完整的元資料
* 管理員可以設定必填欄位，包括自訂欄位
* 管理與學習者成績單新增欄位：外部學習名稱、完成評論、自訂欄位欄位
* API 支援：新增五個學習者範疇化的端點，用於建立、檢索及更新提交

了解更多關於 [外部學習支援——管理員層級的功能](/help/migrated/administrators/feature-summary/settings/basic-settings.md)。 了解更多關於 [外部學習支援——經理級能力](/help/migrated/managers/feature-summary/review-external-learning-requests.md)的資訊。 進一步了解 [外部學習支援——學習者層級的功能](/help/migrated/learners/feature-summary/submit-external-learning.md)。

## AI 功能

### 學習者的 AI 助手

學習者專用的 AI 助理現在除了回答指定學習內容的問題外，還支援四項新功能：

* **課程摘要**：使用 / 指令選取目錄項目並產生摘要，無需開啟課程
* **學習物件比較**：使用 / 指令選擇最多兩個學習物件，並請助理將它們比較
* **Adobe Experience League 解答**：助理現在能從 Adobe Learning Manager 說明文件中取得操作相關問題的解答
* **第三方內容查詢**：可以查詢 Go1 與 LinkedIn Learning 目錄內容（僅限元資料;僅限英文;目錄新增後需 1–2 小時完成擷取）

進一步了解 [學習者專用](/help/migrated/learners/feature-summary/learner-ai-assistant.md)的 AI 助理。

### Learning Path 代理程式

學習者現在可以與 AI 助理進行引導對話，根據目標、背景與可用時間，生成自訂且有序的學習路徑。 學習路徑會自動建立，學習者也會被註冊。

主要功能：

* 多回合對話引導學習者選擇主題、課程複習及路徑確認
* 每場對話最多可建議五個學習主題
* 從指定目錄中選擇課程
* 學習者首頁最多顯示 10 條個人化學習路徑
* 完成的路徑可以與同事分享

了解更多關於 Learning Path Agent 的資訊[&#128279;](/help/migrated/learners/feature-summary/learning-path-agent.md)。

### Insights 代理程式

Insights Agent 協助管理員透過自然語言查詢分析學習資料。 請詢問有關招生趨勢、完成率、學習者參與度及技能缺口的問題。 代理程式會根據此產生報告與視覺化。

了解更多關於 Insights Agent[&#128279;](/help/migrated/administrators/feature-summary/insights-agent.md) 的資訊。

<!--
### Gen AI credits

Adobe Learning Manager integrates AI-powered features managed through a credit-based system linked to Agent Orchestrator licenses. This system requires administrators to activate features, set credit limits, and monitor usage via the Billing page. Linking the Adobe Learning Manager account to an Adobe Admin Console organization with an active Agent Orchestrator license is essential for enabling Gen AI features.

View [Gen AI credits](/help/migrated/administrators/feature-summary/billing-management.md#genaicredits) for more information.
-->

## 頻道（Beta）

頻道提供集中式方式，協助組織、發布及發現來自網頁及 Confluence 頁面的影片內容。 管理員可以透過連接支援的網頁或 Confluence 頁面來建立和管理頻道，設定頻道設定、控制可見性，並同步來自來源的內容。 學習者可以瀏覽可用頻道、訂閱感興趣的頻道，並從單一地點觀看精選影片內容。

了解更多關於建立頻道[&#128279;](/help/migrated/administrators/feature-summary/create-channels.md)的資訊。

## 報告建構器

Report Builder 為管理員提供一個彈性且自助式的報告工具，超越 Adobe Learning Manager 其他地方所提供的固定報告類型。 管理員不再受限於預先定義的報告結構，而是可以將多個資料集的欄位（如使用者、使用者群組、課程與學習路徑、模組、逐字稿、目錄等）合併成一份符合組織特定資料需求的客製化報告。

報告只建立一次，並儲存以供重複使用。 每次下載都不需要重新建立篩選器、重新套用分組或重新加入資料集。 儲存的報告可隨時下載、與其他管理員共享，或透過訂閱設定，讓收件人能定期自動收到更新報告。

了解更多關於報告建構器的[&#128279;](/help/migrated/administrators/feature-summary/alm-report-builder.md)資訊。

## 自訂角色變更

自訂管理員現在可以透過自訂角色定義中的「使用者」中的進階權限等級，獲得擴充的使用者管理能力。

提供兩種存取等級：

| 存取等級 | 自訂管理員能做什麼 |
|---|---|
| **唯讀** | 檢視所有自訂角色、匯入日誌及已刪除的使用者;下載自訂角色報告 |
| **完全控制權** | 所有唯讀功能，並可建立、編輯、刪除及指派自訂角色;透過 CSV 匯入使用者;清除已刪除的使用者 |

### 限制

**僅限**&#x200B;手動建立的角色：擴充的自訂角色管理功能僅適用於透過 Adobe Learning Manager 管理介面建立的角色。 不支援透過 CSV 上傳匯入的角色。

在主題 [「進階使用者權限解鎖](/help/migrated/administrators/feature-summary/custom-role.md#whatadvanceduserpermissionunlocks)什麼」中，進一步了解自訂角色變更。

## LTI 深度連結

整合管理員現在可以為 LTI 工具設定啟用 LTI 深度連結，讓課程作者能直接從外部 LMS 瀏覽並嵌入 Adobe Learning Manager 課程，而無需手動複製課程網址。

啟用後，作者會在外部 LMS 活動設定中看到 **「選擇內容** 」按鈕。 他們可以瀏覽核准的課程目錄、選擇課程並確認選擇——所有欄位都會自動填入。

了解更多關於 LTI 深度連結的[&#128279;](/help/migrated/integration-admin/feature-summary/lti-deep-links.md)資訊。

## 教室地點

教室地點現支援結構化 **的四場地點格式**，包括國家、州/省/地區、城市及地點名稱，讓跨區域的訓練地點管理與組織變得更方便。 本次更新包含從舊有單一欄位格式的一次性遷移，並新增對「位置名稱&#x200B;**」與**「位置資訊&#x200B;**」欄位的多語言支援**，讓學習者能使用本地化的教室資訊。

了解更多關於教室地點的[&#128279;](/help/migrated/administrators/feature-summary/classroom.md)資訊。

## 報告版本變更

了解更多關於 [Adobe Learning Manager](/help/migrated/reporting-changes-august-2026.md) 2026 年 8 月版本中報告變更的資訊。

## 本次版本中的 API 變更

了解更多關於 [Adobe Learning Manager](/help/migrated/api-changes-august-2026.md) 2026 年 8 月版本中 API 變更的資訊。

## 本次發行的其他增強功能

| 強化 | 說明 |
|---|---|
| **MQA：最新分數與最高分數比較** | 對於多次嘗試的模組，作者現在可以選擇在學習者成績單中記錄最新或最高嘗試分數，並用於成績簿計算。 「最新」是現有的預設值，且在未設定時仍維持不變。 欲了解更多資訊，請參閱 [Gradebook for Authors](/help/migrated/authors/feature-summary/alm-author-gradebook.md#configurescoresettingsmultipleattempts)。 |
| **內容庫中的內容預覽** | 作者現在可以在內容庫中直接預覽已上傳的內容檔案，然後再將它們加入課程。 了解更多關於 [預覽內容庫](/help/migrated/authors/feature-summary/content-library.md#previewcontentlibrary)的資訊。 |
| **增量使用者報告** | 新的基於 API 的使用者報告僅回傳自上次請求以來建立或修改的使用者，藉此減少使用自動化使用者同步工作流程的大型帳戶資料傳輸。 了解更多關於增量使用者報告的資訊[&#128279;](/help/migrated/incremental-user-report.md)。 |
| **Fluidic Player 新增 11 種語言** | 流體播放器現在支援 11 種額外語言，包括由右到左（RTL）腳本的支援。 了解更多關於 Fluidic Player[&#128279;](/help/migrated/learners/feature-summary/fluidic-player.md) 的資訊。 |
| **LTI 模組遷移** | 現有的 LTI 1.1 模組現在可透過遷移工具遷移至 LTI 1.3。 了解更多關於 [模組](/help/migrated/integration-admin/feature-summary/migration-manual.md#migrationofltimodules) LTI 遷移的資訊。 |
| **電子郵件建構器：支援富文本編輯器** | Adobe Learning Manager 中的電子郵件範本現在支援富文字格式、附件及自訂自動化。 了解更多關於 Email Builder[&#128279;](/help/migrated/administrators/feature-summary/email-builder.md) 的資訊。 |
| **電子郵件建構器：預覽功能** | 您可以使用預覽選項檢查撰寫好的電子郵件，看看收件人端的樣貌。 了解更多關於 Email Builder[&#128279;](/help/migrated/administrators/feature-summary/email-builder.md) 的資訊。 |
| **Webhook 時間戳標準化** | Webhook 有效載荷物件中 `data` 的所有日期與時間欄位現在都設定 `00`為秒數，提供與學員成績單報告一致的分鐘級精確度。 |
| **連線增強功能** | Azure Data Lake Storage （ADLS） 連接器更新;持續支援重複虛擬教室課程的教室名稱;基於錄影檢視的出席追蹤。 |
| **球員表現提升** | 流暢的賽道玩家經過優化，以加快載入時間與模組間更流暢的轉換。 |
| **退役課程/實習前的撞擊警告** | 作者/管理員會在課程或學習路徑被退休前，先看到相關 LO 的警告清單。 通知作者某位選民 LO 已被退休。 管理員若是 LO 的作者，則會收到，但沒有作者角色。 |
| **CR/VC 模組：預期持續時間** | 作者現在可以為課堂與虛擬教室模組設定預期時長，與排定的課程時間分開。 此值會出現在報告及面向學習者的課程資訊中。 |
| **編輯已取得課程前的確認** | 同儕帳戶的管理員現在在編輯透過目錄共享取得的課程前會看到確認對話框，防止對共享內容的非預期變更。 |
| **帶有實例 ID 的工作階段 URL** | Microsoft Teams、Adobe Connect 和 Zoom 課程的啟動 URL 現在包含實例 ID，確保當多個實例存在時，學習者會被導向正確的會話。 |
| **大量觀眾公告警告** | 當將臨時公告電子郵件寄送給超過可設定的收件者數量時，管理員現在會在發送前看到批量警告。 |
| **電子郵件範本：外部學習者的帳戶網址** | 電子郵件通知範本現在可以為外部學習者提供獨立的帳號 URL，將他們導向正確的登入體驗。 |
| **AEM 網站** | 現在&#x200B;**在「你的個人檔案**」>「你的興趣領域」區塊中，只有一個&#x200B;**「編輯**」按鈕，用來編輯你對產品、角色和技能的偏好設定。這也是 Native Learning Manager 的一部分。 |
| **AEM 網站** | 過去只有兩個 **「編輯** 」按鈕，但現在「 **編輯** 」按鈕是一個整合按鈕，用來修改你對產品、角色和技能的偏好設定。 |
| **時區** | 已新增一個搜尋框，位於已登入使用者的個人檔案設定中時區欄位下方。 搜尋框可直接搜尋時區，而不必瀏覽整個可用時區清單。 如果您想變更現有時區，請選擇新的時區並選擇儲存。 新時區已被保存。 「儲存」按鈕僅在您選擇時區時出現。 |

## 系統需求

進一步了解 [Adobe Learning Manager 系統需求](/help/migrated/system-requirements.md)。

## 發行說明

查看 [最新版本更新的發行說明](/help/migrated/release-note/release-notes.md) 。

## Adobe Learning Manager 先前版本

* [Adobe Learning Manager 2026 年 4 月版本](/help/migrated/whats-new-april-2026.md)
* [Adobe Learning Manager 2025 年 10 月版本](/help/migrated/whats-new-october-2025.md)
