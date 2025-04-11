---
description: 了解如何在學習管理器應用程式中添加用戶或用戶組。
jcr-language: en_us
title: 新增使用者並建立使用者群組
contentowner: manochan
exl-id: 7df98f2b-c422-4733-8ce4-5489506d4fdf
source-git-commit: a28ac8f57710c118ca4ad02872fd100c6f24beac
workflow-type: tm+mt
source-wordcount: '4118'
ht-degree: 0%

---

# 新增使用者並建立使用者群組

瞭解如何在Learning Manager應用程式中新增使用者或使用者群組。


<!--![](assets/user-mgmt-new.png)-->

## 管理使用者群組

>[!INFO]
>
>在本培訓中，您將學習如何按名稱、電子郵件 ID 和組合多個自動生成的用戶組創建使用者群組。<br><br>[![按鈕](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555694)</br></br>

<!--[Launch training](https://learningmanager.adobe.com/app/learner?accountId=98632&sdid=QLD1P6BS&mv=display&mv2=display#/course/7555694)-->

<!--In this training, you will learn how to create a user group by names, email IDs, and combining multiple auto-generated user groups.-->

<!--[![button](assets/launch-training-button.png)](https://learningmanager.adobe.com/app/learner?accountId=98632&sdid=QLD1P6BS&mv=display&mv2=display#/course/7555694)-->

如果您無法啟動訓練，請寫信到<almacademy@adobe.com>。

## 概觀 {#overview}

在Adobe Learning Manager中，您可以擔任下列角色：

* **管理員：**&#x200B;管理員定義組織的訓練策略。 管理員可以新增學習者、搜尋學習者的所需技能、管理和指派課程、建立學習計畫、認證和學習計畫，以及管理整個組織的報表。
* **作者：**&#x200B;作者是教學設計人員和內容建立者。 作者可以將模組和課程新增至Learning Manager。
* **經理：**&#x200B;經理管理團隊的學習活動。 經理可以指派團隊成員參加課程、核准團隊成員的請求，並在完成培訓後提供團隊成員績效的意見回饋。 經理也可以檢視其團隊的報告，以追蹤其績效。
* **學習者：**&#x200B;學習者可存取指派給他們的課程、學習計畫及認證。 學習者也可使用目錄瀏覽所有可用的課程，並註冊課程、學習計畫或認證。

身為管理員，您可以透過三種方式新增使用者：

* 內部
* 外部
* 使用者群組

## 新增單一使用者 {#addasingleuser}

使用單一使用者選項將內部學習者新增至Adobe Learning Manager。

>[!INFO]
>
>在本培訓中，您將學習如何向Adobe Systems學習管理器添加內部學習者。<br><br>[![按鈕](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555534)</br></br>


如果您無法啟動訓練，請寫信到<almacademy@adobe.com>。

若要新增使用者，

1. 以管理員身分登入Adobe Learning Manager。
1. 在首頁按一下&#x200B;**[!UICONTROL Add Users]**。 在此頁面上，您可以使用CSV一次新增一個或多個使用者。 您也可以為內部員工建立自助註冊連結，或建立外部學習者設定檔。
1. 要新增單個使用者，請按下 **[!UICONTROL Add]** 右上角並選擇選項 **[!UICONTROL Single User]**。

1. 要添加單個用戶，請按下 **[!UICONTROL Add]** 右上角並選擇選項 **單使用者**。


   ![](assets/single-user.png)
   *新增單一內部用戶*

1. 在 **[!UICONTROL Add User]** 對話框中，輸入學習者的詳細資訊。 對於欄位 **[!UICONTROL Manager's Name]**，選取系統中現有用戶的名稱。

   ![](assets/manager.png)
   *新增使用者對話方塊*

1. 若要在學習管理器中添加新用戶，請按下 **[!UICONTROL Add]**。 添加用戶后，用戶會收到驗證郵件。 然後，學習者啟動帳戶並開始使用學習管理器。 如果您需要向學習管理器帳戶添加有限數量的學習者，則此工作流程非常有用。 但是，如果您計劃註冊大型組織的所有員工，則可以一次嘗試添加他們。 有關詳細資訊，請參閱下一節。

## 大量新增使用者 {#addusersinbulk}

### 管理使用者

在本訓練中，您將學習如何指派和移除角色、傳送歡迎電子郵件，以及刪除和清除使用者。

[![按鈕](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555586)

如果您無法啟動訓練，請寫信到<almacademy@adobe.com>。

通常，大多陣列織都使用HR管理系統(HRMS)，HRMS會維護所有的員工記錄，例如，指定、地點、加入日期或員工階層。 您可以將此資料匯出為CSV格式。 若要匯入CSV，請遵循下列步驟：


1. 按一下右上角的&#x200B;**[!UICONTROL Add]**，然後選擇選項&#x200B;**[!UICONTROL Upload a CSV]**。

   ![](assets/upload-a-csv.png)
   *上傳 CSV 以大量新增使用者*

1. 您上傳CSV由欄位組成，如下所示：

   ![](assets/csv.png)
   *CSV的結構*

   您必須維護主CSV，並對主CSV執行所有添加和刪除。 主CSV包含下列欄位：

   * 名稱&#42;
   * 電子郵件&#42;
   * 設定檔
   * 經理

   （&#42;） 必填欄位。

1. 按兩下這個選項 **[!UICONTROL Upload a CSV]**&#x200B;後，將顯示以下對話框。

   ![](assets/upload-a-csv-dialog.png)
   *上傳CSV對話框*

1. 選擇CSV或拖放檔。 選擇檔后，將數據欄位與CSV檔中的欄位對應。 單擊必填下拉功能表，然後選擇正確的欄位。

   ![](assets/map-data-fields.png)
   *在 CSV 中映射欄位*

1. 若要開始匯入使用者，請按一下&#x200B;**[!UICONTROL Save]**。 您可以看到一條確認消息。

   ![](assets/save-csv.png)
   *成功上傳CSV的確認訊息*

1. 新使用者現在已新增至您的Adobe Learning Manager帳戶。 若要選取新使用者，請選取名稱旁的核取方塊，以便選取所有人。

   ![](assets/select-new-users.png)
   *新使用者已新增*

>[!NOTE]
>
>如需詳細資訊，請參閱常見問題集，[大量新增使用者](../add-users-in-bulk.md)。

選取使用者後，您可以執行下列動作：

## 註冊使用者 {#registerauser}

選取使用者後，按一下右上角的&#x200B;**[!UICONTROL Actions]**&#x200B;並按一下&#x200B;**[!UICONTROL Register]**。

選取的使用者會收到歡迎電子郵件。 如果學習者已有的Adobe ID，可按一下此連結。 如果他們沒有現有的Adobe ID，他們可以繼續並按一下歡迎連結以建立Adobe ID並將其連結到他們的Learning Manager帳戶。

## 指派角色 {#assignarole}

將學習者新增至Adobe Learning Manager帳戶後，如果您想要變更其角色，請按一下頁面右上角的「動作」 。 選擇選項&#x200B;**[!UICONTROL Assign Role]**。 您可在此決定是否要將作者存取權或管理員存取權授予學習者。 在您指派角色後，此學習者便擁有該帳戶的作者存取權，並可新增模組及建立課程。

![](assets/assign-a-role.png)
*指派角色給使用者*

## 移除角色 {#removearole}

您也可以移除使用者的「作者」或「管理員」存取權。 選取一或多個學習者，按一下&#x200B;**[!UICONTROL Actions]**，然後選取&#x200B;**[!UICONTROL Remove Role]**。 選擇一個選項（例如&#x200B;**[!UICONTROL Remove Author]**），系統會撤銷此學習者的作者存取權。

>[!NOTE]
>
>您無法手動將Manager角色指派給系統中的某人。 當一個或多個員工新增到經理控制面板下時，管理員會自動存取該控制面板。

## 刪除使用者 {#deleteauser}

要刪除用戶，請按下 **[!UICONTROL Actions]**，然後選擇 **[!UICONTROL Delete User]**。 在確認對話方塊中，按一下&#x200B;**[!UICONTROL Yes]**，學習者即被刪除。

![](assets/delete-a-role.png)
*刪除用戶的確認訊息*

## 編輯用戶 {#editauser}

在使用者清單上，選擇一個用戶，然後按兩下用戶。 在使用者詳細資料上，按一下&#x200B;**[!UICONTROL Edit]** ( ![](assets/edit-pen.png))按鈕。 在&#x200B;**[!UICONTROL Edit User]**&#x200B;對話方塊上，進行必要的編輯並儲存變更，請按一下&#x200B;**[!UICONTROL Save]**。

![](assets/edit-user.png)
*編輯使用者對話方塊*

## 作用中的欄位

學習管理器中的Adobe Systems活動欄位是可自定義中繼資料欄位，用於商店和管理特定於用戶的信息。 這些欄位有助於定義與系統中每個用戶相關聯的關鍵屬性或特徵。

### 管理用戶屬性

>[!INFO]
>
>在本培訓中，您將學習如何添加、自定義和配置活動欄位。<br><br>[![按鈕](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555741)</br></br>

如果您無法啟動培訓，請寫信給 <almacademy@adobe.com>。

Adobe Learning Manager會保留使用者屬性及其值區分大小寫。 **例如**，用戶屬性的大小寫區分為“位置”，其值為“PARIS”將以相同的方式保留和顯示。 如果出現任何問題，管理員現在可以編輯屬性名稱和值以更正任何區分大小寫的錯誤。

管理員可以造訪&#x200B;**[!UICONTROL Admin app]** > **[!UICONTROL Users]** > **[!UICONTROL User groups]**&#x200B;並按一下群組名稱來執行此操作。

管理員可以透過UI為學習者新增及更新允許的屬性值。

作用中欄位的型別：

* 可分組：學習者會根據值分組
* 可報告：會根據作用中欄位建立報告使用者群組
* 可匯出： 這些欄位將顯示在報表中的匯出消費者群組。

## 建立自註冊連結 {#createaselfregistrationlink}

您還可以允許組織中的員工將自己註冊為學習者以Adobe Systems學習管理器帳戶，而無需您作為管理員獲得説明。 管理員可以創建自助註冊連結並與員工共享，員工可以使用其Adobe Systems憑據進一步註冊學習管理器。

在頁面的右上角，按兩下 **[!UICONTROL Add]**，然後選擇 **[!UICONTROL Self-Registration]**。


![](assets/self-registration.png)
*建立連結自行註冊為學習者*

對話框出現 **[!UICONTROL Add Self-Registration Profile]** 。 為此設定檔命名。 然後添加經理的名稱。 請務必知道經理必須已經是學習管理器中的註冊學習者。

![](assets/add-self-registrationprofile.png)
*新增設定檔以進行自助註冊*

按兩下 **[!UICONTROL Save]**&#x200B;後，將生成一個URL，您可以與學習者共用該，以便他們可以按下URL並自行註冊。

## 註冊外部學習者 {#enrollexternallearners}

在Adobe Learning Manager中，您也可以為存取您帳戶受限制的外部合作夥伴或機構建立註冊連結，並向他們提供學習資料。

內部註冊和外部註冊之間有些差異。

<table>
 <tbody>
  <tr>
   <td>
    <p><b>內部使用者</b></p></td>
   <td>
    <p><b>外部使用者</b></p></td>
  </tr>
  <tr>
   <td>
    <p>使用 Adobe ID 或 SSO 憑證登入。</p></td>
   <td>
    <p>使用任何電子郵件 ID 登錄。</p></td>
  </tr>
  <tr>
   <td>
    <p>遊戲化是可用的。</p></td>
   <td>
    <p>遊戲化是可用的。 管理員必須在遊戲化設置中為外部學習者啟用遊戲化。</p></td>
  </tr>
  <tr>
   <td>
    <p>學習者層次結構可用。</p></td>
   <td>
    <p>學習者階層不可用。</p></td>
  </tr>
 </tbody>
</table>

若要註冊外部使用者，請遵循下列步驟：

1. 在左側導覽窗格中，按一下&#x200B;**[!UICONTROL External]**。

   ![](assets/click-external.png)

   *註冊外部使用者*

1. 在頁面的右上角，按一下&#x200B;**[!UICONTROL Add]**。

1. 在「添加外部註冊設定檔&#x200B;**」**&#x200B;對話框中，添加以下詳細資訊：


   * 合作夥伴組織的設定檔名稱。
   * 合作夥伴組織經理的電子郵件地址。
   * 此合作夥伴的外部註冊名額限制。
   * 到期日：設定停止允許此群組新註冊的截止日期。 到期日之後，只有現有的註冊使用者才能存取此訓練。

   ![](assets/map-data-fields-2.png)

   *新增外部註冊設定檔對話方塊*

   * 在&#x200B;**[!UICONTROL Advanced Settings]**&#x200B;區段中，輸入下列內容：

      * **[!UICONTROL Login Requirement]：**&#x200B;指定以天為單位的值。 如果學習者在上述期間未登入，則會被刪除。
      * **[!UICONTROL Allowed Domains]：**&#x200B;已列入白名單的電子郵件網域名稱清單（以逗號分隔）。
      * **[!UICONTROL Email Verification Required]：**&#x200B;選取此選項，讓學習者必須驗證電子郵件。

   ![](assets/email-verificationrequired.png)

   *在進階設定區段中輸入詳細資料*

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;後，您會看到下列確認訊息。 您必須與外部合作夥伴共用URL。

   ![](assets/save-and-share-urlwithexternalusers.png)

## 啟用外部設定檔 {#enableanexternalprofile}

建立外部設定檔後，您必須啟用其狀態。 從外部設定檔清單中，選擇所需的設定檔，然後切換狀態按鈕。

![](assets/choose-required-profiles.png)
*啟用外部設定檔*

這將啟用外部註冊連結。 歡迎電子郵件會自動發送到合作夥伴。 您還可以複製連結並通過按兩下複製URL圖示 （） 與他們共用，也可以通過按兩下郵件圖示 （） 將歡迎電子郵件重新發送到合作夥伴組織。

合作夥伴經理可以與必須參加PrLearning Managerime培訓的員工共享連結。 當他們按兩下連結時，他們可以在填寫一些詳細資訊以在學習管理器上創建設定檔后自行註冊。 這些使用者不會與內部員工一起出現在學習者標籤中。 您可以在標籤下 **[!UICONTROL External Learners]** 看到他們的名字。

## 暫停外部設定檔 {#pause}

將外部使用者群組添加到學習管理器后，您還可以暫停外部使用者的註冊過程。 暫停時，外部使用者的註冊進程將被阻止。 但是，僅當使用者尚未通過接受邀請進行註冊時，此過程才有效。

要暫停外部用戶組，請選擇一個或多個群組組，從頁面的右上角按兩下 **[!UICONTROL Actions]** ，然後按兩下 **[!UICONTROL Pause]**。

## 恢復外部設定檔 {#resumeanexternalprofile}

您可以隨時撤銷外部合作夥伴的暫停狀態並恢復正常服務。 **[!UICONTROL Actions]**&#x200B;點擊頁面右上角，然後選擇 **[!UICONTROL Resume]**。

以下狀態適用於外部使用者：

* **非使用中狀態** — 在此狀態下，外部使用者的註冊已過期。 管理員透過新增使用者工作流程新增外部使用者時，可設定其到期日。
* **作用中狀態** — 在此狀態中，外部使用者可以註冊到Learning Manager應用程式，並登入應用程式。
* **暫停** — 在此狀態下，外部使用者的註冊程式被封鎖。 但是，現有的使用者可以繼續登入。

## 檢查已使用的座位 {#checkusedseats}

在外部配置文件清單，按兩下 **[!UICONTROL Seats Used]**。 您可以視圖合作夥伴組織中已添加的學習者數量。

![](assets/seats-used.png)
*檢查二手座位*

## 刪除用戶 {#Deleteauser-1}

選擇一個用戶，然後從右上角按兩下 **[!UICONTROL Actions]** > **[!UICONTROL Delete User]**。

## 變更設定檔 {#changeprofile}

要將用戶移至另一個外部設定檔，請選擇一個用戶，從 **[!UICONTROL Actions]** 右上角按兩下> **[!UICONTROL Change Profile]**。 從使用者檔案清單選擇一個設定檔，然後按下 **[!UICONTROL Change]**。

## 指派角色 {#Assignarole-1}

選擇一個用戶，然後從右上角按兩下 **[!UICONTROL Actions]** > **[!UICONTROL Assign Role]** > **製作`<role>`**。 用戶有了新的角色。

## 拿掉角色 {#Removearole-1}

選擇一個用戶，然後從右上角按兩下 **[!UICONTROL Actions]** > **[!UICONTROL Remove Role]** > **移除`<role>`**。 選取的角色會從指派給使用者的角色清單中移除。

>[!NOTE]
>
>指派新角色不會影響自訂使用者群組。 但是，它會影響自動產生的使用者群組，例如「所有管理員」、「所有作者」和類似的角色型群組。

## 建立使用者群組 {#createusergroups}

使用者群組是指與類別相關的一組使用者。 使用者組可説明管理員根據學習者的屬性選擇組織中的學習者，然後將學習內容分配給他們。 此外，這些使用者組使管理員能夠為學習者分配自定義徽標和目錄，並顯示有關其進度的自定義報告。

要存取使用者群組，請在左側窗格中按兩下 導覽 **[!UICONTROL User Groups]**。

![](assets/user-groups.png)
*建立用戶群組*

Adobe Systems學習管理器“中有兩種類型的組：自定義組和自動生成的組。 當您將學習者添加到帳戶時，某些組會根據其共同屬性自動創建。

要查看自動創建的組，請按下標籤 **[!UICONTROL Auto-generated]**。

![](assets/auto-generated.png)
*檢視自動產生的群組*

您可以看到有不同的群組，例如「所有內部使用者」、「所有經理」、以「成本中心」為基礎的群組、以部門為基礎的群組以及以經理團隊為基礎的群組。

除了自動產生的群組之外，您也可以建立自訂群組。 若要新增自訂群組，請按一下右上角的&#x200B;**[!UICONTROL Add]**。

1. 輸入群組的名稱和描述。
1. 在「隨型別搜尋」欄位中輸入使用者名稱或設定檔，並從下拉式清單中選取，以新增使用者。

1. 要新增更多學習者，請按下 **[!UICONTROL Add More Users]**。

1. 若要建立使用者群組，請按一下&#x200B;**[!UICONTROL Save]**。

此自訂群組現在已建立並新增至設定檔。 您建立的使用者群組本質上為動態的。 如果新使用者新增了類似的屬性，則會自動新增到使用者群組。

若要檢視使用者所屬的群組清單，請導覽至&#x200B;**[!UICONTROL User]** > **[!UICONTROL User Groups]**，搜尋使用者名稱並加以選取。 這會顯示使用者所屬的所有群組。

![](assets/list-of-group.png)

### 下載使用者群組中的使用者清單

若要下載特定使用者群組中的使用者清單，請瀏覽至&#x200B;**[!UICONTROL User]** > **[!UICONTROL User Groups]**，選取群組旁的&#x200B;**[!UICONTROL Download icon]**。 這將產生一個包含該群組使用者清單的CSV檔案。

![](assets/download-list-of-user.png)

## 排除使用者群組

有時候，您會想要從大型使用者使用者群組中排除一小部分使用者。 這是通過學習計劃將這組特定用戶註冊到 培訓 中或設置目錄的正確可見性所必需的。 在此版本的學習管理員中，您可以在創建自定義使用者群組時排除學習者或用戶組。 在「添加使用者組」對話框中，“排除學習者”部分允許您實現此目的。

![](assets/exclude-user-groups.png)
*排除用戶群組*

例如，如果要設置學習計劃，以便註冊屬於「位置 = 加利福尼亞」的除 Store-5（位於加利福尼亞州）之外的所有使用者。

## 進階 {#advancedsettings}

### 數據源 {#datasources}

如果要將組織資料庫中的使用者或學習數據導入/同步到學習管理器應用程式，可以使用此功能。 您還可以設置此同步的頻率。


按兩下 **[!UICONTROL Data Sources]** 部分下的 **[!UICONTROL Advanced]** 左窗格。


![](assets/data-sources-add-users.png)

*數據源傳送至 iport 或同步使用者*

從 **[!UICONTROL Source]** 下拉清單中選擇資料來源類型，選擇更新頻率，然後按兩下 **[!UICONTROL Sync now]** 是否需要立即同步或按兩下 **[!UICONTROL Save]。** 內部用戶的數據源類型為 SFDC、FTP 等。

您可以新增多個資料來源。

### 活動欄位 {#activefields}

此功能使管理員能夠添加更多活動字段，以及用戶註冊期間提供的內容。

按兩下 **[!UICONTROL Active Fields]** 使用者頁面內可用。 學習者只能從自定義值中給出的值中進行選擇。

![](assets/active-fields.png)
*活動欄位*

### 設定欄位 {#configurefields}

**內部使用者**

您可以為內部使用者的用戶欄位添加自訂值。

若要新增自訂值，請遵循下列步驟：

1. 按一下&#x200B;**[!UICONTROL Modify Values]**&#x200B;以取得內部使用者。

   ![](assets/modify-values.png)
   *修改內部使用者的值*

1. 自訂欄位&#x200B;**中的**&#x200B;值對話方塊就會顯示。

   ![](assets/values-in-customfields.png)
   *自訂欄位對話方塊中的值*

1. 從下拉功能表中 **[!UICONTROL Select Field]** 選擇要添加的值。
1. 在 **[!UICONTROL New Value]** 欄位中輸入新值。
1. 按兩下 **[!UICONTROL Done]**。
1. 按兩下右上角的儲存以 **[!UICONTROL Save]** 進行更改。

**外部使用者**

新增與內部使用者類似的自訂值。

![](assets/modify-values-forexternalusers.png)
*修改外部使用者的值*

### 設定 {#settings}

**用戶顯示**

如果啟用了“學習者登入&#x200B;**上僅顯示未填寫字段”選項**，則用戶只能在登入時看到空白字段。

![](assets/settings-tab.png)
*顯示未填寫欄位*

使用此選項，管理員可以決定是否要顯示欄位，或是在這些欄位填入後隱藏它們。

## 限制報告中的作用中欄位 {#restrictactivefields}

Learning Manager 27.7為作用中欄位引進了兩個新選項 — **[!UICONTROL Reportable]**&#x200B;和&#x200B;**[!UICONTROL Exportable]**。

![](assets/options-in-activefields.png)
*在活動中選項*

對於CSV欄位和手動添加的欄位，如果「活動欄位」標記為 **[!UICONTROL Reportable]**，則「活動欄位」可在儀錶板報表內的篩選器中搜索。

![](assets/filters-in-a-dashboardreport.png)
*控制面板報表中的篩選條件*

如果「使用中欄位」標記為 **[!UICONTROL Exportable]**，則在下載任何 Excel 報表時，「使用中欄位」會顯示在 Excel 檔案中。

這些選項同時出現在內部和外部活動欄位中。

您只能刪除自訂活動欄位。

## 用戶顯示

您可以對學習者隱藏整個「完成您的設定檔」頁面。 學習者登入後，頁面不會隨即顯示。

請注意，現有的預設行為不會變更。 這是一項可選功能，現在可供管理員使用。

啟用下列選項：

![](assets/user-display.png)
*「用戶顯示」部分*

## 透過 FTP 和 Box 連接器支援手動CSV欄位 {#import-connector}

通常，使用者希望在學習者登錄到學習管理器時手動提供活動欄位。 目前，當用戶手動導入CSV時，可以在學習管理器中執行此作。

CSV可能不包含所有活動欄位。 對於上傳CSV中未更新的所有活動欄位，用戶需要輸入此類活動欄位的數據。

目前，所有活動欄位都必須從源CSV映射到某個字段。

碰巧的是，有時用戶不希望將活動字段映射到CSV中指定的字段。 在這種情況下，用戶可以將活動欄位映射到值 **[!UICONTROL DontImportFromSource]**。 從 FTP 和 Box 連接器導入使用者時，請從下拉清單中選擇此值。

## 自訂角色 {#customroles}

將您選擇的任何欄位添加為用戶資訊的一部分，然後按下 **[!UICONTROL Save]**。 添加欄位后，您還可以交叉檢查對話框中欄位 **[!UICONTROL Edit users]** 的可用性。


添加欄位后，您可以注意到標有刻度線的欄位來自資料來源或CSV，如以下快照中所述。 管理員可以通過啟用或禁用字段來編輯這些源欄位。

**學習管理器中活動欄位的值**

可透過下列方式讀取使用中欄位的值：

1. 學習管理器應用程式從與帳戶關聯的數據源導入中繼資料。
1. 從手動匯入的 CSV 檔案擷取的元數據。
1. 學習者在登錄時填滿中繼資料
1. 管理員為使用者輸入數據。

>[!NOTE]
>
>學習管理器應用程式從這些中繼資料自動創建用戶組。

**新增自訂值**

您可以為〖內部〗和〖外部〗字段中用戶字段添加自定義值用戶。

若要新增自定義值，追隨以下步驟：

可以添加和刪除自定義欄位，它們適用於所有使用者。 CSV欄位可以啟用或禁用，它們僅在您在活動欄位中進行修改後上傳CSV時生效。 所有內部活動欄位都適用於所有類型的內部使用者。 外部欄位僅適用於外部使用者。 如果CSV中存在自定義欄位，則在接下來的上傳中，它會自動轉換為CSV欄位並啟用。

## CSV欄位的值 {#valuesforcsvfields}

如果複選框已啟用， **[!UICONTROL Restrict Selection]** 則使用者只能從CSV欄位的預定義欄位中選擇。

![](assets/value-field-for-csv.png)
*限制選擇複選框*

## 匯入記錄檔 {#importlogs}

在此空間中，您可以視圖管理員使用批量導入功能添加的使用者的CSV導入歷史記錄。 您還可以按下 **[!UICONTROL Add]** 頁面的右上角以使用CSV上傳功能添加使用者。

## 多值作用中欄位

使用此功能，一個使用中欄位可以有多個欄位。 帳戶中最多可以有三個多值作用中欄位。 多值作用中欄位可供外部和內部使用者使用。

一旦您將使用中的欄位標示為多值，就無法將它轉換回單一值。 這是不可逆的。

無法將現有的單一值欄位標示為多值欄位。

要創建多值活動欄位，追隨以下步驟：

1. 新增活動欄位。

   ![添加活動欄位](assets/add-active-field.png)
   *添加活動欄位*

1. 按一下「新增」。
1. 在設定標籤中，將新字段標記為多值字段。

   ![標記為多值](assets/mark-multi-valued.png)
   *標記為多值*

   還有另一個複選框， **[!UICONTROL Learner Configurable]**&#x200B;禁用后，學習者將無法在個人資料頁面上看到該字段。

1. 使用CSV或按下修改值來新增值。

   ![新增值](assets/add-values.png)
   *新增值*

1. 按一下&#x200B;[!UICONTROL **完成**]。

>[!NOTE]
>
>一旦建立了使用者群組並填入欄位，便無法將多個值轉換為單一值，反之亦然。

### 通過CSV添加多值活動欄位

請遵循以下步驟：

1. 建立將新的活動欄位作為列（逗號分隔或單個值）的CSV。
1. 匯入CSV。
1. 在「自定義欄位中的值」對話框中將欄位標記為多值。
1. 再次匯入CSV。

CSV必須具有與標記為多值的活動欄位同名的列。

CSV包含以下欄位：

* **[!UICONTROL User]**：作為角色創建的用戶組。
* **[!UICONTROL Roles]**：具有值的多值使用中欄位。

如果使用新值或刪除的值重新上傳CSV，則活動字段和組也會相應更新。

### 報表

所有報表都包含多值活動欄位及其值。

管理員可以添加自動生成的活動字段，並配置用戶活動和培訓報表。

學習者成績單報告包含所有活動字段和逗號分隔值。 然後管理員可以相應地篩選數據。

## 使用者群組報表

Adobe Systems學習管理器的新使用者組報告通過提供對管理員離開時未受管理的組的可見性，説明管理用戶組。 管理員可以存取>**[!UICONTROL User Group]**&#x200B;區域下的&#x200B;**[!UICONTROL Users]**&#x200B;報表。它提供了有關每個群組的詳細資訊，包括：

* 使用者群組類型
* 組名
* 說明
* 建立者 （名稱）
* 建立者 （電子郵件）
* 建立日期 （UTC 時區）
* 用戶數量

若要下載報表，追隨以下步驟：

1. 以ID **[!UICONTROL Admin]**&#x200B;登入。
2. 選擇 **[!UICONTROL Users]** > **[!UICONTROL User Group]**。
3. 選擇 **[!UICONTROL Actions]** > **[!UICONTROL Download User Group Report]**。

![](assets/download-user-group-report.png)
_下載使用者群組報表_

## 常見問題 {#faq}

+++如何在學習管理器中註冊使用者？

添加用戶並將角色分配給用戶后，可以通過執行以下步驟註冊用戶：

1. 選擇使用者或使用者後，按下 **[!UICONTROL Actions]** 右上角，然後按下 **[!UICONTROL Register]**。

1. 在快顯視窗視窗中，按兩下 **[!UICONTROL Yes]**。

選定的用戶會收到一封歡迎電子郵件。 如果學習者已有Adobe ID，則可以按兩下此連結。 如果他們沒有現有Adobe ID，可以繼續並按兩下歡迎連結以創建Adobe ID並將其連結到其學習管理器帳戶。

學習者必須按兩下電子郵件中的這些連結之一，因為它可以幫助學習管理員驗證學習者的帳戶。

+++

+++如何编辑用戶數據？

要编辑用戶，追隨以下步驟：

1. 在使用者清單中，按一下您要編輯資料的使用者。
1. 按一下鉛筆圖示，如下所示。

![](assets/edit-user-data.png)

在&#x200B;**編輯使用者**&#x200B;對話方塊中，相應地更新欄位。 若要儲存變更，請按一下&#x200B;**[!UICONTROL Save]**。

+++

+++如何在Learning Manager中暫停並繼續外部使用者？

在外部使用者清單中，選擇要刪除的使用者。 按一下右上角的&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Pause]**。

有關詳細信息，請參閱 [暫停外部設定檔](add-users-user-groups.md#pause)。

暫停設定檔后，外部設定檔會將狀態顯示為 ***「已***&#x200B;暫停」。

+++

+++如何向新創建的外部設定檔發送歡迎電子郵件？

添加外部用戶時，在 **[!UICONTROL Add External Registration Profile]** 對話框中輸入外部經理的電子郵件。 按兩下儲存時，歡迎電子郵件也會發送到您指定的電子郵件位址。 如果要再次發送歡迎郵件，請按下信封圖示，如下所示：

![](assets/send-welcome-mail.png)

+++

+++如何創建自定義用戶組？

按兩下>，然後在&#x200B;**[!UICONTROL Users]**&#x200B;使用者群組頁面上按下&#x200B;**[!UICONTROL Add]**。 **[!UICONTROL User Groups]**&#x200B;在「新增使用者群組」對話框中，逐一或以團隊形式新增使用者。

![](assets/custom-user-group.png)

+++

+++如何禁用已填寫的活動字段？

如果您希望學習者只看到未由他們填寫的活動字段，請追隨以下步驟：

1. 點選 **[!UICONTROL Users]** > **[!UICONTROL Active Fields]**。

1. 按下 **[!UICONTROL Settings]** 並啟用選項 **[!UICONTROL Show only unfilled fields on Learner login]**。

1. 按兩下 **[!UICONTROL Save]**。

+++

+++如何防止學習者在活動字段中輸入隨機值。？

您可以限制學習者的選擇，以便他們只能選擇預定義的值，而不能輸入任何隨機值。 請遵循以下步驟：

1. 點選 **[!UICONTROL Users]** > **[!UICONTROL Active Fields]**。
1. 啟用選項 **[!UICONTROL Restrict Selection]**。
1. 按兩下 **[!UICONTROL Done]**。

+++

+++如何區分CSV活動字段和自定義活動字段？

您只能啟用或停用CSV活動中欄位，而不能將其刪除。 另一方面，您無法啟用或禁用自定義活動欄位。

+++
