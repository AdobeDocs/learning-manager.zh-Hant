---
jcr-language: en_us
title: Learning Manager 遵守 GDPR 規範
description: Adobe Learning Manager 遵守 GDPR 規範
contentowner: dvenkate
exl-id: 8ea31464-b4ce-49e8-b471-5630f0216aa4
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%
---
# Learning Manager 遵守 GDPR 規範

>[!IMPORTANT]
>
>本文件內容非法律建議，亦非法律建議的替代。 請諮詢貴公司的法律部門以獲取有關GDPR的建議。

Adobe Learning Manager 致力於遵守 GDPR 規範，確保使用者資料安全且透明地管理。 它提供必要的 GDPR 功能，例如清除使用者（永久刪除所有個人資料）的能力，並允許管理員產生學習者成績單，以應用戶需求分享資訊。

所有使用者資料在傳輸與儲存過程中均採用強加密保護，標準如 SHA-256。 部分整合中，學習者必須進行驗證，確保在分享任何資料前取得同意。 這些隱私與安全控管有助於使用 Adobe Learning Manager 的組織遵守 GDPR 規定，並保護學習者資訊。

+++什麼是 GDPR？

GDPR 是歐盟於 2018 年 5 月 25 日生效的新法規。 它能強力控制資料隱私，並讓終端使用者能掌控自己的個人資料。

+++

+++作為 Adobe Learning Manager 的客戶，這對你有什麼或為什麼適用？

雖然GDPR是歐盟法規，但它適用於全球企業實體，這些企業會收集任何可能為歐盟居民的用戶提供個人資訊。  作為學習經理的客戶，請評估GDPR是否適用於您的組織。

+++

+++Adobe 作為 Learning Manager 的供應商，在這方面扮演什麼角色？

根據GDPR，如果您的企業向歐盟居民提供產品或服務，並決定如何以及為何收集、追蹤及監控他們的資料，您被視為資料控制](https://gdpr-info.eu/art-24-gdpr/)者[。作為 Adobe Learning Manager 的客戶，如果你執行了這些活動之一，你就被視為資料控制者。

代表控制者處理資料的企業被視為  [資料處理者](https://gdpr-info.eu/art-28-gdpr/)。 作為雲端託管LMS Adobe Learning Manager的供應商，Adobe扮演著資料處理者的角色。 以下是關於  [GDPR與您的企業](https://www.adobe.com/privacy/general-data-protection-regulation.html)的更多細節。

+++

+++Learning Manager 如何協助你遵守 GDPR？

Learning Manager 內建了以下工具與流程，能協助您遵守 GDPR 規範。 為了支持任何超越產品、完全符合法規的流程，你仍可能需要與合規團隊進行評估。

**遺忘權——聯絡資料控制者：** GDPR 要求資料控制者為使用者提供遺忘權功能。 這表示任何使用者都有權請求資料控制者永久刪除為該使用者儲存的個人資料。 如果您收到此類請求並進一步評估其有效性，此功能現在已透過 Learning Manager [的清除使用者](../administrators/feature-summary/purge-users.md) 功能提供。 此功能允許管理員在個人要求下，啟動永久刪除與特定個人相關的資料，此時學習管理員會立即從資料庫中硬性刪除該資料，並自動清除備份日誌（用於系統恢復）。

**遺忘權利——聯絡資料處理者：** 最終使用者也可以獨立聯絡 Adobe 刪除他們的個人識別資訊（PII）。 此時，Learning Manager 會自動偵測該使用者的 PII 擁有者，Adobe 會立即通知管理員此請求。 管理員接著可以透過清除使用者功能評估請求的有效性並對請求進行電話處理。

**存取權：** GDPR 允許終端使用者請求控制者可能為其儲存的資料。 為了支援此請求，Learning Manager 允許管理員自行產生學習者成績單，並與使用者分享。

**隱私設計與資料加密：** 我們使用頂尖的加密標準處理傳輸中及靜止資料，以確保資料安全。 所使用的加密演算法為 SHA-256。 這確保你儲存的任何資料都能得到妥善保護，不會落入不法之手。

+++
