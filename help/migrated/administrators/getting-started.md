---
description: 本檔案為組織提供設定Adobe Learning Manager的建議方法。 Learning Manager團隊建議以分階段方式開始使用應用程式。 您不必以特定順序遵循所有階段。
jcr-language: en_us
title: 設定Learning Manager的最佳實務指南
contentowner: jayakarr
preview: true
source-git-commit: 46afb6603456ced9d7e2aaf98d07ec92fee30c0b
workflow-type: tm+mt
source-wordcount: '3384'
ht-degree: 0%

---



# 設定Learning Manager的最佳實務指南

本檔案為組織提供設定Adobe Learning Manager的建議方法。 Learning Manager團隊建議以分階段方式開始使用應用程式。 您不必以特定順序遵循所有階段。

根據您的組織設定，這些階段可由三個不同的角色執行，或由一個或多個個人執行。 這三個角色如下：

1. **IT管理員** - IT管理員會在組織中執行與Learning Manager應用程式相關的啟動或整合相關活動。 IT管理員也可以新增單一/多個使用者，並執行「整合管理員」的角色。
1. **作者**  — 作者建立組織學習需求所需的學習內容。 您組織的培訓或學習內容的作者可以開始建立Learning Manager應用程式所需的基本內容。
1. **Learning Manager管理員** - Learning Manager應用程式管理員會執行設定活動。 在某些公司中，IT管理員可能也會擔任Learning Manager應用程式管理員。

您可以瀏覽下面提供的資訊圖，以取得階段和對應工作的概觀。

![](assets/learning-manager-getting-started.jpg)

在此階段，我們假設您的組織已收到授權金鑰，且您已啟用Learning Manager帳戶。 如資訊圖表中所述，三個磁軌的說明如下：

## 第1階段 — 技術設定（IT管理員） {#phase1technicalsetupitadministrator}

在路線1中，您組織的IT管理員可以切換到Learning Manager應用程式中的整合管理員角色，並執行以下一些啟用和整合：

### 啟用/新增作用中欄位（Learning Manager管理員） {#enableaddactivefieldscaptivateprimeadministrator}

除了使用者在註冊期間提供的作用中欄位之外，管理員還可以新增更多作用中欄位。 管理員也可以啟用/停用使用者欄位。 這些作用中欄位的值是從與使用者帳戶相關聯的各種資料來源的中繼資料產生的。 請參閱 [使用中欄位說明](feature-summary/add-users-user-groups.md#active-fields) 以取得詳細資訊。

### 單一登入(SSO) {#singlesignonsso}

您可以使用Adobe ID或使用單一登入存取Learning Manager應用程式。 單一登入是一種機制，可讓使用者驗證一次，並多次存取多個應用程式。 組織不強制進行此設定。 如果貴組織擁有以SAML 2.0為基礎的SSO提供者，則可用來設定Learning Manager應用程式。 您的組織層級和Learning Manager應用程式需要此設定。 如果您選擇使用SSO，請聯絡Adobe支援以接收設定指示。 請參閱 [設定說明](feature-summary/settings.md) 以取得詳細資訊。

### 大量匯入使用者 {#bulkimportofusers}

當貴組織中有大量使用者時，您可以使用.CSV檔案大量匯入所有使用者至Learning Manager應用程式。 在執行此工作之前，建議您以.CSV格式從貴組織的人力資源應用程式匯出使用者清單。 即使您在此階段沒有大量匯入使用者，也可以熟悉CSV格式。 若要從Learning Manager的匯入程式開始，請上傳.CSV檔案，並將應用程式資料欄位與組織的CSV欄對應。 請參閱 [大量匯入說明](add-users-in-bulk.md) 以取得詳細資訊。

### FTP聯結器整合 {#ftpconnectorintegration}

如果您面臨組織中的員工持續新增或移除，您可以選擇使用FTP聯結器自動大量匯入使用者。 您必須先建立連線，然後才能上傳CSV並將CSV的屬性對應到對應的Learning Manager欄位。 您可以排程自動匯入程式，並視需要將其同步化。 請參閱 [FTP聯結器說明](../integration-admin/feature-summary/connectors.md#ftpconnector) 以取得詳細資訊。

### Salesforce聯結器整合 {#salesforceconnectorintegration}

如果您的組織中有Salesforce帳戶，您可以將所有使用者從Salesforce匯入Learning Manager應用程式的程式自動化。 如果您想要使用此功能，可以使用Salesforce聯結器將Learning Manager與Salesforce帳戶整合併自動化資料同步。 使用自動排程功能，定期執行自動使用者匯入。 您也可以每天執行同步。 請參閱 [Salesforce聯結器說明](../integration-admin/feature-summary/connectors.md#sfconnector) 以取得詳細資訊。

### Adobe Connect整合 {#adobeconnectintegration}

如果您在組織中使用Adobe Connect，您可將其與Adobe Learning Manager應用程式整合，為學習者提供順暢的使用者體驗。 此整合可讓您的學習者按一下滑鼠，直接在Learning Manager應用程式中存取虛擬教室，無需再次登入Adobe Connect。 使用此功能，您的學習者也可以在Learning Manager應用程式中使用已錄製的虛擬課堂講座。 若要整合，請先整合設定。 使用 **「設定> Adobe Connect >立即設定」** 提供連線URL和登入憑證並整合。 請參閱 [Adobe Connect整合說明](feature-summary/adobeconnect-integration.md) 以取得詳細資訊。

### Salesforce應用程式註冊 {#salesforceappregistration}

您的企業學習者可以直接在其Salesforce帳戶中順利存取Learning Manager應用程式。 學習者可以從Salesforce應用程式存取其指派的學習內容，例如課程、學習計畫和工作輔助。 使用者也可以從Salesforce內的Learning Manager應用程式存取通知和公告。 若要使用此功能，您必須在Learning Manager應用程式中註冊Salesforce精選應用程式。 請參閱 [Salesforce應用程式說明](../integration-admin/feature-summary/sfdc-app.md) 以瞭解安裝和使用指示。

## 第2階段 — 網站設定（Learning Manager管理員） {#phase2siteconfigurationcaptivateprimeadministrator}

您組織的Learning Manager應用程式管理員必須先設定或設定部分功能，才能開始為學習者實作這些功能。

### 品牌化 {#branding}

組織可能想要在Learning Manager應用程式中顯示公司標誌、在URL中擁有自己的網域、顯示組織名稱，以及顯示符合組織品牌的色彩配置。 Learning Manager可讓組織使用所有這些功能。 如果您想要自訂設定並使用自己的品牌，請按一下左窗格的「品牌」區段。 按一下所有這些選項旁的「編輯」 ，並根據您的需求進行自訂。 請參閱 [品牌和主題說明](feature-summary/themes.md) 以取得詳細資訊。

### 新增使用者/使用者群組 {#addusersusergroups}

由於學習者是您學習內容的主要使用者，因此在學習管理系統中新增使用者是主要步驟。 將使用者新增至Learning Manager應用程式並指派角色給他們。 您可以透過下列方式新增使用者：

#### 新增使用者（內部） {#addusersinternal}

* **單一使用者**  — 將單一使用者新增至Learning Manager應用程式可讓您在大量新增使用者之前，先行試用部分使用者。 此外，當您想要在大量匯入使用者後根據需要新增更多單一使用者時，此選項也很有用。
* **自助註冊**  — 此選項可讓管理員讓員工在Learning Manager中註冊自己。
* **大量匯入** （使用CSV上傳） — 使用此選項可將使用者大量匯入Learning Manager應用程式中。 使用此功能之前，必須先以CSV格式保留使用者清單，作為先決條件。

#### 新增使用者（外部設定檔） {#addusersexternalprofiles}

* 透過外部註冊 — 使用此選項，您可以將組織的外部部門成員或外部員工註冊到應用程式。

#### 新增使用者群組 {#addusergroups}

Learning Manager應用程式會根據類似屬性產生預設使用者群組。 除了預設群組之外，您也可以根據指定、位置等引數產生自訂的使用者群組，以便在「遊戲」及報表等中利用這些群組。 請參閱 [新增使用者說明](feature-summary/add-users-user-groups.md) 以取得詳細資訊。

### 指派角色 {#assignroles}

將使用者新增到Learning Manager後，管理員可以根據組織要求開始為使用者指派作者、管理員或整合管理員角色。 若要將角色指派給使用者，您可以在管理員登入中按一下 **[!UICONTROL Users]**  在左窗格中，選取每個使用者名稱的核取方塊，然後按一下 **[!UICONTROL Actions]** 下拉式清單，以選擇要指派的角色。 管理員角色會根據CSV檔案中貴組織提及的角色/許可權，由AdobeLearning Manager指派給使用者。 您也可以使用「編輯使用者」工作流程來變更作為管理員的使用者角色。 請參閱 [新增使用者說明](feature-summary/add-users-user-groups.md) 以取得詳細資訊。

### 通知範本 {#notificationtemplates}

通知對於學習管理系統中的使用者瞭解其狀態或獲知相關事件/活動資訊十分有用。 在建立課程、設定功能或消費課程時，使用者會經歷數個事件，以觸發通知學習者、其經理、管理員或作者。 Learning Manager在應用程式中提供各種電子郵件通知範本。 身為管理員，您可以根據組織需求自訂這些角色。 若要建立電子郵件通知，請選擇 **電子郵件範本** 然後按一下範本名稱。 請參閱 [電子郵件範本說明](feature-summary/email-templates.md) 以取得詳細資訊

**關閉電子郵件通知（建議）**

預設情況下，通知會在Learning Manager應用程式中啟用。 如果您不想通知組織的員工，可以在此階段關閉通知。

### 徽章 {#badges}

徽章是衡量員工完成課程後可取得之成就的指標。 全球的專業人員使用這些徽章作為特定技能或學習成績的表示。 您可以建立徽章集合，以便在學習內容完成後將其指派給學習者。 若要開始建立徽章，您可以按一下 **[!UICONTROL Badges]** 功能。 請參閱  [徽章說明](feature-summary/badges.md) 以取得詳細資訊。

### 意見反應 {#feedback}

意見反應是LMS的重要因素之一，可衡量學習者的學習進度並確保學習內容的品質。 Learning Manager為使用者提供兩種型別的意見回饋選項。

* L1意見是學習者完成課程後提供的意見。
* L3意見是經理根據課程對學習者行為和日常活動的影響，提供給學習者的意見。

組織可選擇性使用此功能。 管理員可以根據您的組織需求自訂意見範本。 若要使用此功能，管理員必須在課程執行個體層級啟用L1和L3意見選項。 若要設定意見反應，請選擇任何課程，按一下左窗格中的「執行個體預設值」並啟用意見反應選項。 請參閱 [意見回饋說明](feature-summary/courses.md) 以取得詳細資訊。

### 遊戲 {#gamification}

讓學習者在消費內容時保持參與，是組織面臨的挑戰之一。 遊戲化可透過遊戲技術吸引並激勵學習者達成目標，進而提高課程完成率。 學習者可與同事競爭各種學習活動的分數，並取得銅、銀、金和白金級成績。 管理員可以啟用/停用每個遊戲化任務，並修改任務點數配置。 Learning Manager提供遊戲化功能及部分預設設定。 您可以在一段時間內開始使用具有預設設定的功能，然後您可以選擇自訂。 您可以自行選擇設定/變更此功能的設定。 如果您的組織有主題專家，我們建議您在使用之前先進行設定。 請參閱 [遊戲化說明](feature-summary/gamification.md) 以取得詳細資訊。

### 建立學習物件 {#createlearningobjects}

這是所有三個軌道（軌道1、軌道2和軌道3）會聚的邏輯階段，讓您採取下一步行動。

此時，建立模組和課程後，您就可以開始建立較高層級的學習物件（例如認證、學習計畫或工作輔助）以繼續進行。 開始建立學習物件之前，請確定您已在Learning Manager應用程式中新增一些使用者、建立了一些模組和課程。

#### 建立認證 {#createcertifications}

認證是學習者完成學習內容的證明，或學習者單次或循環時間範圍內的成就證明。 完成課程後向學習者提供認證，可增加學習者註冊學習內容的機會。 身為管理員，您可以建立內部託管或由第三方執行的認證計畫。 在內部認證中，定義學習者需完成才能獲得認證的課程。 建立認證之前，請確認您帳戶中有某些可用的課程。 請參閱  [認證說明](feature-summary/certifications.md) 有關如何建立認證的詳細資訊。

#### 建立工作輔助 {#createjobaids}

工作輔助是訓練內容的存放庫，可供沒有任何註冊或完成條件的學習者存取。 學習者可在工作中取得協助時，參考這些工作輔助，以在組織中執行任何活動或任務。 雖然課程建立過程中不強制使用工作輔助，但Learning Manager團隊建議您建立工作輔助作為組織的最佳實務。 請參閱  [工作輔助說明](../authors/feature-summary/job-aids.md) 以取得如何建立工作輔助的相關資訊。

#### 建立學習計畫 {#createlearningprograms}

學習計畫是一組設計獨特的課程，可滿足特定學習者的目標。 在建立學習計畫之前，請確定您已建立一些課程或您的帳戶中有現有課程可使用。  雖然組織可以自行選擇使用此功能，Learning Manager團隊仍建議您使用此功能，向員工灌輸重點學習的理念。 若要開始使用學習計畫，請按一下左窗格中的「學習計畫」，從目錄中選擇一組課程並發佈。 請參閱 [學習計畫說明](feature-summary/learning-programs.md) 以取得特定指示。

### 建立目錄 {#createcatalogs}

您可以在組織中使用目錄來建立目標內容，或將內容分類為已定義的學習者集。 在Learning Manager中，目錄是課程、認證或學習計畫等學習物件的集合。 建立目錄時，您可以選擇自己選擇的學習物件。 在建立目錄之前，請確定您已建立一組課程、認證或學習計畫。 如果您想要將學習物件指派給任何內部或外部使用者群組，可以使用一組學習物件自訂建立目錄。 請參閱  [目錄說明](feature-summary/catalogs.md) 以取得有關目錄的詳細資訊。

### 開啟電子郵件通知/使用者存取 {#turnonemailnotificationsuseraccess}

在此階段，您可以開啟傳送電子郵件通知給應用程式使用者，也可以啟用使用者存取權。

## 第3階段 — 撰寫課程（作者） {#phase3authoringcoursesauthor}

您組織中的內容開發人員或作者可以開始建立學習內容。 您必須建立模組和課程，因為這些模組和課程會構成Learning Manager應用程式中所有學習內容的基礎。

### 建立模組 {#createmodules}

模組是Learning Manager應用程式的基本建置組塊。 若要組織您的學習內容，請以作者身分開始建立模組。 Learning Manager可讓您從四種課程模組中選擇任一種，例如教室、自學、活動和虛擬教室模組。 請參閱  [模組說明](../authors/how-to-choose-modules.md) 瞭解哪種型別的課程模組最適合您組織的需求。

### 建立課程 {#createcourses}

管理員可以在Learning Manager應用程式中擔任作者角色並建立課程。 在Learning Manager應用程式中，課程是基本單位，包含可指派給學習者的模組集。 學習者會使用課程。 您可以透過選擇先前建立的課程模組、建立您希望學習者從課程中習得的技能的關聯、建立課程等級、學分和徽章的關聯、根據您的選擇選取工作輔助、先決條件和資源，以及發佈課程來開始建立課程。 您也可以建立多個課程例項，以便將課程例項指派給位於不同時區的多個學習者、進行排程等。 請參閱  [課程說明](../authors/feature-summary/courses.md)以取得如何建立課程的詳細資訊。

### 建立學習物件 {#Createlearningobjects-1}

這是所有三個軌道（軌道1、軌道2和軌道3）會聚的邏輯階段，讓您採取下一步行動。

此時，建立模組和課程後，您就可以開始建立較高層級的學習物件（例如認證、學習計畫或工作輔助）以繼續進行。 開始建立學習物件之前，請確定您已在Learning Manager應用程式中新增一些使用者、建立了一些模組和課程。

#### 建立認證 {#Createcertifications-1}

認證是學習者完成學習內容的證明，或學習者單次或循環時間範圍內的成就證明。 完成課程後向學習者提供認證，可增加學習者註冊學習內容的機會。 身為管理員，您可以建立內部託管或由第三方執行的認證計畫。 在內部認證中，定義學習者需完成才能獲得認證的課程。 建立認證之前，請確認您帳戶中有某些可用的課程。 請參閱  [認證說明](feature-summary/certifications.md) 有關如何建立認證的詳細資訊。

#### 建立工作輔助 {#CreateJobaids-1}

工作輔助是訓練內容的存放庫，可供沒有任何註冊或完成條件的學習者存取。 學習者可在工作中取得協助時，參考這些工作輔助，以在組織中執行任何活動或任務。 雖然課程建立過程中不強制使用工作輔助，但Learning Manager團隊建議您建立工作輔助作為組織的最佳實務。 請參閱  [工作輔助說明](../authors/feature-summary/job-aids.md) 以取得如何建立工作輔助的相關資訊。

#### 建立學習計畫 {#Createlearningprograms-1}

學習計畫是一組設計獨特的課程，可滿足特定學習者的目標。 在建立學習計畫之前，請確定您已建立一些課程或您的帳戶中有現有課程可使用。  雖然組織可以自行選擇使用此功能，Learning Manager團隊仍建議您使用此功能，向員工灌輸重點學習的理念。 若要開始使用學習計畫，請按一下左窗格中的「學習計畫」，從目錄中選擇一組課程並發佈。 請參閱 [學習計畫說明](feature-summary/learning-programs.md) 以取得特定指示。

## 第4階段 — 管理學習管理系統（Learning Manager管理員） {#phase4managingyourlmscaptivateprimeadministrator}

### 公告 {#announcements}

公告對於組織而言十分實用，可一次將任何重要資訊散發給帳戶的所有學習者。 在Learning Manager應用程式中，宣告是多媒體訊息（文字、影像或視訊），管理員可製作並廣播至定義的使用者群組和學習物件集。 您可以立即傳送宣告，或安排在特定日期自動觸發。 如果您想要在Learning Manager應用程式中使用此功能，請從左窗格中選擇「公告」，然後按一下「新增」以建立公告。 請參閱 [公告說明](feature-summary/announcements.md) 以取得詳細資訊。

### 使用者註冊 {#userenrollment}

使用者註冊是LMS應用程式的重要步驟。 在此階段，您可以開始將學習者註冊到Learning Manager應用程式的各種學習物件。 您可以手動或使用學習計畫自動註冊學習者。

#### 手動註冊 {#manualenrollment}

* **自助註冊 —** 如果您在建立學習物件時啟用此選項，學習者可以向學習物件註冊自己。
* **經理核准**  — 如果您在建立課程時在註冊型別中選擇此選項，經理需要核准學習者的註冊。
* **經理指派**  — 如果您在建立課程時選擇此註冊型別，則此類課程必須由經理指派。
* **管理員註冊**  — 在此情況下，管理員可以根據組織的需求註冊一些學習者。

請參閱 [使用者註冊說明](feature-summary/courses.md)內容以取得詳細資訊。

使用下列四種方式手動註冊學習者以學習物件：

### 自動註冊 {#automatedenrollment}

使用學習計畫自動將學習者註冊至學習物件。

#### 學習計畫（根據觸發器） {#learningplansbasedontriggers}

您可以使用學習計畫，根據特定事件的發生次數，自動將課程、學習計畫或認證指派給學習者。 例如，

* 新使用者已新增
* 使用者變更使用者群組
* 學習者完成學習物件
* 使用者完成技能

請參閱 [學習方案說明](feature-summary/learning-plans.md)  內容以取得詳細資訊。

### 建立報表 {#createreports}

在此階段，您可以開始建立和管理各種型別的報表。

Adobe Learning Manager可讓您建立各種報表來追蹤、監控及控制學習者活動。 您可以使用下列三種報告功能來產生報告：

* **報表控制面板**  — 建立摘要報表，根據使用者群組、成效、學習者課程時間等不同類別，針對學習者的學習內容使用情況提供可行的深入分析。
* **學習者成績單**  — 建立以學習者為中心的報表，包含從註冊日到至今的學習者完整歷史記錄。
* **課程報告**  — 根據個別課程建立學習者的課程消耗統計資料。 您也可以在課程層級建立測驗報告。

請參閱  [報表說明](feature-summary/reports.md) 以取得報表產生程式的詳細資訊。

如需Learning Manager應用程式功能使用情況的其他相關資訊，請參閱 [Learning Manager說明](../topics.md) 根據每個角色而定。
