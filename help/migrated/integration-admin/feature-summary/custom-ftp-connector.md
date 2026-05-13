---
description: Adobe Learning Manager 中的自訂 FTP 連接器
jcr-language: en_us
title: 客製化 FTP 連接器
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---


# Adobe Learning Manager 中的自訂 FTP 連接器

## 簡介

Adobe Learning Manager 中的自訂 FTP 連接器能在 Adobe Learning Manager 與貴組織的 FTP（SFTP） 伺服器之間安全且自動化地交換資料。 透過此整合，管理員可從外部系統匯入使用者資料，並排程匯出學習者成績單或技能資料。 此架構簡化了資料同步，減少人工工作，並支持與第三方人力資源或報告系統的無縫整合。 設定需要與您的 IT 團隊協調，並由 Adobe 客戶成功經理（CSM）協助。

>[!NOTE]
>
>若要設定自訂 FTP 連線，請聯絡您的客戶成功經理（CSM）。 設定過程可能需要 IT 團隊協助，將 IP 位址列入白名單、開啟所需埠口，以及建立具備必要存取權限的資料夾。

## 支援功能

自訂 FTP 連接器支援以下動作：

### 資料匯入

使用者匯入流程會自動從您的 FTP 伺服器擷取員工資料並匯入 Adobe Learning Manager。 這在整合多個產生包含使用者資料的 CSV 檔案的系統時非常有用。

- 將 CSV 檔案放入 FTP 伺服器指定的 **匯入** 資料夾。
- Adobe Learning Manager 會偵測檔案，必要時合併，並依照設定的排程匯入使用者資料。

請參閱 [排程](/help/migrated/integration-admin/feature-summary/custom-ftp-connector.md#scheduling-reports) 部分，了解如何自動化此流程。

### 屬性映射

作為整合管理員，你可以將 CSV 檔案中的欄位映射到 Adobe Learning Manager 的可分組屬性。

- 地圖製作是一次性的設定。
- 後續匯入也會使用相同的映射。
- 如果你的資料結構改變，你可以重新配置映射。

### 資料匯出

Adobe Learning Manager 允許您匯出：

- 使用者技能
- 學習者成績單

這些報告檔案會被放在 FTP 的匯出資料夾中，第三方系統可用於報告、分析或其他下游流程。

### 排程報告

整合管理員可以同時排程：

- 使用者匯入
- 學習者轉錄匯出

排程確保你的 Adobe Learning Manager 環境能與來源系統保持同步。 你可以根據需要設定每日同步或自訂間隔。

## 設定自訂 FTP 連接器

要設定自訂 FTP 連接器：

1. 以整合管理員身份登入 Adobe Learning Manager。
2. 將滑鼠移到 **自訂 FTP** 圖塊上，選擇 **連接**。

   ![](assets/custom-ftp-connector1.png)
   _選擇「連接」以設定自訂 FTP 連接器_

### 選擇認證方法

你可以用兩種認證類型之一來設定自訂 FTP 連線：

#### 基本認證帳號

1. 請輸入以下細節：

   - **你的 FTP 網域**
   - **FTP 使用者名稱**
   - **FTP 密碼**

   ![](assets/custom-ftp-connector2.png)
   _輸入 FTP 網域、使用者名稱和密碼來設定設定。_

2. 選擇 **「連接**」。

#### 憑證認證

如果你的 FTP 伺服器支援 SSH 金鑰驗證：

1. 選擇 **產生 SSH 金鑰**。

   ![](assets/custom-ftp-connector3.png)
   _選擇產生 SSH 金鑰以下載金鑰_

2. 公鑰會被下載到你的電腦上。
3. 將此金鑰加入你的 FTP 伺服器授權金鑰清單。
4. 請輸入以下細節：

   - **你的 FTP 網域**
   - **FTP 使用者名稱**
5. 選擇 **「連接**」。

>[!NOTE]
>
>僅 **支援 SFTP** 伺服器以進行自訂 FTP 設定。

## 連線後設定

一旦建立連結：

- Adobe Learning Manager 會自動建立用於 **匯入** 和 **匯出** 的資料夾到你的 FTP 伺服器。
- 你可以根據你的排程和地圖設定開始匯入和匯出資料。
