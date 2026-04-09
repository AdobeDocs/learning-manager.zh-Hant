---
title: Adobe Learning Manager - 安全設定與組態管理
description: 本文件說明 Adobe Learning Manager 的管理帳號類型、安全相關設定、建議的安全預設、API 功能、匯出功能、設定比較方法、發佈慣例及版本歷史。 它詳細說明了特權帳號的運作方式、其安全影響，以及整個平台如何支援配置管理。
jcr-language: en-us
exl-id: a2e34104-c417-407f-af85-9f3f4b2a9fcb
source-git-commit: 3188d7f5593aeee87978e1e46456f01e1f41d57b
workflow-type: tm+mt
source-wordcount: '1954'
ht-degree: 0%

---

# 安全設定與組態管理

本指南提供對 Adobe Learning Manager（ALM）FedRAMP 建議（FRR-RSC-03 至 FRR-RSC-08）的詳細回應。 它概述了安全最佳實務、建議的安全預設值，以及用於審核、匯出和管理特權帳號設定的工具。 本文件旨在為管理員及合規團隊設計，以確保 ALM 帳戶的安全配置與管理。

同時也強調 ALM 在哪些領域符合或部分符合 FedRAMP 標準，並引用 Adobe Experience League 上可取得的相關文件與資源。

+++在 Adobe Learning Manager 中，哪些與安全相關的設定只能由自訂管理員或整合管理員操作？它們會帶來哪些安全影響？

Adobe Learning Manager 有兩種特權帳號類型——自訂管理員和整合管理員。 每個機構都有一套定義的安全相關設定，並有文件化的影響。

**自訂管理員——他們能操作**&#x200B;什麼：

* 自訂角色由完整管理員在 ALM 管理員> 使用者自訂角色>設定。 自訂管理員可獲得一項或多項權限類別的存取權：帳號權限（公告、遊戲化、技能、使用者管理）、功能權限（目錄、報告、標籤）及學習物件權限（課程、認證、學習路徑）。
* 範圍是最敏感的安全設定：自訂角色可限制於特定使用者群組及/或特定目錄。 若無範圍限制，自訂角色實際上擁有全平台權限，存取其授權功能——接近完整管理員的規模。
* 如果自訂角色在帳戶權限下獲得設定權限，該自訂管理員可以修改登入方式、通知設定及帳號層級設定——這是高影響力的權限，只有在明確的商業理由下才應授予。

**整合管理員——他們能操作**&#x200B;什麼：

* 整合管理員在整合管理>應用程式>註冊處管理 OAuth 2.0 應用程式註冊。 他們會從六個 OAuth 範圍中選擇一個，範圍從學習者讀取權限到 Admin 角色讀寫權限。 管理員讀寫範圍透過 API 賦予註冊應用程式與完整管理員相同的權限。
* 整合管理員負責配置 FTP、SFTP、Salesforce、Workday 及其他連接器，匯入使用者紀錄、角色分配及課程完成紀錄，並將平台資料匯出至外部系統。
* 整合管理員會配置 webhook，將即時 ALM 事件資料（註冊、完成、角色變更）推送到外部 URL。 被入侵或設定錯誤的 webhook 端點存在資料外洩風險。
* 整合管理員可以設定 LTI 整合。 一旦啟用，LTI 就無法被關閉。

**參考資料**：

* [自訂角色 |Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/custom-role)
* [透過 CSV 管理自訂角色 |Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/integration/configure-role-csv-files)
* [應用程式開發手冊 \|Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/integration/developer-manual)
* [Adobe Learning Manager 連接器](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/integration/connectors)

+++

+++Adobe Learning Manager 中頂層管理及特權帳號的建議安全預設值是什麼？它們在哪裡設定？

Adobe Learning Manager 文件中針對管理員角色與特權帳號類型，具體建議的安全預設值。

* **頂層管理員帳號預設值（首次配置時設定）：**

* 內部使用者登入方式：透過 SAML 2.0 進行單一登入（SSO）：於 ALM 管理>設定>登入方法設定。 請勿將 Adobe ID 用於員工或管理員。
* 兩步驟驗證（2FA）：對所有使用者強制執行：於 Adobe 管理控制台設定 >隱私與安全>認證設定>設定。
* 最大會話時間：8 小時（或依組織政策）：可在 Adobe 管理控制台設定>>隱私與安全>進階設定中設定。
* 最大閒置時間：30 分鐘（或依組織政策）：與上述地點相同。
* 非活躍使用者自動刪除：啟用時有組織定義的保留期限（例如，90 天非活躍）：ALM 管理員>設定>一般。
* 外部使用者設定檔過期：建立時在每個外部設定檔設定：ALM 管理員>外部使用者>。 沒有無限期的外部檔案。
* IP 存取限制：盡可能限制在核准的 IP 範圍：管理控制台>設定>進階設定。

**自訂管理員角色預設值（建立每個角色時設定）**：

* OAuth 註冊申請範圍：最低要求範圍。 除非絕對必要，否則絕不要授予管理員角色讀寫權限。
* 自訂角色範圍：限制於特定使用者群組與特定目錄。 除非函式確實需要，否則不要建立包含「所有使用者」和「所有目錄」範圍的自訂角色。
* 自訂角色中的設定存取權：除非特定函式需要，否則不要授予權限，因為有權限提升的風險。

**整合管理員預設功能**：

* API OAuth 範圍：選擇最嚴格且符合整合需求的範圍。 不要授權管理員對只需要學習者讀取權限的應用程式進行讀寫。
* 連接器憑證、LTI 憑證與 webhook URL：視為敏感秘密——切勿透過電子郵件分享或提交至原始碼控制。

**參考資料**：

* [場景 |Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/custom-role)
* [安全使用者驗證與密碼 |Adobe 管理控制台](https://helpx.adobe.com/tw/enterprise/using/authentication-settings.html)
* [自訂角色 |Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/admin/custom-role)

+++

+++Adobe Learning Manager 是否提供管理員比較目前帳號設定與建議的安全預設值的方法？

Adobe Learning Manager 沒有專門的比較儀表板，能自動顯示目前設定及建議的安全預設值。

**自訂角色報告：目前特權角色分配**：

* 在 ALM 中，前往管理員>使用者>自訂角色，點選右上角下載，匯出所有自訂角色、權限集及範圍分配的 CSV 檔案。
* 將此匯出與 FRR-RSC-02 第 8 節建議預設值比較——特別檢查是否有自訂角色擁有設定權限、所有使用者範圍或所有目錄範圍，且無文件證明。

**ALM REST API：程式化配置檢索**：

* GET /account 端點會回傳帳號層級的設定資料，格式為 JSON 格式，並可透過管理員角色 OAuth 範圍存取。 客戶可程式化呼叫此端點，並將回應與 FRR-RSC-02 第 8 節建議預設值的基準進行比對。
* GET /users 端點（含 include=角色篩選器）會回傳所有使用者的當前角色指派，使能自動偵測意外的角色指派。

>[!NOTE]
>
>Adobe Learning Manager 沒有提供原生的並排比較介面。 需要自動配置合規檢查的客戶，應將 ALM REST API 整合至現有工具中。

**參考資料**

* [應用程式開發手冊 |Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/integration/developer-manual)

+++

+++管理員能否將 Adobe Learning Manager 中目前與安全相關的設定與設定匯出成機器可讀格式？

Adobe Learning Manager 支援透過多種機制匯出與安全相關的設定資料。 沒有單一匯出能同時產生所有安全設定的完整快照，但以下匯出總共涵蓋所有與安全相關的資料範圍。

**ALM REST API：JSON 匯出目前角色分配與帳號設定**：

* GET /account：回傳以 JSON 格式呈現的帳號層級設定，包括有效的登入設定資料和帳號元資料。
* GET /users？include=role：以 JSON 格式回傳所有使用者目前分配的角色。
* GET /userGroups — 回傳所有使用者群組及其成員資格，與審核自訂角色範圍相關的資料。
* 所有 API 回應都是 JSON（vnd.api+json）。 認證使用 OAuth 2.0，並具備管理員角色的讀寫範圍。

**自訂角色 CSV 匯出：目前特權角色定義**：

* ALM 管理員> 使用者>自訂角色 > 下載 會匯出包含所有自訂角色定義、權限類別及範圍指派的 CSV 文件。
* 此匯出可作為機器可讀的當前特權帳號設定快照。
**

**工作 API：大量使用者與角色資料**：

* ALM Jobs API 支援按需產生使用者報告（包括角色指派），以 CSV 格式呈現。 這些資料可以被排程並由外部合規或 SIEM 工具使用。

**參考資料**

* [應用程式開發手冊 |Adobe Learning Manager](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/integration/developer-manual)

+++

+++Adobe Learning Manager 是否提供一個 API，讓安全相關設定可以程式化地查看和調整？

Adobe Learning Manager 提供完整的 REST API v2，允許透過 OAuth 2.0 認證程式化檢視及調整安全相關設定。 以下是與安全設定相關的具體 API 功能：

**認證與範圍**：

* 應用程式由整合管理員在 Integration Admin > Applications > 註冊處註冊。 OAuth 2.0 客戶端 ID 與秘密是每個應用程式都會發布。
* 提供六種瞄準鏡。 管理安全設定時，需要管理員角色的讀寫權限。 這會讓應用程式透過 API 獲得與正式管理員相同的存取權限。
* 存取權杖可透過標準 OAuth 授權碼或用戶端憑證流程取得。 基本網址：https://learningmanager.adobe.com/primeapi/v2/

**透過 API** 管理使用者與角色：

* GET /users：取得所有使用者及其目前角色
* POST /users：程式化配置新使用者
* PATCH /users/{id}： 更新使用者屬性，包括角色分配
* 刪除 /users/{id}：停用使用者帳號
* POST /users/{id}/purge：永久清除使用者及所有相關紀錄

帳戶設定檢索：

* GET /account：回傳帳號層級設定，包含帳號設定資料（以 JSON 格式呈現），包括 complianceLabelDefaultID、showComplianceLabel 和 custom_injections 等欄位。

+++

+++Adobe Learning Manager 是否會以機器可讀格式（如 OSCAL、JSON 或 YAML）發佈其安全設定指引？

Adobe Learning Manager 目前尚未以機器可讀格式發佈其安全設定指南。 FRR-RSC-01[&#128279;](/help/migrated/alm-administrative-lifecycle.md) 與 [FRR-RSC-02](/help/migrated/alm-secure-administration-guide.md) 中的指引以 HTML 及可下載文件格式發佈於 Adobe Experience League 上，提供人文易讀文件。

目前沒有公開可用的 OSCAL 元件定義、YAML 基線或 JSON 政策檔來編碼 Adobe Learning Manager 推薦的安全預設值。

需要自動比較當前設定與建議基線的客戶，應使用 [ALM REST API](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/integration/developer-manual) 以 JSON 格式取得當前設定資料。

+++

+++Adobe Learning Manager 的安全設定指南是否公開，無需登入或特殊存取？

**公開資訊**：

* [FRR-RSC-01：安全管理指南](/help/migrated/alm-administrative-lifecycle.md)：頂級管理帳戶的完整生命週期指引。
* [FRR-RSC-02：管理安全設定與影響](/help/migrated/alm-secure-administration-guide.md)：所有與安全相關的設定、其影響與建議預設值。
* FRR-RSC-03–10（本文件）— 對所有八項FedRAMP SHOULD建議的問答回應。

+++

+++Adobe Learning Manager 是否提供版本控制和版本歷史，讓機構能追蹤安全相關設定的變更及建議預設值隨時間變化？

Adobe Learning Manager 維護公開且詳細的每次產品更新的發行歷史。 每個版本中都有安全相關的管理設定變更、認證功能、API 端點及角色管理功能。

**ALM 發布說明：編號的累積變更歷史**：

* Adobe 會針對每次 Adobe Learning Manager 更新（例如 Update 100、Update 99）發布編號版本說明。 這些資料會在 Experience League 上發布，記錄所有新功能、現有設定的變更、API 新增與移除、連接器變更及已棄用的功能。
* 每個版本說明都包含一個專門的 API 變更區塊，列出新端點、修改過的回應欄位及棄用內容，直接與安全相關的設定能力相關。

**新內容頁面：各版本功能摘要**：

* 每個主要版本都有專門的「最新資訊」頁面，記錄與安全相關的新功能並附有上下文。 例如，發布說明包含自訂角色權限處理的變更、新增 CSV 建立的自訂角色權限可見性，以及限制 API 速率的變更。

**API 棄用清單：已移除 API 能力**&#x200B;的權威紀錄：

* Adobe 維護一個專門的 API 棄用頁面，列出所有已棄用及移除的 ALM API 端點，並列出每次棄用發生的版本。

**參考資料**：

* [Adobe Learning Manager 發布說明](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/introduction/release-notes)
* [Adobe Learning Manager 的新內容](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/introduction/whats-new-july-2024)
* [Adobe Learning Manager 中的 API 棄用](https://experienceleague.adobe.com/zh-hant/docs/learning-manager/using/introduction/api-deprecations-list)

+++
