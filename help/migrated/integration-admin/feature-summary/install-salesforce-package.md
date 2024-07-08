---
jcr-language: en_us
title: 安裝 Salesforce 套裝
description: Learning Manager 提供 Salesforce 應用程式 套裝。 在 SFDC 中安裝和配置后，銷售員工可以在 SFDC 門戶中執行其培訓活動。 此應用程式允許 SFDC 使用者探索新的培訓、視圖建議並直接在 SFDC 門戶中使用它們。 使用者還可以在 SFDC 門戶內的應用程式內以刊頭的形式接收管理員發送的通知。
contentowner: saghosh
exl-id: 2b1c32e7-81af-4c13-a2bd-66684cde084e
source-git-commit: fb946ae98dce45156e2f4c1cf992319405403ea9
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 0%

---

# 安裝 Salesforce 套裝

## 概觀

Learning Manager 提供 Salesforce 應用程式 套裝。 在 SFDC 中安裝和配置后，銷售員工可以在 SFDC 門戶中執行其培訓活動。 此應用程式允許 SFDC 使用者探索新的培訓、視圖建議並直接在 SFDC 門戶中使用它們。 使用者還可以在 SFDC 門戶內的應用程式內以刊頭的形式接收管理員發送的通知。

### 在學習管理器應用中設置

1. 以集成管理員身份登錄學習管理器管理員帳戶。
1. 點選 **[!UICONTROL Applications]** > **[!UICONTROL Featured Apps]**。
1. 按兩下 **[!UICONTROL Salesforce]**。
1. 在 Salesforce 應用程式頁面上，記下說明中提到的應用程式 ID（也稱為用戶端 ID）和客戶端密碼。
1. 按兩下， **[!UICONTROL Approve]** 您的應用必須成功獲得批准。
1. 點選 **[!UICONTROL Developer Resources]** > **[!UICONTROL Access Tokens for Testing and Development]**。
1. 在“獲取 OAuth Code”部分中，用戶端 ID 和範圍必須設置為 - admin：read，admin：write。 按兩下 **[!UICONTROL Submit]**。
1. 在「獲取重新整理令牌」中，輸入「用戶端 ID」 和「用戶端密碼」。 按兩下 **[!UICONTROL Submit]** 並注意刷新令牌。

### 在 Salesforce 應用程式中建立 帳戶

1. 建立 Salesforce 註冊頁面上的帳戶。 您必須建立開發人員版或企業版的 Salesforce 帳戶。  [開發者註冊URL](https://developer.salesforce.com/signup)。 確保必須使用電子郵件 ID 註冊用於學習管理器的 Salesforce。
1. 通過驗證電子郵件驗證您的帳戶。
1. 建立密碼並登入 Salesforce。
1. 記下 登入 后的 Salesforce url（例如 site.lightning.force.com）

### 安裝學習管理員包

如果要安裝套裝，必須先在 Salesforce 中刪除現有套裝。 在卸載之前，您必須啟用設置，如下所示。 必須應用這些設置，否則將無法安裝包。

![](assets/uninstall-package.png)

*安裝學習管理員包*

>[!NOTE]
>
>Adobe Systems Learning Manager 應用程式僅在 Salesforce Lightning 視圖 中受支持。

1. [Launch學習管理器包 URL](https://test.salesforce.com/packaging/installPackage.apexp?p0=04tDb000000LRvP)。
1. 在 **「登入」** 頁面中，按兩下 **[!UICONTROL Use Custom Domain]**。

1. 輸入封裝URL然後按下 **[!UICONTROL Continue]**。 安裝頁面必須選中「僅供管理員安裝」選項。 請勿變更此選項。
1. 按兩下英 **斯高**。 安裝套件後，按兩下 **[!UICONTROL Done]**。 系統將引導您進入“已安裝的包”頁面，並可以看到Adobe Systems學習管理器已安裝的包。

1. 轉到應用程式啟動器（設置旁邊）並搜尋學習管理器Adobe Systems。
1. 要設定應用程式，請按下 **[!UICONTROL Configure]**。
1. 按下 **[!UICONTROL New]** 並新增以下詳細資訊：

   * **配置：** 輸入您選擇的名稱。
   * **用戶端 ID**：輸入從第一部分獲取的值。
   * **用戶端機密：** 輸入從第一部分獲取的值。
   * **刷新令牌：** 輸入從第一部分獲取的值。
   * **學習管理器基本 URL：** 託管學習管理員的網站的URL。
   * **禁用重定向：** 禁用重定向到學習管理器中的學習者首頁。

>[!NOTE]
>
>您只能建立單個配置。 如果您嘗試添加其他配置，您將看到一條錯誤消息。 該配置將 Salesforce 帳戶與學習者帳戶對應。

### 添加遠端網站設定

1. 在頁面的右上角，按兩下 **[!UICONTROL Setup]**。
1. 在“快速查找”**中**，搜尋“遠端網站設定。
1. 按兩下 **[!UICONTROL New Remote Site]**。
1. 輸入詳細資訊：

   1. **遠端網站名稱：** 輸入您選擇的名稱。
   1. **遠端網站URL：** 託管學習管理器的網站URL。

1. Launch學習管理員。

### 將 Adobe Systems 域新增至 Salesforce 可信 URL

若要將 Adobe Systems 域添加到受信任的 URL，追隨以下步驟：

1. 在 Salesforce 控制台中，轉至 **[!UICONTROL Setup]** > **[!UICONTROL Quick Find]**。
1. Search 並選擇 **[!UICONTROL Trusted URLs]** **[!UICONTROL New Trusted URL]**。
1. 在 **[!UICONTROL API Name]** 欄位中鍵入名稱。
1. `*.adobe.com`鍵入URL欄位。
1. 選取 CSP 指令&#x200B;**中的所有**&#x200B;複選框並儲存變更。
1. 編輯 Salesforce 應用程式的重新整理標記並儲存。
1. 重新啟動 Salesforce 應用程式。

### 為學習管理員應用啟用通知

1. 在右上角 **按兩下設定**。
1. Search自定義通知。
1. 按兩下 **[!UICONTROL New]**。
1. 輸入以下詳細資訊：

   1. **自定義通知名稱：** LearningManagerNotification
   1. **API 名稱：** LearningManagerNotification

1. 選擇桌面&#x200B;**和**&#x200B;行動裝置&#x200B;**作為**&#x200B;支援的頻道。

1. 按兩下 **[!UICONTROL Save]**。
1. 要啟用行動裝置的推送通知，追隨以下步驟：

   1. 在行動電話中安裝 Salesforce 行動應用程式。
   1. 使用您的憑據登錄到應用程式。
   1. 轉至 **設定** 通知> **傳送設定**。
   1. 新增適用於 iOS 和 Android 的 Salesforce。

### 從 Salesforce 中卸載學習管理器

1. 在 Salesforce 應用程式中，轉到已安裝的套件。
1. 按兩下 **[!UICONTROL Uninstall]**。

## 為 Salesforce 使用者設定學習管理員

學習管理器應用程式也可供任何 Salesforce 帳戶中的使用者使用。 Salesforce 管理員可以根據使用者檔案新增使用者。 Salesforce 設定檔與學習管理器中的配置檔類似。 例如，管理員、整合管理員、講師等。 Salesforce 管理員還可以創建自定義設定檔。

### 輪廓

作為 Salesforce 管理員，您可以將設定檔分配給使用者或創建自定義設定檔。

>[!NOTE]
>
>用戶必須同時存在於 Salesforce 和學習管理器中。

![](assets/create-profile.png)

*為學習者分配設定檔*

添加學習者時，必須為學習者分配特定設定檔。 然後轉到該設定檔並授予所需的訪問許可權。

要讓學習者視圖學習管理器應用程式，您必須為所有學習者啟用該應用程式。

下一步是提供訪問學習管理器應用權限。

![](assets/permission-set.png)

*添加訪問學習管理員應用的許可權*

安裝包時，將創建一個新的權限集， **Adobe Systems學習管理器使用者**。 轉到權限集，然後添加使用者。

選擇用戶並相應地分配許可權。 學習者現在可以訪問學習管理器應用程式。

現在，選擇一個設定檔，例如用戶的標準配置文件，然後按下設定檔。 按兩下 **[!UICONTROL Edit]** 並在自定義 **應用程式 設定** 部分中，啟用 **Adobe Systems學習管理器**&#x200B;複選框。 這使得用戶可以訪問該應用程式。

在“**自定義選項卡設定**”部分的“學習者主页&#x200B;**”**&#x200B;下拉清單中，選擇選項 **[!UICONTROL Default On]**。

您必須讓應用程式對所有設定檔可見。

按兩下， **[!UICONTROL Save]** 屬於所有設定檔的學習者將訪問學習管理器應用程式。
