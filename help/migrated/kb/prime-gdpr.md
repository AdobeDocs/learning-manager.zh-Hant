---
jcr-language: en_us
title: Learning Manager法規遵循GDPR
description: Adobe Learning Manager法規遵循GDPR
contentowner: dvenkate
exl-id: 8ea31464-b4ce-49e8-b471-5630f0216aa4
source-git-commit: a01ec6117ad49a1f9af0b31d48ad19ddc8443dde
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 0%

---

# Learning Manager法規遵循GDPR

>[!IMPORTANT]
>
>本檔案的內容不是法律建議，且用意並非要取代法律建議。 請諮詢貴公司的法律部門，以獲取有關GDPR的建議。

Adobe Learning Manager致力於GDPR法規遵循，確保以安全且透明的方式管理使用者資料。 它提供基本的GDPR功能，例如清除使用者（永久刪除所有個人資料）的功能，並可讓管理員產生學習者成績單，以便應要求與使用者共用資訊。

所有使用者資料在傳輸和儲存期間，均會使用SHA-256等標準以高度加密方式受到保護。 對於某些整合，學習者必須驗證，確保在共用任何資料前已獲得其同意。 這些隱私權與安全控制功能可協助使用Adobe Learning Manager的組織遵守GDPR規定，並保護學習者資訊。

+++什麼是GDPR？

GDPR是歐盟的新法規，於2018年5月25日生效。 它為資料隱私權提供強大的控制力，並可讓一般使用者自行掌控個人資料。

+++

+++您身為Adobe Learning Manager客戶，如何或為何需要使用此功能？

雖然GDPR是歐盟法規，但適用於全世界的商業實體，以收集可能居住在歐盟的任何使用者的個人資訊。  身為Learning Manager客戶，請評估GDPR是否適用於您的組織。

+++

+++Adobe身為Learning Manager的廠商，在此扮演什麼角色？

根據GDPR，如果您的企業向歐盟居民提供產品或服務，並決定如何以及為何要收集、追蹤及監控其資料，您即視為[資料控管單位](https://gdpr-info.eu/art-24-gdpr/)。 身為Adobe Learning Manager客戶，如果您執行下列其中一項活動，即視為資料控管單位。

代表控制者處理資料的企業視為[資料處理者](https://gdpr-info.eu/art-28-gdpr/)。 身為雲端託管LMS Adobe Learning Manager的廠商，Adobe扮演資料處理者的角色。 以下是[GDPR和您公司的更多詳細資料](https://www.adobe.com/privacy/general-data-protection-regulation.html)。

+++

+++Learning Manager如何讓您符合GDPR？

Learning Manager已內建下列工具和程式，可協助您符合GDPR規定。 若要支援超出產品範圍的任何程式，以完全符合法規，您可能仍需要與合規團隊一起評估。

**忘記的權利 — 連絡資料控制方：** GDPR要求資料控制方為其使用者支援「忘記的權利」功能。 這表示任何使用者都有權要求資料控管單位永久刪除為該使用者儲存的任何個人資料。 如果您收到這類要求，且進一步評估其是否為有效要求，Learning Manager現在會透過其[清除使用者](../administrators/feature-summary/purge-users.md)功能提供此功能。 此功能可讓管理員起始與特定個人相關之任何資料的永久刪除，在個人要求時，Learning Manager會立即從其資料庫中硬刪除資料，並且備份記錄的清除（用於復原系統）也將自動跟進。

**忘記的權利 — 連絡資料處理程式：**&#x200B;使用者也可以獨立連絡Adobe以刪除其PII。 在此情況下，Learning Manager會自動偵測哪些帳戶擁有該使用者的PII，而Adobe會將此要求立即通知管理員。 然後，管理員可以評估請求的有效性，並透過「清除使用者」功能對請求進行呼叫。

**存取許可權：** GDPR允許一般使用者有權要求控制器可能已為該一般使用者儲存的資料。 為了支援此請求，Learning Manager可讓管理員自行產生學習者成績單，以便與使用者共用。

**設計隱私權，資料加密：**&#x200B;我們使用同級最佳的加密標準，處理傳輸中及閒置的資料，以確保資料安全。 使用的加密演演算法為SHA-256。 這可確保您儲存的任何資料都受到適當保護，因此不會落入不法之徒手中。

+++
