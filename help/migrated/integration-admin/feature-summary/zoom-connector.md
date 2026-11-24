---
description: 了解如何將 Zoom 連接器與 Adobe Learning Manager 整合
jcr-language: en_us
title: Zoom 連接器
contentowner: mmanuel
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: 3628dd3701949da127b138e0e1ffc2db8e84eab1
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 0%
---

# Adobe Learning Manager 中的 Zoom 連接器

## 簡介

Adobe Learning Manager 中的 Zoom 連接器讓組織能夠提供線上線上課程、管理學習者報名，並追蹤出席與完成情況。 它也支援單一帳戶內多個 Zoom 連線，讓整合管理員能依據角色或使用者群組管理存取權限，作者則可選擇課程課程的可用連線。 課程結束後，出席與績效資料會同步回 Adobe Learning Manager，以便報告與追蹤。

## 設定 Zoom 連接器

設定 Zoom 連接器的方法如下：

1. 以整合管理員身份登入 Adobe Learning Manager。
2. 將滑鼠移至「Zoom **」**&#x200B;圖塊上。

   ![](assets/zoom-connector1.png)
   _在 Adobe Learning Manager 中設定 Zoom 連接器_

3. 選擇 **「連線**」。 Zoom 連接器設定頁面開啟。
4. 在相應欄位輸入下列帳戶詳細資訊。 您可以從您的 Zoom 帳戶管理員取得以下憑證：

   * 連線名稱
   * Zoom 帳戶 ID
   * 用戶端 ID
   * 用戶端密鑰
   * 超級管理員電子郵件地址
   * 可使用此連接器的角色或群組（選用）

   ![](assets/zoom-connector2.png)
   _輸入設定細節以設定 Zoom 連接器_

5. 選擇「 **連線** 」以建立整合。

>[!NOTE]
>
>啟用連接器時， **學習者必須為 Zoom 與 Adobe Learning Manager 帳戶使用相同的電子郵件地址** ，以確保使用者資料正確同步。

## 新增多個 Zoom 連線

您可以將多個 Zoom 連線新增至 Adobe Learning Manager，每個連線都連結到不同的 Zoom 帳戶。 例如，您可以為不同的合作夥伴或團隊建立獨立的連線，並指定哪些角色或使用者群組可以使用每個連線。

您可以新增的連線數量取決於您的 Adobe Learning Manager 帳戶等級：

| **帳戶層級** | **最大 Zoom 連線數** |
|---|---|
| Prime | 6 |
| 終極 | 50 |

## 建立 Zoom 課程

連線建立後：

1. 以作者&#x200B;**身份登入**&#x200B;並建立新的虛擬教室課程。
2. 選取 **「縮放** 」作為會議系統，然後從清單中選擇您想使用的 Zoom 連線。
   >[!NOTE]
   >
   >清單僅顯示您角色或使用者群組可用的連線，且每個工作階段一次只使用一個連線。
3. 可透過管理員、經理或自我報名方式將學習者指派至課程。
4. 報名後，學習者會收到一封包含課程詳情的電子郵件。
5. 學習者可登入其 Adobe Learning Manager 帳戶，進入課程並加入 Zoom 課程。

## 作者可使用的縮放連線

當您建立或編輯課程課程時，您可以從適合您角色或使用者群組可用的 Zoom 連線中選擇。 整合管理員定義哪些角色或使用者群組可以存取每個 Zoom 連線。

例如，假設一位整合管理員設定兩個 Zoom 連線，分別是 **合作夥伴 A Zoom** 與 **合作夥伴 B Zoom**，並將每個連線指派給不同的使用者群組：

* 如果您同時屬於合作夥伴 A 與合作夥伴 B 群組，您可以選擇任一連線。
* 如果您僅屬於合作夥伴 A 群組，您可以選擇 **合作夥伴 A 縮放**。
* 如果你不屬於任一群組，這些連結將無法被選取。

>[!NOTE]
>
>您只能為一場會議使用單一 Zoom 連線。 如果您有多個連線可用，請選擇您想用於本次工作階段的連線。

## 管理 Zoom 連線

**「管理連線」頁面會**&#x200B;顯示為您的帳戶設定的 Zoom 連線。**「顯示至**」欄位表示可使用每個連線的角色或使用者群組。在此頁面中，您可以編輯、啟用或停用，以及刪除現有的 Zoom 連線。

![Zoom 連線設定頁面（啟用連線、認證與角色或群組設定](assets/zoom-connection-configure-page.png "）Zoom 連線設定頁面（設定啟用連線、認證及角色或群組設定）")

### 編輯 Zoom 連線

編輯現有的 Zoom 連線：

1. 在「管理連線&#x200B;**」頁面選擇您想要編輯的連線**。
1. 在「設定」標籤中，更新下列任一項：

   1. 若要更新 Zoom 帳戶憑證，請在「憑證」**旁**&#x200B;選擇&#x200B;**「編輯**」，並更新所需資料。
   1. 若要變更誰可以使用此連線，請更新 **可使用此連接器的角色或群組** 。

1. 選擇「 **儲存**」。

### 啟用或停用 Zoom 連線

預設啟用新的 Zoom 連線。 您可以停用連線，以防止作者在不刪除該連線的情況下使用該連線。

停用連線的方法如下：

1. 在 **「管理連線** 」頁面，選取您想要停用的連線。
1. 切換啟用 **連線**。
1. 選擇「 **儲存**」。

   已停用的連線不再對相關角色或群組中的使用者可用。

若要再次啟用連線，請選取&#x200B;**「啟用連線」，然後選擇**「**儲存**」。

### 刪除 Zoom 連線

刪除 Zoom 連線的方法如下：

1. 在 **「管理連線** 」頁面，導覽至您想要刪除的連線。
1. 選取 **連線旁的「刪除」** 圖示。
1. 選擇 **「刪除**」。

## 賽道觀眾與完賽

虛擬會話結束後：

* Adobe Learning Manager 會自動從 Zoom 收到完成狀態。
* 管理員可在 Adobe Learning Manager 中查看出席與評分報告，以追蹤學習者的參與與表現。

## 建立 Zoom 伺服器對伺服器的 OAuth 應用程式

若要在 Adobe Learning Manager 中使用 Zoom 連接器，您必須建立一個 Zoom 伺服器對伺服器的 OAuth 應用程式，並設定所需的範圍。

### 所需的 OAuth 範圍

在 Zoom 中建立應用程式時，請確保已選取以下範圍：

| 你想要的 | 搜尋此關鍵字 | 然後選擇 |
|---|---|---|
| 檢視所有使用者會議 | 會議 | `meeting:read:meeting:admin, meeting:read:list_meetings:admin` |
| 檢視/管理所有使用者會議 | 會議 | `meeting:update:meeting:admin, meeting:delete:meeting:admin, meeting:write:meeting:admin` |
| 檢視報告資料 | 報告 | `report:read:meeting:admin, report:read:user:admin` （選擇與你端點相符的那個。） |
| 檢視所有使用者資訊 | 使用者 | `user:read:user:admin, user:read:list_users:admin` |
| 管理使用者 | 使用者 | `user:update:user:admin, user:write:user:admin` |
| 新增會議註冊人 | 登記人 | `meeting:write:registrant:admin` |
| 列出所有會議報名者 | 登記人 | `meeting:read:list_registrants:admin` |
| 子帳戶會議 | 會議 + 尋找 :master | `meeting:write:meeting:master` |
| 會議參與者報告 | 參與者 | `report:read:list_meeting_participants:admin` |

