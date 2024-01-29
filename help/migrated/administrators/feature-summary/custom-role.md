---
jcr-language: en_us
title: 自訂角色
description: 「學習路徑」功能可協助您定義自訂角色，並將特定責任指派給一組使用者。 此功能可讓您指派個人現有角色許可權以外的職責。
contentowner: dvenkate
source-git-commit: 46afb6603456ced9d7e2aaf98d07ec92fee30c0b
workflow-type: tm+mt
source-wordcount: '2156'
ht-degree: 0%

---



# 自訂角色

此功能可協助您定義自訂角色，並將特定職責指派給一組使用者。 此功能可讓您指派個人現有角色許可權以外的職責。

您可以建立自訂角色，以提供僅限於特定目錄的編寫功能。 您也可以建立專用於管理報告的角色。 然後，這些角色可指派給應承擔這些特定職責的個人。

## 建立自訂角色 {#create-role}

1. 以管理員身分登入。 開啟 **[!UICONTROL Users]** > **[!UICONTROL Custom Role]**.
1. 選取 **[!UICONTROL Create Role]**. 此 **[!UICONTROL Create New Role]** 標籤開啟。

   ![](assets/create-new-role.png)

   *建立自訂角色*

1. 輸入名稱，在 **[!UICONTROL Name of the Role]** 欄位。
1. **[!UICONTROL Account privileges]**：這些許可權可讓角色擁有者存取特定系統設定方面，以及作用於整個帳戶的許可權。 選擇存取許可權。 使用者可完全控制指派的許可權。

>[!NOTE]
>
>   範圍不適用於這些許可權。


![](assets/account-privileges.png)

*設定範圍*

1. **功能許可權 — 核心功能**：用於授予特定功能的存取權，以管理學習活動。 可以使用此選項提供以下功能的許可權。

   * 目錄
   * 報表
   * 標籤

   ![](assets/core-features.png)

   *設定目錄、報表和標籤的範圍*

1. **功能許可權 — 學習物件：**  使用此選項可提供LO相關功能的存取權。 您可以提供下列LO的存取權。

   * 認證
   * 課程
   * 工作輔助
   * 學習計畫

   您也可以授予LO的特定操作控制權。 許可權可以是下列其中一項：

   * 完全控制
   * 編輯和刪除
   * 註冊
   * 報告

   ![](assets/learning-objects.png)

   *授予特定許可權*

1. **功能許可權的範圍：** 配置給此角色的功能許可權範圍可以限製為特定使用者群組或一或多個目錄。

   目錄：使用選項按鈕提供控制權 **[!UICONTROL All catalogs]** 或使用 **[!UICONTROL Set access per Catalog]** 提供特定目錄存取權的選項。 您也可以選取多個目錄。

   使用者群組：提供存取許可權 **[!UICONTROL All User Groups]** 或使用 **[!UICONTROL Set access per user group]** 提供特定使用者群組存取權的選項。 只能指定單一使用者群組。

   >[!NOTE]
   >
   >如果您在「帳戶許可權」下選取宣告、遊戲化、電子郵件範本、技能和使用者，則預設會為所有使用者群組提供「使用者群組」存取權，且此選項會停用。

   如果您在「帳戶許可權」下選取了「學習計畫」，則預設會提供對所有「目錄」和「使用者群組」的存取權，而「範圍」下的這些選項會停用。

   ![](assets/define-scope-of-privileges.png)

   *定義許可權範圍*

>[!NOTE]
>
>   在Learning Manager 27.6中，您可以建立自訂角色，在多個目錄設定範圍，並為每個目錄授予不同許可權。


若要授與目錄的各種許可權，請遵循下列步驟：

1. 按一下選項 **[!UICONTROL Set access per Catalog]**.
1. 選擇目錄，您就能看到每個目錄的許可權層級。 許可權如下：

   <table>
        <tbody>
        <tr>
          <td>
          <p><b>許可權</b></p></td>
          <td>
          <p><b>說明</b></p></td>
        </tr>
        <tr>
          <td>
          <p>完全控制</p></td>
          <td>
          <p>授與所有學習物件的完整控制權。 許可權包括新增、編輯、刪除、讀取、註冊和報告。<br></p></td>
        </tr>
        <tr>
          <td>
          <p>報告</p></td>
          <td>
          <p>僅授予學習物件「報表」標籤的存取權。</p></td>
        </tr>
        <tr>
          <td>
          <p>註冊</p></td>
          <td>
          <p>授予僅註冊學習物件的許可權。</p></td>
        </tr>
        <tr>
          <td>
          <p>唯讀</p></td>
          <td>
          <p>授予僅檢視目錄中的學習物件的許可權。</p></td>
        </tr>
        </tbody>
      </table>

1. 根據您的要求啟用或停用許可權。
1. 若要儲存變更，請按一下 **[!UICONTROL OK]**. 然後，若要儲存自訂角色的變更，請按一下 **[!UICONTROL Save]**.

例如，請考量下列情況。

自訂使用者對學習物件的結果許可權是學習物件許可權和目錄許可權的交集。

自訂使用者擁有課程的完整許可權，且只有目錄A的唯讀存取權，但擁有目錄B的完整許可權。結果是對目錄A的課程的唯讀存取權和對目錄B的課程的完全控制權。

具有自訂角色的使用者可以：

* 僅檢視他/她有權存取的目錄中的內容。
* 根據學習物件所屬的目錄許可權，存取任何學習物件。

身為管理員，您可以：

* 為自訂角色選擇多個目錄。
* 隨時修改目錄許可權。
* 從您不想再授與許可權的領域移除目錄。
* 當您授與目錄的許可權時，隱含地授與目錄的唯讀許可權。

下表說明許可權的授予方式。

<table>
    <tbody>
     <tr>
      <td>
       <p><strong> </strong></p></td>
      <td>
       <p><strong>目錄層級許可權</strong></p></td>
     </tr>
     <tr>
      <td>
       <p><strong>學習物件 — 層級許可權</strong></p>
       <p><strong>（例如：課程）</strong></p></td>
      <td>
       <p>完全控制</p></td>
      <td>
       <p>註冊</p></td>
      <td>
       <p>報告</p></td>
      <td>
       <p>唯讀</p></td>
     </tr>
     <tr>
      <td>
       <p>完全控制</p></td>
      <td>
       <p>完全控制</p></td>
      <td>
       <p>註冊</p></td>
      <td>
       <p>報告</p></td>
      <td>
       <p>唯讀</p></td>
     </tr>
     <tr>
      <td>
       <p>註冊</p></td>
      <td>
       <p>註冊</p></td>
      <td>
       <p>註冊</p></td>
      <td>
       <p>唯讀</p></td>
      <td>
       <p>唯讀</p></td>
     </tr>
     <tr>
      <td>
       <p>編輯和刪除</p></td>
      <td>
       <p>編輯和刪除</p></td>
      <td>
       <p>唯讀</p></td>
      <td>
       <p>唯讀</p></td>
      <td>
       <p>唯讀</p></td>
     </tr>
     <tr>
      <td>
       <p>報告</p></td>
      <td>
       <p>報告</p></td>
      <td>
       <p>唯讀</p></td>
      <td>
       <p>報告</p></td>
      <td>
       <p>唯讀</p></td>
     </tr>
    </tbody>
   </table>
1. **使用者：**使用此選項可決定哪些使用者被指派此角色。 您可以使用搜尋方塊選擇一或多個使用者。

**新增使用者至自訂角色CSV上傳：** 若要透過CSV更新新增使用者，請新增CustomRole欄至.csv檔案（管理員用來匯入使用者）。 在您要指派自訂角色的使用者的CustomRole欄位下，輸入使用者的角色。 若要上傳CSV檔案，請按一下  **[!UICONTROL Add > Upload a CSV]**.

CustomRole欄注意：

* 您無法搜尋使用者群組。
* 您無法搜尋已指派管理員角色的使用者。
* 指派新的自訂角色給使用者，將會覆寫使用者先前的自訂角色。

<!--![](assets/users.png)-->

* 具有「設定」許可權的自訂管理員將能夠設定從資料來源同步或同步使用者的排程，即使他們沒有「使用者」實體的許可權。
* 如果自訂管理員擁有使用者實體的許可權，則可指派管理員角色給自己，成為標準管理員。

## 限制自訂作者的資料夾存取權 {#folder-custom-author}

Learning Manager已支援使用自訂角色授予內容資料庫存取權的功能。 所有已擁有內容資料庫存取權的自訂作者，即便已設定內容資料夾，仍可繼續存取所有內容檔案。 這是為了維護舊版行為。 如果管理員希望繼續目前的行為，則不需要進行任何變更。

如果他們想要限制對這些自訂作者的存取權，管理員需要編輯現有的自訂角色，並透過僅提供對特定內容資料夾的存取權來設定它們。

![](assets/folder-access-forcustomauthors.png)

*限制自訂作者的資料夾存取權*

建立自訂作者時，您現在可以將內容資料夾指派給作者。 選擇選項 **選取的資料夾**.

按一下選項後，會開啟一個新對話方塊，您可以在其中將資料夾指派給自訂作者。

![](assets/choose-folder.png)

*選取自訂作者的資料夾*

選擇資料夾並按一下 **[!UICONTROL OK]**.

## 自訂管理員的學習摘要儀表板 {#custom-admin-dashboard}

自訂管理員看到的檢視與管理員看到的相同。 自訂管理員可能會提供超出其範圍的資料。 這僅適用於自訂管理員具有完整範圍的情況。 若要在建立自訂管理員時授與完整範圍，請啟用選項 **[!UICONTROL Full Control]** 在帳戶摘要報表中。

![](assets/create-custom-role.png)

*建立自訂角色*

因此，選項 **[!UICONTROL All Catalogs]** 和 **[!UICONTROL All User Groups]** 將會被選取，而其餘的則會被停用。

![](assets/scope-of-featureprivileges.png)

*定義許可權範圍*

## 隱含許可權 {#implicitpermissions}

當使用者獲得具有特定實體的角色時，他們可能需要存取其他實體以及能夠在授與的實體上執行任務的情況。 例如，如果使用者獲得了課程實體的「建立」存取權，他們需要存取技能和標籤實體，以便他們能夠將他們與正在建立的課程相關聯。 此表格提供這類隱含許可權的資訊。

<table>
 <tbody>
  <tr>
   <th>存取型別</th>
   <th>管理員授予的實體許可權</th>
   <th>隱含實體許可權</th>
   <th>隱含存取</th>
  </tr>
  <tr>
   <td>管理</td>
   <td>使用者</td>
   <td>群組</td>
   <td>Crud</td>
  </tr>
  <tr>
   <td>註冊</td>
   <td>所有失敗（課程、工作輔助、學習計畫、認證）</td>
   <td>使用者<br>
     學習方案</td>
   <td>讀取</td>
  </tr>
  <tr>
   <td>建立</td>
   <td>
    <p>內容群組<br>
      工作輔助<br></p></td>
   <td>標籤</td>
   <td>讀取</td>
  </tr>
  <tr>
   <td>建立</td>
   <td>課程</td>
   <td>內容群組<br>
     標籤<br>
     技能<br>
     徽章<br>
     工作輔助</td>
   <td>全部讀取</td>
  </tr>
  <tr>
   <td>建立</td>
   <td>學習計畫<br>
     認證<br></td>
   <td>課程<br>
     標籤<br>
     技能<br>
     徽章</td>
   <td>讀取</td>
  </tr>
  <tr>
   <td>建立</td>
   <td>學習方案</td>
   <td>目錄<br>
     群組<br>
     技能<br>
     所有失敗（課程、工作輔助、學習計畫、認證）</td>
   <td>讀取</td>
  </tr>
  <tr>
   <td>建立</td>
   <td>宣告</td>
   <td>使用者<br>
     群組<br>
     所有失敗（課程、工作輔助、學習計畫、認證）</td>
   <td>讀取</td>
  </tr>
  <tr>
   <td>建立</td>
   <td>遊戲</td>
   <td>品牌化</td>
   <td>寫入</td>
  </tr>
  <tr>
   <td>*</td>
   <td>使用者</td>
   <td>帳單</td>
   <td>讀取</td>
  </tr>
  <tr>
   <td>*</td>
   <td>目錄</td>
   <td>群組<br>
     所有失敗（課程、工作輔助、學習計畫、認證）</td>
   <td>讀取</td>
  </tr>
  <tr>
   <td>*</td>
   <td>設定</td>
   <td>品牌化<br>
     使用者</td>
   <td>讀取</td>
  </tr>
  <tr>
   <td>*</td>
   <td>品牌化</td>
   <td>設定</td>
   <td>讀取</td>
  </tr>
  <tr>
   <td>*</td>
   <td>帳單<br>
     遊戲</td>
   <td>使用者</td>
   <td>讀取</td>
  </tr>
 </tbody>
</table>

## 存取自訂角色 {#accessacustomrole}

管理員指派自訂角色時，您會收到電子郵件通知。

注意：如果您已使用自訂角色登入Learning Manager，則需要重新登入Learning Manager才能存取新角色。

若要切換角色，請按一下Learning Manager右上角的設定檔圖示，然後選取角色。

## 由可設定角色界定的學習計畫 {#scopeconfigure}

在舊版Learning Manager中，任何有權建立學習計畫的自訂角色都可以設定所有型別使用者群組和學習物件的學習計畫範圍。

此範圍設定過去會在授與學習計畫存取權時停用，依預設會授與使用者存取所有目錄和所有使用者群組的許可權。

依預設，管理員建立的所有學習計畫均適用於所有使用者。 您也可以為使用者指派任何學習物件。 另一方面，擁有「自訂角色」的使用者可存取完整範圍，例如所有目錄、學習物件或使用者群組。 這表示管理員無法按預期建立自訂角色，以允許有限範圍的使用者存取學習計畫。

在這個Learning Manager更新中，您可以建立學習計畫的自訂角色，以設定使用者和學習物件的範圍。 換言之，您可以使用衍生自自訂管理員角色範圍的有限範圍來建立學習計畫。

現在，管理員可以在授與學習計畫管理存取權時定義或限制範圍。

自訂管理員可用有限的範圍建立學習計畫，具體取決於自訂管理員可設定角色的範圍。 這類學習計畫除了可供一般管理員存取外，僅供具有相同角色的自訂管理員存取。 此外，自訂管理員無法在帳戶中看到任何其他學習計畫。

有權存取學習計畫的現有自訂管理員將一律具有完整範圍（依定義）。 他們會像一般管理員一樣存取帳戶中的所有學習計畫。 以完整範圍建立的新自訂角色，以及新增至這些角色的新自訂管理員，將可繼續存取所有學習計畫。

管理員和完整範圍自訂管理員建立的學習計畫會照常建立，不受範圍限制。

在區段中 **功能許可權範圍**，授與自訂角色的使用者群組和/或目錄的存取權。

![](assets/scope-for-featureprivileges.png)

*授與自訂角色的使用者群組和/或目錄的存取權*

將使用者指派給自訂角色。

![](assets/assign-users-to-customrole.png)

*將使用者指派給自訂角色*

使用者現在以自訂管理員身分登入Learning Manager，並新增學習計畫。

新增新學習者時，自訂管理員只能從可設定角色的範圍目錄中選取訓練。

此學習計畫現在僅適用於學習者，前提是使用者也新增至學習計畫範圍內使用者群組中的群組。 所有其他學習者可獲劐免使用此學習方案。

## 學習者已新增至群組 {#learnergetsaddedtothegroup}

<!--![](assets/add-learner-to-thegroup.png)-->

自訂管理員可從角色所屬範圍內的使用者群組中，選取擁有使用者的任何使用者群組。

將使用者新增至指定群組時，只有已屬於學習計畫之範圍使用者群組，且已新增至指定使用者群組的使用者，才會獲指派學習物件。

## 範圍變更 {#changeinscope}

當管理員變更自訂角色的範圍時，變更也會級聯到自訂管理員。 當自訂管理員選擇已受先前自訂角色範圍的學習計畫時，會顯示訊息，如下所示：

![](assets/change-scope.png)

*範圍變更後的訊息*

自訂管理員現在必須將先前的範圍更新或重新整理到新範圍。

按一下 **[!UICONTROL Refresh Scope]** 更新範圍。 系統會顯示警告訊息。

![](assets/refresh-scope-message.png)

*重新整理範圍後的警告訊息*

按一下 **[!UICONTROL Yes]** 更新範圍。

## 新增遊戲化報表至自訂角色 {#gamification-custom}

管理員可以為自訂使用者啟用遊戲化報表。

1. 在 **[!UICONTROL Custom Roles]** 頁面，輸入自訂角色的名稱。
1. 在 **[!UICONTROL Feature Privileges: Core Features]** 區段，啟用選項 **[!UICONTROL Full Control]** 類別 **[!UICONTROL Reports]**.

1. 在區段中 **[!UICONTROL Users]**，選取將指派新建立之自訂角色的使用者。
1. 按一下 **[!UICONTROL Save]**.

當使用者以自訂管理員身份登入並按一下 **[!UICONTROL Reports]** 成績單會顯示在左窗格中，如下所示：

![](assets/download-gamificationtranscripts.png)

*下載遊戲成績單*

按一下 **[!UICONTROL Gamification Transcripts]**，選擇使用者並產生報表。

如果管理員變更了層級點，報表會根據目前點顯示層級。

重設遊戲化不會重設層級的達成日期。

## 常見問題 {#frequentlyaskedquestions}

+++如何建立自訂角色？

自訂角色就像作者或管理員角色的子集。 允許一或多個許可權、定義範圍，並將角色指派給使用者。

按一下 **[!UICONTROL Users]** > **[!UICONTROL Custom Roles]**. 在「自訂角色」頁面中，按一下 **[!UICONTROL Create Role]**. 輸入自訂角色的名稱並設定角色的許可權。 如需詳細資訊，請參閱 [建立自訂角色](custom-role.md#create-role).
+++
