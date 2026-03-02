---
title: Adobe Learning Manager管理帳戶生命週期
description: 本檔案提供在Adobe Learning Manager (ALM)中安全管理頂層管理帳戶的完整指引，以符合FedRAMP合規性和最佳安全性實務。
jcr-language: en-us
source-git-commit: db3ed4dc44da75b418e923999bdf3776bf81b11f
workflow-type: tm+mt
source-wordcount: '2122'
ht-degree: 0%

---


# Adobe Learning Manager中的管理帳戶型別

## ALM角色對映

在Adobe Learning Manager中，最上層管理帳戶是管理員角色。 這是本指南使用FedRAMP術語「頂層管理帳戶」時參考的角色。 自訂管理員和整合管理員會被視為有特殊許可權（範圍）的帳戶。

下表將FedRAMP帳戶層對應至Adobe Learning Manager中使用的特定角色：

| FedRAMP辭彙 | ALM角色名稱 | 說明 |
|--------------------------------------|----------------------------|-------------|
| 頂層管理帳戶 | 管理員 | ALM中的最高許可權角色。 完整控制使用者、角色、學習內容、報表、整合和所有系統設定。 直接對應到FedRAMP頂層管理帳戶定義。 |
| 有特殊許可權的帳戶（範圍） | 自訂管理員 | 限定在特定功能（例如，報告、目錄管理）範圍內的管理員許可權之已定義子集。 沒有完整的帳戶層級控制項。 |
| 有特殊許可權的帳戶（整合） | 整合管理員 | 管理ALM和外部系統之間的整合和API型存取。 提升的許可權範圍僅限於整合管理。 |


Adobe Learning Manager使用角色型存取控制(RBAC)模型來管理管理存取權。 管理角色僅由授權管理員指派。

如需詳細資訊，請參閱Adobe Learning Manager中的[自訂角色](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/custom-role)

## 身分型別和建議的驗證

Adobe Admin Console支援管理員帳戶的三種身分型別。 身分型別的選擇有直接的安全性影響：

| 身分型別 | 說明 | 安全性建議 |
|---------------------------|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Adobe ID （個人ID） | 預設型別；由Adobe管理。 任何人都可以建立一個。 | 不建議管理員使用。 組織無法控制此帳戶型別。 |
| Enterprise ID | 由Admin Console系統管理員管理的組織擁有帳戶。 | 如果無法使用Federated ID/SSO，則可接受。 強制執行2FA。 |
| Federated ID (SSO) | 組織擁有；與SAML 2.0 SSO整合。 組織完全控制驗證。 | 建議使用。 透過組織的IdP進行驗證；支援身分提供者層級的MFA強制執行。 |

如需詳細資訊，請參閱下列內容：

* [身分型別](https://helpx.adobe.com/tw/enterprise/using/admin-console.html)
* [安全的使用者驗證和密碼](https://helpx.adobe.com/tw/enterprise/using/authentication-settings.html)

## 角色指派與存取控制

現有系統管理員透過明確的[角色指派](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/user-management/add-users-user-groups)來控制對Adobe Learning Manager中管理帳戶的存取。 安全管理存取的主要特性包括：

* 管理角色僅由授權管理員指派。
* 存取權以角色為基礎，並根據指派的許可權設定範圍。
* 組織負責限制具有合法業務需求之使用者的管理存取權。

Adobe建議客戶定期檢閱管理存取權，以確保遵循最低許可權原則。

## 強制執行多重驗證(MFA)

Adobe強烈建議管理員在整個組織內執行兩步驟驗證(2FA)。 MFA適用於Enterprise ID和Adobe ID使用者。 Federated ID使用者應該在其組織的身分提供者處強制執行MFA。

若要在Adobe Admin Console中強制執行2FA：

1. 登入Adobe Admin Console。
2. 瀏覽至「設定>隱私權與安全性>驗證設定」。
3. 啟用兩步驟驗證，並選取強制選項以防止使用者停用它。
4. 可選擇設定IP型存取限制和進階工作階段設定（工作階段存留時間上限/閒置時間上限）。

>[!IMPORTANT]
>
>Adobe建議強制執行2FA，且請勿讓使用者將其保留為選用專案。 2FA最多可能需要24小時的時間來套用。 若為Federated ID使用者，請在您的身分提供者強制執行MFA。

如需詳細資訊，請參閱[安全使用者驗證](https://helpx.adobe.com/tw/enterprise/using/authentication-settings.html)。


## 以管理員身分登入

ALM [管理員](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/get-started/getting-started-admin)使用透過Admin Console管理的組織認證，直接登入ALM平台。

### 指派管理員角色

在ALM平台中，管理員可透過建立和管理角色、指派許可權給使用者，以及根據作業職責定義許可權範圍來設定管理存取權。

若要在ALM中指派管理員角色：

1. 以現有管理員身分登入Adobe Learning Manager。
2. 導覽至「使用者>內部」。
3. 搜尋或選取目標使用者。
4. 選取動作>指派角色>建立管理員。

自訂管理角色可讓客戶委派管理任務，同時保持對帳戶層級許可權的集中控制。 自訂管理員的適用範圍可設為特定使用者群組或目錄。

如需詳細資訊，請參閱[新增使用者和使用者群組](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/user-management/add-users-user-groups)。

## 設定登入方法和SSO

ALM管理員可透過「設定>登入方法」（一項重要的安全性相關設定）控制所有使用者可用的登入方法：

* **內部使用者**：將登入模式設定為Adobe ID或單一登入(SSO)。 強烈建議透過SAML 2.0執行SSO。
* **外部使用者**：將登入模式設定為Adobe ID、SSO或Learning Manager ID。 將選取的方法與您組織的安全性原則對應。

Adobe建議對所有內部使用者使用Federated ID / SAML 2.0 SSO作為登入方法。 這可確保驗證完全由您組織的身分提供者控制，以啟用集中式MFA強制並在使用者離開時立即撤銷帳戶。

如需詳細資訊，請參閱[設定](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/settings)。

## 布建時建議的安全預設值

首次布建ALM帳戶時，Adobe建議在授與任何系統管理使用者作業存取權之前，先驗證下列預設設定：

| 設定 | 建議的安全預設值 | 設定位置 |
|------------------------------|------------------------------------------------------------------|-------------------------------------------------|
| 登入方法 — 內部使用者 | 單一登入(SSO) / Federated ID | ALM >設定>登入方法 |
| 兩步驟驗證(2FA) | 強制（任何使用者皆非選擇性） | Admin Console >設定>隱私權與安全性 |
| 最長工作階段期限 | 8小時或根據組織原則 | Admin Console >設定>進階設定 |
| 最長閒置時間 | 30分鐘或根據組織原則 | Admin Console >設定>進階設定 |
| 管理員角色範圍 | 最低許可權；儘可能使用自訂管理員角色 | ALM >使用者>自訂角色 |
| 外部使用者到期 | 在每個外部使用者設定檔上設定到期日期 | ALM >使用者>外部 |

### 新管理員的初始設定檢查清單

布建新的最上層管理帳戶時，請先完成下列作業，再授與作業存取權：

* 確認身分型別為Enterprise ID或Federated ID — 而非個人Adobe ID。
* 在Admin Console層級強制執行2FA （「設定>驗證設定」）。
* 設定SSO / Federated ID （如果尚未啟用）。
* 在「Admin Console >設定>進階設定」中，設定「最大工作階段期限」和「最大閒置時間」 。
* 限制管理員角色範圍 — 僅指派使用者職責所需的許可權。
* 確認管理員帳戶繫結至您IT團隊所控制的組織電子郵件地址。
* 在貴組織的特權存取登記簿中記錄該帳戶。

## 管理帳戶的操作

### 日常管理任務

管理帳戶用於執行日常操作工作，包括：

* **使用者生命週期管理**：正在建立使用者、更新設定檔，以及進行角色變更。
* **學習內容管理**：管理課程、學習計畫、認證和目錄。
* **報告與分析**：產生並檢閱學習者進度和平台使用情形的報告。
* **整合與系統組態**：管理聯結器、以API為基礎的存取和系統層級設定。

執行管理動作時，管理員應遵循其組織的內部存取控制和變更管理原則。

請參閱[Adobe Learning Manager管理員的常見問題](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/faq/frequently-asked-questions-for-administrators)


### 角色階層與委派

Adobe Admin Console使用階層式管理結構。 系統管理員可以將職責委派給較低許可權的角色，以減少頂層管理員帳戶的攻擊面：

* 產品管理員：管理特定Adobe產品(例如Adobe Learning Manager)的存取權。
* 產品設定檔管理員：管理特定產品設定檔中的使用者成員資格。
* 使用者群組管理員：管理使用者群組成員資格。
* ALM自訂管理員： ALM中的已設定範圍管理員，可依每個目錄和使用者群組設定許可權。

### 持續的治理實務

執行ALM管理員帳戶的組織應持續遵循下列作法：

* **定期存取檢閱**：定期稽核Admin Console中的系統管理員（使用者>管理員）和ALM管理員（使用者>內部）清單，以確保只有最新的授權人員才能擔任這些角色。
* **稽核記錄監控**： Admin Console稽核記錄會記錄管理員所做的所有變更。 系統管理員具有完整可見性。 請定期檢閱記錄檔，以檢視未授權的變更。
* **最低長期存取權**：避免使用最上層管理帳戶執行例行工作。 保留明確所需工作的完整管理員存取權。
* **工作階段安全性**：在「Admin Console >設定>進階設定」中設定「工作階段存留時間上限」和「閒置時間上限」，以限制無人參與工作階段的曝光。

如需詳細資訊，請參閱[Admin Console總覽](https://helpx.adobe.com/tw/enterprise/using/admin-console.html)。

### 在管理員控制下管理使用者帳戶

ALM管理員可管理內部和外部使用者帳戶。 安全性相關作業包括：

* 使用者自動刪除：在「設定」中，管理員可以將非作用中的內部使用者設定為在指定的天數後自動刪除，減少休眠帳戶的風險。
* 外部使用者到期：管理員在建立外部使用者設定檔時設定到期日期。 過期的帳戶會自動移至非使用中狀態。
* 使用者刪除：管理員可以透過使用者>內部>動作>刪除使用者來手動刪除使用者。
* 使用者清除：刪除後，管理員可以永久清除使用者記錄，以符合資料保留政策，並防止未經授權存取過時的使用者資料。

如需詳細資訊，請參閱下列內容：

* [新增使用者和使用者群組](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/user-management/add-users-user-groups)
* [清除使用者](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/purge-users)

## 解除管理帳戶的委派

當不再需要管理存取權時，必須將其移除。 停用管理帳戶可能包括：

* 撤銷使用者的管理角色。
* 在不再需要完整管理存取權時減少許可權。
* 在適當的時候從系統中移除使用者。

定期檢閱及移除不必要的管理存取權，有助於維持最低許可權的存取權。

### 移除系統管理員許可權(Admin Console)

當系統管理員離開組織或變更角色時，必須立即撤銷許可權：

1. 以系統管理員身分登入Adobe Admin Console。
2. 導覽至「使用者>管理員」。
3. 選取要移除的管理員。
4. 按一下「更多選項(...)」圖示>編輯管理員，然後移除系統管理員角色 — 或選取「移除使用者」將使用者從組織中完全移除。
5. 如果管理員有其他角色（產品管理員、支援管理員等），也請撤銷這些角色。

>[!IMPORTANT]
>
>如果離職管理員是組織的「合約擁有者」，則必須先將「合約擁有者」角色移轉至其他人員，才能將其移除。 如有需要，請聯絡Adobe支援。

如需詳細資訊，請參閱下列內容：

* [在Admin Console上建立、更新或移除使用者帳戶](https://helpx.adobe.com/tw/enterprise/using/manage-users-individually.html)
* [如何離開貴組織擁有的帳戶](https://helpx.adobe.com/tw/enterprise/using/leave-organization.html)

### 移除ALM管理員角色

撤銷ALM管理員存取權而不刪除使用者帳戶（例如，當人員仍為學習者時）：

1. 以管理員身分登入Adobe Learning Manager。
2. 導覽至「使用者>內部」。
3. 搜尋並選取使用者。
4. 選取動作>移除角色>移除管理員。

使用者將恢復為學習者角色。 他們的學習歷程和課程註冊均會保留。

如需詳細資訊，請參閱[新增使用者與使用者群組](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/user-management/add-users-user-groups)。

### 刪除和清除使用者

當使用者完全離開組織時，其帳戶應從平台中移除：

* 刪除使用者：使用者>內部>選取使用者>動作>刪除使用者。 這會停用帳戶並移除作用中的存取權。
* 永久刪除使用者：刪除之後，請移至「使用者>使用者清除」，選取刪除月份，選取使用者，然後選擇「動作>永久刪除使用者」。 永久清除會移除所有使用者記錄。

如需詳細資訊，請參閱[清除使用者](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/purge-users)。


## 安全性與共同責任

Adobe Learning Manager是以共同責任模式運作：

* Adobe負責保護基礎的ALM平台和基礎架構。
* 客戶負責管理其ALM帳戶內的管理存取權、角色指派和使用者生命週期活動。

有關Adobe Learning Manager安全性實務的其他資訊，請參閱[Adobe Learning Manager安全性概覽(PDF)](https://experienceleague.adobe.com/docs/learning-manager/assets/alm-security-whitepaper-2024.pdf?lang=zh-Hant)

## 檔案維護

此檔案可能會定期更新，以反映Adobe Learning Manager功能或管理最佳實務中的變更。 版本和上次更新日期會保留在檔案中繼資料和FedRAMP授權套件中。 客戶應該參考Adobe Experience League上公開可用的版本，以確保他們使用最新的指引。

## 增強的安全性功能涵蓋範圍

### SCG-ENH-CMP

Adobe會維護有記錄的元件存貨、擁有權和生命週期管理流程，以確保跨系統元件的受控設定和合規性。

### SCG-ENH-API

Adobe會實施標準化的API安全性控制，包括驗證、授權和監控，並透過檔案控管和平台防護措施提供支援。

### SCG-ENH-MRG

Adobe會套用正式的變更和合併管理程式，包括審查和核准控制，以維護系統完整性並降低部署風險。

### SCG-ENH-VRH

Adobe遵循已定義的弱點管理和補救程式，包括識別、優先順序、追蹤和及時解決。
