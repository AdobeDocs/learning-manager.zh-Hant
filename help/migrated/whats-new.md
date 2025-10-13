---
description: 瞭解2025年10月發行的Adobe Learning Manager中的新功能和增強功能
jcr-language: en_us
title: Adobe Learning Manager 2025年10月版本的新增功能
source-git-commit: c1a201e97a8944dddb6361aade0017f5745f933c
workflow-type: tm+mt
source-wordcount: '5605'
ht-degree: 0%

---


# Adobe Learning Manager 2025年10月版本的新增功能

2025年10月發行的Adobe Learning Manager引進了多項重要增強功能，旨在改善報表正確性、擴充整合功能，並增強管理員、作者和學習者的學習體驗。

* Experience Builder：根據貴組織的需求，設計完全品牌化、角色導向的學習入口網站。 使用Widget、選單和頁面建立品牌化、角色型學習入口網站。
* 學習版中的社交標籤：學習者現在可以在貼文和評論中使用標@username來標籤同行，在社交學習社群中啟用目標式共同作業和通知。
* 限定範圍的宣告許可權：自訂管理員可建立僅限於其指派之使用者群組或目錄的宣告，以確保目標式通訊並減少資訊超載。
* 語言型進度追蹤：學習者進度現在可針對每個地區設定獨立儲存，以便順暢地切換語言之間而不會失去進度。
* 增量自訂角色管理：管理員現在可以在Adobe Learning Manager中支援增量和多增量匯入，更有效率地管理自訂角色。
* 增強的分析及移轉API：全新及改善的API提供更出色的測驗效能追蹤、移轉狀態監控，以及社交學習使用者標籤支援。

## Experience Builder

>[!IMPORTANT]
>
>我們很高興地宣佈，建立自訂學習入口網站的創新工具Experience Builder將在2025年10月Adobe Learning Manager發行後推出。
>
>臨近發行日期之際，請繼續關注更多更新消息。 我們期待瞭解您如何使用Experience Builder來轉換學習入口網站。
>
>如有疑問或需要其他資訊，請聯絡客戶成功案例經理。

Experience Builder是Adobe Learning Manager中的無程式碼/低程式碼工具，可協助您建立自訂的學習入口網站。 它可讓您設計品牌化、方便使用的學習入口網站，而不需要技術技能或廣泛的程式碼知識。
有了Experience Builder，管理員可以輕鬆建立頁面、功能表和Widget，為受眾量身打造個人化學習體驗。

在Experience Builder之前，組織面臨幾個挑戰：

1. **有限的自訂**：入口網站已修正設計，但只有少數幾個選項可反映您的品牌。 管理員只能進行基本變更（例如修改頁首、頁尾或顏色），這會限制建立獨特體驗的能力。
2. **成本**：建置自訂入口網站需要昂貴的開發人員和漫長的時間，通常需要6到9個月才能完成。 此方法會增加總體擁有成本，並延遲部署。
3. **一般體驗**：每個人都看到相同的內容，即使內容與其角色或需求無關。 缺乏個人化降低了學習者的參與度和滿意度。
4. **技術障礙**：非技術管理員因需要編碼知識或外部支援而難以建立或更新入口網站。

Experience Builder提供簡單、無程式碼/低程式碼解決方案，用於建立個人化的品牌入口網站，藉此解決這些問題。

它可讓管理員設計符合其組織需求的入口網站，而不需依賴技術專業知識或外部開發人員。

**使用案例**

* **品牌入口網站**：建立與您公司網站相符的入口網站，並包含標誌、顏色和版面配置。 例如，醫療保健公司可以設計入口網站，在提供學習內容的同時反映其企業品牌。
* **以角色為基礎的學習**：建立為特定角色量身打造的頁面。 銷售團隊可以檢視產品培訓，而工程師則可存取技術課程。
* **產品培訓**：為不同的產品設定專屬頁面，例如Photoshop或Illustrator，其中包含顯示課程、認證和相關資源的Widget。

檢視[Experience Builder](/help/migrated/administrators/feature-summary/experience-builder/overview.md)，以取得使用Widget建立自訂頁面的詳細資訊。

## 語言型學習者進度

目前，Adobe Learning Manager僅追蹤學習者所選地區設定語言的進度，導致在播放器中切換語言/地區設定時重大進度損失。 此限制可能會導致使用者體驗不佳，因為學習者在存取不同語言的內容時可能會失去進度。 系統會在使用者和模組層級追蹤播放器中每個模組的進度。 這會導致在使用者切換回相同模組先前使用的地區設定時，覆寫使用者進度的情況。

例如，如果學習者在地區設定A （英文）中達到75%的進度，然後切換到地區設定B （西班牙文），在返回地區設定A時，他們的進度會重設為0%，而不是從75%恢復。

為了解決這些限制，已增強功能以支援地區設定特定的進度追蹤：

* **地區設定專屬儲存**：當學習者切換播放器中的地區設定（例如，從地區設定A切換為地區設定B）時，Adobe Learning Manager現在會分別儲存內容的每個地區設定的進度狀態。
* **進度恢復**：當使用者切換回先前使用的地區設定（從地區設定B切換回地區設定A）時，內容會從該特定地區設定中他們中斷的地方繼續。
* **獨立的進度追蹤**：每個地區設定會維持自己的進度狀態，讓學習者能夠探索多種語言的內容，而不會失去他們每種語言的個別進度。

語言型學習者進度不支援下列內容型別：

* 不支援視訊和音訊內容。
* 不支援協力廠商內容，包括Go1、LinkedIn Learning、getAbstract和Harvard ManageMentor。
* 若內容未傳送資料至學習記錄存放區(LRS)，將不會追蹤或儲存進度。
* 在離線模式中，行動應用程式使用者無法追蹤此功能的進度。

檢視[我的學習](/help/migrated/learners/feature-summary/courses.md#language-based-progress-management)，以取得語言型學習者進度的詳細資訊。

## 對自訂角色的增量和多增量支援

Adobe Learning Manager現在支援對自訂角色和角色指派進行累加和多累加匯入。 使用增量匯入時，管理員只能上傳使用者的新記錄、更新記錄或刪除記錄，而不是重新上傳整個CSV檔案。

多重增量匯入可讓大型組織依地區或部門（例如，美國、歐盟、APAC）分割增量檔案，並同時處理這些檔案，藉此擴充此功能。 Adobe Learning Manager也支援最多20個增量使用者CSV及其對應的自訂角色CSV，使其可針對大型作業進行擴充。

管理員現在可以逐步上傳角色和使用者角色檔案（role.csv和user_role.csv）以及使用者檔案(user.csv)，而不是一律完全上傳。 每個使用者匯入(user1.csv)都會連結到自己的角色和角色對應檔案(user1_role.csv、user1_user_role.csv)，這些檔案儲存在單獨的FTP資料夾中。

下列CSV已新增下列三個其他欄：

* 使用者註冊狀態(user.csv)：指出使用者在系統中的目前註冊狀態（例如，使用中、非使用中或刪除）。
* 角色狀態(role.csv)：指出帳戶中的自訂角色目前為作用中或非作用中。
* 使用者角色狀態(user_role.csv)：定義使用者與角色之間對應的狀態，顯示指派是否作用中或已移除。

Adobe Learning Manager現在會擷取使用者稽核和自訂角色報表中的新增、更新和刪除動作，讓管理員更能瞭解變更。

>[!NOTE]
>
>這些變更僅適用於使用增量使用者的帳戶。

檢視[自訂角色的增量與多重增量支援](/help/migrated/integration-admin/feature-summary/configure-role-csv-files.md#incremental-and-multi-incremental-support-for-custom-roles)，以取得自訂角色的增量與多重增量支援的詳細資訊。

## Go1整合增強功能

Go1整合已增強，可讓您直接組織在Adobe Learning Manager中建立學習計畫(LP)的Go1課程。 此更新支援將Go1課程納入定期認證，並引進新版本的Go1內容中心體驗，實現更有效的課程策劃。

* 使用AI聊天協助或手動選取功能，直接在Go1中建立和管理播放清單。
* 在自動進度重設的循環認證週期中包含Go1課程。 檢視[認證](/help/migrated/administrators/feature-summary/certifications.md)以取得建立憑證的詳細資訊。
* 升級內容探索介面，以改善瀏覽和內容管理。

**重要備註**

* 所有Go1功能都需要有效的Go1授權。
* 先前免費的Go1內容將停止服務。 組織必須預覽和購買所需的內容組合。
* 管理員和作者可以建立和管理播放清單；學習者維持僅供檢視的存取權。

檢視[將Go1課程組織到學習路徑](/help/migrated/administrators/feature-summary/content-marketplace/curate-go1-playlist.md)，瞭解將Go1課程新增到學習路徑的詳細資訊。

## 支援活動模組中的vimeo URL

活動模組現在支援內嵌Vimeo URL，類似於YouTube內嵌。 此增強功能可讓管理員直接將Vimeo視訊連結新增至活動模組。 當作者建立課程並新增活動模組時，他們現在會看到包含Vimeo URL的選項。 與新增YouTube連結的方式類似，作者可以直接將Vimeo連結貼到模組設定中。 發佈後，學習者便可在學習者應用程式內順暢播放Vimeo影片，不需在平台外部重新導向。

檢視[新增模組](/help/migrated/authors/feature-summary/courses.md#add-modules)，以取得新增模組至課程的詳細資訊。

## CR/VC模組的時區資訊

時區詳細資訊現在顯示在「課程總覽」頁面、「執行個體」頁面、「學習者預覽」頁面和「日曆Widget」中的教室(CR)和虛擬教室(VC)模組。 學習者和管理員可跨重要頁面和行事曆邀請，清楚檢視與已排程工作階段相關的時區。 學習者可以更有效地規劃及加入工作階段，避免時區誤解。 此增強功能僅在沈浸式學習者應用程式中提供。

不同地區的學習者可以在正確的時區確認工作階段時間。 清楚顯示時區有助於防止工作階段錯過，並確保行事曆排程的準確性。

## 建立課程時自動填入作者姓名

在建立課程期間，**[!UICONTROL Author(s)]**&#x200B;欄位現在會自動填入建立課程的作者名稱。 作者不再需要手動輸入自己的名稱。 您仍可視需要新增或更新其他作者。

對於具有嚴格內容所有權規則的組織，自動填入可確保始終正確歸因作者。 編輯現有課程時，作者可更新或新增共同作者，且不會遺失自動填入的專案。

檢視[建立課程](/help/migrated/authors/feature-summary/courses.md#create-a-course---advanced-workflow)，以取得建立課程的詳細資訊。

## 變更設定檔時搜尋外部設定檔

之前，管理員會捲動瀏覽整個外部設定檔清單，並在重新指派學習者時手動選取所需的設定檔。 這使得該程式相當耗時，尤其是對於擁有許多設定檔的帳戶。 透過此增強功能，管理員和自訂管理員現在可以在變更設定檔工作流程期間，直接在索引標籤中搜尋外部設定檔。

**使用案例**

* 在擁有數百個外部設定檔的帳戶（例如特許經營位置、合作夥伴公司或區域群組），管理員現在可以使用搜尋立即找到正確的設定檔，減少錯誤並節省時間。
* 在組織變更期間（例如合併或部門調整），可能需要將學習者大量移至新的外部設定檔。 以搜尋為基礎的重新指派可讓此工作更順暢、更準確。

檢視[變更外部設定檔](/help/migrated/administrators/feature-summary/add-users-user-groups.md#change-profile)，以取得變更設定檔的詳細資訊。

## 為Microsoft Teams工作階段新增共同召集人

之前，「作者」只能將單一組織者指派給Microsoft Teams工作階段。 透過這項增強功能，管理員現在可以將共同組織者新增至工作階段。 已在Microsoft Teams工作階段中引進新欄位&#x200B;**[!UICONTROL Co-Organizer]**，可讓「作者」在主要召集人旁邊指派其他召集人。

作者可為每個Microsoft Teams工作階段指派多個共同召集人。 共同召集人擁有與主要召集人相同的存取權和許可權。 每個工作階段最多可新增10個召集人，提供更大的彈性並改善工作階段管理。

**使用案例**

與許多學習者進行大規模研討會時，共同組織者可協助管理出席情況、稽核討論及監控聊天，而主要組織者則專注於提供培訓。

檢視[新增模組](/help/migrated/authors/feature-summary/courses.md#add-modules)文章，以取得有關將CR/VC工作階段新增至課程的詳細資訊。

## 下載感興趣的學習者報表

當管理員處分所有課程執行個體（例如，在課程生命週期結束時）時，**[!UICONTROL Enroll]**&#x200B;頁面上的&#x200B;**[!UICONTROL Course Overview]**&#x200B;按鈕會以[!UICONTROL Register Interest]選項取代。 學習者可選取此選項，以表達參加課程的興趣。 管理員現在可以檢視和匯出已註冊課程興趣的學習者清單。

然後，管理員可以存取此清單並將其下載為報表。 當沒有可用的作用中執行個體時，**[!UICONTROL Interested Learners]**&#x200B;按鈕已新增到課程頁面。 它會顯示學習者的名稱及其在管理員UI中註冊的日期。

管理員可以選取&#x200B;**[!UICONTROL Actions]**，然後選取&#x200B;**[!UICONTROL Export Report]**&#x200B;以匯出&#x200B;**[!UICONTROL Interested Learners report]**。

![](assets/register-interest.png)
_課程概觀區段，學習者可在此檢視註冊興趣選項_

檢視[下載感興趣的學習者](/help/migrated/administrators/feature-summary/courses.md#download-the-interested-learner-report)以取得詳細資訊。

## 在Salesforce應用程式中重設建議

過去，使用Adobe Learning Manager Salesforce應用程式的學習者只能選取角色和建議偏好設定一次。 如果他們的角色有所變更，他們必須切換到原生Adobe Learning Manager應用程式來更新其設定檔，並接收相關的課程建議。 透過最新的增強功能，學習者現在可以直接在Salesforce應用程式中快速重設其偏好設定，只要其工作角色、團隊或責任有所變更。

這個簡化的程式能確保學員在不離開Salesforce的情況下持續收到最新的相關課程建議。 管理員可受益於更高的學習完成率，以及使用者角色與建議內容之間更佳的協調，所有這些都不需要在交換平台上提供額外的支援或指導。

Adobe Learning Manager現在提供Salesforce應用程式中的&#x200B;**[!UICONTROL Reset Interests]**&#x200B;按鈕。 學習者現在無需離開Salesforce或登入原生Adobe Learning Manager應用程式，即可重設角色和學習偏好設定。

檢視[在Salesforce應用程式中重設建議](/help/migrated/learners/feature-summary/sfdc-app.md#reset-recommendations-in-salesforce-app)，以取得在Salesforce應用程式中重設建議的詳細資訊。

## 行事曆Widget增強功能

學習者現在可以在行事曆Widget中檢視過去和即將進行的課程。 他們可以在行事曆中移動至任何日期並檢查工作階段詳細資訊。 這表示他們可以檢閱已發生的會議，協助他們追蹤他們錯過或參加的內容。 他們還可以檢視未來24個月（包括當月）的所有近期課程，更輕鬆地提前規劃和管理他們的排程。

檢視[行事曆](/help/migrated/learners/feature-summary/learner-home-page.md#calendar)以取得有關行事曆Widget的詳細資訊。

## 在社交面板中標籤使用者

社交面板現在支援使用者標籤功能，可啟用更具針對性的討論，並改善學習社群內的共同作業。 學習者可以透過學習者應用程式、API和Adobe Learning Manager參考網站，在社交學習貼文和評論中受到標籤。

無法標籤展示板範圍外的使用者，以防止不想要的通知。 如果從系統中刪除已標籤的使用者，他們的提及會顯示為「匿名」。 不允許標籤使用者群組或&quot;@all&quot;來防止通知垃圾訊息。

* **@username標籤**：使用者可以使用「@username」格式標籤其他展示板成員。
* **範圍受限制的標籤**：只能標籤具有特定展示板存取許可權的使用者，以確保隱私權和關聯性。
* **多頻道通知**：標籤的使用者會同時收到應用程式內通知和電子郵件通知，其中包含相關貼文或評論的直接連結。

**使用案例**

* 尋求特定同事對醫療案例提供意見的醫療保健專業人員：標籤可讓醫生和護士快速通知合適的專家，確保對複雜的患者案例提供及時而準確的建議。
* 就專門主題諮詢主題專家：透過標籤專家，團隊可以直接讓合適的人參與、縮短回應時間，並改善技術或專業查詢的決策。
* 需要特定利害關係人投入的團隊討論：標籤利害關係人可確保相關決策者知道更新，並可提供投入，讓專案保持正常進行，並與業務目標一致。

檢視[社交面板中的使用者標籤](/help/migrated/learners/feature-summary/social-learning-web-user.md#tag-users-in-social-board-posts)，以取得在社交面板中標籤使用者的詳細資訊。

## 自訂管理員的限定範圍宣告許可權

自訂管理員現在可以建立公告，但僅限於其獲指派的使用者群組或目錄。 這可以防止跨組織界限的意外通訊。 自訂管理員只能為其指派範圍內的使用者建立公告。 公告的範圍可設為特定使用者群組或目錄。 完整管理員可維護所有公告的可見度和控制權，包括由特定範圍自訂管理員建立的公告。

**主要優點**

* 鎖定目標的通訊，確保公告只會送達相關對象。
* 藉由防止無關的通知影響非預期的使用者，減少資訊過載。
* 維護組織界限並防止意外的跨通訊。

**重要備註**

* 如果自訂管理員的範圍變更，受影響的宣告會顯示警告圖示，並需要個別範圍重設。
* 每個宣告都必須在範圍變更時個別更新。
* [通知宣告](/help/migrated/administrators/feature-summary/announcements.md)報告只顯示自訂管理員指派範圍內的學習者。

**使用案例**

* 特許經營組織，地區經理只需與其特許經營人溝通。
* 大型組織，擁有區域或部門管理員，負責向團隊發佈公告。

檢視[為指派的範圍建立宣告](/help/migrated/administrators/feature-summary/announcements.md#create-announcement-for-the-assigned-scope)，以取得為指派的範圍建立宣告的詳細資訊。

## 從Adobe Captivate發佈內容時選取自訂角色

從Adobe Captivate發佈內容到Adobe Learning Manager時，如果使用者有多個自訂角色，系統會提示他們選取應發佈課程的特定自訂角色。 這可確保將正確的角色所有權和許可權套用至發佈的課程。

檢視[自訂角色](/help/migrated/administrators/feature-summary/custom-role.md)，以取得建立使用者自訂角色的詳細資訊。

## 「由我儲存」Widget的增強功能

先前，選取&#x200B;**[!UICONTROL Saved By Me]**&#x200B;分段會顯示目錄中的所有可用課程。 現在，學習者在學習者首頁的&#x200B;**[!UICONTROL Saved By Me]**&#x200B;列中只會看到其已建立書籤的課程。 選取此分段會將學習者帶往目錄頁面，其中僅顯示他們已儲存的課程。

在目錄內，學習者可以套用其他篩選器來調整其搜尋。 套用篩選器時，只會顯示符合所選條件的課程。 先前加入書籤的課程只有在符合套用的篩選器時才會出現。

檢視[設定AEM網站中已儲存的課程Widget](/help/migrated/integrate-aem-learning-manager.md#configure-my-saved-courses-widgets-in-aem-sites)，以取得有關AEM網站中已儲存課程Widget的詳細資訊。

## 支援在共用課程中顯示作者姓名

先前，當課程與[對等帳戶](/help/migrated/administrators/feature-summary/peer-account.md)共用時，作者會顯示為外部作者。 現在，課程會顯示作者的名稱，無論他們是主要帳戶的內部使用者還是舊版作者（即在課程建立期間在「作者」欄位中輸入的任何名稱作為字串）。 選取「作者」會顯示他們與對等帳戶共用的課程數；不過，這些「作者」並非對等帳戶中的實際使用者。

如果從主帳戶中刪除使用者，其資料會在該處移除，但作者資訊會保留在已共用其內容的任何對等帳戶中。

>[!NOTE]
>
>這是旗標式功能，請透過[learningmanagersupport@adobe.com](mailto:learningmanagersupport@adobe.com)聯絡我們的客戶支援團隊以啟用此選項。

檢視[對等帳戶](/help/migrated/administrators/feature-summary/peer-account.md)，以取得將內容共用給對等帳戶的詳細資訊。

## 搜尋低階學習物件的可見度

以往，當課程屬於更高層級學習物件（例如學習路徑或認證）時，搜尋結果無法一致地顯示個別課程。 如果學習者僅註冊了學習路徑或認證，則搜尋僅傳回更高階結構，而不是個別課程。

透過此增強功能，學習者現在可以在搜尋結果中檢視個別課程，即使這些課程屬於學習路徑或認證亦然。 已引入新的管理員設定&#x200B;**[!UICONTROL Show all enrolled courses in search results]**。 啟用後，此設定可確保搜尋特定課程時，一律會顯示課程本身以及任何相關的「學習路徑」或「認證」。

檢視[設定](/help/migrated/administrators/feature-summary/settings.md#general-settings)以取得一般設定的詳細資訊。

## API變更

### 移轉API增強功能

Adobe Learning Manager現在支援透過移轉程式，將各種資料物件移轉至帳戶。 此程式可以透過API和使用者介面來起始。 移轉失敗時，可透過介面下載錯誤。 這些錯誤對於偵錯移轉錯誤和管理移轉執行非常有用。

在此版本中，錯誤記錄檔也可透過API下載，以進行有效率的程式化錯誤追蹤和偵錯。

**API變更**

有一個新的移轉API `runStatus`，可讓整合管理員檢查透過API觸發的移轉執行狀態，這是舊版Adobe Learning Manager所無法做到的。

此外，`runStatus` API現在提供直接連結，可下載已完成執行的錯誤記錄檔(CSV)。 請注意，連結僅七天有效，而記錄會保留一個月。

`startRun` API的回應已更新，以包含查詢新狀態端點所需的移轉專案識別碼、衝刺ID和衝刺執行ID。

#### runStatus API

**描述**

擷取現有移轉回合的狀態。

**端點**

```
GET /bulkimport/runStatus
```

**引數**

* **migrationProjectId**： （必要）。 適用於移轉專案的唯一識別碼。 移轉專案用於將資料和內容從現有的學習管理系統(LMS)傳輸到Adobe Learning Manager。 每個移轉專案都可包含多個衝刺，這些是移轉任務的較小單位。

* **sprintId**： （必要）。 移轉專案中衝刺的唯一識別碼。 短期衝刺是移轉工作的子集，其中包括要從現有LMS移轉至Adobe Learning Manager的特定學習專案（例如課程、模組、學習者記錄）。 每個衝刺都可以獨立執行，允許分階段移轉。

* **sprintRunId**： （必要）。 用於追蹤移轉專案中特定衝刺執行的唯一識別碼。 它與衝刺中定義之專案的實際移轉程式相關聯。 sprintRunId有助於監視、疑難排解及管理移轉工作。

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

`startRun` API回應已更新為包含三個額外的欄位 — migrationProjectId、sprintId和sprintRunId。 這些欄位可讓使用者使用新的runStatus API追蹤及查詢特定移轉執行的狀態。

```
curl -X GET --header 'Accept: text/html' 'https://learningmanager.adobe.com/primeapi/v2/bulkimport/runStatus?migrationProjectId=001&sprintId=10001&sprintRunId=7'
```

產生下列回應。 回應包含：

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

檢視[移轉手冊](/help/migrated/integration-admin/feature-summary/migration-manual.md)，以取得從現有LMS移轉內容的詳細資訊。

### 社交API變更（使用者標籤、評論和回覆）

Adobe Learning Manager現在支援@user社交面板中的標籤功能，讓學習者在貼文、評論和回覆中提及和通知同行。 此功能可加強整個平台的共同作業和內容探索。

此發行版本引進了新的API功能來支援使用者提及，包括增強的POST和GET端點，以及標籤使用者的新搜尋功能。

**API變更總覽**

* 更新建立包含使用者提及的貼文/評論/回覆的POST API
* 更新GET API，在回應中使用者提及資料

**使用者提及的格式**

使用下列格式提及使用者： @(user:userId)

#### 建立提及的貼文

**端點**

```
POST /primeapi/v2/posts
```

**描述**

建立包含使用者提及內容的新社交學習貼文。

**要求內文**

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

含有&#x200B;_userMentions_&#x200B;關聯性中所包含提及資料的標準貼文建立回應。

#### 使用提及內容建立評論

**端點**

```
POST /primeapi/v2/comments
```

**描述**

新增註解至包含使用者提及的貼文。

**要求內文**

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

#### 建立提及的回覆

**端點**

```
POST /primeapi/v2/replies
```

**描述**

回覆含有使用者提及的評論。

**要求內文**

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

#### 擷取提及的貼文

**端點**

```
GET /primeapi/v2/posts/{id}
```

**描述**

擷取貼文詳細資料，包括提及的使用者。

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

### 社交API變更（使用者搜尋）

**端點**

```
GET /primeapi/v2/users/search?q={searchTerm}&context=tagging
```

**描述**

搜尋可根據社交範圍設定進行標籤的使用者。

**要求引數**


* q （必要）：搜尋字詞（至少3個字元）。
* 內容：設為「標籤」可讓使用者符合提及資格。
* 展示板ID （選用）：展示板ID，可根據存取許可權篩選使用者。

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

### 學習者API的測驗效能追蹤增強功能

`GET /loResourceGrades` API已增強，可提供詳細的測驗效能資料，進而啟用更複雜的分析和自動化決策。

API回應現在包含兩個額外的欄位：

* **[!UICONTROL highestScore]**：學習者在所有測驗嘗試中取得的最佳分數
* **[!UICONTROL maxScore]**：測驗的總可能分數

**API回應範例**

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

回應時，**course:15067_30122_41715_1_3400468**&#x200B;是正在要求資訊的學習物件資源等級識別碼。 可從`learningObjectResourceGrad` API取得`GET /enrollments/{id}`e ID。

### API回應支援作者名稱區分大小寫

API回應現在會提供在建立或更新課程時所輸入的舊版作者名稱的確切案例。 這可確保在學習者UI和公用API中顯示的名稱一致。

* 新增作者名稱時，案例會儲存並完全依照輸入傳回。
* 如果移除現有的作者名稱，並以不同的案例重新新增，則會接受更新的案例，並反映在使用該作者名稱的所有課程中。
* 先前儲存的名稱不會執行自動移轉；只有新新增或更新後的名稱會遵循此行為。

### 日曆API增強功能

行事曆現在會載入使用者所選月份的工作階段。 若要透過API擷取過去和即將進行的工作階段，已將新的`year`引數新增至學習者端點`GET /users/{id}/calendar`。 `month`和`year`引數必須一起提供，才能擷取工作階段詳細資料。

**樣本CURL**

```
curl -X GET --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth a4ae04eb9f06f4bf88abcde17' 'https://abc.adobe.com/primeapi/v2/users/12345678/calendar?month=7&year=2025&currentMonthOnly=false&filter.allSessions=false'
```

### 透過管理員API支援標籤完成

先前，公用API不支援在多重註冊情境中執行個體型完成標示。 透過此增強功能，您現在可以在要求內文`POST /users/{userId}/userModuleGrade`中包含課程執行個體ID，管理員可以標籤特定執行個體的完成。

### 設定SCORM報告的使用者ID偏好設定

有些客戶會要求學習者的UUID （通用唯一識別碼），而非SCORM內容完成的預設user_id。 使用UUID可獲得跨學習計畫更準確的追蹤，並防止MAU （每月活躍使用者）帳戶中授權使用量的重複。

為了支援此功能，已新增新的帳戶層級設定`reporting_userid_preference`。 啟用後，每當學習者完成SCORM內容時，此設定會傳送UUID來取代user_id。

>[!NOTE]
>
> 請透過[learningmanagersupport@adobe.com](mailto:learningmanagersupport@adobe.com)聯絡我們的客戶支援團隊以設定此設定。

新屬性`reportingUserIdPreference`已引入`get /account`以追蹤使用者ID偏好設定。

### 撰寫共用課程中的資訊

「學習物件API」已更新「作者」資訊的傳回方式，以區分主帳戶課程與共用至對等帳戶的課程：

* 共用課程（對等帳戶）：作者詳細資料現在會在新屬性`authorDetails`下傳回。 即使課程源自其他帳戶，此屬性仍會提供作者名稱。

* 主要帳戶課程：作者資訊會繼續以現有`authors`屬性傳回，目前行為不會有任何變更。

這項變更可確保透過API公開主要和共用課程之作者資料的一致性，同時保留現有整合的相容性。

## Webhook的變更

### 使用聯結器註冊LinkedIn學習Webhook

之前，管理員必須透過API手動將LinkedIn學習Webhook註冊至Adobe Learning Manager。 透過此增強功能，LinkedIn Learning (LIL)聯結器現在可於ALM中設定新連線時自動支援webhook註冊。 將在LinkedIn學習設定頁面上自動填入&#x200B;**OAuth伺服器URL**&#x200B;和&#x200B;**租使用者伺服器URL**。

檢視[LinkedIn學習專案](/help/migrated/integration-admin/feature-summary/connectors.md#linkedin-learning-connector)，瞭解有關LinkedIn學習專案整合的詳細資訊。

### LinkedIn學習中MAU授權使用方式的變更

先前，針對MAU （每月活躍使用者）帳戶，當學習者直接在LinkedIn學習平台上完成LinkedIn學習課程時，Adobe Learning Manager不會計算授權使用量。 僅針對透過Adobe Learning Manager播放器上線的課程觸發授權消耗，導致追蹤每月活躍使用者(MAU)不準確。

透過此增強功能，Adobe Learning Manager現在會在學習者使用LinkedIn學習平台中的課程時產生外部Webhook。 當Adobe Learning Manager收到此webhook時，它會計算授權使用情況，以確保跨兩個平台的準確追蹤。

## 報告變更

### 學習者成績單中由講師標籤的完成

增量學習者成績單現在會擷取由講師標籤的完成，即使出席記錄是在工作階段日期之後。
此增強功能解決增量學習者成績單中的關鍵差距，即如果出席記錄是在原始工作階段日期之後，則先前會遺漏講師標籤的完成。

增量學習者成績單是排程報告，僅擷取指定期間內發生的變更（例如完成或進度更新），而不是提供完整的歷史資料傾印。 它們通常用於自動化、儀表板和整合，讓使用者能夠有效地追蹤最近的學習活動，而無需每次都處理整個成績單歷史記錄。

* **標示完成日期（UTC時區）資料行**：新的時間戳記資料行，可擷取講師將工作階段或模組標示為完成的確切日期和時間。
* **增強的完成來源追蹤**：追蹤記錄完成的特定講師和模組（例如「教室」）。

這些變更可確保工作階段日期之後標籤的完成專案能正確反映在增量學習者成績單中。

**使用案例**

* 擁有教室工作階段的組織，其講師可在實際工作階段後標籤出席天數。
* 依賴增量學習者成績單的自動化系統或控制面板，以符合合規性或提供報告。

![在Adobe學習中顯示標籤完成日期（以黃色醒目提示）的學習者成績單報告](/help/migrated/assets/mark-completion-column.png)
_學習者成績單報告以黃色顯示新欄，醒目顯示每個使用者的個別完成日期_

檢視[學習者成績單](/help/migrated/administrators/feature-summary/learner-transcripts.md)，以取得學習者成績單報告的詳細資訊。

### 具有延伸資料欄位的增強型使用者報告

使用者報表現在包含其他欄位，以增強使用者追蹤和組織對應。 這些更新可簡化使用者識別、支援與下游使用者管理工作流程的整合、提升對報告關係的理解，並維護組織界限以防止意外的跨通訊。

* 內部使用者ID欄：提供不重複的內部識別碼，以便跨不同系統和API端點順暢地追蹤使用者。
* 經理電子郵件欄：包含組織階層追蹤的直接經理聯絡資訊。

![顯示內部使用者ID和管理員電子郵件欄以黃色反白顯示的使用者報告](/help/migrated/assets/user-report-columns.png)
_強調內部使用者ID和管理員電子郵件地址的使用者報告，以簡化使用者管理_

檢視[下載使用者報告](/help/migrated/administrators/feature-summary/add-users-user-groups.md#download-the-user-report)，以取得使用者報告的詳細資訊。

### FTP、自訂FTP和方塊中的使用者報表

**總覽**

除了現有的工作API之外，使用者報表現在可用於盒子、FTP和自訂FTP聯結器。 這些報告提供內部使用者ID、使用者電子郵件、名稱、管理員電子郵件、使用者型別等詳細資訊。

可隨選或排程產生報表，並將資料儲存在各自的聯結器中，以便輕鬆存取和分析。 此增強功能可改善使用者活動的監控和稽核，並支援更好的安全性和合規性追蹤。

這些報告可與現有報告一併取得，例如使用者註冊、登入存取、gamification和訓練，讓管理員從單一位置存取所有基本報告，以簡化資料管理和分析。

檢視[聯結器](/help/migrated/integration-admin/feature-summary/connectors.md)，以取得有關FTP、自訂FTP和方塊聯結器的詳細資訊。

### 在學習者成績單中包含暫停的使用者

**總覽**

組織現在可以在學習者成績單中包含已暫停的使用者（具有停用外部設定檔的使用者），以確保完整的歷史學習資料保留。

* 帳戶層級旗標可設定暫停的使用者可見度，讓暫停的使用者顯示在學習者成績單中。
* 即使停用已暫停的外部設定檔後，仍會保留歷史資料。

**實作需求**

* 請聯絡您的客戶成功經理(CSM)以啟用帳戶層級標幟。

>[!NOTE]
>
>依預設，現有帳戶會停用此旗標，而且必須為新帳戶明確要求此旗標。

檢視[學習者成績單](/help/migrated/administrators/feature-summary/learner-transcripts.md)文章詳細資訊。

### 具有直接存取連結的工作輔助報告

**總覽**

工作輔助報告已增強，包含工作輔助的直接下載連結，精簡管理員和作者的內容管理和稽核程式。 此增強功能提供直接檔案下載，以及報表中的URL存取權。 省去尋找及下載工作輔助工具的手動工作，以進行合規性或協助工具稽核。

* 工作輔助連結欄：從報表中直接存取工作輔助檔案和外部URL。
* 角色型存取控制：連結存取許可權取決於使用者角色和目錄許可權。
* 已刪除的工作輔助仍然可以存取，如果仍連結到使用中的課程。

**使用案例**

* 作者或管理員會根據大型組織的要求，定期對工作輔助進行協助工具稽核。
* 任何需要以角色為基礎快速存取工作輔助檔案的情境，以進行檢閱或法規遵循。

![](/help/migrated/assets/job-aid-report.png)
_工作輔助報告會顯示直接下載連結，讓您在Adobe Learning Manager中輕鬆存取及下載工作輔助_

檢視[工作輔助報告](/help/migrated/administrators/feature-summary/reports.md#job-aids-report)，以取得工作輔助報告的詳細資訊。

## 此更新中修正的錯誤

* 現在可以正確為非互動式測驗產生L2測驗分數，包括完成測驗的使用者詳細資訊。
* 現在，在連線設定期間，當驗證機制設定為「簽章」時，就會將簽章正確傳送至目標主機。
* 工作階段完成後，在Adobe Connect工作階段期間建立的虛擬使用者沒有刪除。 SnapLogic管線現在會正確移除這些使用者，即使`principals-delete` API先前傳回200回應而未刪除這些使用者。
* API回應中的`null` `eventDetail`物件不再造成例外狀況。 系統現在會略過Null專案並處理整個陣列，以確保完成錄製。
* 意見回饋報表中的意見回饋日期欄現在會顯示正確的日期。 以前，秒錯誤地傳遞給Date建構函式，它期望毫秒，導致日期顯示為1970年1月。 已修正此問題，以確保在產生意見反應報表時正確顯示日期。
* 學習者現在可以更新Flex學習路徑的註冊，即使其中一個課程例項已淘汰。 以前，選擇新執行個體會導致控制檯錯誤（無法讀取未定義的屬性）並阻止更新。
* 「學習路徑」中的資源名稱現在可正確顯示，不會中斷中間字。
* 現在為新使用者建立連線時，會從LIL聯結器啟用LinkedIn學習Webhook。 系統也會透過私人API註冊帳戶，並在LinkedIn學習設定頁面上顯示其他設定資訊（OAuth URL和租使用者URL）。
* 透過SAML工作流程更新的使用者屬性值(`UpdateUserWorkerTask`)現在會以其原始大小寫儲存，而非轉換為小寫。
* 課程中的模組重新排序後，必修模組數量不再重設為「全部」；數量現在維持設定狀態。
* Go1管道現在會將兩個字母的程式碼對應到四個字母的程式碼，以一致的方式處理語言程式碼，類似於LinkedIn學習管道。
* 在「淘汰+帳戶」中，學習者從認證取消註冊後啟動學習路徑課程時，先前看到「此課程不存在」。 註冊來源現在已正確更新，可讓「學習路徑」中的課程順利啟動。
* 當module_version.csv檔案包含具有空白或Null值的contentType欄位時，課程建立現在可正常運作，不會出現任何問題。
* 依目錄或目錄標籤篩選時，課程現在會正確顯示。 以前，在課程頁面上套用這些篩選器時，即使課程與目錄相關聯，也不會顯示課程。
* 在學習者應用程式中，按下Fluidic Player中的TAB鍵時「進入全熒幕」按鈕卡住。 鍵盤導覽現在可在所有熒幕元素中正確移動。
* 在經理應用程式的合規性控制面板中，將游標暫留在較長的課程名稱上，現在會顯示已註冊或合規性課程的全名。
* 在module.csv中，模組可見性欄只接受「共用」或「隱藏」。 移轉期間，任何其他值都會觸發錯誤，避免後端發生失敗。
* 停用UUID時，若使用混合大小寫電子郵件建立新管理員，將不再產生重複的使用者專案。 系統現在會一致地處理電子郵件大小寫，以避免重複專案。
* 備註PDF現在可正確顯示阿拉伯文、希臘文、希伯來文、印地文、泰文和烏克蘭文等語言的課程。 過去，即使字元在播放器中正確顯示，下載的PDF仍會顯示扭曲的字元。

## 系統需求

檢視[Adobe Learning Manager系統需求](/help/migrated/system-requirements.md)。

## 發行說明

如需最新版本的更新，請參閱[發行說明](/help/migrated/release-note/release-notes.md)。

## Adobe Learning Manager舊版

* [Adobe Learning Manager 2025年5月發行版本](/help/migrated/whats-new-may-2025.md)
* [Adobe Learning Manager 2025年11月發行版本](/help/migrated/whats-new-nov-24.md)


