---
description: 學習如何將 ADFS 連接器與 Adobe Learning Manager 整合
jcr-language: en_us
title: ADFS 連接器
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---


# Adobe Learning Manager 中的 ADFS 連接器

## 簡介

Adobe Learning Manager 中的 ADFS 連接器允許您透過 Active Directory 聯邦服務（ADFS）與 Microsoft Azure Active Directory 整合。 此整合使使用者資料能自動同步 Azure AD 至 Learning Manager。 結合屬性映射、使用者過濾及排程匯入等功能，該連接器有助於簡化使用者管理，確保學習者資料保持準確且最新。 它對於依賴 ADFS 進行集中身份與存取管理的組織尤其有用。

## 先決條件

在 Adobe Learning Manager 設定 ADFS 連接器之前，請先在 Azure 入口網站完成以下步驟：

- 註冊應用程式
- 產生一個客戶端秘密
- 設定 API 權限

### Register an application in Azure

要在 Azure 註冊應用程式：

1. [登入 Azure 入口網站](https://portal.azure.com/)。
2. 進入 **Azure Active Directory**。
3. 選擇 **新增** ，然後選擇 **應用程式註冊**。
4. 輸入您的申請名稱並選擇 **註冊**。

### 產生一個客戶端秘密

要建立客戶端秘密：

1. 在新註冊的應用程式中，請前往&#x200B;**「憑證與秘密」。**
2. 選擇 **新客戶端秘密**。
3. 新增描述，並將有效期限設為 **24個月**。
4. 將客戶端的秘密值&#x200B;**儲存**&#x200B;在安全的地方。

### 設定 API 權限

要新增 API 權限：

1. 選擇 **API 權限** ，然後選擇 **新增權限**。
2. 選擇 **Microsoft Graph** ，然後選擇 **應用程式權限**。
3. 請搜尋並選擇以下權限：

   - **Directory.Read.All** – Read Directory data
   - **User.Read.All** – 閱讀所有使用者的完整個人檔案
4. 選擇 **新增權限**。
5. 授權&#x200B;****&#x200B;管理員同意權限。

## 在 Learning Manager 中設定 ADFS 連接器

你可以在 Adobe Learning Manager 中設定 ADFS 連接器，匯入 ADFS 的使用者資料、匯出使用者技能回 ADFS，並排程自動同步以保持兩系統的即時更新。

要設定 ADFS 連接器：

1. 以整合管理員身份登入 Adobe Learning Manager。
2. 將滑鼠移到ADFS **連接器圖**&#x200B;塊上。
3. 選擇 **「連接**」。

   ![](assets/adfs-connector1.png)
   _選擇「連接」以設定 ADFS 連接器_

### 進入連接細節

在 ADFS 設定頁面：

1. 請輸入以下細節：

   - 連接名稱
   - 客戶識別碼
   - 客戶秘密

   ![](assets/adfs-connector2.png)
   _輸入設定細節以連接 ADFS_

2. 選擇 **「連接**」。
3. Adobe Learning Manager 會自動從你的 Azure 入口網站取得並填充 **租戶 ID** 和 **主要網域** 。

## 從 ADFS 匯入使用者

### 地圖屬性

- 整合管理員可以將 ADFS 屬性映射到對應的 Adobe Learning Manager 中可分組屬性。
- 此映射為一次性設定，並用於所有後續使用者匯入。
- 如果需要，你可以隨時修改屬性映射。

### 自動使用者匯入

- Adobe Learning Manager 會自動在排程間隔中從 ADFS 擷取使用者資料。
- 這有助於讓使用者紀錄在不同系統間保持同步。

### 篩選使用者

- 管理員可以套用篩選器來限制匯入的使用者。
- 例如，只匯入特定經理或部門下的使用者。
