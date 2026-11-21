---
description: 了解 Adobe Learning Manager 如何利用 NRPS 將 LTI 1.3 平台的自訂學習者屬性同步到學習者檔案中作為活動欄位
jcr-language: en_us
title: NRPS 的 LTI 支援
exl-id: 4c972319-b8ce-4f2d-9ccb-1b93c6cc6ac0
source-git-commit: 92be9eb8ece6d083efe595894a492540cd96eead
workflow-type: tm+mt
source-wordcount: '1845'
ht-degree: 0%
---

# NRPS 的 LTI 支援

## 概觀

Adobe Learning Manager 支援名稱與角色配置服務（NRPS）規範，當它作為學習工具互通性（LTI）1.3 工具時。 當學習者從外部學習管理系統（平台）啟動 Learning Manager 時，Learning Manager 會從平台擷取學習者的會員紀錄。 接著，它會將該紀錄中的自訂屬性，例如部門或員工編號，複製到學習者的個人檔案中作為啟用欄位。

## 使用案例

* **自動豐富學習者檔案。** 無需手動輸入資料或單獨匯入，即可將部門、員工編號或自訂元資料等屬性從您的平台導入 Learning Manager。
* **分析你的學習者來自何處。** 擷取地理位置屬性，例如國家與城市，以建立學習者來自哪些地理的全貌。 在 Learning Manager 中使用產生的個人檔案欄位進行分析。
* **保持個人資料資料與來源平台對齊。** 平台依然是真相的來源。 Learning Manager 每次學習者啟動時都會刷新數值。
* **在同一帳戶中支援多個平台。** 命名空間前綴會將不同平台的屬性分開使用，即使這些平台使用相同的屬性名稱。

使用 NRPS 自訂欄位同步時，Learning Manager 在啟動時會執行以下操作：

1. 偵測平台是否支援 NRPS。
2. 從平台請求啟動學習者的會員紀錄。
3. 從該記錄中擷取自訂屬性。
4. 將學習者個人資料中的屬性寫入為活動欄位。 每個欄位名稱都帶有 `<namespace>` 前綴，因此來自不同平台的屬性不會互相碰撞。
5. Learning Manager 會重複使用它已用於作業與成績服務（AGS）的 OAuth 2.0 用戶端憑證。 您不需要設定新的令牌端點。

>[!NOTE]
>
>NRPS 是 LTI Advantage 中的一項選配規格。 對 NRPS 及自訂屬性的支援因平台而異。 在計劃使用此功能之前，請確保您的平台已公開 NRPS 2.0。

## 主要特色

* **支援 NRPS 聲明：** Learning Manager 會檢查每次 LTI 1.3 啟動是否包含 NRPS 聲明。 若申請缺失，啟動將正常進行，無錯誤且不影響學習者。
  * 本聲明提供以下資訊：
    * **會員端點：**`context_memberships_url `識別學習者啟動 ALM 所依據課程或學習環境的服務 URL。
    * **支援版本：**`service_versions`列出該端點可用的 NRPS 版本。
      此功能支援 NRPS 2.0。
  * **共享憑證基礎架構：** Learning Manager 將 NRPS 範圍新增至現有的 AGS 憑證請求，並重複使用現有的每次註冊憑證快取。
* **將自訂參數同步至學習者設定檔**
  * **命名空間前綴的活動欄位：** 每個自訂屬性對應到名為 `<namespace>_<field_name>`的活動欄位。
  * **自動建立欄位：** 若不存在匹配的活動欄位，Learning Manager 會建立一個類型為 **文字** 、狀態 **為「Active**」的欄位。
  * **平台作為真實來源：** Learning Manager 會用平台最新的值覆蓋現有的個人檔案值。 學習者與管理員無法編輯這些欄位。
  * **非阻塞行為：** NRPS 錯誤不會阻止學習者啟動學習內容。
  * **自訂屬性的多重來源：** Learning Manager 可從 NRPS 端點及 LTI 啟動令牌中的自訂參數讀取自訂屬性。 了解更多關於 [啟動代幣](#custom-attributes-in-the-launch-token)中的自訂屬性。

## 支援的配置

| 商品 | 支援 |
|----------------------------------------------------------------|--------------------------------------------------------------------------|
| Learning Manager 角色 | LTI 1.3 工具 |
| LTI 版本 | LTI 1.3 |
| NRPS 服務版本 | 2.0 |
| 平台（符合規範的自訂欄位格式） | Moodle、D2L Brightspace、Blackboard（選集版）、Sakai |
| 自訂欄位類型 | 文字 |
| 觸發點 | 每次 LTI 1.3 的發射 |

平台支援取決於 NRPS 成員紀錄中使用的自訂欄位序列化模式。 多個模式可以共存，但 Learning Manager 只會處理目前版本中支援的模式。

## 運作方式

### 發射流程

1. 學習者從平台啟動 Learning Manager。
2. Learning Manager 讀取了 LTI 1.3 啟動令牌中的 NRPS 聲明。 如果聲明列出 NRPS 服務版本 2.0，Learning Manager 會儲存該工作階段及 LTI 情境（課程）的版本 `context_memberships_url` 。
3. Learning Manager 要求包含 NRPS 範圍 `https://purl.imsglobal.org/spec/lti-nrps/scope/contextmembership.readonly`的存取權杖。
4. Learning Manager 使用持有人令牌呼叫 `context_memberships_url?rlid=<lti_user_id>` 以擷取啟動學習者的紀錄。 如果平台忽略篩選 `rlid` 並回傳完整名冊，Learning Manager 會透過 `user_id`找到該學習者。
5. Learning Manager 會從記錄中擷取自訂欄位。
6. Learning Manager 會將每個自訂欄位對應到一個活動欄位，並將這些值寫入學習者的個人檔案。
7. 另外，ALM 也支援擷取自訂參數，並在工具啟動時同步至學習者設定檔，前提是自訂參數前綴為 ALM 可識別欄位 `ALMfield`。

### 自訂欄位格式

NRPS 2.0 規範將自訂資料定義為成員記錄中的陣 `message` 列。 Learning Manager 會讀取該陣列內 LTI 自訂聲明的自訂資料。 在此版本中，Learning Manager 支援符合規範的 Pattern S 表示方式。

```json
{
  "user_id": "abc123",
  "message": [
    {
      "https://purl.imsglobal.org/spec/lti/claim/custom": {
        "department": "Engineering",
        "employee_id": "E4567"
      }
    }
  ]
}
```

### 啟動令牌中的自訂屬性

平台也可以將自訂屬性作為自訂參數傳送到 LTI 啟動令牌中。 Learning Manager 會從啟動代幣與 NRPS 端點收集屬性，並將其儲存在學習者設定檔中。

對於啟動權杖中的屬性，參數名稱必須以 Learning Manager 所要求的前綴 `almfield-` 開頭。 若沒有前綴，Learning Manager 無法將這些參數與其他自訂參數區分，也無法匯入。 從 NRPS 端點擷取的屬性不需要此前綴。 只有當 ALM 的啟動權杖匯入自訂參數以識別應同步至學習者活動欄位時，才需要此前綴。

>[!NOTE]
>
>在您設定平台自訂參數前，請先與您的 Learning Manager 代表確認所需的精確前綴。

### 主動欄位命名與對應

Learning Manager 會將作用中欄位名稱建立為 `<namespace>_<field_name>`。 例如， `department` 命名空間 `https://purl.imsglobal.org/spec/lti/claim/custom` 中的欄位會變成 `https://purl.imsglobal.org/spec/lti/claim/custom_department`。

Learning Manager 套用以下規則：

* **名稱長度：** 若名稱超過目前的欄位名稱字元限制，Learning Manager 會先縮短命名空間部分，並保留欄位名稱。
* **名稱衝突：** 縮短後，Learning Manager 會檢查與來自不同來源的現有活動欄位是否有衝突。 若存在衝突，它會調整縮短長度，直到找到唯一的名稱為止。 如果找不到唯一名稱，它會跳過該欄位並記錄錯誤。
* **匹配：** 欄位名稱的匹配不區分大小寫。
* **現有且已啟用欄位：** Learning Manager 會將該值寫入學習者的個人檔案。
* **現有且停用欄位：** Learning Manager 會跳過該欄位而不記錄錯誤。
* **無現有欄位：** Learning Manager 會建立&#x200B;**一個狀態**&#x200B;為「啟用&#x200B;**」的文字**&#x200B;欄位。

### 將數值寫入設定檔

* 在每次啟動時，Learning Manager 擷取 NRPS 資料時，會將所有解析的自訂欄位值寫入啟動學習者的設定檔。 其他學習者設定檔不會被更改。
* 如果欄位已有某個值，Learning Manager 會以平台中最新的值覆蓋該欄位。
* 如果平台值為空或為空，Learning Manager 會保留現有的設定檔值。
* 未寫入某個欄位不會阻礙啟動或其他欄位的寫入。
* Learning Manager 會在可能的情況下，將欄位更新套用在同一啟動交易中。
* 學習者無法編輯其個人頁面上的 NRPS 來源欄位，管理員也無法代表學習者編輯這些數值。

## 設定 NRPS 自訂欄位同步

### 先決條件

* 您的平台已註冊為 LTI 1.3 工具，註冊於 Learning Manager。 此功能不支援 LTI 1.1 或 LTI 1.2。
* 您的平台支援 NRPS 服務版本 2.0，並以符合 `message` 規範的格式公開自訂屬性。
* LTI 啟動代幣包含該 `namesroleservice` 聲明。
* 該聲明提供 `context_memberships_url`，用以識別課程專屬的 NRPS 端點。
* `service_versions`聲明中的值包含 `2.0`。
* 您擁有平台工具註冊的管理員權限。

### 將 NRPS 範圍授予 Learning Manager

包含 NRPS 範圍的新註冊不需要在 Learning Manager 中進行額外設定。

包含 NRPS 範圍的新註冊在 Learning Manager 中無需進一步變更即可運作。 對於現有的註冊，平台管理員必須在平台端更新工具註冊。

>[!NOTE]
>
>你不需要在 Learning Manager 中更改令牌端點、客戶端 ID 或私鑰。 現有的 AGS 配置會被重複使用。 如果平台未授予 NRPS 範圍，Learning Manager 會跳過 NRPS，而不影響 AGS 或啟動。

### 在平台上顯示學習者屬性

平台控制其分享的學習者屬性。 具體步驟會依平台而異。 例如，在 Moodle 中：

1. 使用 LTI 1.3 將 Learning Manager 新增為外部工具。
2. 啟用允許平台與工具共享學習者資訊的隱私設定。
3. 定義您想要傳送的自訂屬性。 您可以使用平台變數或預先定義的值。
4. 如果您也在啟動令牌中以自訂參數形式傳送屬性，請在每個參數名稱後加入 Learning Manager 所需的前綴。

>[!NOTE]
>
>只公開學習使用情境所需的屬性。 Learning Manager 將平台視為真實來源，並未在本版本中提供獨立的同意或隱私控制。

### 驗證同步

1. 以測試學習者身份從平台啟動 Learning Manager。
2. 確認發射已正常完成。
3. 在 Learning Manager 管理應用程式中，開啟「活動欄位」頁面。
4. 確認欄位是否以命名空間前綴出現，類型為 **Text，狀態**&#x200B;為 Active ****。
5. 開啟測驗學習者的個人檔案，並確認數值是否與平台相符。
6. 確認 NRPS 來源欄位為唯讀。 學習者與管理員皆無法手動編輯已同步的值。
7. 在更改非空來源值後重新啟動，並確認 Learning Manager 是否以最新的 NRPS 值覆蓋現有設定檔值。

>[!TIP]
>
>如果欄位存在但已停用，Learning Manager 不會寫入該欄位。 如果你想填入該欄位，請啟用它。

## 錯誤處理與記錄

Learning Manager 從不會因為 NRPS 問題而封鎖學習者。 它不會重試。 它會記錄失敗，並跳過該啟動時的 NRPS 同步。 下一次發射再次嘗試。

| 狀況 | 結果 |
|------------------------------------------------------------------|-------------------------------------------------------|
| NRPS 聲明在啟動代幣中缺失 | NRPS 被跳過了。 發射繼續進行。 |
| 目前僅有 NRPS 服務版本 1.0 | NRPS 被跳過了。 發射繼續進行。 |
| 令牌請求失敗或平台未授予 NRPS 範圍 | NRPS 被跳過了。 AGS和發射都沒有受到影響。 |
| NRPS 呼叫失敗（逾時、4xx 或 5xx） | 錯誤已記錄。 發射繼續進行。 |
| 在 NRPS 回應中找不到 Learner | 現場同步被跳過。 發射繼續進行。 |
| NRPS 回應中沒有自訂欄位 | 欄位同步會被跳過且不會出現錯誤。 |
| 欄位名稱衝突無法解決 | 該欄位會被跳過並記錄錯誤。 |
| 單一欄位寫入失敗 | 其他欄位仍然會被寫入。 發射繼續進行。 |

每個日誌條目包含時間戳記、平台註冊 ID、學習者 ID 及失敗原因。 Learning Manager 系統管理員可以存取這些日誌。

## 筆記

* 只有啟動學習者的紀錄會同步。 Learning Manager 不會同步完整的課程名單。
* 僅支援 NRPS 服務版本 2.0。
* 所有同步欄位的類型 **為 Text**。 Learning Manager 不會從數值推斷類型。 不支援數字、日期及布林欄位類型。
* Learning Manager 充當 LTI 工具。 它不作為 NRPS 平台，也沒有提供其他工具的名單端點。
* 自訂欄位同步會在 LTI 啟動時進行。
