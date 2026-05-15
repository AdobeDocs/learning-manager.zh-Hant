---
description: 關於每個 ALM 支援連接器的概述
jcr-language: en_us
title: ALM 支援連接器的綜述
contentowner: mmanuel
source-git-commit: bd80ca31ff633e21ec81e717772e43989f0d9aae
workflow-type: tm+mt
source-wordcount: '1424'
ht-degree: 0%

---


# Adobe Learning Manager 連接器

## 簡介

Adobe Learning Manager （ALM） 提供一套完整的連接器，使得與第三方應用程式及企業系統無縫整合。 這些連接器作為學習管理系統與外部平台之間的橋樑，促進自動資料同步、使用者管理、內容匯入及學習紀錄匯出。

本文件可作為您理解並選擇適合組織學習生態系統連結工具的完整參考指南。 無論你想整合人力資源系統、電子商務平台、虛擬會議工具，或是商業智慧解決方案。

如需Adobe Learning Manager支援的完整連接器清單，請參閱左側目錄中本文下方巢狀的連接器文章。

>[!NOTE]
>
>此功能部分可在 FedRAMP 授權環境中提供。 詳情請參閱 [FedRAMP 環境](/help/migrated/feature-availability-in-fedramp-authorized-environment.md) 的功能可用性。

>[!NOTE]
>
>隨著 2022 年 11 月 Adobe Learning Manager 的發布，Zoom 已於 2023[&#128279;](https://developers.zoom.us/docs/internal-apps/s2s-oauth/) 年 6 月停止使用 JWT 認證。因此，與 JWT 的 Zoom 連接器將持續使用直到指定日期，但我們建議用戶建立伺服器對伺服器的 OAuth 應用程式，以取代帳號中的此功能。 任何新連線預設都會有 Zoom OAuth 認證。

## 連接器類別

Adobe Learning Manager 連接器可依其主要用途及整合能力組織為數個功能類別：

| 類別 | 目的 | 連接器範例 |
|---------|--------|-------------------|
| 資料傳輸 | 基於檔案的資料交換與批量操作 | FTP、自訂 FTP、盒子 |
| 虛擬教室 | 現場訓練與會議整合 | Microsoft Teams、Zoom、Adobe Connect |
| 企業系統 | 人力資源與商業系統整合 | Workday、Salesforce、ADFS |
| 內容平台 | 外部學習內容整合 | LinkedIn Learning、Harvard ManageMentor、getAbstract |
| 分析與商業智慧 | 報告與資料視覺化 | Power BI，訓練資料存取 |
| Authentication | 身份管理與安全 | ADFS（單點單點功能） |
| 電子商務與行銷 | 銷售與行銷整合 | Adobe 商務、Marketo Engage |

## 資料傳輸與檔案管理連接器

這些連接器透過檔案傳輸協定促進自動資料交換，實現大規模操作及系統間通訊。

### Adobe Learning Manager FTP 連接器

FTP 連接器使組織能利用廣泛採用的檔案傳輸協定，自動化 Adobe Learning Manager 與外部系統之間的資料同步。 此連接器支援多種安全變體，包括 SFTP（SSH 檔案傳輸協定）與 FTPS（FTP Secure）以提升安全性。

#### 主要能力：

- 在 Adobe Learning Manager 與遠端伺服器之間上傳與下載檔案。
- 自動化資料交換，用於使用者資訊與訓練紀錄。
- 支援安全檔案傳輸協定（SFTP、FTPS）。
- 大量資料集的批次處理。

欲了解更多資訊，請參閱 [FTP 連接器](/help/migrated/integration-admin/feature-summary/ftp-connector.md)。

### 客製化 FTP 連接器

自訂 FTP 連接器提供更先進的檔案傳輸功能，支援結構化資料格式及 xAPI 語句交換。 此連接器專為需要對資料交換流程進行更細緻控制的組織設計。

#### 主要能力：

- 透過結構化 CSV 檔案匯入與匯出使用者資料。
- 處理學習記錄和 xAPI 語句。
- 自動處理指定 FTP 資料夾的檔案。
- 強化安全功能以傳輸敏感資料。

欲了解更多資訊，請參閱 [自訂 FTP 連接器](/help/migrated/integration-admin/feature-summary/custom-ftp-connector.md)。

### 盒式連接器

Box 連接器利用 Box 的雲端儲存平台，促進外部系統與 Adobe Learning Manager 之間的無縫資料同步。 此連接器對於已使用 Box 進行檔案管理的組織特別有用。

#### 主要能力：

- 雲端檔案儲存與同步。
- 自動化 CSV 資料處理。
- 與現有 Box 工作流程整合。
- 來自指定資料夾的即時資料更新。

更多資訊請參見 [盒子連接器](/help/migrated/integration-admin/feature-summary/box-connector.md)。

## 虛擬教室與會議連結器

這些連接器將 Adobe Learning Manager 與熱門的視訊會議及虛擬會議平台整合，實現無縫的即時培訓課程。

### Microsoft Teams 連接器

Microsoft Teams 連接器將 Adobe Learning Manager 轉化為完整的虛擬教室解決方案，直接整合 Teams 的會議功能。 此連接器對於使用 Microsoft 365 生態系統的組織來說至關重要。

#### 主要能力：

- 直接從 Adobe Learning Manager 安排線上教室課程。
- 自動建立與管理 Teams 會議。
- 無需獨立會議連結，學習者可無縫接入。

欲了解更多資訊，請參閱 [MS Teams 連接器](/help/migrated/integration-admin/feature-summary/install-microsoft-teams-connector.md)。

### Zoom 連接器

Zoom 連接器讓組織能直接在其 Adobe Learning Manager 環境中運用 Zoom 強大的視訊會議功能，為講師與學習者提供無縫的體驗。

#### 主要能力：

- Adobe Learning Manager 直接安排 Zoom 會議。
- 自動化會議連結產生與分發。
- 即時出勤監控。
- 錄音管理與播放整合。
- 互動會議的分組討論室支援。

更多資訊請參閱 [Zoom 連接器](/help/migrated/integration-admin/feature-summary/zoom-connector.md)。

### Adobe Connect 連接器

Adobe Connect 連接器與 Adobe 自家虛擬教室平台深度整合，提供互動式線上學習體驗的先進功能。

#### 主要能力：

- 進階互動功能（投票、測驗、分組討論）。
- 高品質的螢幕共享與簡報工具。
- 完整的錄音與播放。
- 行動優化的虛擬教室體驗。

欲了解更多資訊，請參閱 [Adobe Connect 連接器](/help/migrated/integration-admin/feature-summary/adobe-connect-connector.md)。

## 企業系統整合連接器

這些連接器使 Adobe Learning Manager 能與核心業務系統整合，促進自動化使用者管理與組織資料同步。

### Workday 連接器

Workday 連接器能無縫銜接您的人力資源系統與學習管理平台，確保員工紀錄、組織架構與角色分配在兩系統間保持同步。

#### 主要能力：

- Workday 的自動使用者配置。
- 即時員工資料同步。
- 組織階層映射。
- 基於角色的學習作業自動化。

欲了解更多資訊，請參閱 [Workday 連接器](/help/migrated/integration-admin/feature-summary/workday-connector.md)。

### Salesforce 連接器

Salesforce 連接器使組織能將客戶關係管理系統與學習計畫整合，創造銷售培訓、客戶教育及績效追蹤的機會。

#### 主要能力：

- 自動從 Salesforce 匯入使用者。
- 自訂資料欄位映射。
- 學習如何匯出紀錄到 Salesforce。
- 銷售績效與培訓完成度的相關性。
- 客戶教育計畫管理。

欲了解更多資訊，請參閱 [Salesforce 連接器](/help/migrated/integration-admin/feature-summary/salesforce-connector.md)。

### ADFS（Active Directory Federation Services）連接器

ADFS 連接器使組織能實作企業級認證與授權，使用者能利用現有的 Active Directory 憑證存取 Adobe Learning Manager。

#### 主要能力：

- 單一登入（SSO）實作
- 企業安全合規
- 無縫使用者認證
- 自動使用者匯入
- 排程能力
- 過濾能力

欲了解更多資訊，請參閱 [ADFS 連接器](/help/migrated/integration-admin/feature-summary/adfs-connector.md)。

## 內容與學習平台連接器

這些連接器透過整合外部內容庫與專門學習平台，擴展您的學習目錄。

### LinkedIn Learning 連接器

LinkedIn Learning 連接器提供 LinkedIn 豐富的專業發展課程庫，讓組織能以業界領先的外部內容補充內部訓練。

#### 主要能力：

- 可存取 LinkedIn Learning 的完整課程目錄。
- 自動化課程發現與匯入。
- Adobe Learning Manager 內建學習者進度追蹤功能。

欲了解更多資訊，請參閱 [LinkedIn 連結](/help/migrated/integration-admin/feature-summary/linkedin-learning-connector.md)工具。

### 哈佛 ManageMentor 連接器

哈佛管理導師連接器將世界級的領導與管理培訓內容直接帶入您的 Adobe Learning Manager 環境，讓您能使用哈佛商學院著名的教育資源。

#### 主要能力：

- 哈佛商學院高級內容存取權。
- 管理與領導力發展模組。
- 無縫匯入與組織內容。

欲了解更多資訊，請參閱 [哈佛管理導師連接器](/help/migrated/integration-admin/feature-summary/harvard-managementor-connector.md)。

### getAbstract Connector

getAbstract 連接器提供簡明的商業書籍摘要與專業見解，使組織能透過易於理解的內容格式持續學習。

#### 主要能力：

- 提供商業書籍摘要與見解。
- 使用數據追蹤與報告。
- 自動完成紀錄建立。

欲了解更多資訊，請參閱 [getAbstract connector](/help/migrated/integration-admin/feature-summary/getabstract-connector.md)。

## 商業智慧與分析連接器

這些連接器透過整合學習資料與外部分析平台，實現進階報告、資料視覺化及商業智慧功能。

### Power BI 連接器

Power BI 連接器能將你的學習數據轉化為可行的商業洞察，透過自動同步學習指標與 Microsoft 強大的商業智慧平台。

#### 主要能力：

- 即時學習資料同步。
- 自訂儀表板建立與管理。
- 進階資料視覺化與報告。
- 學習者成績單與技能報告整合。

更多資訊請參見 [Power BI 連接器](/help/migrated/integration-admin/feature-summary/power-bi-connector.md)。

### 訓練資料存取連接器

訓練資料存取連接器讓組織能透過提供 API 存取訓練資料與課程資訊，建立自訂的學習介面與無頭學習體驗。

**主要能力：**

- 公開的 API 存取課程與學習路徑資料。
- 支援自訂使用者介面開發。
- 無頭學習體驗創建。
- 進階的搜尋與篩選功能。

欲了解更多資訊，請參閱 [訓練資料存取連接器](/help/migrated/integration-admin/feature-summary/training-data-access-connector.md)。

## 電子商務與行銷連結器

這些連接器使學習內容能夠變現，並與行銷自動化平台整合。

### Adobe Commerce 連接器

Adobe Commerce 連接器將 Adobe Learning Manager 轉型為一個完整的學習商務平台，使組織能透過完整整合的電子商務體驗銷售課程、證照與培訓計畫。

**主要能力：**

- 無縫整合電子商務平台。
- 課程目錄與定價管理。
- 自動化付款處理與登記。

欲了解更多資訊，請參閱 [Adobe Commerce 連接器](/help/migrated/integration-admin/feature-summary/adobe-commerce-connector.md)。

### Marketo Engage 連接器

Marketo Engage 連接器在學習活動與行銷活動之間創造強大的協同效應，使組織能利用教育互動進行潛在客戶培育與客戶開發。

#### 主要能力：

- 自動化潛在客戶建立與更新。
- 學習活動追蹤以提供行銷洞察。
- 課程註冊與完成事件觸發。

欲了解更多資訊，請參閱 [Marketo Engage 連接器](/help/migrated/integration-admin/feature-summary/marketo-engage-connector.md)。
