---
title: Adobe Learning Manager 管理帳號生命週期
description: 本文件提供全面指引，說明如何在 Adobe Learning Manager （ALM） 中安全管理頂層管理帳戶，以符合 FedRAMP 合規及最佳安全實務。
jcr-language: en-us
exl-id: 79049f3d-8ebe-47e7-9895-9a7aaee504b3
source-git-commit: 88298726a8cd4622e412200b3318e18890817ae8
workflow-type: tm+mt
source-wordcount: '2122'
ht-degree: 0%
---
# Adobe Learning Manager 中的管理帳號類型

## ALM 角色映射

在 Adobe Learning Manager 中，頂層的管理帳號是管理員角色。 本指南使用 FedRAMP 術語「頂層管理帳號」時，即指此角色。自訂管理員與整合管理員被視為特權（範圍）帳號。

下表將 FedRAMP 帳號層級對應至 Adobe Learning Manager 中所使用的具體角色：

| 聯邦RAMP條款 | ALM 角色名稱 | 說明 |
|--------------------------------------|----------------------------|-------------|
| 頂層行政帳號 | 行政長官 | ALM中最高特權的職位。 完全掌控使用者、角色、學習內容、報告、整合及所有系統配置。 直接對應 FedRAMP 頂層管理帳戶定義。 |
| 特權帳戶（範圍） | 自訂管理員 | 管理員權限的子集，範圍涵蓋特定功能（例如報告、目錄管理）。 沒有完整的帳戶層級控制權。 |
| 特權帳號（整合） | 整合管理員 | 管理ALM與外部系統之間的整合及API存取。 權限提升至僅限於整合管理。 |


Adobe Learning Manager 採用基於角色的存取控制（RBAC）模型來管理管理存取權限。 行政職務僅由授權管理員指派。

更多資訊請參閱 [Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/custom-role) 中的自訂角色

## 身份類型與推薦的認證方式

Adobe 管理控制台支援三種管理員帳號的身份類型。 身份類型的選擇具有直接的安全意涵：

| 身份類型 | 說明 | 安全建議 |
|---------------------------|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Adobe ID（個人ID） | 預設類型;由 Adobe 管理。 任何人都可以創造一個。 | 不建議管理員使用。 該組織對此帳戶類型沒有控制權。 |
| 企業識別碼 | 組織擁有的帳號由管理員控制台系統管理員管理。 | 若無法取得聯邦身份證/SSO，則可接受。 執行雙重驗證（2FA）。 |
| 聯邦身份證（SSO） | 組織擁有;整合了 SAML 2.0 SSO。 組織完全控制認證。 | 推薦。 透過組織的 IdP 進行認證;支援身份提供者層級的多重驗證（MFA）強制執行。 |

更多資訊請參見以下內容：

* [身份類型](https://helpx.adobe.com/tw/enterprise/using/admin-console.html)
* [安全使用者驗證與密碼](https://helpx.adobe.com/tw/enterprise/using/authentication-settings.html)

## 角色指派與存取控制

Adobe Learning Manager 中對管理員帳號的存取，是透過 [現有管理員明確指派](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/user-management/add-users-user-groups) 角色來控制的。 安全管理存取的主要特徵包括：

* 行政職務僅由授權管理員指派。
* 存取權限是基於角色的，並依據分配權限來設定範圍。
* 組織有責任限制有正當業務需求的使用者的管理存取權限。

Adobe 建議客戶定期檢視管理員存取權，以確保遵守最小權限原則。

## 強制多重身份驗證（MFA）

Adobe 強烈建議管理員在全組織範圍內執行兩步驟驗證（2FA）。 多重身份驗證適用於企業識別碼（Enterprise ID）及 Adobe ID 使用者。 Federated ID 使用者應該在組織的身份提供者執行 MFA。

在 Adobe 管理控制台強制執行雙重驗證：

1. 登入 Adobe 管理控制台。
2. 請前往隱私與安全設定>>認證設定。
3. 啟用雙步驟驗證並選擇強制執行選項，防止使用者停用該功能。
4. 可選擇性地設定基於 IP 的存取限制及進階會話設定（最大會話壽命/最大閒置時間）。

>[!IMPORTANT]
>
>Adobe 建議強制執行雙重驗證，且不讓使用者成為可選。 雙重驗證可能需要長達24小時才能申請。 對於聯邦身份證使用者，請在你的身份提供者處強制執行多重認證（MFA）。

更多資訊[&#128279;](https://helpx.adobe.com/tw/enterprise/using/authentication-settings.html)請參閱安全使用者驗證。


## 以管理員身份登入

ALM [管理員可](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/get-started/getting-started-admin) 直接使用管理控制台管理的組織憑證登入 ALM 平台。

### 指派管理員角色

在 ALM 平台中，管理員透過建立和管理角色、分配使用者權限，以及根據營運責任定義權限範圍來配置管理員存取權。

要在 ALM 中指派管理員角色：

1. 以現有管理員身份登入 Adobe Learning Manager。
2. 前往內部>使用者。
3. 搜尋或選擇目標使用者。
4. 選擇動作>指派角色>設為管理員。

自訂管理角色讓客戶能委派管理任務，同時維持對帳號層級權限的集中控制。 自訂管理員可設定為特定使用者群組或目錄。

更多資訊請參見 [新增使用者與使用者群組](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/user-management/add-users-user-groups) 。

## 設定登入方式與單點登入

ALM 管理員透過設定>登入方法控制所有使用者可用的登入方式，這是一項關鍵的安全相關設定：

* **內部使用者**：請將登入模式設為 Adobe ID 或單一登入（SSO）。 強烈建議使用 SAML 2.0 進行單點定位。
* **外部使用者**：將登入模式設為 Adobe ID、SSO 或學習管理員 ID。 將所選方法與您組織的安全政策對齊。

Adobe 建議所有內部使用者使用 Federated ID / SAML 2.0 SSO 作為登入方式。 這確保認證由貴組織的身份提供者完全控制，實現集中多重身份驗證（MFA）執行及用戶離開後立即撤銷帳號。

更多資訊請參閱 [設定](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/settings) 。

## 推薦的配置安全預設

當 ALM 帳號首次配置時，Adobe 建議在授予任何管理使用者操作權限前，先驗證以下預設設定：

| 背景設定 | 建議的安全預設 | 設定地點 |
|------------------------------|------------------------------------------------------------------|-------------------------------------------------|
| 登入方式 — 內部使用者 | 單一登入（SSO）/聯邦識別 | ALM > 設定>登入方法 |
| 兩步驟驗證（2FA） | 強制執行（任何使用者都不可選擇） | 管理主控台>隱私與安全設定> |
| 最大會話壽命 | 8小時或依組織政策 | 管理控制台>設定>進階設定 |
| 最大閒置時間 | 每30分鐘或依組織政策 | 管理控制台>設定>進階設定 |
| 行政職務範圍 | 最低權限;盡可能使用自訂管理員角色 | ALM >使用者>自訂角色 |
| 外部使用者過期 | 為每個外部使用者設定一個有效期限 | ALM >外部使用者> |

### 新管理員初始設定清單

在配置新的頂層管理員帳號時，請在授權營運權限前完成以下事項：

* 確認身份類型是企業識別碼（Enterprise ID）或聯邦識別碼（Federated ID），而非個人 Adobe ID。
* 在管理控制台層級強制執行雙重驗證（設定>認證設定）。
* 如果還沒啟用，請設定 SSO / 聯邦識別碼。
* 在管理控制台設定中設定最大會話壽命和最大閒置時間>>進階設定。
* 限制管理員角色範圍——只分配使用者職責所需的權限。
* 確認管理員帳號是否綁定到由你的 IT 團隊控制的組織電子郵件地址。
* 將該帳戶記錄在您的組織的特權存取登記冊中。

## 行政帳戶的運作

### 日常行政工作

管理帳號用於執行日常營運任務，包括：

* **使用者生命週期管理**：建立使用者、更新個人資料及角色變更。
* **學習內容管理**：管理課程、學習計畫、認證及目錄。
* **報告與分析**：產生並檢視學習者進度與平台使用報告。
* **整合與系統設定**：管理連接器、基於 API 的存取及系統層級設定。

管理員在執行行政操作時，預期必須遵守組織內部的存取控制與變更管理政策。

請參閱 [Adobe Learning Manager 管理員常見問題](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/faq/frequently-asked-questions-for-administrators)


### 角色階層與委派

Adobe 管理主控台採用階層式管理架構。 系統管理員可以將責任委派給權限較低的角色，以減少頂層管理員帳號的攻擊面：

* 產品管理員：管理特定 Adobe 產品的存取權限（例如 Adobe Learning Manager）。
* 產品設定檔管理員：管理特定產品設定檔的使用者會員資格。
* 使用者群組管理員：管理使用者群組成員資格。
* ALM 自訂管理員：ALM 內有範圍的管理員，可依目錄與使用者群組設定權限。

### 持續的治理實務

持續經營 ALM 管理帳號的組織應遵循以下做法：

* **定期存取審查**：定期稽核管理主控台（使用者>管理員）及 ALM 管理員（>內部使用者）的系統管理員名單，確保只有目前授權的員工擔任這些職務。
* **稽核日誌監控**：管理控制台稽核日誌記錄管理員所做的所有變更。 系統管理員擁有完整的可視性。 定期檢查日誌是否有未經授權的變更。
* **最低常駐存取**&#x200B;權：避免使用頂層管理員帳號執行例行任務。 將完整管理員權限保留給特別需要的任務。
* **會話安全**：在管理控制台>設定>進階設定中設定最大會話壽命與最大閒置時間，以減少無人值守會話的暴露。

更多資訊請參閱 [管理控制台總覽](https://helpx.adobe.com/tw/enterprise/using/admin-console.html) 。

### 管理管理員控制下的使用者帳號

ALM 管理員管理內部及外部使用者帳號。 與安全相關的作業包括：

* 使用者自動刪除：在設定中，管理員可設定非活躍的內部使用者在指定天數後自動刪除，降低帳號休眠風險。
* 外部使用者過期：管理員在建立外部使用者設定檔時會設定有效期限。 過期帳戶會自動移至非活躍狀態。
* 使用者刪除：管理員可透過內部>動作>手動刪除使用者>刪除使用者。
* 使用者清除：刪除後，管理員可永久清除使用者紀錄，以符合資料保留政策，防止未經授權存取過時資料。

更多資訊請參見以下內容：

* [新增使用者及使用者群組](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/user-management/add-users-user-groups)
* [清除使用者](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/purge-users)

## 行政帳目解碼

當管理員權限不再需要時，必須移除。 停用行政帳戶可能包括：

* 撤銷使用者的管理員角色。
* 當不再需要完整管理權限時，會減少權限。
* 適當時將使用者從系統中移除。

定期檢視並移除不必要的行政存取，有助於維持最低權限的存取權限。

### 移除系統管理員權限（管理控制台）

當系統管理員離開組織或更換角色時，權限必須立即撤銷：

1. 以系統管理員身份登入 Adobe 管理主控台。
2. 前往使用者>管理員。
3. 選擇要移除的管理員。
4. 點擊編輯管理員>「更多選項」圖示，然後移除系統管理員角色——或選擇移除使用者，將該使用者完全從組織中移除。
5. 如果管理員同時擔任其他職務（產品管理員、支援管理員等），也要撤銷這些職務。

>[!IMPORTANT]
>
>若離職管理員是組織的合約擁有人，合約擁有人角色必須先轉移給他人，才能將其移除。 如有需要，請聯絡 Adobe 客服。

更多資訊請參見以下內容：

* [在管理控制台建立、更新或移除使用者帳號](https://helpx.adobe.com/tw/enterprise/using/manage-users-individually.html)
* [如何離開你所屬的組織帳號](https://helpx.adobe.com/tw/enterprise/using/leave-organization.html)

### 移除 ALM 管理員角色

若要在不刪除使用者帳號的情況下撤銷 ALM 管理員的存取權（例如，當該人仍為學習者時）：

1. 以管理員身份登入 Adobe Learning Manager。
2. 前往內部>使用者。
3. 搜尋並選擇使用者。
4. 選擇動作>移除角色>移除管理員。

使用者會回復到學習者角色。 他們的學習歷史與課程註冊紀錄均被保留。

更多資訊請參閱 [新增使用者及使用者群組](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/user-management/add-users-user-groups) 。

### 刪除並清除使用者

當使用者完全離開組織，且其帳號應從平台上移除時：

* 刪除使用者：使用者>內部>選擇使用者>動作>刪除使用者。 這會讓帳號失效並移除主動存取權限。
* 清除使用者：刪除後，前往使用者>使用者清理，選擇刪除月份，選擇使用者，並選擇行動>清除使用者。 清除會永久移除所有使用者紀錄。

更多資訊請參閱 [清除用戶](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/purge-users) 。


## 安全與共同責任

Adobe Learning Manager 採用共同責任模式：

* Adobe 負責保護底層的 ALM 平台與基礎設施。
* 客戶需負責管理其 ALM 帳戶中的管理權限、角色指派及使用者生命週期活動。

關於 Adobe Learning Manager 安全實務的更多資訊，請參閱 [Adobe Learning Manager 安全概覽（PDF）](https://experienceleague.adobe.com/docs/learning-manager/assets/alm-security-whitepaper-2024.pdf?lang=zh-Hant)

## 文件維護

本文件可能會定期更新，以反映 Adobe Learning Manager 功能或管理最佳實務的變更。 版本與最後更新日期會被保留在文件的元資料及 FedRAMP 授權套件中。 客戶應參考 Adobe Experience League 公開版本，以確保使用最新的指引。

## 強化安全能力覆蓋

### SCG-ENH-CMP

Adobe 維護有文件記錄的元件庫存、所有權及生命週期管理流程，以確保系統元件間受控的配置與合規性。

### SCG-ENH-API

Adobe 強制執行標準化的 API 安全控管，包括認證、授權與監控，並由有文件化的治理與平台防護措施支持。

### SCG-ENH-MRG

Adobe 採用正式的變更與合併管理流程，包括審查與核准控制，以維持系統完整性並降低部署風險。

### SCG-ENH-VRH

Adobe 遵循明確的漏洞管理與修復流程，涵蓋識別、優先排序、追蹤及及時解決。
