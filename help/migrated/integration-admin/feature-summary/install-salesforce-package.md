---
jcr-language: en_us
title: 安裝Salesforce套件
description: Learning Manager提供Salesforce應用程式套件。 在SFDC中安裝並設定後，銷售員工可以在SFDC入口網站內執行其培訓活動。 此應用程式可讓SFDC使用者直接在SFDC入口網站中探索新培訓、檢視建議和使用這些內容。 使用者也可以在SFDC入口網站的應用程式內，直接透過刊頭取得管理員傳送的公告。
contentowner: saghosh
exl-id: 2b1c32e7-81af-4c13-a2bd-66684cde084e
source-git-commit: 5d50bd56b6663b26fc6db0ff33d19ad809e9bf6a
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 0%

---

# 安裝Salesforce套件

## 概觀

Learning Manager提供Salesforce應用程式套件。 在SFDC中安裝並設定後，銷售員工可以在SFDC入口網站內執行其培訓活動。 此應用程式可讓SFDC使用者直接在SFDC入口網站中探索新培訓、檢視建議和使用這些內容。 使用者也可以在SFDC入口網站的應用程式內，直接透過刊頭取得管理員傳送的公告。

### 在Learning Manager應用程式中設定

1. 以整合管理員身分登入您的Learning Manager管理員帳戶。
1. 按一下&#x200B;**[!UICONTROL Applications]** > **[!UICONTROL Featured Apps]**。
1. 按一下&#x200B;**[!UICONTROL Salesforce]**。
1. 在Salesforce應用程式頁面上，記下說明中提及的應用程式ID （也稱為使用者端ID）和使用者端密碼。
1. 按一下「**[!UICONTROL Approve]**」，您的應用程式必須成功核准。
1. 按一下&#x200B;**[!UICONTROL Developer Resources]** > **[!UICONTROL Access Tokens for Testing and Development]**。
1. 在「取得OAuth代碼」區段中，使用者端ID和範圍必須設定為 — admin:read，admin:write。 按一下&#x200B;**[!UICONTROL Submit]**。
1. 在取得重新整理權杖中，輸入使用者端ID和使用者端密碼。 按一下&#x200B;**[!UICONTROL Submit]**&#x200B;並記下重新整理權杖。

### 在Salesforce應用程式中建立帳戶

1. 在Salesforce註冊頁面上建立帳戶。 您必須在開發人員版或企業版中建立Salesforce帳戶。  [開發人員註冊網址](https://developer.salesforce.com/signup)。 請確定您必須使用電子郵件ID來註冊用於Learning Manager的Salesforce。
1. 透過驗證電子郵件驗證您的帳戶。
1. 建立密碼並登入Salesforce。
1. 請注意登入後的Salesforce URL (例如site.lightning.force.com)

### 安裝Learning Manager套件

如果您想要安裝套件，必須先刪除Salesforce中的現有套件。 在解除安裝之前，您必須啟用設定，如下所示。 必須套用這些設定，否則您將無法安裝套件。

![](assets/uninstall-package.png)

*安裝Learning Manager套件*

>[!NOTE]
>
>Adobe Learning Manager應用程式僅在Salesforce閃電檢視中支援。

1. 啟動[Learning Manager封裝url](https://test.salesforce.com/packaging/installPackage.apexp?p0=04tDb000000FvU2)。
1. 在&#x200B;**登入**&#x200B;頁面中，按一下&#x200B;**[!UICONTROL Use Custom Domain]**。
1. 輸入封裝URL並按一下&#x200B;**[!UICONTROL Continue]**。 安裝頁面必須選取僅供管理員安裝的選項。 請勿變更此選項。
1. 按一下&#x200B;**[!UICONTROL Install]**。 安裝套件後，按一下&#x200B;**[!UICONTROL Done]**。 系統引導您前往已安裝的套件頁面，而您可以看到Adobe Learning Manager已安裝的套件。

1. 前往應用程式啟動器（「設定」旁邊）並搜尋Adobe Learning Manager。
1. 若要設定應用程式，請按一下&#x200B;**[!UICONTROL Configure]**。
1. 按一下&#x200B;**[!UICONTROL New]**&#x200B;並新增下列詳細資料：

   * **設定：**&#x200B;請輸入您選擇的名稱。
   * **ClientID**：輸入您從第一個區段取得的值。
   * **ClientSecret：**&#x200B;請輸入您從第一個區段取得的值。
   * **RefreshToken：**&#x200B;請輸入您從第一個區段取得的值。
   * **LearningManagerBaseURL：** Learning Manager託管所在網站的URL。
   * **停用重新導向：**&#x200B;停用重新導向至Learning Manager中的學習者首頁。

>[!NOTE]
>
>您只能建立單一組態。 如果您嘗試新增其他設定，則會看到錯誤訊息。 此設定會將Salesforce帳戶與學習者帳戶對應。

### 新增遠端站台設定

1. 在頁面的右上角，按一下&#x200B;**[!UICONTROL Setup]**。
1. 在&#x200B;**快速尋找**&#x200B;中搜尋遠端網站設定。
1. 按一下&#x200B;**[!UICONTROL New Remote Site]**。
1. 輸入詳細資料：

   1. **遠端站台名稱：**&#x200B;請輸入您選擇的名稱。
   1. **遠端站台URL：** Learning Manager所在站台的URL。

1. 啟動Learning Manager。

### 將Adobe網域新增至Salesforce信任的URL

若要將Adobe網域新增至信任的URL，請遵循下列步驟：

1. 在Salesforce主控台中，前往&#x200B;**[!UICONTROL Setup]** > **[!UICONTROL Quick Find]**。
1. 搜尋&#x200B;**[!UICONTROL Trusted URLs]**&#x200B;並選取&#x200B;**[!UICONTROL New Trusted URL]**。
1. 在&#x200B;**[!UICONTROL API Name]**&#x200B;欄位中輸入名稱。
1. 在URL欄位中輸入`*.adobe.com`。
1. 選取&#x200B;**CSP指示**&#x200B;中的所有核取方塊並儲存變更。
1. 編輯Salesforce應用程式的重新整理權杖並儲存。
1. 重新啟動Salesforce App。

### 啟用Learning Manager應用程式的通知

1. 按一下右上角的&#x200B;**設定**。
1. 搜尋自訂通知。
1. 按一下&#x200B;**[!UICONTROL New]**。
1. 輸入下列明細：

   1. **自訂通知名稱：** LearningManagerNotification
   1. **API名稱：** LearningManagerNotification

1. 選取&#x200B;**案頭**&#x200B;和&#x200B;**行動裝置**&#x200B;作為支援的頻道。

1. 按一下&#x200B;**[!UICONTROL Save]**。
1. 若要啟用行動裝置的推播通知，請遵循下列步驟：

   1. 在行動電話中安裝Salesforce行動應用程式。
   1. 使用您的憑證登入應用程式。
   1. 移至&#x200B;**設定** > **通知傳遞設定**。
   1. 新增適用於iOS和Android的Salesforce。

### 從Salesforce解除安裝Learning Manager

1. 在Salesforce應用程式中，前往已安裝的套件。
1. 按一下&#x200B;**[!UICONTROL Uninstall]**。

## 為Salesforce使用者設定Learning Manager

使用者也可以使用存在於任何Learning Manager帳戶中的Salesforce應用程式。 Salesforce管理員可以根據設定檔新增使用者。 Salesforce設定檔類似於Learning Manager中的設定檔。 例如，管理員、整合管理員、講師等。 Salesforce管理員也可以建立自訂設定檔。

### 個人資料

身為Salesforce管理員，您可以將設定檔指派給使用者或建立自訂設定檔。

>[!NOTE]
>
>使用者必須同時出現在Salesforce和Learning Manager中。

![](assets/create-profile.png)

*將設定檔指派給學習者*

新增學習者時，您必須將特定設定檔指派給學習者。 然後前往該設定檔並授予所需的存取權。

若要讓學習者檢視Learning Manager應用程式，您必須為所有學習者啟用應用程式。

下一步是提供存取Learning Manager應用程式的許可權。

![](assets/permission-set.png)

*新增存取Learning Manager應用程式的許可權*

當您安裝套件時，會建立新的許可權集，**Adobe Learning Manager使用者**。 前往許可權集，然後新增使用者。

選取使用者並據此指派許可權。 學習者現在可以存取Learning Manager應用程式。

現在，選取設定檔，例如，使用者的標準設定檔，然後按一下該設定檔。 按一下&#x200B;**[!UICONTROL Edit]**，然後在&#x200B;**自訂應用程式設定**&#x200B;區段中，啟用核取方塊&#x200B;**Adobe Learning Manager**。 這可讓使用者存取應用程式。

在&#x200B;**自訂標籤設定**&#x200B;區段的&#x200B;**學習者首頁**&#x200B;下拉式清單中，選取選項&#x200B;**[!UICONTROL Default On]**。

您必須讓所有設定檔都能看見應用程式。

按一下「**[!UICONTROL Save]**」，則屬於所有設定檔的學習者將會存取Learning Manager應用程式。
