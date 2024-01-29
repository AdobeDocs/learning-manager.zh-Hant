---
jcr-language: en_us
title: 安裝Salesforce套件
description: Learning Manager提供Salesforce應用程式套件。 在SFDC中安裝並設定後，銷售員工可以在SFDC入口網站中執行其培訓活動。 此應用程式可讓SFDC使用者直接在SFDC入口網站中探索新培訓、檢視建議並加以使用。 使用者也可以直接在SFDC入口網站的應用程式中，取得管理員以刊頭形式傳送的公告。
contentowner: saghosh
source-git-commit: ab6737e8b43222a6538921b0628a504a5f15859d
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 0%

---



# 安裝Salesforce套件

## 概觀

Learning Manager提供Salesforce應用程式套件。 在SFDC中安裝並設定後，銷售員工可以在SFDC入口網站中執行其培訓活動。 此應用程式可讓SFDC使用者直接在SFDC入口網站中探索新培訓、檢視建議並加以使用。 使用者也可以直接在SFDC入口網站的應用程式中，取得管理員以刊頭形式傳送的公告。

### 在Learning Manager應用程式中設定

1. 以整合管理員身分登入您的Learning Manager管理員帳戶。
1. 按一下 **[!UICONTROL Applications]** > **[!UICONTROL Featured Apps]**.
1. 按一下 **[!UICONTROL Salesforce]**.
1. 在Salesforce應用程式頁面上，記下說明中提及的應用程式ID （也稱為使用者端ID）和使用者端密碼。
1. 按一下 **[!UICONTROL Approve]** 而且您的應用程式必須成功核准。
1. 按一下 **[!UICONTROL Developer Resources]** > **[!UICONTROL Access Tokens for Testing and Development]**.
1. 在取得OAuth程式碼區段中，使用者端ID和範圍必須設定為 — admin：read，admin：write。 按一下 **[!UICONTROL Submit]**.
1. 在取得重新整理權杖中，輸入使用者端ID和使用者端密碼。 按一下 **[!UICONTROL Submit]** 並記下重新整理權杖。

### 在Salesforce應用程式中建立帳戶

1. 在Salesforce註冊頁面上建立帳戶。 您必須在開發人員版或企業版中建立Salesforce帳戶。  [開發人員註冊URL](https://developer.salesforce.com/signup). 請務必使用電子郵件ID註冊用於Learning Manager的Salesforce。
1. 透過驗證電子郵件驗證您的帳戶。
1. 建立密碼並登入Salesforce。
1. 記下登入後的Salesforce URL (例如site.lightning.force.com)

### 安裝Learning Manager套件

如果要安裝套件，必須先刪除Salesforce中的現有套件。 在解除安裝之前，您必須啟用設定，如下所示。 必須套用這些設定，否則您將無法安裝套件。

![](assets/uninstall-package.png)

*安裝Learning Manager套件*

>[!NOTE]
>
>Adobe Learning Manager應用程式僅在Salesforce閃電檢視中受支援。

1. 啟動  [Learning Manager套件url](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Ftest.salesforce.com%2Fpackaging%2FinstallPackage.apexp%3Fp0%3D04t1k0000008YWn&amp;data=04%7C01%7Ckillamse%40adobe.com%7Cf588f553fc694d2edee108d9a5c74711%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C637723097572585825%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&amp;sdata=mhYKVdwvS4F7WPruy0Kvw%2FsqgWxzTQpaZJyEACu8CNw%3D&amp;reserved=0).
1. 在 **登入** 頁面，按一下 **[!UICONTROL Use Custom Domain]**.

1. 輸入封裝URL並按一下 **[!UICONTROL Continue]**. 安裝頁面必須選取僅供管理員安裝的選項。 請勿變更此選項。
1. 按一下 **Ins高**. 安裝套件後，按一下 **[!UICONTROL Done]**. 系統會引導您前往已安裝套件頁面，您會看到AdobeLearning Manager已安裝套件。

1. 前往App Launcher （「設定」旁）搜尋AdobeLearning Manager。
1. 若要設定應用程式，請按一下 **[!UICONTROL Configure]**.
1. 按一下 **[!UICONTROL New]** 並新增下列詳細資料：

   * **設定：** 輸入您選擇的名稱。
   * **使用者端ID**：輸入您從第一個區段取得的值。
   * **使用者端密碼：** 輸入您從第一個區段中取得的值。
   * **RefreshToken：** 輸入您從第一個區段中取得的值。
   * **LearningManager基礎URL：** Learning Manager託管所在網站的URL。
   * **停用重新導向：** 在Learning Manager中停用學習者首頁的重新導向。

>[!NOTE]
>
>您只能建立單一組態。 如果您嘗試新增其他設定，則會看到錯誤訊息。 此設定會將Salesforce帳戶與學習者帳戶對應。

### 新增遠端站台設定

1. 在頁面的右上角，按一下 **[!UICONTROL Setup]**.
1. 在 **快速尋找**，搜尋遠端網站設定。
1. 按一下 **[!UICONTROL New Remote Site]**.
1. 輸入詳細資料：

   1. **遠端站台名稱：** 輸入您選擇的名稱。
   1. **遠端站台URL：** Learning Manager託管所在網站的URL。

1. 啟動Learning Manager。

### 啟用Learning Manager應用程式通知

1. 在右上角，按一下 **設定**.
1. 搜尋自訂通知。
1. 按一下 **[!UICONTROL New]**.
1. 輸入下列明細：

   1. **自訂通知名稱：** LearningManager通知
   1. **API名稱：** LearningManager通知

1. 選取兩者 **案頭** 和 **行動** 作為支援的管道。

1. 按一下 **[!UICONTROL Save]**.
1. 若要啟用行動裝置的推播通知，請遵循下列步驟：

   1. 在行動電話中安裝Salesforce行動應用程式。
   1. 使用您的憑證登入應用程式。
   1. 前往 **設定** > **通知傳送設定**.
   1. 新增適用於iOS和Android的Salesforce。

### 從Salesforce解除安裝Learning Manager

1. 在Salesforce應用程式中，前往已安裝的套件。
1. 按一下 **[!UICONTROL Uninstall]**.

## 為Salesforce使用者設定Learning Manager

Learning Manager應用程式也可供任何Salesforce帳戶中的使用者使用。 Salesforce管理員可以根據設定檔新增使用者。 Salesforce設定檔類似於Learning Manager中的設定檔。 例如，管理員、整合管理員、講師等。 Salesforce管理員也可以建立自訂設定檔。

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

當您安裝套件時，會建立新的許可權集， **AdobeLearning Manager使用者**. 前往許可權集，然後新增使用者。

選取使用者並據此指派許可權。 學習者現在可以存取Learning Manager應用程式。

現在，選取設定檔，例如，使用者的標準設定檔，然後按一下該設定檔。 按一下 **[!UICONTROL Edit]** 和 **自訂應用程式設定** 區段，啟用核取方塊 **AdobeLearning Manager**. 這可讓使用者存取應用程式。

在 **自訂標籤設定** 區段，在 **學習者首頁** 從下拉式清單中選取選項 **[!UICONTROL Default On]**.

您必須讓所有設定檔都能看見應用程式。

按一下 **[!UICONTROL Save]** 而屬於所有設定檔的學習者將可存取Learning Manager應用程式。
