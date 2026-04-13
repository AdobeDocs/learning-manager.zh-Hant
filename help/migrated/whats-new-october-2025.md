---
description: 了解 2025 年 10 月版本 Adobe Learning Manager 中的新功能與增強功能。
jcr-language: en_us
title: Adobe Learning Manager 2025 年 10 月版本的新內容
exl-id: 8a2f5c82-2150-46c6-a50b-a3d8a4c8ae53
source-git-commit: f200caa15d4e58ce1a4b947c1d5b8a35ba87afc3
workflow-type: tm+mt
source-wordcount: '5609'
ht-degree: 0%

---

# Adobe Learning Manager 2025 年 10 月版本的新內容

Adobe Learning Manager 2025 年 10 月版本引入了重大改進，旨在提升報告準確性、擴展整合能力，並提升管理員、作者與學習者的學習體驗。

* 體驗建構器：設計完全品牌化、以角色為基礎的學習入口網站，量身打造符合組織需求。 建立品牌化、以角色為基礎的學習入口網站，包含小工具、選單和頁面。
* 學習板上的社交標籤：學習者現在可以在貼文和留言中使用@username標註同儕，促進針對性的協作與社交學習社群內的通知。
* 範圍限定公告權限：自訂管理員可建立僅限於其指定使用者群組或目錄的公告，確保溝通目標並減少資訊過載。
* 基於語言的進度追蹤：學習者進度現在會獨立儲存在每個地區，讓學習者能無縫切換語言而不損失進度。
* 增量自訂角色管理：管理員現在能更有效率地管理自訂角色，支援 Adobe Learning Manager 的增量與多增量匯入。
* 強化的分析與遷移 API：全新且改良的 API 提供更佳的測驗績效追蹤、遷移狀態監控，以及社群學習中使用者標籤的支援。

## 體驗建構器

Experience Builder 是 Adobe Learning Manager 中的一個無程式碼/低程式碼工具，幫助你建立客製化的學習入口網站。 它讓你能設計出品牌化、使用者友善的學習入口網站，無需具備技術能力或豐富的程式設計知識。
透過體驗建構器，管理員可以輕鬆建立頁面、選單和小工具，提供符合受眾需求的個人化學習體驗。

在 Experience Builder 之前，組織面臨多項挑戰：

1. **自訂有限**：傳送門設計固定，能反映品牌的選項很少。 管理員只能做基本的修改，例如修改頁首、頁尾或顏色，這限制了創造獨特體驗的能力。
2. **成本**：建立自訂入口網站需要昂貴的開發者和漫長的工期，通常需要 6 到 9 個月才能完成。 此做法增加了總擁有成本並延遲部署。
3. **通用體驗**：大家看到的內容都一樣，即使內容與他們的職務或需求無關。 這種缺乏個人化的現象降低了學習者的參與度與滿意度。
4. **技術障礙**：非技術管理員在建立或更新入口網站時遇到困難，因為他們需要程式知識或外部支援。

Experience Builder 透過提供簡單的無程式碼/低程式碼解決方案，幫助建立個人化且帶有品牌的入口網站，解決這些問題。

它允許管理員設計符合組織需求的入口網站，而無需依賴技術專長或外部開發者。

**使用案例**

* **品牌入口網站**：建立一個與公司網站相符的入口網站，包含標誌、顏色和版面設計。 例如，一家醫療公司可以在提供學習內容的同時，設計一個反映企業品牌的入口網站。
* **角色導向學習**：建立針對特定角色量身打造的頁面。 銷售團隊可以查看產品培訓，而工程師則可取得技術課程。
* **產品培訓**：為不同產品（如 Photoshop 或 Illustrator）設置專屬頁面，並設有展示課程、證照及相關資源的小工具。

請參閱 [體驗建構器](/help/migrated/administrators/feature-summary/experience-builder/overview.md) ，了解更多使用小工具建立自訂頁面的資訊。

## 語言型學習者的進展

目前，Adobe Learning Manager 只追蹤所選區域語言的學習進度，導致在播放器中切換語言/地點時，進度會大幅下降。 這種限制可能導致使用者體驗不佳，因為學習者在存取不同語言內容時可能會失去進度。 玩家中每個模組的進度會在使用者層級與模組層級同步追蹤。 這導致使用者在切換回先前使用過的區域時，進度會被覆蓋。

例如，若學習者在區域A（英語）達成75%進步，然後切換到地點B（西班牙語），回到地點A時，進度會重置為0%，而非從75%恢復。

為了解決這些限制，功能已強化以支援區域專屬進度追蹤：

* **區域專屬儲存**：當學習者在播放器內切換區域（例如從區域 A 切換到 區域 B）時，Adobe Learning Manager 現在會分別儲存每個區域的進度狀態。
* **進度恢復：當使用者切回先前使用的地點（從區域 B 回到區域 A）時，內容會從該區域中斷的地方繼續。**
* **獨立進度追蹤**：每個地點都維持自己的進度狀態，讓學習者能在不失去每種語言的個人進度的情況下探索多種語言的內容。

以下內容類型不支援語言型學習者的進步：

* 不支援影片與音訊內容。
* 第三方內容，包括 Go1、LinkedIn Learning、getAbstract 及 Harvard ManageMentor，均不被支援。
* 未將資料傳送至學習記錄庫（LRS）的內容將不會被追蹤或儲存進度。
* 行動應用程式用戶在離線模式下無法追蹤此功能的進度。

請參閱 [「我的學習](/help/migrated/learners/feature-summary/courses.md#language-based-progress-management) 」以了解語言型學習者的進展。

## 自訂角色的增量與多增量支援

Adobe Learning Manager 現在支援自訂角色與角色指派的增量與多增量匯入。 透過增量匯入，管理員只能上傳新的、更新或已刪除的使用者紀錄，而不必重新上傳整個 CSV 檔案。

多增量匯入擴展了此功能，允許大型組織依地區或部門（例如美國、歐盟、亞太區）拆分增量檔案並平行處理。 Adobe Learning Manager 也支援最多 20 個增量式使用者 CSV 檔及其對應的自訂角色 CSV，使其可擴展至大型營運。

管理員現在可以逐步上傳角色與使用者角色檔案（role.csv 和 user_role.csv），同時上傳使用者檔案（user.csv），而不必總是完整上傳。 每個使用者匯入（user1.csv）都連結到自己的角色與角色映射檔案（user1_role.csv、user1_user_role.csv），這些檔案存放在獨立的 FTP 資料夾中。

以下三個欄位已新增至以下 CSV 中：

* 使用者註冊狀態（user.csv）：表示系統中使用者的當前註冊狀態（例如啟用、非啟用或已刪除）。
* 角色狀態（role.csv）：表示該帳戶中自訂角色目前是啟用還是非啟用。
* 使用者角色狀態（user_role.csv）：定義使用者與角色之間映射的狀態，顯示指派是否仍在運作或已被移除。

Adobe Learning Manager 現在能在使用者稽核與自訂角色報告中擷取新增、更新與刪除的操作，讓管理員能更清楚地掌握變更。

>[!NOTE]
>
>這些變更僅適用於使用增量用戶的帳號。

請參閱 [自訂角色](/help/migrated/integration-admin/feature-summary/configure-role-csv-files.md#incremental-and-multi-incremental-support-for-custom-roles) 的增量與多增量支援，了解更多關於自訂角色的增量與多增量支援資訊。

## Go1 整合增強

Go1 整合強化，允許直接策劃 Go1 課程，以在 Adobe Learning Manager 中建立學習程式（LP）。 此更新支持將 Go1 課程納入定期認證，並引入新版本的 Go1 內容中心體驗，使課程策劃更有效率。

* 可直接在 Go1 內使用 AI 聊天協助或手動選擇來建立和管理播放清單。
* 將 Go1 課程納入定期認證週期，並自動重置進度。 請參閱 [認證以](/help/migrated/administrators/feature-summary/certifications.md) 獲取更多關於建立證書的資訊。
* 升級內容發現介面，提升瀏覽與內容策劃。

**重要說明**

* 所有 Go1 功能都需要有效的 Go1 授權。
* 先前免費的Go1內容將被下架。 組織必須預覽並購買所需的內容組合包。
* 管理員與作者可建立及管理播放清單;學習者維持僅可觀看的存取權限。

請參閱 [「Curate Go1」課程至學習路徑](/help/migrated/administrators/feature-summary/content-marketplace/curate-go1-playlist.md) ，了解如何將Go1課程加入學習路徑。

## 活動模組中對 Vimeo URL 的支援

活動模組現在支援嵌入 Vimeo 網址，類似於 YouTube 嵌入。 此強化功能允許管理員直接將 Vimeo 影片連結加入活動模組。 當作者建立課程並新增活動模組時，他們現在可以看到包含 Vimeo 網址的選項。 就像 YouTube 連結被加入一樣，作者可以直接將 Vimeo 連結貼到模組設定中。 影片發布後，學習者可在 Learner 應用程式內無縫播放 Vimeo，而不會被導向到平台外。

請參閱 [「新增模組](/help/migrated/authors/feature-summary/courses.md#add-modules) 」以了解更多關於如何為課程新增模組的資訊。

## CR/VC 模組的時區資訊

教室（CR）與虛擬教室（VC）模組的時區細節現已顯示於課程概覽頁面、實例頁面、學習者預覽頁面及行事曆小工具中。 學習者與管理員可以清楚看到與重要頁面及行事曆邀請中排定課程相關的時區。 學習者能更好地規劃並參與課程，避免時區誤會。 此強化僅在沉浸式學習者應用程式中提供。

不同地區的學習者可以確認正確的時區課程時間。 清楚顯示時區有助於防止錯過課程，並確保行程安排準確。

## 建立課程時自動填入作者姓名

在課程建立過程中， **[!UICONTROL Author(s)]** 欄位會自動填入創建課程的作者姓名。 作者不再需要手動輸入自己的名字。 其他作者仍可依需求新增或更新。

對於內容擁有權規定嚴格的組織，自動填充確保作者始終正確歸屬。 編輯現有課程時，作者可以更新或新增合著者，而不會失去自動填入的條目。

請參閱 [「建立課程](/help/migrated/authors/feature-summary/courses.md#create-a-course---advanced-workflow) 」以了解更多關於創建課程的資訊。

## 在更換個人資料時搜尋外部設定檔

過去管理員會在重新指派學習者時，瀏覽整個外部設定檔清單並手動選擇所需的設定檔。 這使得這個過程非常耗時，尤其是對於擁有多個個人資料的帳戶而言。 透過此強化，管理員及自訂管理員現在可以在變更設定檔工作流程中直接在標籤中搜尋外部設定檔。

**使用案例**

* 在擁有數百個外部資料的帳戶（例如加盟店地點、合作夥伴公司或區域團體）中，管理員現在能透過搜尋即時找到精確的個人資料，減少錯誤並節省時間。
* 在組織變動期間，如合併或部門重組，可能需要大量調動學習者至新的外部配置檔。 基於搜尋的重新指派使此任務更順暢且更準確。

請參閱 [「變更外部設定檔](/help/migrated/administrators/feature-summary/add-users-user-groups.md#change-profile) 」以了解更多關於更改設定檔的資訊。

## 新增 Microsoft Teams 會議的共同組織者

過去，作者只能指派單一組織者給 Microsoft Teams 會話。 透過這項改進，管理員現在可以將共同組織者加入會議。 Microsoft Teams 會議中新增了一個欄位 **[!UICONTROL Co-Organizer]**，允許作者在主要組織者之外，指派額外的組織者。

作者可為每個 Microsoft Teams 會話指派多位共同組織者。 共同組織者擁有與主要組織者相同的存取權與權限。 作者每場最多可增加10位組織者，提供更大彈性並改善會議管理。

**使用情境**

在舉辦大型多學員課程時，共同組織者能協助管理出席、主持討論並監控聊天，而主要主辦人則專注於培訓內容。

請參閱 [「新增模組](/help/migrated/authors/feature-summary/courses.md#add-modules) 」文章，了解更多關於將 CR/VC 課程加入課程的資訊。

## 下載有興趣學習者報告

當管理員退休所有課程實例（例如課程生命週期結束時），頁面上的&#x200B;**[!UICONTROL Enroll]**&#x200B;**[!UICONTROL Course Overview]**&#x200B;按鈕會被[!UICONTROL Register Interest]選項取代。學習者可選擇此選項，表達對課程的興趣。 管理員現在可以查看並匯出對課程有註冊興趣的學習者名單。

管理員接著可以存取此清單並下載報告。 當沒有活躍實例可用時，課程頁面新增了一個 **[!UICONTROL Interested Learners]** 按鈕。 它會顯示學習者的姓名以及他們在管理員介面中註冊興趣的日期。

管理員可以選擇 ， **[!UICONTROL Actions]** 然後選擇 **[!UICONTROL Export Report]** 匯出 **[!UICONTROL Interested Learners report]**。

![](assets/register-interest.png)
_課程概覽區塊，學習者可在此查看「註冊興趣」選項_

查看 [下載有興趣的學習者](/help/migrated/administrators/feature-summary/courses.md#download-the-interested-learner-report) 以獲取更多資訊。

## 在 Salesforce 應用程式中重設建議

過去，使用 Adobe Learning Manager Salesforce 應用程式的學習者只能選擇一次角色與推薦偏好。 如果角色改變，他們必須切換到原生的 Adobe Learning Manager 應用程式，以更新個人資料並獲得相關課程推薦。 透過最新強化，學習者現在可以在 Salesforce 應用程式內快速重置偏好設定，當他們的職務、團隊或責任改變時。

這種簡化的流程確保他們能持續收到更新且相關的課程推薦，而不必離開 Salesforce。 管理員可享有較高的學習完成率及用戶角色與推薦內容間更佳的對齊，且無需額外支援或指導平台轉換。

Adobe Learning Manager 現在在 Salesforce 應用程式內新增了一個  **[!UICONTROL Reset Interests]** 按鈕。 學習者現在可以重置角色與學習偏好，無需離開 Salesforce 或登入原生的 Adobe Learning Manager 應用程式。

請參閱 [Salesforce 應用程式](/help/migrated/learners/feature-summary/sfdc-app.md#reset-recommendations-in-salesforce-app) 中的重置建議，了解更多關於 Salesforce 應用程式中重置建議的資訊。

## 行事曆小工具增強

學習者現在可以在行事曆小工具中查看過去及即將進行的課程。 他們可以瀏覽行事曆，查看任何日期並查看會議細節。 這表示他們可以回顧已進行的課程，幫助追蹤錯過或參加的內容。 他們也能查看未來24個月所有即將進行的課程，包括當月，方便提前規劃與管理行程。

[請參閱行事曆](/help/migrated/learners/feature-summary/learner-home-page.md#calendar)以獲取更多關於行事曆小工具的資訊。

## 社群論壇中的標籤用戶

社群論壇現支援用戶標籤功能，促進更具針對性的討論與學習社群間的協作。 學習者可以透過學習者應用程式、API 及 Adobe Learning Manager 參考網站，在社交學習貼文和留言中被標記。

不在看板範圍內的使用者無法被標記，避免不受歡迎的通知。 如果被標記的使用者從系統中刪除，他們的提及會顯示為「匿名」。 不允許標記用戶群組或「@all」以防止通知垃圾訊息。

* **@username標籤**：使用者可以使用「@username」格式標註其他董事會成員。
* **範圍限制標籤**：只有擁有特定公告板存取權限的用戶才能被標記，確保隱私與相關性。
* **多頻道通知**：已標記用戶會收到應用程式內及電子郵件通知，並直接連結至相關貼文或留言。

**使用案例**

* 醫療專業人員尋求特定同事對醫療病例的意見：標籤讓醫師和護理人員能迅速通知合適的專科醫師，確保對複雜病患病例的及時且準確的建議。
* 專家專家被諮詢專業主題：透過標註專家，團隊能直接邀請合適的人選參與，縮短回應時間並改善技術或利基問題的決策。
* 團隊討論需特定利害關係人參與：標註利害關係人確保相關決策者掌握最新消息並提供意見，確保專案順利進行並符合業務目標。

欲了解更多關於在社群論壇標記用戶的資訊，請參閱 [「社群論壇](/help/migrated/learners/feature-summary/social-learning-web-user.md#tag-users-in-social-board-posts) 中的用戶標籤」。

## 自訂管理員的範圍公告權限

自訂管理員現在可以為其指定的使用者群組或目錄建立公告。 這可防止組織界線間的非預期溝通。 自訂管理員只能在其指定範圍內為使用者建立公告。 公告可針對特定使用者群組或目錄進行。 完整管理員負責對所有公告保持可見性與控制權，包括由有範圍的自訂管理員所建立的公告。

**主要優點**

* 針對性的溝通，確保公告只觸及相關受眾。
* 透過防止無關通知傳達到非預期用戶，減少資訊過載。
* 維護組織界線並防止意外的交叉溝通。

**重要說明**

* 若自訂管理員的權限變更，受影響公告會顯示警告圖示並需個別重置範圍。
* 每則公告在範圍變更時必須個別更新。
* 通知公告[&#128279;](/help/migrated/administrators/feature-summary/announcements.md)報告只顯示自訂管理員指定範圍內的學習者。

**使用案例**

* 加盟組織中區域經理只需與加盟主溝通。
* 大型組織有區域或部門行政人員，專門向團隊發布公告。

請參閱 [「為指定範圍](/help/migrated/administrators/feature-summary/announcements.md#create-announcement-for-the-assigned-scope) 建立公告」以了解更多關於為指定範圍建立公告的資訊。

## 在發佈 Adobe Captivate 內容時選擇自訂角色

當將內容從 Adobe Captivate 發佈到 Adobe Learning Manager 時，如果使用者有多個自訂角色，系統會提示他們選擇該課程應該以特定自訂角色發佈。 這確保已發佈課程能正確套用正確的角色所有權與權限。

請參閱 [自訂角色](/help/migrated/administrators/feature-summary/custom-role.md) ，了解更多關於為使用者建立自訂角色的資訊。

## Saved by Me 小工具的增強功能

過去選擇 **[!UICONTROL Saved By Me]** 條帶會顯示目錄中所有可用的課程。 現在，學習者在學習者首頁的條帶中只會看到自己已收藏的課程 **[!UICONTROL Saved By Me]** 。 選擇此條帶會帶到目錄頁面，僅顯示已儲存的課程。

在目錄中，學習者可套用額外篩選器以精細搜尋。 當套用篩選器時，僅顯示符合選定標準的課程。 先前被書籤標記的課程只有在符合套用篩選條件時才會顯示。

查看 [在 AEM 網站](/help/migrated/integrate-aem-learning-manager.md#configure-my-saved-courses-widgets-in-aem-sites) 中配置已儲存課程元件，以了解更多關於 AEM 網站中已儲存課程元件的資訊。

## 支援在共享課程中顯示作者姓名

過去，當課程與 [同儕帳號](/help/migrated/administrators/feature-summary/peer-account.md)共享時，作者會顯示為外部作者。 現在，課程會顯示作者姓名，無論他們是主帳號的內部使用者，還是舊有作者（即在課程建立時以字串形式輸入的任何名字）。 選擇作者會顯示他們與同儕帳號共享的課程數量;然而，這些作者並非同儕帳號的實際使用者。

如果使用者從主帳號被刪除，他們的資料會被移除，但作者資訊仍會留在任何有其內容分享過的同儕帳號中。

>[!NOTE]
>
>這是一個基於旗幟的功能，請聯絡我們的客服團隊 [learningmanagersupport@adobe.com](mailto:learningmanagersupport@adobe.com) 以啟用此選項。

查看 [同儕帳號](/help/migrated/administrators/feature-summary/peer-account.md) ，了解更多關於分享內容至同儕帳號的資訊。

## 搜尋低階學習物件的可見性

過去，當課程屬於較高階的學習對象（如學習路徑或認證）時，搜尋結果並不一致地顯示個別課程。 若學習者僅註冊學習路徑或認證，搜尋僅回傳高階結構，而非個別課程。

透過這項強化，學習者現在可以在搜尋結果中看到個別課程，即使這些課程屬於學習路徑或證照的一部分。 新增了一個管理員設定 ，為 **[!UICONTROL Show all enrolled courses in search results]**。 啟用後，此設定確保搜尋特定課程時，會同時顯示該課程本身及相關的學習路徑或證照。

請參閱 [設定](/help/migrated/administrators/feature-summary/settings.md#general-settings) 以獲取一般設定的更多資訊。

## API 變更

### 遷移 API 增強

Adobe Learning Manager 現在支援透過遷移流程將各種資料物件遷移到帳號。 此流程可透過 API 與使用者介面啟動。 當遷移失敗時，錯誤可透過介面下載。 這些錯誤對於除錯遷移錯誤及管理遷移執行非常有用。

隨著這次釋出，錯誤日誌也將可透過 API 下載，方便高效且程式化的錯誤追蹤與除錯。

**API 變更**

新增了一個遷移 API， `runStatus`允許整合管理員檢查透過該 API 觸發的遷移執行狀態，這是過去版本 Adobe Learning Manager 無法做到的。

此外， `runStatus` API 現在提供完成跑動的下載錯誤日誌（CSV）直接連結。 請注意，該連結僅有效七天，日誌保存一個月。

`startRun` API 回應已更新，包含遷移專案 ID、衝刺 ID 及衝刺執行 ID，這些資料是查詢新狀態端點所必需的。

#### runStatus API

**描述**

取得已存在遷移執行的狀態。

**終點**

```
GET /bulkimport/runStatus
```

**參數**

* **migrationProjectId**：（必填）。 遷移專案的唯一識別碼。 遷移專案用於將資料與內容從現有的學習管理系統（LMS）轉移至 Adobe Learning Manager。 每個遷移專案可包含多個衝刺，這些衝刺是較小的遷移任務單元。

* **sprintId**：（必填）。 遷移專案中衝刺的唯一識別碼。 衝刺是遷移任務的子集，包含特定學習項目（例如課程、模組、學習者紀錄）需從現有 LMS 遷移到 Adobe Learning Manager。 每個衝刺都可以獨立執行，允許分階段遷移。

* **sprintRunId**：（必需）。 一種用於追蹤遷移專案中特定衝刺執行的唯一識別碼。 它與 sprint 中定義項目的實際遷移流程相關聯。 sprintRunId 有助於監控、排除故障並管理遷移作業。

**回應**

```
{
  "sprintId": 2510080,
  "sprintRunId": 2740845,
  "migrationProjectId": 2509173,
  "startTime": 1746524711052,
  "endTime": 1746524711052,
  [
    {
      "id": 2609923,
      "lastHeartbeatTime": 1746524711052,
      "objectName": "content",
      "jobState": "COMPLETED",
      "errorCsvLink": "",
      "errorLogLink": "migration/5830/2509173/2510080/2740845/content_err.csv",
      "sequenceNumber": 1
    },
    {
      "id": 2609922,
      "lastHeartbeatTime": 1746524713577,
      "objectName": "course",
      "jobState": "WAITING_IN_QUEUE",
      "errorCsvLink": "",
      "errorLogLink": null,
      "sequenceNumber": 2
    }
  ]
}
```

#### startRun API

`startRun` API 回應更新後新增三個欄位——migrationProjectId、sprintId 和 sprintRunId。這些欄位讓使用者能利用新的 runStatus API 追蹤並查詢特定遷移執行的狀態。

```
curl -X GET --header 'Accept: text/html' 'https://learningmanager.adobe.com/primeapi/v2/bulkimport/runStatus?migrationProjectId=001&sprintId=10001&sprintRunId=7'
```

產生以下回應。 回應內容包括：

* `migrationId`
* `sprintId`
* `sprintRunId`

**回應**

```
{
  "status": "OK",
  "title": "BULKIMPORT_RUN_INITIATED_SUCCESSFULLY",
  "source": {
    "info": "Success",
    "migrationInfo": {
      "migrationProjectId": "001",
      "sprintId": "10001",
      "sprintRunId": "7"
    }
  }
}
```

請參閱 [遷移手冊](/help/migrated/integration-admin/feature-summary/migration-manual.md) 以獲取更多關於從現有 LMS 遷移內容的資訊。

### 社群 API 變更（使用者標籤、留言與回覆）

Adobe Learning Manager 現在支援社群板@user標籤功能，讓學習者能在貼文、留言和回覆中提及並通知同儕。 此功能促進了跨平台的協作與內容發現。

此版本引入了新的 API 功能以支援使用者提及，包括強化的 POST 與 GET 端點，以及針對標籤使用者的新搜尋功能。

**API 變更概述**

* 更新後的 POST API 用於建立帶有用戶提及的貼文/留言/回覆
* 更新的 GET API 中包含用戶提及資料於回應中

**使用者提及格式**

使用者的名稱格式為：@（user:userId）

#### 請建立帶有提及的貼文

**終點**

```
POST /primeapi/v2/posts
```

**描述**

建立一篇包含用戶提及的新社交學習貼文。

**請求機構**

```
{
  "data": {
    "type": "post",
    "attributes": {
      "boardId": 13282,
      "accountId": 11152,
      "text": "<p>This is a new post mentioning @[user:11257229]</p>",
      "createdByUserId": 11257228,
      "postType": "discussion"
    },
    "id": null
  }
}
```

**回應**

標準的貼文回應，並包含提及資料於 userMentions _關聯中_。

#### 請留言並提及

**終點**

```
POST /primeapi/v2/comments
```

**描述**

在有用戶提及的貼文下留言。

**請求機構**

```
{
  "data": {
    "type": "comment",
    "attributes": {
      "postId": 20746,
      "accountId": 11152,
      "text": "<p>Test Comment @[user:11257229]</p>",
      "createdByUserId": 11257228,
      "commentLevel": 0
    },
    "id": null
  }
}
```

#### 請回覆並提及

**終點**

```
POST /primeapi/v2/replies
```

**描述**

回覆留言並附上用戶提及。

**請求機構**

```
{
  "data": {
    "type": "reply",
    "attributes": {
      "postId": 20746,
      "accountId": 11152,
      "text": "<p>Thanks for the update @[user:11257229]</p>",
      "createdByUserId": 11257228,
      "commentLevel": 1,
      "parentCommentId": 55621
    },
    "id": null
  }
}
```

#### 檢索有提及的貼文

**終點**

```
GET /primeapi/v2/posts/{id}
```

**描述**

檢索貼文細節，包括提及的使用者。

**回應**

```
{
  "links": {
    "self": "https://learningmanager.adobe.com/primeapi/v2/posts/7522"
  },
  "data": {
    "id": "7522",
    "type": "post",
    "attributes": {
      "commentCount": 3,
      "dateCreated": "2025-06-10T11:33:29.000Z",
      "dateUpdated": "2025-06-25T14:52:04.000Z",
      "downVote": 0,
      "postingType": "DEFAULT",
      "richText": "<p>my updated fourth post @[user:14707776] second mention my first post</p>",
      "state": "ACTIVE",
      "text": "my updated fourth post @[user:14707776] second mention my first post",
      "upVote": 0,
      "viewsCount": 0
    },
    "relationships": {
      "createdBy": {
        "data": {
          "id": "14707776",
          "type": "user"
        }
      },
      "parent": {
        "data": {
          "id": "3971",
          "type": "board"
        }
      },
      "userMentions": {
        "data": [
          {
            "id": "14707776",
            "type": "user"
          }
        ]
      }
    }
  },
  "included": [
    {
      "id": "14707776",
      "type": "user",
      "attributes": {
        "avatarUrl": "https://cpcontents.adobe.com/public/images/default_user_avatar.svg",
        "binUserId": "45664b87-75a3-43ec-b0b7-5064958eac6f",
        "email": "user@example.com",
        "enrollOnClick": false,
        "fields": {
          "Location": "BLR"
        },
        "gamificationEnabled": true,
        "lastLoginDate": "2025-06-27T11:21:17.000Z",
        "name": "John Doe",
        "pointsEarned": 1690,
        "pointsRedeemed": 0,
        "preferredResolution": "AUTO",
        "profile": "admin",
        "roles": [
          "Learner",
          "Admin",
          "Author",
          "Instructor",
          "Integration Admin",
          "Manager"
        ],
        "state": "ACTIVE",
        "userType": "Internal"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "9238",
            "type": "account"
          }
        }
      }
    }
  ]
}
```

### 社群 API 變更（使用者搜尋）

**終點**

```
GET /primeapi/v2/users/search?q={searchTerm}&context=tagging
```

**描述**

根據社會範圍設定搜尋可供標記的使用者。

**請求參數**


* q（必填）：搜尋詞（至少3個字元）。
* 背景說明：設定為「標籤」以讓使用者有資格被提及。
* boardID（可選）：用來根據存取權限篩選使用者的board ID。

**回應**

```
{
  "data": [
    {
      "id": "11257229",
      "type": "user",
      "attributes": {
        "name": "Jane Smith",
        "email": "jane.smith@example.com",
        "avatarUrl": "https://cpcontents.adobe.com/public/images/default_user_avatar.svg",
        "userType": "Internal",
        "state": "ACTIVE"
      }
    }
  ]
}
```

### 學習器 API 增強功能以追蹤測驗表現

API `GET /loResourceGrades` 已增強，提供詳細的測驗表現數據，使分析更為複雜，並能自動決策。

API 回應現在新增了兩個欄位：

* **[!UICONTROL highestScore]**：學習者在所有測驗嘗試中取得的最佳分數
* **[!UICONTROL maxScore]**：測驗的總分

**API 回應範例**

```
{
    "links": {
        "self": "https://learningmanagerstage1.adobe.com/primeapi/v2/loResourceGrades/course:15067_30122_41715_1_3400468"
    },
    "data": {
        "id": "course:15067_30122_41715_1_3400468",
        "type": "learningObjectResourceGrade",
        "attributes": {
            "completed": false,
            "duration": 0,
            "hasPassed": false,
            "highestScore": 0,
            "maxScore": 0,. 
            "progressPercent": 0,
            "score": 0
        },
        "relationships": {
            "loResource": {
                "data": {
                    "id": "course:15067_30122_41715_1",
                    "type": "learningObjectResource"
                }
            }
        }
    }
}
```

因此， **課程:15067_30122_41715_1_3400468** 是所請求資訊的學習物件資源等級的 ID。 `learningObjectResourceGrad`e ID 可從 `GET /enrollments/{id}` API 取得。

### API 回應支援作者姓名的大小寫敏感性

API 回應現在會顯示在課程建立或更新時輸入的舊有作者名稱。 這確保名稱在學習者介面與公開 API 中一致出現。

* 當新增作者名稱時，案件會被儲存並完全照輸入的方式回傳。
* 若已移除作者姓名後以不同案例重新加入，更新後的案例將被尊重並反映於所有使用該作者姓名的課程中。
* 先前儲存的名稱不會自動遷移;只有新增或更新的名字才會遵循此行為。

### 行事曆 API 增強

行事曆現在會載入使用者選擇的月份的會話。 為了透過 API 擷取過去及即將進行的會話，學習端`GET /users/{id}/calendar`點新增了一個參數`year`。`month`必須同時提供 和 `year` 參數以取得會話細節。

**樣本捲度**

```
curl -X GET --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth a4ae04eb9f06f4bf88abcde17' 'https://abc.adobe.com/primeapi/v2/users/12345678/calendar?month=7&year=2025&currentMonthOnly=false&filter.allSessions=false'
```

### 透過管理員 API 支援標記補全

過去，公開 API 在多重註冊情境下不支援實例式完成標記。 有了這項改進，你現在可以在請求文 `POST /users/{userId}/userModuleGrade` 中加入課程實例 ID，管理員也能標記特定實例的完成。

### 設定 SCORM 報告的使用者 ID 偏好

部分客戶要求學習者的 UUID（通用唯一識別碼）取代預設的 SCORM 內容完成user_id。 使用 UUID 能更精確地追蹤各學習計畫，並防止 MAU（月活躍用戶）帳戶中授權使用重複。

為支援此點，新增了一個帳號層級設定 `reporting_userid_preference`。 啟用此設定時，當學習者完成 SCORM 內容時，UUID 會以 UUID 取代 user_id。

>[!NOTE]
>
> 請聯絡我們 learningmanagersupport@adobe.com [&#128279;](mailto:learningmanagersupport@adobe.com) 的客服團隊以設定此設定。

新增屬性 `reportingUserIdPreference` 是用來 `get /account` 追蹤使用者 ID 偏好設定的。

### 共享課程中的作者資訊

在學習物件 API 中，作者資訊的回傳方式已更新，以區分主帳號課程與與同儕帳號共享的課程：

* 共享課程（同儕帳號）：作者資料現以新屬性 `authorDetails`回傳。 即使課程來自其他帳號，這個屬性仍會顯示作者名稱。

* 主要帳戶課程：作者資訊仍以現有 `authors` 屬性返回，且行為未改變。

此變更確保作者資料透過 API 公開的方式一致，無論是主課程還是共享課程，同時也維持現有整合的相容性。

## Webhook 的變更

### 使用 connector 註冊 LinkedIn Learning 的 webhook

過去，管理員必須透過 API 手動將 LinkedIn Learning 的 webhook 註冊到 Adobe Learning Manager。 透過此強化，LinkedIn Learning（LIL）連接器現在支援在 ALM 新連線建立時自動註冊 webhook。 **OAuth 伺服器的網址**&#x200B;與&#x200B;**租戶伺服器的網址**&#x200B;會自動填入 LinkedIn Learning 設定頁面。

欲了解更多有關LinkedIn Learning整合的資訊，請參閱 [LinkedIn Learning](/help/migrated/integration-admin/feature-summary/connectors.md#linkedin-learning-connector) 。

### LinkedIn Learning 中 MAU 授權使用的變更

過去，對於 MAU（每月活躍用戶）帳號，當學習者直接在 LinkedIn Learning 平台完成 LinkedIn Learning 課程時，Adobe Learning Manager 不會計算授權使用情況。 僅在透過 Adobe Learning Manager 播放器修讀的課程時觸發授權消耗，導致月活躍用戶（MAU）追蹤不準確。

透過這項強化，Adobe Learning Manager 現在每當學習者在 LinkedIn Learning 平台使用課程時，都會產生外部 webhook。 當 Adobe Learning Manager 收到這個 webhook 時，會計算授權使用情況，以確保兩個平台間的準確追蹤。

## 報告變更

### 講師標記的完成度在學習者成績單中

增量學習者成績單現在會記錄講師標記的完成度，即使出勤記錄是在課程日期之後。
此強化彌補了增量學習者成績單中一個關鍵缺口，過去若出席時間在原始課程日期後，教師已標記的完成紀錄會被遺漏。

增量學習者成績單是排程報告，僅記錄指定期間內發生的變更（如完成或進度更新），而非提供完整的歷史資料傾倒。 它們常用於自動化、儀表板與整合，讓使用者能有效追蹤近期學習活動，而不必每次都處理完整的成績單歷史。

* **標記完成日期（UTC 時區）欄**：一個新的時間戳欄，記錄講師標記課程或模組完成的確切日期與時間。
* **強化完成來源追蹤**：追蹤記錄完成進度的特定講師及模組（例如「教室」）。

這些變更確保課程日期之後的完成成績能準確反映在增量學習者成績單中。

**使用案例**

* 有教室課程的組織，教師可在實際課程結束後數天標記出席。
* 依賴增量學習者成績單以符合法規或報告的自動化系統或儀表板。

![學習者成績單報告顯示已完成日期（黃色高亮），用於 Adobe Learning 課程完成追蹤](/help/migrated/assets/mark-completion-column.png)
_學習者成績單報告會顯示一個新的黃色欄位，標示每位使用者的個別完成日期_

[欲了解更多學習者成績單報告資訊，請參閱學習者成績單](/help/migrated/administrators/feature-summary/reports/learner-transcripts.md)。

### 增強版用戶報告，包含擴充資料欄位

使用者報告現在新增欄位，以強化使用者追蹤與組織映射。 這些更新簡化了使用者識別，支持與下游使用者管理工作流程的整合，增進對報告關係的理解，並維持組織界線以防止意外的交叉溝通。

* 內部使用者識別欄位：提供獨特內部識別碼，方便用戶在不同系統與 API 端點間順暢追蹤。
* 經理電子郵件欄：包含直接管理人員聯絡資訊，用於組織階層追蹤。

![使用者報告顯示內部使用者 ID 及經理電子郵件欄位以黃色標示](/help/migrated/assets/user-report-columns.png)
_使用者報告，強調內部使用者 ID 與管理者電子郵件地址，以簡化使用者管理_

查看 [下載用戶報告](/help/migrated/administrators/feature-summary/add-users-user-groups.md#download-the-user-report) 以獲取更多用戶報告資訊。

### FTP、自訂 FTP 與 Box 中的使用者回報

**概述**

除了現有的工作 API 外，使用者報告現已提供 Box、FTP 及自訂 FTP 連接器。 這些報告提供內部使用者 ID、使用者電子郵件、姓名、管理者電子郵件、使用者類型等詳細資訊。

報告可按需產生或排程，資料儲存在相應連接器中，方便存取與分析。 此強化提升了對使用者活動的監控與稽核，支持更佳的安全與合規追蹤。

這些報告與現有報告（如用戶註冊、登入權限、遊戲化及培訓）並行提供，讓管理員能從單一地點存取所有重要報告，簡化資料管理與分析。

請參閱 [連接器](/help/migrated/integration-admin/feature-summary/connectors.md) ，了解更多關於 FTP、客製化 FTP 及 Box 連接器的資訊。

### 將被暫停的使用者納入學習者成績單中

**概述**

組織現在可以在學習者成績單中包含被暫停的使用者（即有殘障外部設定檔者），確保完整的歷史學習資料保存。

* 帳號層級旗標用來設定暫停使用者可見性，讓被暫停的使用者出現在學習者成績單中。
* 即使在停用暫停的外部設定檔後，歷史資料仍能保留。

**實施要求**

* 請聯絡您的客戶成功經理（CSM）以啟用帳戶層級的標記。

>[!NOTE]
>
>此標記預設為現有帳戶停用，且新帳戶必須明確申請。

查看 [學習者成績單](/help/migrated/administrators/feature-summary/reports/learner-transcripts.md) 文章及更多資訊。

### 帶有直接存取連結的工作輔助報告

**概述**

工作輔助報告已增強，新增了直接下載的工作輔助工具連結，簡化了管理員與作者的內容管理與審核流程。 此強化功能提供直接檔案下載及報告內網址存取。 省去手動尋找及下載合規或無障礙審核工作輔助工具的繁瑣工作。

* 求職連結欄：直接從報告內存取求職說明檔案及外部網址。
* 基於角色的存取控制：連結可及性依賴使用者角色與目錄權限。
* 刪除的工作輔助工具若仍連結至活躍課程，仍可存取。

**使用案例**

* 作者或管理員會定期對工作輔助工具進行無障礙審核，這是大型組織的要求。
* 任何需要快速、基於角色的職務輔助資料存取以進行審查或合規的情境。

![](/help/migrated/assets/job-aid-report.png)
_工作輔助工具報告顯示直接下載連結，方便在 Adobe Learning Manager 中存取與下載工作輔助工具_

請參閱 [工作輔助報告](/help/migrated/administrators/feature-summary/reports.md#job-aids-report) 以獲取更多有關工作輔助報告的資訊。

## 本次更新修正的錯誤

* 非互動測驗的 L2 測驗分數現在會正確產生，並包含完成測驗的使用者資料。
* 當認證機制在連線設定時被設定為簽章時，簽章會正確傳送到目標主機。
* Adobe Connect 會話期間建立的虛擬使用者在會話結束後不會被刪除。 SnapLogic 管線現在能正確移除這些使用者，即使 `principals-delete` API 先前回傳 200 的回應且未刪除他們。
* `null` `eventDetail` API 回應中的物件不再會引發例外。系統現在會跳過空輸入，並處理整個陣列，確保完整錄音。
* 回饋報告中的「回饋日期」欄位現在顯示正確的日期。 過去，秒數錯誤傳給日期構造器，該建構器預期是毫秒，導致日期顯示為1970年1月。 此點已修正，以確保產生回饋報告時日期顯示準確。
* 即使其中一個課程實例已退休，學習者現在仍可更新彈性學習路徑的註冊情況。 過去，選擇新實例會引發主控台錯誤（無法讀取未定義屬性），導致更新無法完成。
* 學習路徑中的資源名稱現在能正確顯示，且不會在字中斷。
* LinkedIn Learning 的 webhook 現在可以在為新用戶建立連結時，透過 LIL 連接器啟用。 系統也會透過私人 API 註冊帳號，並在 LinkedIn Learning 配置頁面顯示額外的設定資訊（OAuth URL 和 Tenant URL）。
* 透過 SAML 工作流程`UpdateUserWorkerTask`更新的使用者屬性值（）現在會以原始大小寫儲存，而非轉為小寫。
* 課程中模組的重新排序不再會將必修模組數量重置為「全部」;計數現在保持不變。
* Go1 流程現在透過將兩字母代碼映射到四字母代碼，類似 LinkedIn Learning 流程，以一致的方式處理語言代碼。
* 在 Retire+ 帳戶中，學習者在退選認證後啟動學習路徑課程時，曾看到「本課程不存在」。 報名來源現在已正確更新，使學習路徑中的課程能順利啟動且不會出錯。
* 當 module_version.csv 檔案包含 contentType 欄位且為空白或空值時，課程建立現在可順利運作。
* 課程現在在依目錄或目錄標籤篩選時會正確顯示。 過去，在課程頁面套用這些篩選器時，即使課程與目錄相關聯，也不會顯示課程。
* 在學習者應用程式中，按流體玩家的 TAB 鍵卡在「進入全螢幕」按鈕。 鍵盤導航現在能正確地在所有螢幕元素中移動。
* 在 Manager 應用程式的合規儀表板中，將滑鼠移至長課程名稱上，現在會顯示已報名或合規課程的完整名稱。
* module.csv 中模組可見欄只接受共享或隱藏。 任何其他值在遷移過程中都會觸發錯誤，防止後端失敗。
* 使用混合大小寫電子郵件建立新管理員，當 UUID 被停用時，不再產生重複使用者條目。 系統現在會持續處理電子郵件外殼，以防止重複。
* 阿拉伯語、希臘語、希伯來語、印地語、泰語和烏克蘭語等語言課程的筆記PDF現在能正確顯示。 過去，下載的 PDF 中角色會顯示扭曲，儘管在播放器中顯示正確。

## 系統需求

查看 [Adobe Learning Manager 系統需求](/help/migrated/system-requirements.md)。

## 發行說明

請 [查看最新發行公告](/help/migrated/release-note/release-notes.md) 。

## Adobe Learning Manager 先前版本

* [Adobe Learning Manager 2025 年 5 月版本](/help/migrated/whats-new-may-2025.md)
* [Adobe Learning Manager 2025 年 11 月版本](/help/migrated/whats-new-nov-24.md)
