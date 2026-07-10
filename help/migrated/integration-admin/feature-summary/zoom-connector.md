---
description: 學習如何將 Zoom 連接器與 Adobe Learning Manager 整合
jcr-language: en_us
title: Zoom 連接器
contentowner: mmanuel
source-git-commit: 481eed24a5ac72329228c8d27b625d443bd637ce
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---


# Adobe Learning Manager 中的 Zoom 連接器

## 簡介

Adobe Learning Manager 中的 Zoom 連接器可無縫整合 Zoom 進行線上虛擬教室課程。 透過此整合，教師可直接從學習管理員主持 Zoom 會議，註冊學員，並追蹤出席與完成數據。 學習者會收到自動邀請，並可透過 Adobe Learning Manager 帳號加入課程。 課程結束後，出席與績效資料會同步回 Adobe Learning Manager，以便報告與追蹤。

## 設定 Zoom 連接器

要設定 Zoom 連接器：

1. 以整合管理員身份登入 Adobe Learning Manager。
2. 將滑鼠移到Zoom **圖塊上**。

   ![](assets/zoom-connector1.png)
   _在 Adobe Learning Manager 中設定 Zoom 連接器_

3. 選擇 **「連接**」。 Zoom 連接器設定頁面打開了。
4. 在相關欄位輸入以下帳戶詳情。 你可以從你的 Zoom 帳號管理員那裡取得這些憑證：

   * 連接名稱
   * Zoom 帳號 ID
   * 客戶識別碼
   * 客戶秘密
   * 超級管理員電子郵件地址

   ![](assets/zoom-connector2.png)
   _輸入設定細節以設定 Zoom 連接器_

5. 選擇 **連接** 以建立整合。

>[!NOTE]
>
>啟用連接器時， **學習者必須同時使用相同的電子郵件地址** 來管理 Zoom 與 Adobe Learning Manager 帳號，以確保使用者資料正確同步。

## 建立 Zoom 課程

一旦建立連結：

1. 以作者&#x200B;**身份登入**&#x200B;並建立新的虛擬教室課程。
2. 在課程建立時選擇 **Zoom** 作為會議系統。
3. 可透過管理員、經理或自我報名方式分配學習者參加課程。
4. 註冊後，學習者會收到一封包含課程詳情的電子郵件。
5. 學習者可登入 Adobe Learning Manager 帳號，存取課程並加入 Zoom 課程。

## 賽道觀眾人數與完賽

虛擬會議結束後：

* Adobe Learning Manager 會自動從 Zoom 收到完成狀態。
* 管理員可在 Adobe Learning Manager 中查看出席與評分報告，以追蹤學習者的參與與表現。

## 建立 Zoom 伺服器間的 OAuth 應用程式

要使用 Zoom 連接器搭配 Adobe Learning Manager，您必須建立 Zoom 伺服器對伺服器的 OAuth 應用程式並設定所需的範圍。

### 必備OAuth示波器

在 Zoom 中建立應用程式時，請確保選取以下範圍：

```
| Scope Description | Zoom Scope |
|---|---|
| View all user meetings | meeting:read:admin |
| View and manage all user meetings | meeting:write:admin |
| View report data | report:read:admin |
| View all user information | user:read:admin |
| Manage users | user:write:admin |
| Add a meeting registrant | meeting:write:registrant:admin |
| List all meeting registrants | meeting:read:list_registrants:admin |
| Manage sub-account meetings | meeting:write:meeting:master |
| View meeting participants report | report:read:list_meeting_participants:admin |
```
