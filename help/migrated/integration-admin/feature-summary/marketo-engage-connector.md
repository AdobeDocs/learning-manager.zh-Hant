---
description: 學習如何將 Marketo Engage 連接器與 Adobe Learning Manager 整合
jcr-language: en_us
title: Marketo Engage 連接器
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# Adobe Learning Manager 中的 Marketo Engage 連接器

## 簡介

Marketo Engage 連接器讓 Adobe Learning Manager 能無縫整合行銷自動化平台 Marketo Engage。 此整合協助行銷人員追蹤並依據 Adobe Learning Manager 的學習者行為數據與 Marketo 資料庫同步。

Marketo Engage 連接器能在兩個系統間無縫同步資料，並讓行銷人員能利用學習活動數據打造目標行銷活動。

Marketo Engage 連接器允許您：

- 當使用者加入 Adobe Learning Manager 時，自動在 Marketo Engage 資料庫中新增或更新潛在客戶。
- 將使用者學習行為（如課程註冊、完成、技能指派及技能完成）同步為 Marketo 中的自訂物件。
- 利用這些數據在 Marketo 中建立動態廣告活動，並善用智慧清單等&#x200B;**功能**。

此整合幫助行銷人員根據 Adobe Learning Manager 中的學習歷程來精準鎖定目標受眾。

## 主要特色

- 基於 Adobe Learning Manager 使用者的自動化潛在客戶建立與更新。
- 將學習活動（報名、完成、技能成就）匯出為自訂物件到 Marketo。
- 按需排程或觸發出口。
- 支援統一報告，包括：
   - 使用者報告
   - 學習成績單
   - 使用者技能報告

## 先決條件

整合前，請確保您的 Marketo 帳號支援透過 API 建立結構。

你需要以下資料來建立連結：

- **連接名稱**
- **客戶識別碼**
- **客戶秘密**
- **Marketo Engage 網域**

>[!NOTE]
>
>你可以從 Marketo Engage 應用程式的 **LaunchPoint** 取得客戶端 ID 和客戶端秘密，網域則從 **Web Services** 區塊取得。

## 設定連接器

要設定 Marketo Engage 連接器：

1. 以整合管理員身份登入 Adobe Learning Manager。
2. 將滑鼠移到 **Marketo Engage** 圖塊上，選擇 **「連接**」。

   ![](assets/marketo-engage-connector1.png)
   _選擇 Connect 以設定 Marketo Engage 連接器_

3. 請輸入所需的證件

   - 連接名稱
   - 客戶識別碼
   - 客戶秘密
   - Marketo Engage 網域

   ![](assets/marketo-engage-connector2.png)
   _輸入 Marketo Engage 連接器所需的詳細資訊_

4. 選擇 **連接** 以建立連線。

## 事件與戰役觸發點

您可以根據以下事件觸發資料匯出至 Marketo Engage：

- Adobe Learning Manager 新增了一個新使用者。
- 使用者正在註冊一門課程。
- 使用者完成課程。
- 使用者註冊了一項技能。
- 使用者完成一項技能。

這些活動可以按需&#x200B;****&#x200B;或預定&#x200B;**進行**&#x200B;輸出。

## 柱映射

Marketo 使用兩個資料庫：

- **潛在客戶資料庫** – 用於使用者紀錄（潛在客戶）
- **自訂物件資料庫 – 用於自訂** 活動與事件紀錄

要映射 Adobe Learning Manager 與 Marketo 之間的欄位：

1. **Adobe Learning Manager 的使用者報告**&#x200B;欄位會顯示在同一欄。
2. 對應 **的Marketo欄位** 列於相鄰欄位。
3. 將 Learning Manager 對應到的相關欄位，用來建立並更新潛在客戶。
4. 完成地圖後，所有匯出的使用者都會以 Marketo 潛在客戶資料庫的潛在客戶身份出現。

Marketo 自訂物件&#x200B;**區塊中**&#x200B;匯出的報表前綴為「cp_」。

## 支援的出口活動

您可以將以下與使用者相關的事件匯出到您的 Marketo Engage 實例：

- 新增使用者
- 用戶元資料已更新
- 用戶活動更新
- 培訓招生
- 自我報名
- 技能完成

這些輸出有助於推動互動並利用學習活動數據個人化推廣活動。
