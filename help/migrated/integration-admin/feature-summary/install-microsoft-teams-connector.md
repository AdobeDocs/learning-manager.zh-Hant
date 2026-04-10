---
description: 在 Adobe Learning Manager 安裝 Microsoft Teams 連接器
jcr-language: en_us
title: 在 Adobe Learning Manager 安裝 Microsoft Teams 連接器
contentowner: saghosh
exl-id: 68092187-ac69-4727-a3dc-f3047a1e164d
source-git-commit: 864c3a4e60cf1bf1c049838fb2ba46ebbcb28ddf
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 0%

---

# 在 Adobe Learning Manager 安裝 Microsoft Teams 連接器

## 概觀

Microsoft Teams® 是一個持久的聊天協作平台，完全支援文件分享、線上會議及其他商業溝通功能。

Adobe Learning Manager 使用虛擬教室連接器，可將 Microsoft Teams 會議與 Learning Manager 整合。

Microsoft Teams 連接器連接 Learning Manager 與 Microsoft Teams 系統，以啟用自動虛擬會議同步。 以下列表描述 Microsoft Teams 連接器的功能：

**使用 Microsoft Teams 設定虛擬會議**

這個連接器有助於將你的 Adobe Learning Manager 帳號與 Microsoft Teams 帳號整合。 整合後，該連接器使學習管理員的作者能使用 Microsoft Teams 作為 Learning Manager 中虛擬教室模組的技術服務提供者。

**允許 Microsoft Teams 在進入虛擬教室時驗證學習者**

這個連接器在建立會議時，幫助從 Learning Manager 設定 Microsoft Teams 會議組織器。 會議組織者可以管理大廳限制或允許進入會議，並控制 Microsoft Teams 提供的其他會議選項。

**使用自動使用者完成同步**

自動化的使用者完成同步流程允許學習管理員管理員自動取得 Microsoft Teams 會議的完成紀錄及錄音網址。

## Microsoft Teams 中的角色

如果你要組織多位參與者的會議，可以為每位參與者分配角色，讓每位參與者知道自己在會議中能做什麼。

有兩種角色可選： **講者** 與 **出席者**。

欲了解更多資訊，請參閱  [Teams 會議中的角色 - Microsoft](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)。

## 設定 Microsoft Teams 連接器

>[!NOTE]
>
>以下標示的項目 &lt;Developer ptional=&quot;&quot;> 是可選的，主要是用來在 Microsoft 設定試用/開發租戶，以防使用者沒有生產租戶。 &lt;/Developer>這些是可選的，因為大多數已經由你們團隊的管理員執行過。

## 建立開發者 E5 Microsoft 帳號 &lt;Developer/Optional>

如果你有 Office 365 E3 或 Office 365 E5，可以使用 Microsoft Teams 連接器。 推薦的選項是 Office 365 E5。

* 請造訪 [Microsoft 方案頁面](https://www.microsoft.com/en-in/microsoft-365/enterprise/compare-office-365-plans?&ef_id=CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE:G:s&OCID=AID2100137_SEM_CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE:G:s&lnkd=Google_O365SMB_Brand&gclid=CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE)。 在網頁上，你可以購買 E3 或 E5 帳號，或點擊「免費試用」。
* 提供所需資訊並建立帳號。

>[!NOTE]
>
>帳號必須使用格式。`<username>@<company name>.onmicrosoft.com`

## Create application for Microsoft Teams connector

1. 造訪  [Microsoft Azure® 入口網站](https://portal.azure.com/)。
1. 請用你在前一節建立的 Microsoft E5 帳號登入。
1. 搜尋 **Azure Active Directory**。
1. 點擊 **[!UICONTROL App Registrations]**。
1. 點擊 **[!UICONTROL New Registration]**，輸入以下資訊，並註冊申請：

   1. **名字** - 你想取的任何名字。
   1. **支援的帳號類型** - 任何組織目錄中的帳號（任何 Azure Active Directory - 多租戶）。
   1. **Redirect URI（可選）** -可選欄位，指示回覆網址。

1. 在 **「Essentials」** 欄位中，請注意以下 ID，這些 ID 將在整合過程中進一步使用：

   1. **應用程式（用戶端）ID**
   1. **目錄（租戶）ID**

1. 搜尋客戶憑證並點擊 **[!UICONTROL Add a certificate or secret]**。
1. 點擊 **[!UICONTROL New Client secret]** 並補充以下細節：

   1. **說明** - 輸入任意名稱。
   1. **到期日** - 設定為任意值（建議值為24個月）。 確保在先前的客戶憑證過期後，新的客戶憑證會被產生。

請注意客戶端秘密，該秘密將在整合過程中進一步使用。

## 取得 Microsoft Teams 連接器的存取權限

1. 造訪  [Microsoft Azure 入口網站](https://portal.azure.com/)。
1. 用你之前建立的 Microsoft E5 登入。
1. 搜尋 **Azure Active Directory**。
1. 點擊 **[!UICONTROL App Registrations]**。
1. 點擊你在上一節建立的應用程式。
1. 點擊 **[!UICONTROL API permissions]**。
1. 點擊 **[!UICONTROL Add a permission]**。
1. 選擇 **[!UICONTROL Microsoft Graph]** > **[!UICONTROL Application permissions]** 並新增以下權限：

   1. 聊天。全部閱讀
   1. 目錄.閱讀.全部
   1. 線上會議文物。全部閱讀
   1. 線上會議。全部閱讀
   1. 線上會議。閱讀、書寫、全部
   1. 使用者。全部閱讀
   1. 線上會議錄音。全部閱讀

1. 點擊 **[!UICONTROL Grant admin access for Adobe]**。
1. 點擊 **[!UICONTROL App roles]** > **[!UICONTROL Create app role]**。
1. 輸入以下數值：

   1. **顯示名稱** - API 名稱/權限名稱（例如 Calendars.ReadWrite）。

   1. **允許的成員類型** - 同時指定使用者與應用程式（使用者/群組 + 應用程式）。

   1. **Value** - API 名稱/權限名稱（例如 Calendars.ReadWrite）。

   1. **說明** - API 名稱/權限名稱（例如 Calendars.ReadWrite）。

   1. **你想啟用這個應用程式角色嗎？** - 選擇這個勾選框。

1. 對新增的九個 API/權限重複前述步驟。

## 使用 PowerShell 腳本來設定存取政策

若要透過執行 PowerShell 腳本來設定 Microsoft Teams 連接器的應用程式存取政策，請依照本  [文件](https://docs.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy)中描述的程序操作。

這使連接器能夠存取 Microsoft Teams 線上會議。

>[!NOTE]
>
>在上述文件中，也執行可選步驟 5，確保任何活躍使用者都能從學習管理員作者應用程式中獲得組織者的角色。 若此步驟未執行，使用者將無法取得成為組織者的存取權限，會議建立將失敗（Microsoft API 將組織者視為 Teams 會議的創建者）。

## 在 Learning Manager 中設定 Microsoft Teams 連接器

1. 以整合管理員&#x200B;**身份登入學習管理員**。

1. 在連接器頁面，選擇 Microsoft Teams 連接器並點選 **[!UICONTROL Connect]**。

1. 輸入以下數值：

   1. **連線名稱** - 提供作者在建立會話時會看到的名稱。

   1. **Microsoft Teams 租戶 ID** - 輸入先前確定的數值。

   1. **Microsoft Teams 用戶端識別碼 - 輸入** 先前確定的值。

   1. **Microsoft Teams 用戶端秘密** - 輸入先前確定的數值。

   1. **Microsoft Teams 管理員使用者電子郵件** - 輸入預設的組織者電子郵件。 此使用者（通常是服務使用者）將成為會議創建者，以防學習管理作者應用程式未選擇明確組織者。

## 將授權分配給使用者 &lt;Developer/Optional>

1. 請造訪 [https://admin.microsoft.com/#/homepage](https://admin.microsoft.com/#/homepage)。
1. 點擊 **[!UICONTROL Users]** > **[!UICONTROL Active Users]**。
1. 點擊 **[!UICONTROL More actions for Users]** 你想提供 Microsoft Teams 存取權限的使用者。
1. 點擊 **[!UICONTROL Manage Product Licenses]**。
1. 啟用Office 365 E5授權，但不使用音訊會議。

<!--
## Record a session

The API used for recording a session is a protected API. To access the API, you must request access from Microsoft. For more information, see this  [document](https://docs.microsoft.com/en-us/graph/teams-protected-apis).

In the document,

*"To request access to these protected APIs, complete the following  [request form](https://aka.ms/teamsgraph/requestaccess). We review access requests every Wednesday and deploy approvals every Friday, except during major holiday weeks in the U.S. Submissions during those weeks will be processed the following non-holiday week. To verify whether your request has been approved, test your application access on the next applicable Monday."*

For learners, the recording URL is displayed on the VC course overview page.

After 30 minutes of completing a course, the attendance for the learner gets marked. 
-->

## 常見問題

+++誰是組織者與演講者？

請參閱  [Microfsoft 的文件](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019) ，了解 Microsoft Teams 支援的不同角色與能力。

+++

+++組織者應該同時註冊在 Learning Manager 和 Microsoft Teams 嗎？ 

是的，組織者也應該同時包含學習管理員和 Microsoft Teams。 此外，組織者必須是同一 Microsoft 租戶的一部分，該租戶在整合管理應用程式中已設定。

+++

+++講者應該同時是 Learning Manager 和 Microsoft Teams 的註冊用戶嗎？ 

是的，講者也應該同時加入學習管理器和 Microsoft Teams。 presenter 必須擁有 Azure Active Directory ID（可以是與組織者同屬一個租戶，或是任何其他租戶的一部分）。 此外，即使是匿名用戶（僅以使用者名稱登入而非Active Directory成員）也可能被主辦方或現有講者指定為會議中的講者。

+++

+++Microsoft Teams 有會議、網路研討會和現場活動。 Teams 連接器支援哪一種？ 

目前，Teams 連接器僅支援 Microsoft Teams 中的會議。 欲了解更多資訊，請參閱此  [文件](https://docs.microsoft.com/en-us/microsoftteams/quick-start-meetings-live-events)。

+++
