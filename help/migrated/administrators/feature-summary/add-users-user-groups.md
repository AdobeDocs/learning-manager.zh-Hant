---
description: 瞭解如何使用逐步指示，將內部和外部使用者新增到Adobe Learning Manager。 探索手動輸入、大量匯入和自動使用者同步處理等不同方法，以簡化使用者管理並增強您的學習平台。
jcr-language: en_us
title: 在Adobe Learning Manager中新增使用者
contentowner: manochan
exl-id: 7df98f2b-c422-4733-8ce4-5489506d4fdf
source-git-commit: c2a4a0ea8c9a4a5f28427a95caf63f0690b6dcc7
workflow-type: tm+mt
source-wordcount: '2257'
ht-degree: 0%

---


# 在Adobe Learning Manager中新增使用者

在Adobe Learning Manager中，使用者是指使用平台進行學習或訓練的學習者。 有兩種使用者：內部使用者和外部使用者。

內部使用者是您組織的員工或團隊成員。

外部使用者是指公司外的學習者，例如客戶、合作夥伴、廠商或客戶，可存取您的學習內容。

Adobe Learning Manager (ALM)可讓管理員使用各種方法（包括手動輸入、CSV上傳、自助註冊和系統整合），來建立和管理內部和外部使用者。

## 內部使用者

Adobe Learning Manager中的內部使用者是指您組織內的員工或團隊成員。 您可以手動新增、大量上傳檔案，或透過系統整合匯入檔案。 新增這些使用者後，您可以將其組織到群組中、指派課程並監視其學習進度。

Adobe Learning Manager中的使用者可以根據其獲指派的角色承擔不同的責任及管理不同的工作。 每個角色（包括管理員、作者、講師和整合管理員）都提供一組量身打造的特定功能，以支援使用者在平台內的責任。

Adobe Learning Manager支援下列使用者角色：

* **管理員**：管理使用者和使用者群組、指派角色，以及設定系統範圍的喜好設定，例如資料來源、允許的網域和顯示選項。 管理員也負責建立及組織學習內容、追蹤學習者進度、產生報表，以及設定與外部系統的整合。
* **作者**：建立及管理內容，包括模組及課程。
* **經理**：監督團隊學習活動、指派課程團隊成員、核准請求，以及提供意見回饋。
* **整合管理員**：管理ALM與外部平台之間的系統整合和資料連線。
* **自訂角色**：管理員可以建立自訂角色，根據使用者的職責為其提供量身打造的存取權。 請參閱本文章，深入瞭解自訂角色。

### 新增內部使用者的方法

管理員可以使用以下方法新增內部使用者：

* **新增單一使用者**：一次手動新增一個使用者。
* **自助註冊設定檔**：允許學習者使用管理員建立的註冊連結在Adobe Learning Manager中自助註冊為學習者。
* **透過CSV大量上傳**：上傳CSV檔案以一次新增多個使用者。

### 手動新增內部使用者

管理員可以手動新增個別使用者，方法是輸入其名稱、電子郵件ID、唯一識別碼及管理員名稱。 Adobe Learning Manager中的唯一識別碼是管理員在建立使用者時指派的必要識別碼。 每個使用者都必須有專屬的值，並作為整個系統的一致參考。

>[!INFO]
>
>觀看這場ALM Academy培訓，瞭解更多有關在Adobe Learning Manager中新增單一使用者的資訊。<br>[![按鈕](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555534)</br>

若要將單一使用者新增至Adobe Learning Manager：

1. 以管理員身分登入。
2. 選取&#x200B;**使用者**，然後選取&#x200B;**內部**。
3. 選取&#x200B;**新增**，然後選取&#x200B;**單一使用者**。

   ![](assets/add-single-user.png)
   _管理員介面顯示手動新增單一內部使用者的選項_
4. 在&#x200B;**新增使用者**&#x200B;提示上，輸入使用者的&#x200B;**名稱**、**電子郵件**&#x200B;和&#x200B;**設定檔** （職稱）。

   ![](assets/add-a-user-prompt.png)
   _輸入新使用者的姓名、電子郵件、唯一識別碼和設定檔的欄位_
5. 搜尋使用者的管理員，並從管理員清單中選取名稱。
6. 選取&#x200B;**新增**。
使用者會收到包含存取登入URL的歡迎電子郵件。


### 允許內部使用者自行註冊

自助註冊是自助式上線流程，使用者可在此流程中造訪註冊URL、輸入其詳細資訊，以及自動在平台中註冊。 此方法可讓使用者透過提供的URL註冊自己，以儘量減少管理工作。

若要建立使用者的自我註冊URL：

1. 以管理員身分登入。
2. 選取&#x200B;**使用者**，然後選取&#x200B;**內部**。
3. 選取右上角的&#x200B;**新增**，然後選取&#x200B;**自行註冊。**


   ![](assets/add-self-register-link.png)
   _選取自助註冊選項的下拉式功能表_
4. 在&#x200B;**新增自我註冊設定檔**&#x200B;提示上，在&#x200B;**設定檔名稱** （使用者的職稱）欄位中輸入設定檔。
5. 在&#x200B;**管理員名稱**&#x200B;欄位中搜尋管理員，以選取使用者的管理員。 指派給自助註冊設定檔的管理員應該是Adobe Learning Manager中的註冊使用者。


   ![](assets/add-a-user-prompt.png)
   _輸入欄位，用於設定職稱及指派管理員到自我註冊設定檔_
6. 使用&#x200B;**新增影像**&#x200B;選項選取影像。 設定檔區段中的學習者可看見此影像。
7. 選取&#x200B;**儲存**。

   Adobe Learning Manager會建立使用者設定檔並產生自助註冊URL，此URL可與使用者共用以完成其註冊。


   ![](assets/self-register-url.png)
   _確認訊息，表示已成功建立自助註冊URL_
8. 與想要自行註冊的使用者共用URL。


   此URL可與多位使用者共用以進行註冊。 例如，您可以產生&#x200B;**Sales Associate**&#x200B;設定檔的URL，並與Sales Associate團隊共用，讓他們可以註冊。

![](assets/self-register-screem.png)
_自助註冊連結會開啟註冊頁面_

### 檢視自助註冊URL的清單

若要檢視自行註冊URL清單：

1. 選取&#x200B;**使用者**，然後選取&#x200B;**內部**。
2. 選取&#x200B;**自行註冊**。

   管理員可檢視自我註冊URL清單。

![](assets/self-registration-profile.png)
_清單檢視顯示內部使用者可用的現有自我註冊URL_

### 大量上傳內部使用者

Adobe Learning Manager可讓管理員上傳包含使用者資訊（包括姓名、電子郵件ID和管理員姓名）的CSV，一次新增多個使用者。 與個別新增使用者相比，這項大量上傳功能可節省時間和精力。

>[!INFO]
>
>觀看這場ALM Academy培訓，瞭解如何透過CSV大量新增使用者。 <br>[![按鈕](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555555)</br>

若要新增多個使用者：

1. 以管理員身分登入。
2. 選取&#x200B;**使用者**，然後選取&#x200B;**內部**。
3. 選取右上角的&#x200B;**新增**&#x200B;並選取&#x200B;**上傳CSV**。

   ![](assets/select-upload-acsv.png)
   _可上傳CSV檔案以大量匯入使用者的選項_

4. 準備包含下列欄位的CSV檔案：

   * 員工姓名*
   * 員工電子郵件*
   * 員工的設定檔/指定
   * 經理ID/電子郵件\
     (*)必填欄位。

5. 在為任何員工新增經理的電子郵件ID之前，請確保該經理已作為員工包含在CSV檔案中。 例如，在下方的快照中檢視名為Howard Walters的員工。

   ![](assets/csv-image.png)
   _包含所有欄位的範例CSV影像_

6. 上傳CSV檔案並對應相應的資料欄位。

   ![](assets/map-the-column.png)
   _CSV對應介面，將試算表欄與系統欄位對齊_
7. 選取&#x200B;**儲存**&#x200B;以匯入使用者。

   上傳成功後會顯示確認訊息。

   ![](assets/csv-save-success.png)
   _影像將CSV上傳的狀態顯示為成功_

>[!NOTE]
>
>維護所有新增和刪除的主CSV。 不支援更新及重新上傳現有的CSV檔案。

上傳CSV檔案以新增使用者時，請務必以正確順序包含所有相關資訊。 如果您將經理的電子郵件ID指派給員工，則經理的詳細資料必須較早地顯示在CSV檔案中。 這可確保系統在將管理員連結至其團隊成員之前，將其識別為現有使用者。 例如，如果Howard Walters是經理，請先在CSV中納入他的完整使用者詳細資訊，再列出向他報告的員工。

### 管理使用者註冊

個別或大量新增使用者後，您需要註冊他們以啟動其帳戶。 這可讓使用者存取Adobe Learning Manager並開始使用平台。

註冊使用者：

1. 在管理員首頁上選取&#x200B;**使用者**。
2. 選取您要註冊之使用者名稱旁的核取方塊。
3. 選取&#x200B;**動作**，然後選取&#x200B;**註冊**。

   ![](assets/register-user.png)
   _註冊按鈕以啟用Adobe Learning Manager中選取的使用者_

4. 選取&#x200B;**是**&#x200B;以啟動使用者。

驗證電子郵件會傳送給使用者。 使用者必須選取電子郵件中的連結，才能啟動其帳戶並開始使用Adobe Learning Manager。

## 外部使用者

Adobe Learning Manager可讓您新增公司以外的使用者（例如客戶、合作夥伴、廠商或客戶）以存取學習內容。 新增課程後，您就能進行分組、指派課程及追蹤其學習進度。

在Adobe Learning Manager中新增外部使用者涉及以下步驟：

* 建立外部註冊設定檔
* 啟用註冊設定檔
* 與外部使用者共用註冊連結
* 需要時暫停或恢復設定檔

Adobe Learning Manager支援透過外部註冊設定檔註冊這類使用者。

若要建立外部使用者，請遵循下列步驟：

1. 以管理員身分登入。
2. 選取&#x200B;**使用者**，然後選取&#x200B;**外部**。
3. 在右上角，選取&#x200B;**新增**&#x200B;以建立外部使用者的註冊。
4. 在&#x200B;**新增外部註冊設定檔**&#x200B;對話方塊中，提供下列專案：

   * **設定檔名稱：**&#x200B;輸入想要存取Adobe Learning Manager的合作夥伴組織名稱
   * **管理員電子郵件：**&#x200B;輸入使用者的管理員電子郵件地址。
   * **名額限制：**&#x200B;設定允許註冊數目上限。
   * **到期日：**&#x200B;定義新註冊的最後日期。 到期後，此連結將無法用於新使用者註冊。

   ![](assets/add-external-user-prompt.png)
   _用於輸入設定檔名稱、管理員電子郵件、名額限制和到期日的對話方塊_

5. 使用&#x200B;**新增影像**&#x200B;選項選取影像。 設定檔區段中的學習者可看見此影像。
6. 選取「**進階設定**」區段以展開並輸入必要的詳細資料：
   * **登入需求：**&#x200B;輸入天數。 如果學習者在整個期間都停用，系統會自動將其移除。
   * **允許的網域：**&#x200B;請輸入允許的電子郵件網域清單（以逗號分隔）。 只有擁有來自已核准網域的電子郵件地址的使用者才能註冊。
   * **需要電子郵件驗證：**&#x200B;選取此項以在註冊期間強制執行電子郵件驗證。

   ![](assets/advanced-settings-add-external.png)
   _進階設定面板，可設定登入需求、允許的網域及電子郵件驗證_

7. 選取&#x200B;**儲存**。

已產生註冊URL。

### 啟用外部設定檔

若要啟用外部設定檔：

1. 在外部設定檔清單中找出新建立的設定檔。

2. 選取&#x200B;**狀態**&#x200B;切換按鈕以啟用它。

管理員可與外部合作夥伴共用此URL，讓他們可以註冊並使用它登入Adobe Learning Manager。

![](assets/enable-the-external-user.png)
_選取切換以啟用外部設定檔_

### 複製並共用外部設定檔的註冊URL

外部設定檔的註冊URL可以從&#x200B;**外部使用者**&#x200B;區段複製。

![](assets/copy.png)
_複製外部設定檔的註冊URL_

### 內部和外部使用者註冊之間的主要差異

內部註冊和外部註冊之間有些差異：

| 內部使用者 | 外部使用者 |
|---|---|
| 可使用Adobe ID或SSO憑證登入。 | 可使用任何電子郵件ID登入。 |
| gamification現已推出。 | gamification現已推出。 管理員必須在[Gamification設定](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/gamification)中為外部學習者啟用gamification。 |

### 暫停外部註冊設定檔

在Adobe Learning Manager中，管理員可以透過暫停其設定檔來管理外部使用者註冊。 當您想要暫時暫停新使用者使用特定外部使用者設定檔加入時，這會很有幫助。 暫停設定檔會使收到邀請但尚未註冊的使用者無法完成註冊程式。 此動作不會影響已完成註冊的使用者。

暫停外部設定檔：

1. 選取&#x200B;**外部使用者**&#x200B;頁面右上角的&#x200B;**動作**。
2. 選取&#x200B;**暫停**&#x200B;以暫停外部使用者設定檔。

這會封鎖尚未接受邀請的使用者的註冊程式。 請注意，此動作只會影響尚未完成註冊的使用者。

![](assets/pause-external-user.png)
_從[動作]功能表暫停現有外部使用者設定檔的選項_

### 繼續外部註冊設定檔

如果先前暫停了外部設定檔，管理員可以恢復該設定檔，以允許新使用者完成註冊。 這會針對受邀但未完成註冊的使用者重新啟用註冊程式。

若要繼續外部使用者：

1. 選取頁面右上角的&#x200B;**動作**。
2. 選取&#x200B;**繼續**&#x200B;以繼續暫停夥伴的存取。

![](assets/resume-an-external-user.png)
_繼續先前暫停的外部使用者設定檔的選項_

### 監視外部座位使用情況

管理員可以在Adobe學習中追蹤新增到每個外部設定檔的使用者數量。

檢查已使用的座位：

1. 在外部設定檔清單中選取&#x200B;**已使用的座位**。

您可以檢視新增至合作夥伴組織的學習者人數，以及學習者是否活躍。

## 管理使用者

管理員可以編輯使用者詳細資訊、刪除使用者、指派角色及移除角色。 這可協助確保每位使用者都擁有正確的存取權和工作。

>[!INFO]
>
>觀看這場ALM Academy培訓，瞭解如何指派和移除角色、傳送歡迎電子郵件，以及刪除和清除使用者。<br>[！[按鈕]](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555586)</br>

### 編輯使用者

使用Adobe Learning Manager中的&#x200B;**編輯使用者**&#x200B;選項來更新使用者的設定檔資訊，例如，名稱、電子郵件地址、唯一識別碼、設定檔和管理員名稱。 管理員可進行這些變更，以確保使用者資料保持準確且為最新狀態。

若要編輯使用者：

1. 在管理員首頁上選取&#x200B;**使用者**。
2. 從&#x200B;**使用者**&#x200B;清單中選取您要編輯的使用者。
3. 選取&#x200B;**編輯設定檔**。

   ![](assets/edit-a-profile.png)
   _在[動作]功能表下的[刪除使用者]選項，將使用者從平台移除_

4. 選取&#x200B;**是**&#x200B;以刪除使用者。

成功刪除使用者後，系統會顯示確認訊息。

## 指派角色給使用者

Adobe Learning Manager中的使用者角色會定義每個人都能在系統中執行的動作。 每個角色都根據使用者的職責提供特定許可權。

若要指派角色給使用者：

1. 在管理員首頁上選取&#x200B;**使用者**。
2. 選取您要指派角色的使用者。
3. 選取右上角的&#x200B;**動作**。
4. 選取&#x200B;**指派角色**。
5. 選取所需的角色。

   ![](assets/assign-roles-users.png)
   _指派角色功能表選項顯示所選使用者的可用角色_

6. 在確認對話方塊上選取&#x200B;**是**。

## 移除角色

移除使用者角色會撤銷該角色所授予的許可權。

若要從使用者中移除角色：

1. 在系統管理員首頁上選取&#x200B;**使用者**。
2. 選取您要移除其角色的使用者。
3. 選取&#x200B;**動作**，然後選取&#x200B;**移除角色**。

   ![](assets/remove-a-role.png)
   _從[動作]功能表下的使用者移除指派角色的選項_

4. 在確認對話方塊上選取&#x200B;**是**。
<!--# Add users and create user groups


Learn how to add users or user groups in Learning Manager application.

<!--![](assets/user-mgmt-new.png)-->

<!--## Overview {#overview}

In Adobe Learning Manager, you can assume the following roles:

* **Administrator:** An Administrator defines the training strategy for the organization. An Administrator can add learners, search required skills for learners, manage and assign courses, create learning plans, certifications, and learning programs, and manage reports for the entire organization.
* **Author:** Authors are Instructional Designers and content creators. An Author can add modules and courses to Learning Manager.
* **Manager:** A Manager manages the learning activities of a team. A Manager can nominate team members to take a course, approve requests from team members, and provide feedback on performance of their team members post-completion of training. Managers can also view reports for their team to track their performance.
* **Learner:** Learners can access courses, learning programs, and certifications assigned to them. Learners can also browse through all the available courses by using a catalog and enroll themselves for either courses, learning programs, or certifications.

As an Administrator, you can add users in three ways:

* Internal
* External
* User groups

## Add a single user {#addasingleuser}

Add internal learners to the Adobe Learning Manager using a single user option.

>[!INFO]
>
>In this training, you will learn how to add internal learners to the Adobe Learning Manager.<br><br>[![button](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555534)</br></br>


If you're unable to launch the training, write to <almacademy@adobe.com>.

To add users,

1. Log into Adobe Learning Manager as an Administrator. 
1. On the home page, click **[!UICONTROL Add Users]**. On this page, you can add a single user or multiple users at a time using a CSV. You can also create a self-registration link for internal employees or create an external learner profile.
1. To add a single user, click **[!UICONTROL Add]** on the upper-right corner and choose the option **[!UICONTROL Single User]**.

1. To add a single user, click **[!UICONTROL Add]** on the upper-right corner and choose the option **Single User**.


   ![](assets/single-user.png)
   *Add a single internal user*

1. On the **[!UICONTROL Add User]** dialog, enter the details of the learner. For the field **[!UICONTROL Manager's Name]**, pick the name of an existing user in the system.

   ![](assets/manager.png)
   *Add user dialog box*

1. To add the new user in Learning Manager, click **[!UICONTROL Add]**. After the user is added, the user receives a verification mail. The Learner then activates the account and starts using Learning Manager. This workflow is helpful if you need to add limited number of learners to your Learning Manager Account. But if you're planning to enroll all the employees of a large organization, you can add them in a singe attempt. For more information, see the next section.

## Add users in bulk {#addusersinbulk}

Typically, most organizations work with an HR Management System (HRMS), which maintains all employee records, such as, designation, location, date of joining, or employee hierarchy. You can export this data in a CSV format. To import a CSV, follow the steps below:


1. Click **[!UICONTROL Add]** on the upper-right corner, and choose the option **[!UICONTROL Upload a CSV]**.

   ![](assets/upload-a-csv.png)
   *Upload a CSV to add users in bulk*

1. The CSV that you upload consists of the fields, as shown below:

   ![](assets/csv.png)
   *Structure of the CSV*

   You must maintain a master CSV and perform perform all additions and deletions on the master CSV. The master CSV contains the following fields:

   * name &#42;
   * email &#42;
   * profile
   * manager

   (&#42;) Required field.

1. After you click the option **[!UICONTROL Upload a CSV]**, the following dialog displays.

   ![](assets/upload-a-csv-dialog.png)
   *Upload a CSV dialog*

1. Choose the CSV or drag-and-drop the file. After you've chosen the file, map the data fields with the ones in the CSV file. Click the required drop-down and choose the right field.

   ![](assets/map-data-fields.png)
   *Map fields in CSV*

1. To start importing the users, click **[!UICONTROL Save]**. You can see a confirmation message.

   ![](assets/save-csv.png)
   *Confirmation message for successful upload of the CSV*

1. The new users are now added to your Adobe Learning Manager account. To select the new users, select the check-box next to the names so that everybody is selected. 

   ![](assets/select-new-users.png)
   *New users added*

>[!NOTE]
>
>For more information, see the FAQ, [Add users in bulk](../add-users-in-bulk.md).

>[!INFO]
>
>In this training, you will learn how to add users in bulk through a CSV.<br><br>[![button](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555555)</br></br>

If you're unable to launch the training, write to <almacademy@adobe.com>.

## Register a user {#registerauser}

With the user selected, click **[!UICONTROL Actions]** on the upper-right corner and click **[!UICONTROL Register]**.

The selected users receive a Welcome email. If the learners have an existing Adobe ID, they can click this link. If they don't have an existing Adobe ID, they can go ahead and click the Welcome link to create an Adobe ID and link it to their Learning Manager account.

### Manage users

In this training, you will learn how to assign and remove roles, send a welcome email, and delete and purge users. 

[![button](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555586)

If you're unable to launch the training, write to <almacademy@adobe.com>.

## Assign a role {#assignarole}

After adding learners to the Adobe Learning Manager account, if you want to change their roles, click Actions on the upper-right corner of the page. Choose the option **[!UICONTROL Assign Role]**. Here you can decide whether you want to give Author access or Admin access to the learner. After you have assigned a role, this learner has Author access to the account and can add modules and create courses. 

![](assets/assign-a-role.png)
*Assign a role to a user*

## Remove a role {#removearole}

You can also remove Author or Admin access for the users. Select one or more learners, click **[!UICONTROL Actions]**, and select **[!UICONTROL Remove Role]**. Choose an option, for example, **[!UICONTROL Remove Author]**, and the author access gets revoked for this learner. 

>[!NOTE]
>
>You cannot manually assign a Manager role to someone in the system. They automatically get access to the Manager dashboard when one or more employees are added under them.

## Delete a user {#deleteauser}

To delete a user, click **[!UICONTROL Actions]**, and choose **[!UICONTROL Delete User]**. On the confirmation dialog, click **[!UICONTROL Yes]**, and the learner gets deleted.

![](assets/delete-a-role.png)
*Confirmation message to delete a user*

## Edit a user {#editauser}

On the list of users, choose a user, and click the user. On the user details, click the **[!UICONTROL Edit]** ( ![](assets/edit-pen.png)) button. On the **[!UICONTROL Edit User]** dialog, make the necessary edits and to save the changes, click **[!UICONTROL Save]**.

![](assets/edit-user.png)
*Edit User dialog*

## Active fields

Active Fields in Adobe Learning Manager are customizable metadata fields used to store and manage user-specific information. These fields help define key attributes or characteristics associated with each user in the system.

### Manage user attributes

>[!INFO]
>
>In this training, you will learn how to add, customize, and configure Active Fields.<br><br>[![button](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555741)</br></br>

If you're unable to launch the training, write to <almacademy@adobe.com>.

Adobe Learning Manager preserves the case sensitivity of the user attribute and its value. **For example**, the case sensitivity of a user attribute is 'location' and its value as 'PARIS' will be preserved and displayed in the same manner. In case of any issues, the Administrator can now edit the attribute name and values to correct any case sensitivity errors. 

The Administrator can do this by visiting **[!UICONTROL Admin app]** > **[!UICONTROL Users]** > **[!UICONTROL User groups]** and clicking on the group name.  

An Admin can add and update allowed attribute values for a learner through UI.

Types of active fields:

* Groupable: Learners would get grouped on the basis of the Values
* Reportable: Reporting user groups would be created based on the active fields
* Exportable: The fields will be seen in exported in user group report.

## Create a self-registration link {#createaselfregistrationlink}

You can also enable employees in your organization to register themselves as Learners to Adobe Learning Manager Account, without taking help from you as an administrator. The administrator can create a Self-Registration link and share with the employees, who can further register to Learning Manager using their Adobe credentials.

On the upper-right corner of the page, click **[!UICONTROL Add]**, and select **[!UICONTROL Self-Registration]**.


![](assets/self-registration.png)
*Create link to self-register as learner*

The **[!UICONTROL Add Self-Registration Profile]** dialog appears. Give this profile a name. Then add the manager's name. It's important to know that the manager must already be registered learner in Learning Manager.

![](assets/add-self-registrationprofile.png)
*Add profile for self-registration*

After you click **[!UICONTROL Save]**, a URL gets generated, which you can share with the learners, so that they can click the URL and self-register themselves.

## Enroll external learners {#enrollexternallearners}

In Adobe Learning Manager, you can also create Registration links for external partners or agencies with limited access to your account and provide them learning material.

There are a few differences between internal and external registrations.

<table>
 <tbody>
  <tr>
   <td>
    <p><b>Internal users</b></p></td>
   <td>
    <p><b>External users</b></p></td>
  </tr>
  <tr>
   <td>
    <p>Log in using Adobe ID or SSO credentials.</p></td>
   <td>
    <p>Log in using any email ID.</p></td>
  </tr>
  <tr>
   <td>
    <p>Gamification is available.</p></td>
   <td>
    <p>Gamification is available. The admin must enable gamification for external learners in the Gamification settings.</p></td>
  </tr>
  <tr>
   <td>
    <p>Learner hierarchies are available.</p></td>
   <td>
    <p>Learner hierarchies are not available.</p></td>
  </tr>
 </tbody>
</table>

To enroll external users, follow the steps below:

1. In the left navigation pane, click **[!UICONTROL External]**.

   ![](assets/click-external.png)
   
   *Enroll external users*

1. On the upper-right corner of the page, click **[!UICONTROL Add]**.

1. On the **Add External Registration Profile** dialog, add the following details:


   * The profile name of the partner organization.
   * The email address of the manager of the partner organization.
   * Seat limit for external enrollment for this partner.
   * Expiry date to set a deadline to stop allowing new registrations to this group. After the Expiry date, only the existing registered users can access this training.

   ![](assets/map-data-fields-2.png)

   *Add External Registration Profile dialog*

   * In the **[!UICONTROL Advanced Settings]** section, enter the following:

     * **[!UICONTROL Login Requirement]:** Specify a value in days. Learners get deleted if they do not login for the above duration.
     * **[!UICONTROL Allowed Domains]:** A comma-separated list of whitelisted email domain names.
     * **[!UICONTROL Email Verification Required]:** Select this option to make email verification mandatory for a learner.

   ![](assets/email-verificationrequired.png)

   *Enter the details in the Advanced Settings section* 

1. After you click **[!UICONTROL Save]**, you can see the following confirmation message. You must share the URL with your external partner.

   ![](assets/save-and-share-urlwithexternalusers.png)

## Enable an external profile {#enableanexternalprofile}

After an external profile has been created, you must enable its status. From the list of external profiles, choose the required profile, and toggle the status button.

![](assets/choose-required-profiles.png)
*Enable an external profile*

This enables the External Enrollment link. A welcome email is automatically be sent to the partner. You can also copy the link and share with them by clicking the Copy URL icon (), or you can resend the welcome email to the partner organization by clicking the Mail icon ().

The partner manager can share the link with the employees who must take the training in PrLearning Managerime. When they click the link, they can self-enroll themselves after filling out some details to create their profile on Learning Manager. These users will not appear on the Learners tab along with the internal employees. You can see their names under the **[!UICONTROL External Learners]** tab.

## Pause an external profile {#pause}

After adding an external user group to Learning Manager, you can also pause the external users' registration process. When you pause, the external users' registration process is blocked. However, this process works only when the users haven't registered yet by accepting the invitation.

To pause the external user groups, choose a group or groups, click **[!UICONTROL Actions]** from the upper-right corner of the page, and click **[!UICONTROL Pause]**.

## Resume an external profile {#resumeanexternalprofile}

At any time, you can always revoke the paused state of an external partner and resume normal services. Click **[!UICONTROL Actions]** at the upper-right corner of the page and select **[!UICONTROL Resume]**.

The following states are applicable for external users:

* **Inactive state** - In this state, the external users' registration is expired. Administrators set the expiry date for the external users while adding them through the add user workflow.
* **Active state** - In this state, the external users can register to the Learning Manager application, and log in to the application.
* **Pause** - In this state, the registration process for external users is blocked. However, the existing users can continue to log in.

## Check used seats {#checkusedseats}

On the list of external profiles, click **[!UICONTROL Seats Used]**. You can view the number of learners in the partner organization who have been added.

![](assets/seats-used.png)
*Check used seats*

## Delete a user {#Deleteauser-1}

Choose a user, and from the upper-right corner, click **[!UICONTROL Actions]** > **[!UICONTROL Delete User]**.

## Change profile {#changeprofile}

To move a user to another external profile, choose a user, from the upper-right corner, click **[!UICONTROL Actions]** > **[!UICONTROL Change Profile]**. From the list of profiles, choose a profile, and click **[!UICONTROL Change]**.

## Assign a role {#Assignarole-1}

Choose a user, and from the upper-right corner, click **[!UICONTROL Actions]** > **[!UICONTROL Assign Role]** > **Make `<role>`**. The user gets a new role.

## Remove a role {#Removearole-1}

Choose a user, and from the upper-right corner, click **[!UICONTROL Actions]** > **[!UICONTROL Remove Role]** > **Remove `<role>`**. The selected role gets removed from the list of roles that were assigned to the user.

>[!NOTE]
>
>Assigning a new role will not affect custom user groups. However, it will impact auto-generated user groups such as All Admins, All Authors, and similar role-based groups.

## Create user groups {#createusergroups}

A User Group is a set of users who are related to a category. User Groups help administrators to select learners in their organization based on their attributes, and then assign learning content to them. Also, these User Groups enable administrators to assign customized logos and catalogs to learners and show customized reports on their progress.

To access User Groups, on the left navigation pane, click **[!UICONTROL User Groups]**.

![](assets/user-groups.png)
*Create user groups*

### Manage user groups

>[!INFO]
>
>In this training, you will learn how to create a user group by names, email IDs, and combining multiple auto-generated user groups.<br><br>[![button](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555694)</br></br>

If you're unable to launch the training, write to <almacademy@adobe.com>.

There are two types of groups in Adobe Learning Manager, Custom and Auto-generated. When you add learners to your account, some groups are automatically created based on their common properties.

To see the automatically created groups, click the tab **[!UICONTROL Auto-generated]**.

![](assets/auto-generated.png)
*View Auto-generated groups*

You can see that there are different groups, like All Internal Users, All Managers, groups based on the Cost Center, based on the department, and based on the teams of the managers.

In addition to Auto-generated groups, you can create Custom groups. To add a new Custom Group, on the upper-right corner, click **[!UICONTROL Add]**. 

1. Enter the name, and description for the group.
1. Enter user name or profile in search-as-you-type field and select from the drop-down list, to add users.

1. To add more learners, click **[!UICONTROL Add More Users]**.

1. To create the user group, click **[!UICONTROL Save]**.

This Custom Group is now created and added to the profile. The User Groups that you create are dynamic in nature. If new users are added with similar attributes, they're automatically added to the User Group.

To view the list of groups a user belongs to, navigate to **[!UICONTROL User]** > **[!UICONTROL User Groups]**, search for the user's name, and select it. This will display all the groups the user is part of.

![](assets/list-of-group.png)

### Download the list of users in a user group

To download the list of users in a specific user group, navigate to **[!UICONTROL User]** > **[!UICONTROL User Groups]**, select the **[!UICONTROL Download icon]** next to the group. This will generate a CSV file containing the list of users in that group.

![](assets/download-list-of-user.png) 

## Exclusion of user groups

At times you would want to exclude a small set of users from a large user group. This is required to enroll this specific set of users into training via Learning Plans or to setup the correct visibility of catalogs. In this release of Learning Manager, you can exclude learners or User Groups when you create a custom user group. In the Add User Group dialog, the Exclude Learners section enables you to achieve so.

![](assets/exclude-user-groups.png)
*Exclude user groups*

For example, if you want to set up a Learning Plan so that all users belonging to location = California except Store-5 (located in California) get enrolled. 

## Advanced settings {#advancedsettings}

### Data Sources {#datasources}

You can use this feature when you want to import/sync the users or learning data from your organization's database in to the Learning Manager application. You can also set up the frequency of this sync. 


Click **[!UICONTROL Data Sources]** on the left pane under **[!UICONTROL Advanced]** section. 


![](assets/data-sources-add-users.png)

*Data sources to iport or sync users*

Choose the data source type from the **[!UICONTROL Source]** drop-down, select the update frequency, and click **[!UICONTROL Sync now]** if you need to sync immediately or click **[!UICONTROL Save].** Data source types are SFDC, FTP, and so on for internal users. 

You can add multiple data sources. 

### Active Fields {#activefields}

This feature enables administrators to add more active fields in addition to what has been provided during user registration. 

Click **[!UICONTROL Active Fields]** available inside users page. Learners can only choose from the values given in custom values.

![](assets/active-fields.png)
*Active fields*

### Configure Fields {#configurefields}

**Internal users**

You can add custom value for user fields for internal users.

To add  custom values, follow these steps:

1. Click  **[!UICONTROL Modify Values]** for an Internal user. 

   ![](assets/modify-values.png)
   *Modify values for internal users*

1. The **Values in Custom field** dialog box appears.

   ![](assets/values-in-customfields.png)
   *Values in Custom Fields dialog box*

1. Select the value to add from the **[!UICONTROL Select Field]** drop-down menu.
1. Enter new values in the **[!UICONTROL New Value]** field.
1. Click **[!UICONTROL Done]**. 
1. Click Save on the top right corner to **[!UICONTROL Save]** changes.

**External users**

Add custom values similar to that for internal users.

![](assets/modify-values-forexternalusers.png)
*Modify values for external users*

### Settings {#settings}

**User Display**

If the option **Show only unfilled fields on Learner login** is enabled, a user only sees the blank fields upon login.

![](assets/settings-tab.png)
*Show unfilled fields*

Using this option, an Administrator can decide whether he/she wants to show the fields or hide them once these have been populated.

## Restrict Active Fields in reports {#restrictactivefields}

Learning Manager 27.7 introduces two new options- **[!UICONTROL Reportable]** and **[!UICONTROL Exportable]**, for Active Fields.

![](assets/options-in-activefields.png)
*Options in Active Fields*

For CSV fields and manually added fields, if an Active Field is marked as **[!UICONTROL Reportable]**, the Active Field becomes searchable in a filter inside a dashboard report.

![](assets/filters-in-a-dashboardreport.png)
*Filters in a dashboard report*

If an Active Field is marked as **[!UICONTROL Exportable]**, then the Active Field appears in the Excel file upon downloading any Excel report.

These options appear for both internal and external Active Fields.

You can only delete a custom Active Field.

## User Display

You can hide the entire 'Complete your profile' page from the learners. The page will not pop up once the learner logs in.

Note that the existing default behavior does not change. This is an optional capability now available to Administrators. 

Enable the options below:

![](assets/user-display.png)
*User Display section*

## Support for manual CSV fields by FTP and Box connectors {#import-connector}

Often, users want Active fields to be manually provided when a learner logs in to Learning Manager. This is possible in Learning Manager at present, when the user imports a CSV manually.

The CSV may not contain all the Active fields. For all the Active fields that are not updated in the uploaded CSV, the user needs to enter the data for such Active fields.

Presently, all Active fields must be mapped to some field from the source CSV.

It so happens that sometimes a user does not want to map an Active field to a field specified in the CSV. In such cases, the user can map the Active field to the value **[!UICONTROL DontImportFromSource]**. Select this value from the drop-down list, when importing users from FTP and Box connectors.

## Custom Roles {#customroles}

Add any field of your choice as part of your user information and click **[!UICONTROL Save]**. After adding the fields, you can also cross check the availabilities of the fields in the **[!UICONTROL Edit users]** dialog. 


After adding the fields, you can notice that the fields marked with tick mark are sourced from data source or CSV as mentioned in the below snapshot. Administrator can edit these sourced fields by enabling or disabling the fields. 

**Values for active fields in Learning Manager**

The values for active fields are fetched in the following ways: 

1. Learning Manager application imports metadata from data sources associated with your account. 
1. Metadata captured from the manually imported CSV file. 
1. Learners fill up metadata when they log in
1. Administrator enters data for the users. 

>[!NOTE]
>
>Learning Manager application creates user groups automatically, from these metadata. 

**Add custom value**

You can add custom value for user fields in the Internal and External user fields.

To add  custom values, follow these steps:

Custom fields can be added and deleted, they are applicable to all users. CSV fields can be enabled or disabled, they come into effect only when you upload CSV after making the modifications in Active fields. All internal active fields are applicable to all types of Internal users. External fields are applicable only to external users. If a custom field is present in CSV, on next upload it gets converted to a CSV field automatically and it is enabled. 

## Values for CSV fields {#valuesforcsvfields}

Users can only choose from predefined fields for CSV fields if the **[!UICONTROL Restrict Selection]** check-box is enabled.

![](assets/value-field-for-csv.png)
*Restrict selection check-box*

## Import Logs {#importlogs}

In this space, you can view the CSV import history for the users the administrator has added using bulk import feature. You can also click **[!UICONTROL Add]** at the upper-right corner of the page to add users using CSV upload feature. 

## Multi-valued Active Fields

With this feature, you can have more than one field for an active field. In an account, there can be at most three multi-valued active fields. The multi-valued active fields are available for both external and internal users.

Once you mark an active field as multi-valued, you cannot convert it back to single valued. This is irreversible.

An existing single valued field cannot be marked as multi-valued field.

To create a multi-valued active field, follow the steps below:

1. Add an active field.

   ![Add an active field](assets/add-active-field.png)
   *Add an active field*

1. Click Add.
1. In the Settings tab, mark the new field as multi-valued.

   ![Mark as multi-valued](assets/mark-multi-valued.png)
   *Mark as multi-valued*

   There is another checkbox, **[!UICONTROL Learner Configurable]**, which when disabled, the learner will not be able to see the field on the Profile page.

1. Add the values using a CSV or by clicking Modify Values.

   ![Add values](assets/add-values.png)
   *Add values*

1. Click [!UICONTROL **Done**].

>[!NOTE]
>
>Once is the user group is created and the field is populated, multi values cannot be converted to single values, and vice versa.

### Add multi-valued active field via CSV

Follow the steps below:

1. Create a CSV with the new active fields as columns (comma-separated or single values).
1. Import the CSV.
1. Mark the fields as multi-valued in the Values in Custom Fields dialog.
1. Import the CSV again.

The CSV must have a column with the same name as that of an active field that was marked as multi-valued.

The CSV contains the fields:

* **[!UICONTROL User]**: User groups created as roles.
* **[!UICONTROL Roles]**: Multi-valued active field with values.

If the CSV is re-uploaded with new values or deleted values, the active fields and groups also get updated accordingly.

### Reports

All reports include the multi-valued active fields and their values.

The Administrator can add auto-generated active fields, and configure user activity and training reports.

The Learner Transcript report contains all the active fields and comma-separated values. The Administrator can then filter the data accordingly.

## User group report

Adobe Learning Manager's new User Group Report helps manage user groups by providing visibility into groups left unmanaged when admins left. Admins can access the reports under the **[!UICONTROL Users]** > **[!UICONTROL User Group]** section. It provides detailed information about each group, including:

* User group type
* Group name
* Description
* Created by (Name)
* Created by (Email)
* Created on (UTC Timezone)
* Number of Users

To download the report, follow these steps:

1. Log in as an **[!UICONTROL Admin]**.
2. Select **[!UICONTROL Users]** > **[!UICONTROL User Group]**.
3. Select **[!UICONTROL Actions]** > **[!UICONTROL Download User Group Report]**.

![](assets/download-user-group-report.png) 
_Download the User Group report_

## Frequently Asked Questions {#faq}

+++How to register users in Learning Manager?

After adding a user and assigning a role to the user, you can register the user by performing the steps below:

1. With the user or users selected, click **[!UICONTROL Actions]** on the upper-right corner, and click **[!UICONTROL Register]**.

1. On the pop-up window, click **[!UICONTROL Yes]**.

The selected user(s) receive a Welcome email. If the learners have an existing Adobe ID, they can click this link. If they don't have an existing Adobe ID, they can go ahead and click the Welcome link to create an Adobe ID and link it to their Learning Manager account.

Clicking one of these links in the email is mandatory for the learners as it helps Learning Manager to verify the learner's account.

+++

+++How to edit user data?

To edit a user, follow the steps below:

1. In the list of users, click the user for who you want to edit the data.
1. Click the pencil icon, as shown below.

![](assets/edit-user-data.png)

In the **Edit User** dialog, update the fields accordingly. To save the changes, click **[!UICONTROL Save]**.

+++

+++How to pause and resume an external user in Learning Manager?

In the list of External Users, choose the user that you want to delete. On the upper-right corner, click **[!UICONTROL Actions]** > **[!UICONTROL Pause]**.

For more information, see [Pause an external profile](add-users-user-groups.md#pause).

After you pause a profile, the external profile displays the status as ***Paused***.

+++

+++How to send welcome email to newly created external profile?

When adding an external user, in the **[!UICONTROL Add External Registration Profile]** dialog, enter the email of the external manager. When you click Save, a welcome email also gets sent to the email address that you had specified. If you want to send the welcome mail again, click the envelope icon, as shown below:

![](assets/send-welcome-mail.png)

+++

+++How to create Custom User Groups?

Click **[!UICONTROL Users]** > **[!UICONTROL User Groups]** and on the User Groups page, click **[!UICONTROL Add]**. In the Add User Group dialog, add the users both individually and as a team.

![](assets/custom-user-group.png)

+++

+++How to disable already filled active fields?

If you want learners to only see the active fields that are not filled by them, then follow the steps below:

1. Click **[!UICONTROL Users]** > **[!UICONTROL Active Fields]**.  

1. Click **[!UICONTROL Settings]** and enable the option **[!UICONTROL Show only unfilled fields on Learner login]**.

1. Click **[!UICONTROL Save]**.

+++

+++How to prevent learners from entering random values in the active fields.?

You can restrict the selection for learners so that they can only select the values that are pre-defined and not enter any random values. Follow the steps below:

1. Click **[!UICONTROL Users]** > **[!UICONTROL Active Fields]**.
1. Enable the option **[!UICONTROL Restrict Selection]**.
1. Click **[!UICONTROL Done]**.

+++

+++How do I differentiate CSV active fields and Custom Active fields?

You can only enable or disable CSV active fields, but cannot delete them. On the other hand, you cannot enable or disable custom active fields.

+++-->