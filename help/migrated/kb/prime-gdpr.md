---
jcr-language: en_us
title: Learning Manager法規遵循GDPR
description: 將Learning Manager合規性Adobe至GDPR
contentowner: dvenkate
source-git-commit: 864b1796f1ca99ae7b5643e8c58d1756ff2461a1
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---



# Learning Manager法規遵循GDPR

>[!IMPORTANT]
>
>本檔案的內容不是法律建議，且用意並非要取代法律建議。 請諮詢貴公司的法律部門，以獲取有關GDPR的建議。

+++什麼是GDPR？

GDPR是歐盟的新法規，於2018年5月25日生效。 它為資料隱私權提供強大的控制力，並可讓一般使用者自行掌控個人資料。

+++

+++它如何或為何適用於身為AdobeLearning Manager客戶的您？

雖然GDPR是歐盟法規，但適用於全世界的商業實體，以收集可能居住在歐盟的任何使用者的個人資訊。  身為Learning Manager客戶，請評估GDPR是否適用於您的組織。

+++

+++Adobe身為Learning Manager的供應商，在此扮演什麼角色？

根據GDPR，若您的企業向歐盟居民提供產品或服務，並決定如何以及為何要收集、追蹤及監控其資料，您即視為 [資料控制方](https://gdpr-info.eu/art-24-gdpr/). 作為AdobeLearning Manager客戶，如果您執行其中一項活動，即被視為資料控制方。

代表控制者處理資料的企業  [資料處理者](https://gdpr-info.eu/art-28-gdpr/). 身為雲端託管LMSAdobeLearning Manager的廠商，Adobe扮演資料處理者的角色。 以下是有關以下專案的更多詳細資料：  [GDPR與您的業務](https://www.adobe.com/privacy/general-data-protection-regulation.html).

+++

+++Learning Manager如何讓您符合GDPR？

Learning Manager已內建下列工具和流程，可協助您符合GDPR規定。 若要支援超出產品範圍的任何程式，以完全符合法規，您可能仍需要與合規團隊一起評估。

**立即忘記 — 連絡資料控制方：** GDPR要求資料控管單位為其使用者提供「忘記權利」功能。 這表示任何使用者都有權要求資料控管單位永久刪除為該使用者儲存的任何個人資料。 如果您收到這類請求，並進一步評估是否為有效請求，Learning Manager現在透過其提供此功能 [清除使用者](../administrators/feature-summary/purge-users.md) 功能。 此功能可讓管理員起始與特定個人相關之任何資料的永久刪除，在個人請求時，Learning Manager會立即從資料庫中硬性刪除資料，並且備份記錄的清除（用於系統復原）也將自動進行。

**立即忘記 — 連絡資料處理者：** 使用者也可以單獨聯絡Adobe以刪除其PII。 在這種情況下，Learning Manager會自動偵測擁有該使用者PII的帳戶，Adobe會立即將這類請求通知管理員。 然後，管理員可以評估請求的有效性，並透過「清除使用者」功能對請求進行呼叫。

**存取許可權：** GDPR允許一般使用者有權要求控制器可能已為該一般使用者儲存的資料。 為了支援此請求，Learning Manager可讓管理員自行產生學習者成績單，以便與使用者共用。

**設計隱私權、資料加密：** 我們使用同級最佳的加密標準來處理傳輸中及閒置中的資料，以確保資料安全性。 使用的加密演演算法為SHA-256。 這可確保您儲存的任何資料都受到適當保護，因此不會落入不法之徒手中。

+++

