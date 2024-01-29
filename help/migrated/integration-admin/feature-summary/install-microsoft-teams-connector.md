---
description: 在Adobe Learning Manager中安裝Microsoft Teams聯結器
jcr-language: en_us
title: 在Adobe Learning Manager中安裝Microsoft Teams聯結器
contentowner: saghosh
source-git-commit: ab6737e8b43222a6538921b0628a504a5f15859d
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 0%

---



# 在Adobe Learning Manager中安裝Microsoft Teams聯結器

## 概觀

Microsoft® Teams®是永續性的聊天式共同作業平台，可完全支援檔案共用、線上會議和其他商務通訊功能。

Adobe Learning Manager使用虛擬教室聯結器，可用來將Microsoft Teams會議與Learning Manager整合。

Microsoft Teams聯結器會連線Learning Manager和Microsoft Teams系統，以啟用自動虛擬會議同步。 下列清單說明Microsoft Teams聯結器功能：

**使用Microsoft Teams設定虛擬工作階段**

此聯結器有助於將您的AdobeLearning Manager帳戶與Microsoft Teams帳戶整合。 整合後，聯結器可讓Learning Manager中的作者將Microsoft Teams作為在Learning Manager中建立的虛擬教室模組的技術服務提供者。

**允許Microsoft Teams在進入虛擬教室時驗證學習者**

此聯結器可協助您在建立會議時從Learning Manager設定Microsoft Teams會議召集人。 「會議召集人」可以管理大廳來限制或允許進入會議，以及控制Microsoft Teams提供的其他會議選項。

**使用自動使用者完成同步**

自動使用者完成同步程式可讓Learning Manager管理員自動擷取完成記錄，並記錄Microsoft Teams會議的URL。

## Microsoft Teams中的角色

如果您要組織具有多個參與者的會議，您可以指派角色給每個參與者，讓參與者知道他/她在會議中可以做什麼。

有兩個角色可供選擇： **簡報者** 和 **出席者**.

如需詳細資訊，請參閱  [Teams會議中的角色 — Microsoft](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

## 設定Microsoft Teams聯結器

>[!NOTE]
>
>已標籤的專案 &lt;developer optional=&quot;&quot;> 以下是選用專案，主要用於使用Microsoft設定試用/開發人員租使用者，以防使用者沒有生產租使用者。 這些是選擇性的，因為它們大多已經由您的團隊管理員執行。

## 建立開發人員E5 Microsoft帳戶 &lt;developer optional=&quot;&quot;>

如果您有Office 365 E3或Office 365 E5，則可以存取Microsoft Teams聯結器。 建議的選項是Office 365 E5。

* 造訪 [Microsoft計畫頁面](https://www.microsoft.com/en-in/microsoft-365/enterprise/compare-office-365-plans?&amp;ef_id=CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE:G:s&amp;OCID=AID2100137_SEM_CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE:G:s&amp;lnkd=Google_O365SMB_Brand&amp;gclid=CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE) . 在網頁上，您可以購買E3或E5帳戶，或按一下「免費試用」。

* 提供必要資訊並建立帳戶。

>[!NOTE]
>
>帳戶必須使用格式 `<username>@<company name>.onmicrosoft.com`.

## 建立Microsoft Teams聯結器的應用程式

1. 造訪  [Microsoft Azure®入口網站](https://portal.azure.com/).
1. 使用您在上一節建立的Microsoft E5帳戶登入。
1. 搜尋 **Azure Active Directory**.
1. 按一下 **[!UICONTROL App Registrations]**.
1. 按一下 **[!UICONTROL New Registration]**，輸入下列詳細資料並註冊應用程式：

   1. **名稱**  — 您選擇的任何名稱。
   1. **支援的帳戶型別**  — 任何組織目錄（任何Azure Active Directory — 多租使用者）中的帳戶。
   1. **重新導向URI （選擇性）**  — 表示回覆URL的選用欄位。

1. 在 **Essentials** 欄中，請注意下列ID，這些ID將在整合期間進一步使用：

   1. **應用程式（使用者端） ID**
   1. **目錄（租使用者） ID**

1. 搜尋使用者端認證，然後按一下 **[!UICONTROL Add a certificate or secret]**.
1. 按一下 **[!UICONTROL New Client secret]** 並新增下列詳細資料：

   1. **說明**  — 輸入任何名稱。
   1. **過期**  — 設為任何值(建議值為24個月。 確保前一個使用者端憑證過期後，才會產生新的使用者端憑證)。

請注意使用者端密碼，此密碼將在整合期間進一步使用。

## 取得Microsoft Teams聯結器的存取許可權

1. 造訪  [Microsoft Azure入口網站](https://portal.azure.com/).
1. 使用您先前建立的Microsoft E5登入。
1. 搜尋 **Azure Active Directory**.
1. 按一下 **[!UICONTROL App Registrations]**.
1. 按一下您在上一節中建立的應用程式。
1. 按一下 **[!UICONTROL API permissions]**.
1. 按一下 **[!UICONTROL Add a permission]**.
1. 選取 **[!UICONTROL Microsoft Graph]** > **[!UICONTROL Application permissions]** 並新增下列許可權：

   1. Chat.Read.All
   1. Directory.Read.All
   1. OnlineMeetingArtifact.Read.All
   1. OnlineMeetings.Read.All
   1. OnlineMeetings.ReadWrite.All
   1. User.Read.All

1. 按一下 **[!UICONTROL Grant admin access for Adobe]**.
1. 按一下 **[!UICONTROL App roles]** > **[!UICONTROL Create app role]**.
1. 輸入下列值：

   1. **顯示名稱** - API/許可權名稱的名稱（例如Calendars.ReadWrite）。

   1. **允許的成員型別**  — 同時指定使用者和應用程式（使用者/群組+應用程式）。

   1. **值** - API/許可權名稱的名稱（例如Calendars.ReadWrite）。

   1. **說明** - API/許可權名稱的名稱（例如Calendars.ReadWrite）。

   1. **您要啟用此應用程式角色嗎？**  — 選取此核取方塊。

1. 針對新增的所有9個API/許可權，重複上述步驟。

## 使用PowerShell指令碼設定存取原則

若要透過執行PowerShell指令碼來設定Microsoft Teams聯結器的應用程式存取原則，請遵循以下所述的程式  [檔案](https://docs.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy).

這可讓聯結器存取Microsoft Teams線上會議。

>[!NOTE]
>
>在上述檔案中，也請執行可選步驟5，以確保任何作用中使用者都可以從Learning Manager作者應用程式中獲得召集人的角色。 如果未執行此步驟，使用者將沒有擔任召集人的必要存取許可權，會議建立將失敗(Microsoft API會將召集人視為Teams會議的建立者)。

## 在Learning Manager中設定Microsoft Teams聯結器

1. 以整合管理員身分登入Learning Manager 。

1. 在「聯結器」頁面中，選取「Microsoft Teams」聯結器，然後按一下 **[!UICONTROL Connect]**.

1. 輸入下列值：

   1. **連線名稱**  — 提供作者建立工作階段時將看到的名稱。

   1. **Microsoft Teams租使用者ID**  — 輸入先前決定的值。

   1. **Microsoft Teams使用者端ID**  — 輸入先前決定的值。

   1. **Microsoft Teams使用者端密碼**  — 輸入先前決定的值。

   1. **Microsoft Teams管理員使用者電子郵件**  — 輸入預設的組織者電子郵件。 若未從Learning Manager作者應用程式中選取明確的召集人，則此使用者（通常為服務使用者）將是會議建立者。

## 分配授權給使用者 &lt;developer optional=&quot;&quot;>

1. 造訪 [https://admin.microsoft.com/#/homepage](https://admin.microsoft.com/#/homepage).
1. 按一下 **[!UICONTROL Users]** > **[!UICONTROL Active Users]**.
1. 按一下 **[!UICONTROL More actions for Users]** ，用於您要提供Microsoft Teams存取許可權的使用者。
1. 按一下 **[!UICONTROL Manage Product Licenses]**.
1. 啟用不透過音訊會議的Office 365 E5授權。

## 錄製工作階段

用於記錄工作階段的API是受保護的API。 若要存取API，您必須向Microsoft請求存取權。 如需詳細資訊，請參閱此  [檔案](https://docs.microsoft.com/en-us/graph/teams-protected-apis).

在檔案中，

*「若要請求存取這些受保護的API，請完成下列操作  [請求表單](https://aka.ms/teamsgraph/requestaccess). 我們每星期三審查存取請求，每星期五部署核准，除了美國的主要假日週期間。這些周內的提交將會在下個非假日周處理。 若要確認您的請求是否已核准，請在下一個適用的星期一測試您的應用程式存取權。」*

學習者錄製的URL會顯示在VC課程概觀頁面上。

完成課程30分鐘後，系統會標籤學習者的出席情況。

## 常見問題

+++誰是組織者和簡報者？

請參閱  [檔案](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019) Microsoft Teams支援的不同角色和功能。

+++

+++召集人是否同時身為Learning Manager和Microsoft Teams的註冊使用者？

是，組織者應同時屬於Learning Manager和Microsoft Teams。 此外，召集人必須屬於在整合管理應用程式中設定的相同Microsoft租使用者。

+++

+++簡報者是否同時身為Learning Manager和Microsoft Teams的註冊使用者？

是，簡報者應為Learning Manager及Microsoft Teams的一分子。 簡報者必須具有Azure Active Directory ID （可以是召集人相同租使用者的一部分，或任何其他租使用者的一部分）。 此外，會議期間，即使是匿名使用者（僅以使用者名稱登入，不屬於Active Directory的使用者），也可以由召集人/現有主持人擔任主持人。

+++

+++Microsoft Teams有會議、網路研討會和即時活動。 Teams聯結器支援哪一個？

目前，團隊聯結器僅支援Microsoft Teams中的會議。 如需詳細資訊，請參閱此  [檔案](https://docs.microsoft.com/en-us/microsoftteams/quick-start-meetings-live-events).

+++
