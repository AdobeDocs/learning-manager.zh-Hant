---
title: Adobe Learning Manager — 安全性設定和組態管理
description: 本檔案概述Adobe Learning Manager的管理帳戶型別、安全性相關設定、建議的安全預設值、API功能、匯出功能、設定比較方法、發佈實務和版本記錄。 它提供有關特殊許可權帳戶如何運作、其安全性影響，以及如何跨平台支援設定管理的詳細指引。
jcr-language: en-us
exl-id: a2e34104-c417-407f-af85-9f3f4b2a9fcb
source-git-commit: 8b4ac7a99a9bf0cbeaa4ed07fd979deb7130302d
workflow-type: tm+mt
source-wordcount: '1944'
ht-degree: 0%

---

# 安全性設定與組態管理

本指南針對Adobe Learning Manager (ALM)的FedRAMP建議（FRR-RSC-03至FRR-RSC-08）提供詳細回應。 它概述了安全性最佳實務、建議的安全預設值，以及稽核、匯出和管理特權帳戶設定的工具。 該檔案專為管理員和合規團隊設計，以確保ALM帳戶的安全配置和管理。

此外也強調ALM符合或部分符合FedRAMP標準的領域，並提供Adobe Experience League上可用的支援檔案和資源參考。

+++Adobe Learning Manager中的自訂管理員或整合管理員才能操作哪些安全性相關設定，以及這些設定對安全性有何影響？

Adobe Learning Manager的兩種特殊許可權帳戶型別 — 自訂管理員和整合管理員。 每個檔案都有一組已定義的安全性相關設定，並附有記錄的含意。

**自訂管理員 — 他們可以操作的專案**：

* 自訂角色由完整管理員在ALM管理員>使用者>自訂角色中設定。 自訂管理員可以取得一或多個許可權類別的存取權：帳戶許可權(公告、gamification、技能、使用者管理)、功能許可權（目錄、報表、標籤）和學習物件許可權（課程、認證、學習路徑）。
* 範圍是最安全敏感的設定：自訂角色可以限製為特定使用者群組和/或特定目錄。 在沒有範圍限制的情況下，自訂角色實際上可在平台範圍記憶體取其授與的功能，接近完整管理員的足跡。
* 如果自訂角色在「帳戶許可權」下被授與「設定」存取權，則該自訂管理員可以修改登入方法、通知設定和帳戶層級的設定 — 這個高影響力的許可權應該只能以明確的業務理由授予。

**整合系統管理員 — 他們可以操作的專案**：

* 整合管理員可在整合管理員>應用程式>註冊中管理OAuth 2.0應用程式註冊。 他們從六個OAuth範圍中選取一個，範圍包括學習者讀取存取權及管理員角色讀取/寫入存取權。 管理員讀取/寫入範圍透過API授予註冊的應用程式與完整管理員相同的許可權。
* 整合管理員會設定FTP、SFTP、Salesforce、Workday和其他聯結器，匯入使用者記錄、角色指派和課程完成，並將平台資料匯出至外部系統。
* 整合管理員會設定Webhook，將即時ALM事件資料（註冊、完成、角色變更）推送至外部URL。 webhook端點遭到破壞或設定錯誤會導致資料外送風險。
* 整合管理員可設定LTI整合。 LTI一經啟用即無法停用。

**個參考**：

* [自訂角色 | Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/custom-role)
* [透過CSV管理自訂角色 | Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/integration/configure-role-csv-files)
* [應用程式開發人員手冊 | Adobe Learning Manager][https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/integration/developer-manual]
* [Adobe Learning Manager聯結器](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/integration/connectors)

+++

+++Adobe Learning Manager中高層管理及特殊許可權帳戶的安全預設值建議為何，其設定位置為何？

Adobe Learning Manager會記錄管理員角色和特殊許可權帳戶型別的特定建議安全預設值。

* **最上層系統管理員帳戶預設值（在第一次布建時設定）**：

* 內部使用者的登入方法：透過SAML 2.0的單一登入(SSO)：在ALM 「管理員>設定>登入方法」中設定。 員工或管理員請勿使用Adobe ID。
* 兩步驟驗證(2FA)：對所有使用者強制執行：在Adobe Admin Console >設定>隱私權與安全性>驗證設定中設定。
* 最長工作階段有效期：8小時（或依組織原則）：已在Adobe Admin Console >設定>隱私權與安全性>進階設定中設定。
* 最長閒置時間： 30分鐘（或根據組織原則）：與上述位置相同。
* 非使用中使用者自動刪除：以組織定義的保留期間（例如90天非使用中）啟用： ALM管理員>設定>一般。
* 外部使用者設定檔到期日：建立時，在每個外部設定檔上設定： ALM管理員>使用者>外部。 沒有無限的外部設定檔。
* IP存取限制：在可行的情況下，將限製為已核准的IP範圍： 「Admin Console >設定>進階設定」。

**自訂管理員角色預設值（建立每個角色時設定）**：

* 已登入應用程式的OAuth範圍：最低必要範圍。 除非絕對必要，否則絕對不要授予管理員角色讀取/寫入許可權。
* 自訂角色範圍：僅限於特定使用者群組和特定目錄。 請勿建立具有「所有使用者」和「所有目錄」範圍的自訂角色，除非函式確實需要它。
* 自訂角色中的設定存取權：考慮到許可權提升的風險，除非特定功能需要此許可權，否則請勿授與存取權。

**整合管理員預設值**：

* API OAuth範圍：選取符合整合需求的最嚴格範圍。 請勿將管理員讀取/寫入許可權授予僅需要學習者讀取存取權的應用程式。
* 聯結器憑證、LTI憑證和webhook URL：視為敏感機密 — 切勿透過電子郵件共用或提交至原始檔控制。

**個參考**：

* [設定 | Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/custom-role)
* [安全的使用者驗證和密碼 | Adobe Admin Console](https://helpx.adobe.com/tw/enterprise/using/authentication-settings.html)
* [自訂角色 | Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/custom-role)

+++

+++Adobe Learning Manager是否讓管理員可將目前的帳戶設定與建議的安全預設值進行比較？

Adobe Learning Manager沒有專用的比較控制面板，無法自動顯示目前設定及建議的安全預設值。

**自訂角色報告：目前授權的角色指派**：

* 在ALM中，導覽至「管理員>使用者>自訂角色」 ，然後按一下「下載」 （右上方），匯出所有自訂角色、其許可權集及其範圍指派的CSV。
* 將此匯出與FRR-RSC-02第8節中建議的預設值進行比較 — 特別檢查是否有任何自訂角色具有「設定」存取權、「所有使用者」範圍或「所有目錄」範圍，但沒有檔案證明。

**ALM REST API：程式化組態擷取**：

* GET /account端點會傳回JSON格式的帳戶層級設定資料，並可使用管理員角色OAuth範圍存取。 客戶可以程式設計方式呼叫此端點，並將回應與根據FRR-RSC-02第8節中的建議預設值衍生的基準值進行比較。
* GET /users端點（具有include=role篩選器）會傳回所有使用者的目前角色指派，啟用自動偵測非預期角色指派的功能。

>[!NOTE]
>
>Adobe Learning Manager不提供原生並排比較UI。 需要自動化設定合規性檢查的客戶應將ALM REST API與其現有工具整合。

**參考**

* [應用程式開發人員手冊 | Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/integration/developer-manual)

+++

+++管理員是否能夠以機器可讀的格式從Adobe Learning Manager匯出目前的安全性相關設定和設定？

Adobe Learning Manager支援透過數個機制匯出安全性相關設定資料。 單一匯出不會一次產生所有安全性設定的完整快照，但下列匯出內容會共同涵蓋安全性相關資料的完整範圍。

**ALM REST API：目前角色指派和帳戶設定的JSON匯出**：

* GET /account：傳回JSON中的帳戶層級設定，包括作用中登入設定資料和帳戶中繼資料。
* GET /users？include=role：傳回所有使用者，以及他們目前在JSON中指派的角色。
* GET /userGroups — 傳回與稽核自訂角色範圍相關的所有使用者群組及其成員資格。
* 所有API回應均為JSON (vnd.api+json)。 驗證使用具有管理員角色讀取/寫入範圍的OAuth 2.0。

**自訂角色CSV匯出：目前有特殊許可權的角色定義**：

* ALM管理員>使用者>自訂角色>下載會匯出包含所有自訂角色定義、其許可權類別和範圍指派的CSV。
* 此匯出可做為目前特殊許可權帳戶設定的機器可讀快照。
**

**工作API：大量使用者和角色資料**：

* ALM工作API支援隨選產生CSV格式的使用者報表（包括角色指派）。 這些可以由外部合規性或SIEM工具排程和使用。

**參考**

* [應用程式開發人員手冊 | Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/integration/developer-manual)

+++

+++Adobe Learning Manager是否提供API，可透過該API以程式設計方式檢視和調整安全性相關設定？

Adobe Learning Manager提供完整的REST API v2，可讓您使用OAuth 2.0驗證以程式設計方式檢視和調整安全性相關設定。 以下是與安全性設定相關的特定API功能：

**驗證和範圍**：

* 應用程式是由整合管理員在「整合管理員>應用程式>註冊」中註冊。 OAuth 2.0使用者端ID和密碼是按應用程式發行。
* 有六個可用的範圍。 對於安全性設定管理，需要管理員角色讀取/寫入許可權。 這會透過API授予應用程式與完整管理員的相同存取權。
* 存取權杖可透過標準OAuth授權代碼或使用者端憑證流程取得。 基底URL： https://learningmanager.adobe.com/primeapi/v2/

**透過API管理使用者和角色**：

* GET /users：擷取所有使用者及其目前的角色
* POST /users：以程式設計方式布建新使用者
* PATCH /users/{id}：更新使用者屬性，包括角色指派
* DELETE /users/{id}：停用使用者帳戶
* POST /users/{id}/purge：永久清除使用者及所有相關記錄

帳戶設定擷取：

* GET /account：傳回帳戶層級設定，包括JSON格式的帳戶設定資料，包括complianceLabelDefaultID、showComplianceLabel和custom_insertions等欄位。

+++

+++Adobe Learning Manager是否以機器可讀的格式（例如OSCAL、JSON或YAML）發佈其安全設定指引？

Adobe Learning Manager目前未以機器可讀的格式發佈其安全設定指南。 [FRR-RSC-01](/help/migrated/alm-administrative-lifecycle.md)和[FRR-RSC-02](/help/migrated/alm-secure-administration-guide.md)中的指引已發佈為HTML中人類可讀取的Adobe Experience League檔案和可下載的檔案格式。

沒有公開可用的OSCAL元件定義、YAML基準或JSON原則檔案，可編碼Adobe Learning Manager的建議安全預設值。

客戶若需要自動比較目前設定與建議的基準，應使用[ALM REST API](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/integration/developer-manual)擷取JSON格式的目前設定資料。

+++

+++Adobe Learning Manager的安全設定指南是否可公開使用，不需要登入或特殊存取？

**公開可用的專案**：

* [FRR-RSC-01：安全管理指南](/help/migrated/alm-administrative-lifecycle.md)：最上層管理帳戶的完整生命週期指南。
* [FRR-RSC-02：系統管理安全性設定與影響](/help/migrated/alm-secure-administration-guide.md)：所有安全性相關設定、其影響，以及建議的預設值。
* FRR-RSC-03-10 （本檔案） — 針對所有八個FedRAMP SHOULD建議的問答回應。

+++

+++Adobe Learning Manager是否提供版本設定和發行版本記錄，好讓機構追蹤安全性相關設定和建議預設值在一段時間內的變更？

Adobe Learning Manager會維護每個產品更新的公開可用詳細版本記錄。 管理設定、驗證功能、API端點和角色管理功能的安全性相關變更，會記錄在每個版本中。

**ALM發行說明：編號、累積變更記錄**：

* Adobe會為每個Adobe Learning Manager更新發佈編號的發行說明（例如更新100、更新99）。 這些功能會發佈在Experience League上，並記錄所有新功能、現有設定的變更、API新增和移除、聯結器變更以及過時的功能。
* 每個版本注意事項都包含API變更的專屬區段，其中列出與安全性相關設定功能直接相關的新端點、修改的回應欄位及淘汰內容。

**新增功能頁面：每次發行功能摘要**：

* 每個主要發行版本都有專屬的「新功能」頁面，記錄具有內容的安全性相關新功能。 例如，發行說明包含對自訂角色許可權處理的變更、為自訂角色新增CSV建立的許可權可見度，以及API速率限制變更。

**API淘汰清單：已移除API功能的權威記錄**：

* Adobe會維護一個專用的「API淘汰」頁面，其中列出所有已淘汰和已移除的ALM API端點以及每次淘汰發生的發行版本。

**個參考**：

* [Adobe Learning Manager發行說明](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/introduction/release-notes)
* [Adobe Learning Manager的新增功能](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/introduction/whats-new-july-2024)
* [Adobe Learning Manager不再使用API](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/introduction/api-deprecations-list)

+++
