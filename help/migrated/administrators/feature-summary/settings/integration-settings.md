---
description: 了解更多整合設定如何將 Adobe Learning Manager 與第三方解決方案連結起來
jcr-language: en_us
title: Adobe Learning Manager 中的整合設定
source-git-commit: 03123dcd8d9066cdfcb0fe97e61acb3df625a23e
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 0%

---


# Adobe Learning Manager 中的整合設定

## 登入方式

Adobe Learning Manager 提供多種登入方式，確保內部與外部使用者都能安全且靈活地存取。 管理員可根據組織需求配置這些登入方式。

可用的登入方式包括：

* Adobe Learning Manager ID
* Adobe ID
* 單一登入

### 內部使用者

內部使用者區塊允許你為內部使用者設定登入選項。 內部使用者可透過 Adobe ID 或單一登入（SSO）存取帳號。

**Adobe ID：**

* 內部使用者可以使用他們的 Adobe ID 憑證登入。
* 適合已使用 Adobe 服務的組織。

**單一登入（SSO）：**

* 允許內部使用者使用 組織的身份提供者（IdP）進行單點單點（SSO）。
* 支援基於 SAML 2.0 的認證，實現無縫登入體驗。

若要允許內部使用者使用 SSO 登入，請選擇啟用多重單點登入（SSO）並開始設定 SSO。

**[!UICONTROL SSO Active Field]** Adobe Learning Manager 用於將單一登入（SSO）設定映射到特定的使用者屬性或群組。你可以設定此欄位，根據組織、地點或其他條件，為內部使用者啟用多個 SSO 設定。

### 外部使用者

Adobe Learning Manager 中的外部使用者區塊允許您管理需要有限存取權限的外部學習者，例如合作夥伴或代理商。 本區提供建立註冊設定檔、管理外部使用者群組及設定針對外部學習者的專屬設定的工具。

外部使用者可使用以下方式登入：

* Adobe ID：外部使用者可以使用其 Adobe ID 憑證登入。
* 單一登入（SSO）：外部使用者可透過 SSO 登入，若管理員設定。
* Adobe Learning Manager ID：外部使用者可建立 Learning Manager 使用者名稱與密碼以存取平台。

**重點：**

* 你可以為外部使用者啟用一種或多種登入方式。
* 若選擇 Adobe Learning Manager ID 時，外部使用者必須自行建立憑證。
* 可根據組織需求為外部使用者設定單點單點（SSO）。

### Adobe Learning Manager 中的 SSO 設定

Adobe Learning Manager 支援單一登入（SSO），讓使用者只需一次驗證即可存取多個應用程式。 管理員可透過基於 SAML 2.0 的提供者，為內部及外部使用者設定 SSO。

更多資訊請參閱 [Adobe Learning Manager](/help/migrated/administrators/feature-summary/multiple-sso-logins.md) 中的單點登入（SSO logins）。

>[!NOTE]
>
>* 一個帳號最多可新增 20 個 SSO 設定。
>* 如需協助使用 SAML 2.0 的 SSO 服務，請聯絡 Adobe 客服。

## 資料來源

資料來源允許你或整合管理員整合外部系統，以匯入與同步使用者及學習資料。 此功能確保與人力資源管理系統（HRMS）、Salesforce、FTP 等系統無縫管理與同步。

**資料來源類型範例**

* **FTP 連接器**：基於 FTP 的資料來源允許組織透過安全的檔案傳輸協議，直接將使用者資料檔案上傳至 Adobe Learning Manager。 這些連線對於批次匯入使用者資訊、課程註冊及其他大量資料操作特別有用。
* **第三方整合**：Adobe Learning Manager 支援透過預先建置的連接器與各種企業系統整合。 這些整合可能包括人力資源管理系統、客戶關係管理平台及其他學習管理系統。
Salesforce 整合**：Salesforce 連接器可直接同步使用者資料、課程資訊及學習紀錄，並於 Adobe Learning Manager 之間同步。

更多資訊請參閱 [Adobe Learning Manager](/help/migrated/integration-admin/feature-summary/connectors.md) 中的連接器。

## 同儕帳號

Adobe Learning Manager 中的同儕帳號允許你分享已購買的座位，並查看相關帳號間的報告。 此功能對於需要在不同帳戶間協作或共享資源的組織非常有用。

更多資訊請參閱 [Adobe Learning Manager 中的同儕帳號](/help/migrated/administrators/feature-summary/peer-account.md) 。





