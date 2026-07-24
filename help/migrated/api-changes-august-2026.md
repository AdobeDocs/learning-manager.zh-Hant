---
description: ALM 中的 API 變更
jcr-language: en_us
title: Adobe Learning Manager 2026 年 8 月版本的 API 變更
source-git-commit: 0862e0d042fac74377b44c3387a72336ec625161
workflow-type: tm+mt
source-wordcount: '3369'
ht-degree: 1%

---


# Adobe Learning Manager 2026 年 8 月版本的 API 變更

## Adobe Learning Manager 中的使用者群組管理 API

此版本新增三個管理員範圍的公開 API 端點，用於程式化管理自訂使用者群組。 你可以在不使用管理應用程式的情況下建立、重新命名和刪除自訂使用者群組，讓你能將群組管理自動化，作為身份或配置工作流程的一部分。

這些端點僅能與自訂使用者群組合作。 系統管理群組，如 All Users 群組與自動產生的使用者群組，API 回應中為 readOnly： 為真，且無法透過這些端點修改或刪除。

關於 API 認證要求，請參見 [Adobe Learning Manager API 認證](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/developer-manual#authentication-using-oauth-20)。

### 使用者群組 API 端點

這三個端點都需要一個帶有寫入權限（ROLE_ADMIN）的管理員存取權杖。

| **方法** | **路徑** | **運作** | **成功代碼** |
|---|---|---|---|
| 後期 | /primeapi/v2/userGroups | 建立自訂使用者群組 | 201 創立 |
| 賣權 | /primeapi/v2/userGroups/{id} | 更新團體名稱或描述 | 200 OK |
| 刪除 | /primeapi/v2/userGroups/{id} | 刪除自訂使用者群組 | 204 無內容 |

## **常見請求標頭**

三個端點都需要以下標頭。

```
Authorization: Bearer \<access-token\>
X-acap-user: \<user-id\>
X-acap-account: \<account-id\>
X-acap-caller-role: ROLE_ADMIN
Content-Type: application/vnd.api+json
Accept: application/vnd.api+json
```

### **建立使用者群組**

```
POST /primeapi/v2/userGroups
```

建立一個新的自訂使用者群組，並建立初始成員清單。 該群組可立即在管理應用程式中使用。

#### **請求機構**

```
{
  "name": "Marketing Team",
  "description": "Custom user group for marketing onboarding",
  "data": [
    { "type": "user", "id": "11282373" },
    { "type": "user", "id": "11282374" }
  ]
}
```

#### **請求參數**

| **參數** | **必修** | **類型** | **描述** |
|---------------|--------------|----------|-------------------------------------------------------------------------------------|
| 名稱 | 是的 | 字串 | 顯示團體名稱。 不能是空白或只有空白。 |
| 描述 | 不 | 字串 | 可選的團體目的說明。 |
| 資料 | 是的 | 陣列 | 初始成員名單。 至少1件，最多100件。 |
| data.type[] | 是的 | 字串 | 一定是「使用者」。 不接受其他資源類型。 |
| data.id[] | 是的 | 字串 | 數字使用者 ID 字串。 使用者必須屬於該帳號並擁有有效狀態。 |

> **注意：** 資料陣列僅在建立時用於設定初始成員清單。 建立後新增或移除成員時，請使用現有的使用者群組成員端點。

#### **回應201已建立**

```
{
  "links": {
    "self": "https://<host>/primeapi/v2/userGroups"
  },
  "data": {
    "id": "2769204",
    "type": "userGroup",
    "attributes": {
      "dateCreated": "2026-06-04T14:19:53.000Z",
      "description": "Custom user group for marketing onboarding",
      "name": "Marketing Team",
      "readOnly": false,
      "userCount": 2
    }
  }
}
```

#### **驗證規則 POST**

| **#** | **驗證** | **錯誤代碼** | **觸發** |
|-------|-------------------------------------------------------|----------------------------------------------------------|------------------------------------------------|
| 1 | 名字出現且非空白 | USERGROUP_CREATE_NAME_REQUIRED | 名稱省略或僅留白 |
| 2 | 資料中至少包含一名使用者 | USERGROUP_CREATE_USERS_REQUIRED | 資料缺失或空陣列 |
| 3 | 資料中用戶數不超過 100 人 | USERGROUP_USERS_MAX_LIMIT_EXCEEDED | 超過100個資料條目[] |
| 4 | 所有使用者 ID 皆為數字字串 | INVALID_USER_IDS | data.id 中非[]數字字串 |
| 5 | 所有使用者都存在於該帳戶中，且狀態為 ACTIVE（活躍） | INVALID_USER_IDS / USERGROUP_CREATE_USERS_NOT_IN_ACCOUNT | 使用者未找到或未啟用 |
| 6 | 帳號尚未達到自訂群組上限 | 400 | 自訂群組的帳號層級限制超過了 |

### **更新使用者群組**

```
PUT /primeapi/v2/userGroups/{id}
```

更新現有自訂使用者群組的名稱和/或描述。 此端點無法新增或移除群組成員。

任一欄位都可以省略;省略欄位則保持其當前值不變。 通過 null 來做描述就能清除。 傳遞空白字串作為名稱會被拒絕。

#### **請求機構**

```json
{
  "name": "Updated Group Name",
  "description": "Updated description text"
}
```

#### **請求參數**

| **參數** | **必修** | **類型** | **描述** |
|---------------|--------------|----------|---------------------------------------------------------------------------|
| 名稱 | 不 | 字串 | 新的顯示名稱。 若提供，則不得為空白。 省略，保持不變。 |
| 描述 | 不 | 字串 | 新的描述。 傳給無效以清除。 省略，保持不變。 |
| 資料 | — | null | 必須是無效或缺失。 任何非空值都會回傳 400 錯誤。 |

#### **回應：200 OK**

```
{
  "data": {
    "type": "userGroup",
    "id": "2767870",
    "attributes": {
      "name": "Updated Group Name",
      "description": "Updated description text",
      "readOnly": false,
      "state": "Active",
      "userCount": 3
    }
  }
}
```

#### **驗證規則 PUT**

| **#** | **驗證** | **錯誤代碼** | **觸發** |
|-------|-------------------------------------|----------------------------------------|----------------------------------------------------------|
| 1 | 資料為空或缺失 | USERGROUP_UPDATE_USERS_NOT_ALLOWED | 呼叫者傳遞非空資料嘗試變更成員 |
| 2 | 若提供名稱，則不為空白 | USERGROUP_UPDATE_NAME_BLANK | 名稱以僅留白字串形式傳送 |
| 3 | 本說法中存在該群體 | INVALID_USER_GROUP_ID | 未知 {id} 路徑參數 |
| 4 | 群組尚未被刪除 | DELETED_USERGROUP | 群組先前已被刪除 |
| 5 | 群組 readOnly 為假 | READ_ONLY_USERGROUP | 系統管理群組 |
| 6 | 群組是一種自訂（非系統）類型 | USERGROUP_UPDATE_OPERATION_NOT_ALLOWED | 系統內部群組類型 |

### **刪除使用者群組**

```
DELETE /primeapi/v2/userGroups/{id}
```

標記指定的自訂使用者群組為已刪除。 群組紀錄並不會永久移除——其狀態被設為 DELETED，這會讓它在管理應用程式中看不見，也無法在新設定中使用。 群組 ID 不可重複使用。

#### **請求範例**

```
DELETE /primeapi/v2/userGroups/2767870
Authorization: Bearer <access-token>
X-acap-user: <user-id>
X-acap-account: <account-id>
X-acap-caller-role: ROLE_ADMIN
```

#### **回應 204 無內容**

回應本體是空的。

> **注意：** DELETE 並非冪起位元。 向同一群組 ID 發送第二次 DELETE 請求時，會回傳 400 錯誤，並帶有 DELETED_USERGROUP 碼，而非 204。 將 400 的回覆DELETED_USERGROUP視為該群組已被刪除的確認。 不支援批量刪除;每個群組都需要獨立的 DELETE 請求。

#### **驗證規則刪除**

| **#** | **驗證** | **錯誤代碼** | **觸發** |
|-------|-------------------------------------|----------------------------------------|---------------------------------------------------|
| 1 | 本說法中存在該群體 | INVALID_USER_GROUP_ID | 未知 {id} 路徑參數 |
| 2 | 群組尚未被刪除 | DELETED_USERGROUP | 對已刪除狀態的群組重複 DELETE |
| 3 | 群組 readOnly 為假 | READ_ONLY_USERGROUP | 系統管理群組 |
| 4 | 群組是一種自訂（非系統）類型 | USERGROUP_UPDATE_OPERATION_NOT_ALLOWED | 系統內部群組類型 |

## Adobe Learning Manager 中的外部學習 API

此版本新增五個學習者範圍的 API 端點，作為外部學習功能。 這些端點允許學習者以程式化方式創建、檢索及更新外部學習提交，例如來自行動應用程式、整合人力資源系統或自訂學習入口網站。

透過 API 的外部學習工作流程與學習者應用程式的工作流程相呼應：學習者提交訓練細節及可選的證明文件，其直屬主管會收到審查提交的通知，經核准後，該紀錄會出現在學習者的成績單中。

五個端點皆為學習者範圍。 學習者只能存取自己的提交資料——若學習者嘗試存取其他學習者的資料，API 會回傳錯誤。

關於 API 認證要求，請參見 [Adobe Learning Manager API 認證](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/developer-manual#authentication-using-oauth-20)。

### 外部學習 API 端點

所有端點都需要學習者存取權杖（ROLE_LEARNER）。

| **方法** | **路徑** | **運作** | **成功代碼** |
|------------|---------------------------------------|----------------------------------|------------------|
| 去 | /primeapi/v2/externalLearningSettings | Fetch 帳戶表單配置 | 200 OK |
| 去 | /primeapi/v2/externalLearnings | 列出來電者的投稿 | 200 OK |
| 去 | /primeapi/v2/externalLearnings/{id} | 取一個提交 | 200 OK |
| 後期 | /primeapi/v2/externalLearnings | 建立一個新投稿 | 201 創立 |
| 賣權 | /primeapi/v2/externalLearnings/{id} | 更新待提交的文章 | 200 OK |

### 常見請求標頭

```
Authorization: Bearer <access-token>
X-acap-user: <user-id>
X-acap-account: <account-id>
X-acap-caller-role: ROLE_LEARNER
Accept: application/vnd.api+json
Content-Type: application/vnd.api+json (POST and PUT only)
```

### 服從狀態生命週期

| **現況** | **設定** | **意義** | **學習者可以更新嗎？** |
|------------|------------------|-----------------------------------------|-----------------------------|
| 待定 | 系統創建 | 等待經理審查 | 是的——透過 PUT |
| 核准 | 經理 | 已錄取;出現在學習者成績單中 | 否-PUT回報409 |
| 拒絕 | 經理 | 拒絕;附上評論評論 | 不——建立新的投稿 |

APPROVED 和 REJECTED 是末期狀態。 被拒絕的提交無法重新開啟;學習者必須重新創建新的提交。

### Fetch 帳戶表單配置

```
GET /primeapi/v2/externalLearningSettings
```

回傳帳戶層級表單設定。 在呈現提交表單前，先呼叫這個端點。 回應定義要顯示哪些欄位、哪些欄位是必須的、它們的資料型態，以及管理員設定的任何自訂欄位。

在繼續前請檢查頂層啟用屬性，若錯誤，表示該帳號的外部學習功能未啟用，提交端點將回傳錯誤。

#### 回應：200 OK

```
{
  "data": {
    "id": "8627",
    "type": "externalLearningSettings",
    "attributes": {
      "enabled": true,
      "updatedAt": "2026-06-05T06:51:20.000Z",
      "coreFields": [
        { "id": "title", "type": "TEXT", "mandatory": true, "editable": false, "order": 0 },
        { "id": "description_notes", "type": "TEXT", "mandatory": false, "editable": true, "order": 1 },
        { "id": "date", "type": "TIMESTAMP", "mandatory": false, "editable": true, "order": 2 },
        { "id": "score", "type": "NUMBER", "mandatory": true, "editable": true, "order": 3 },
        { "id": "duration", "type": "TEXT", "mandatory": false, "editable": true, "order": 4 },
        { "id": "attachments", "type": "FILE_UPLOAD", "mandatory": true, "editable": true, "order": 5 }
      ],
      "customFields": [
        {
          "id": "960369b2-...",
          "type": "NUMBER",
          "mandatory": true,
          "order": 0,
          "label": { "en_US": "Employee Code" }
        },
        {
          "id": "3c6cc6d9-...",
          "type": "DROPDOWN",
          "mandatory": true,
          "order": 1,
          "label": { "en_US": "Department" },
          "options": [
            { "option_id": "opt_1", "label": { "en_US": "IT" } },
            { "option_id": "opt_2", "label": { "en_US": "HR" } },
            { "option_id": "opt_3", "label": { "en_US": "FIN" } }
          ]
        }
      ]
    }
  }
}
```

#### 核心場域參考

| **欄位識別碼** | **類型** | **預設強制性** | **註釋** |
|-------------------|-------------|-----------------------|----------------------------------------------------------------------------------------------------------|
| 標題 | 文本 | 是的 | 訓練名稱。 永遠在場。 管理員無法停用。 |
| description_notes | 文本 | 不 | 自由文字描述或註解。 |
| 日期 | 時間戳記 | 不 | 日期範圍。 數值形狀：{ “start_date”： ”<ISO-Z>「，end_date」：<ISO-Z>&quot; }. 任一值皆為零值。 |
| 配樂 | 人數 | 是的 | 值形狀：{ “achieved_score”： <number>， 「max_score」： <number> }. 兩個值都必須是數字。 |
| 持續時間 | 文本 | 不 | 自由形式字串，例如「40 hours」。 |
| 附屬品 | FILE_UPLOAD | 是的 | 完成證明。 **不要** 在欄位[] 內傳遞——請使用頂層的 submissionUrl 屬性。 |

自訂欄位由管理員定義，並回傳於 customFields[]。 他們的識別碼、類型、必須的旗標、標籤和下拉選單會依帳號設定而異。

### 名單提交

```
GET /primeapi/v2/externalLearnings
```

回傳一個分頁的清單，列出已認證學習者自身提交的檔案，排序順序為 modifiedAt，遞減排序（最近修改者為先）。

#### **查詢參數**

| **參數** | **預設** | **極限** | **描述** |
|---------------|-------------|-------------|-------------------------------------------------------------------------------------------------------|
| 頁面[偏移] | 0 | 5000 | 零基紀錄偏移。 |
| 頁數[限制] | 10 | 100 | 每頁紀錄。 超過 100 的數值會靜默地被固定在 100。 |
| ls_qp_status | — | — | 依狀態篩選。 所有結果都省略。 有效值：待處理、批准、拒絕（不區分大小寫）。 |

#### **回應：200 OK**

```
{
  "links": {
    "next": "/primeapi/v2/externalLearnings?page[offset]=10&page[limit]=10"
  },
  "data": [
    { "id": "1001", "type": "externalLearning", "attributes": { "status": "PENDING", ... } },
    { "id": "1002", "type": "externalLearning", "attributes": { "status": "APPROVED", ... } }
  ]
}
```

### 取一個提交

```
GET /primeapi/v2/externalLearnings/{id}
```

回傳屬於認證學習者的單一提交完整紀錄。

#### **回應200 OK

```
{
  "data": {
    "id": "1001",
    "type": "externalLearning",
    "attributes": {
      "submissionUrl": "https://<cdn-url>/cert.pdf",
      "title": "Java Fundamentals Certification",
      "status": "PENDING",
      "creationSource": "LEARNER",
      "createdAt": "2026-04-14T08:30:00.000Z",
      "modifiedAt": "2026-04-16T11:45:00.000Z",
      "fields": [ "...resolved against live settings..." ]
    },
    "relationships": {
      "reviewerUser": { "data": null }
    }
  }
}
```

### 建立一個投稿

```
POST /primeapi/v2/externalLearnings
```

建立一個新的外部學習提交，處於待處理狀態。 帳戶設定中定義的所有必填欄位都必須包含。 成功完成POST後，學員的經理會收到平台內通知以審核提交。

### **檔案上傳**

附件欄位是獨立於其他欄位處理的。 不要把它放在田野[]裡。 取而代之的是：

&#x200B;1. 從 ALM 檔案上傳端點取得預先簽署的 S3 上傳網址。

&#x200B;2. 將檔案上傳到該網址。

&#x200B;3. 將您的 POST 請求中，將結果的 URL 作為頂層 submissionUrl 屬性傳遞。

#### **請求機構**

```
{
  "data": {
    "type": "externalLearning",
    "attributes": {
      "submissionUrl": "<pre-signed-upload-url>",
      "fields": [
        { "id": "title", "type": "TEXT", "value": "Java Fundamentals Certification" },
        { "id": "description_notes", "type": "TEXT", "value": "Completed via online course platform." },
        { "id": "date", "type": "TIMESTAMP", "value": { "start_date": "2026-05-01T00:00:00.000Z", "end_date": "2026-05-15T00:00:00.000Z" } },
        { "id": "score", "type": "NUMBER", "value": { "achieved_score": 88, "max_score": 100 } },
        { "id": "duration", "type": "TEXT", "value": "40 hours" },
        { "id": "960369b2-...", "type": "NUMBER", "value": "1225" },
        { "id": "3c6cc6d9-...", "type": "DROPDOWN", "value": "opt_3" }
      ]
    }
  }
}
```

#### 場值形狀

| **場型** | **值形狀** | **範例** |
|----------------|---------------------------------------------------------|----------------------------------------------------------------|
| 文本 | 弦 | 「Java 基礎」 |
| 人數 | 帶有achieved_score和max_score的物件 | {「achieved_score」：88，「max_score」：100 } |
| 時間戳記 | 具有start_date與end_date的物件（ISO 8601，或空） | { “start_date”： “2026-05-01T00:00:00.000Z”， “end_date”： null } |
| 下拉選單 | option_id 帳號設定的字串 | 「opt_3」 |
| FILE_UPLOAD | 不允許在欄位[] 內輸入 — 請使用 submissionUrl | — |

#### 驗證規則 POST

| **#** | **驗證** | **觸發** |
|-------|-----------------------------------------------------------------|----------------------------------------------------------|
| 1 | 該帳號已啟用外部學習功能 | 功能標誌已停用 |
| 2 | 所有必填欄位皆存在於欄位中[] | 必須欄位省略 |
| 3 | 每個欄位的 ID、類型和值形狀都與帳號設定相符 | 錯誤型別或錯誤的值物件 |
| 4 | FILE_UPLOAD類型在場內不存在[] | 附件是放在欄位[] 內寄出，而不是 submissionUrl |
| 5 | submissionUrl 是一個有效的 S3 預簽名 URL | 建立時拒絕的 CDN URL 與非 S3 URL |
| 6 | 當 attas.mandatory 為真時，submissionUrl 存在 | 附件是必須的，但缺少 submissionUrl |

### 更新提交

```
PUT /primeapi/v2/externalLearnings/{id}
```

更新現有待處理的提交。 只有待處理的投稿才能更新。 嘗試輸入已批准或拒絕提交時，會回傳 409 錯誤。

**此端點使用全替換語意。** 在每個 PUT 請求中提供完整的欄位[] 陣列，而不只是你要更改的欄位。 陣列中被遺漏的欄位會被清除。

#### 學習者可更新的欄位

| **欄位 / 屬性** | **學習者可以更新** | **註釋** |
|-----------------------|------------------------|----------------------------------------------------------------------------|
| 場[] | 是的 | 完全替換——包含所有欄位，而非僅更改過的欄位 |
| 投稿網址 | 是的 | PUT接受CDN URL;僅在POST中要求S3預先簽署的URL。 |
| reviewerUserID | 不 | 由管理者動作設定;唯讀給學習者 |
| 評論於 | 不 | 由管理者動作設定;唯讀給學習者 |
| 評論者評論 | 不 | 由管理者動作設定;唯讀給學習者 |
| 現況 | 不 | 由經理控制：待處理→批准或拒絕 |
| 創作來源 | 不 | API 建立的提交 Always LEARNER |
| 創造於 | 不 | 設定在創建時間;不可變 |

#### 請求機構

```
{
  "data": {
    "type": "externalLearning",
    "attributes": {
      "submissionUrl": "<cdn-url>/cert-v2.pdf",
      "fields": [
        { "id": "title", "type": "TEXT", "value": "Java Fundamentals — Updated" },
        { "id": "description_notes", "type": "TEXT", "value": "Updated notes." },
        { "id": "date", "type": "TIMESTAMP", "value": { "start_date": null, "end_date": null } },
        { "id": "score", "type": "NUMBER", "value": { "achieved_score": 92, "max_score": 100 } },
        { "id": "duration", "type": "TEXT", "value": "42 hours" },
        { "id": "960369b2-...", "type": "NUMBER", "value": "1227" },
        { "id": "3c6cc6d9-...", "type": "DROPDOWN", "value": "opt_2" }
      ]
    }
  }
}
```

## LT 中學習者相關認證 ID 與根認證 ID 的 API

當持續認證更新時，Adobe Learning Manager 會建立新版本的認證，並自動為活躍學習者報名。 如果你的整合直接查詢認證資料，而非依賴 Adobe Learning Manager 學習者體驗，你可以利用此 API 精確判斷某個持續認證版本在特定學習者特定時間點相關。

### API 的目的

定期認證每次續期都會產生新的認證 ID。 在原生的 Adobe Learning Manager 學習者體驗中，只會顯示每位學習者相關的版本。 舊版本一旦學習者切換到新版本，就會自動隱藏。

如果您的整合獨立取得認證資料，例如為了在外部入口網站上顯示認證資訊，可能不會自動套用此過濾。 若無此證照，學習者可能會看到所有歷史版本的重複認證，包括已不再相關的版本，卻無法判斷該依據哪個版本行動。

這個 API 就填補了這個缺口。 給定根認證 ID，它會回傳適用於特定學習者的認證版本，並考慮其註冊歷史及任何重複認證。

### 了解認證的重複性

當認證設定為重複驗證時，每次續期都會產生一個具有獨特 ID 的新認證版本。 所有版本都追溯到單一 **根憑證 ID，即** 原始憑證創建時的 ID。

例如，每月重複的認證可能會隨時間產生一連串版本，當重複間隔達到時，每個新版本都會自動產生。 當重複發生時，積極註冊的學習者將自動被納入新版本。

由於每個版本都有不同的 ID，學習者的相關版本會依其個別的註冊時間軸而定：

- 在復發前註冊並在下一次復發前完成認證的學習者，隨時間會經歷多個版本。

- 在重複課程週期中途註冊的學習者，將直接註冊到其註冊時的最新版本。

### 確定相關的認證版本

使用認證版本 API 來識別哪個版本的重複認證與特定學習者相關。

輸入 **是根認證 ID** 。 API 會評估學習者的註冊歷史，並根據以下規則回傳相應版本：

| **學習者狀態** | **API 回傳的內容** |
|--------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| 學習者尚未註冊認證 | 最新版本的認證 |
| 學習者目前已註冊 | 學習者目前所就讀的具體版本，並考慮自原始註冊以來發生的任何重複性事件 |

這表示兩個學習者同時查詢相同的根認證 ID，可能會根據各自的註冊歷史獲得不同的結果。

**注意**：在新版本建立及註冊遷移期間，可能會有短暫的視窗，API 可能會回傳即將取代的版本，而非新建立的版本。

**範例**

以每月重複的認證為例，因為連續重複，已產生四個版本：

- 在第一個版本註冊並隨著每次重複進行進行的學習者，將被返回他們目前活躍的版本，反映其完成與重複歷史，而不一定是目前存在的最新版本。

- 尚未註冊的學習者將被返回最新建立的版本，因為新註冊者應加入該版本。

這讓整合系統能始終引導學習者前往與其相關的認證版本，而不必展示所有歷史版本或猜測適用哪一個。

### API 參考

**取得根認證所需的相關認證**

```
GET /primeapi/v2/learningObjects/{loId}/applicableCertification
```

解析依據根認證 ID 的 ID，適用於目前學習者的認證版本。 對於已註冊的學習者，此系統會回傳他們目前所註冊的版本。 對於未註冊的學習者，此系統會回傳最新的有效版本。

| **財產** | **價值** |
|----------------------------------------------------------|--------------------------|
| **範圍** | 學習者閱讀存取 |
| **速率限制（標準學習者通話）** | 每分鐘70個請求 |
| **速率限制（提升或管理員級 API 憑證）** | 每小時500次請求 |
| **回應格式** | application/vnd.api+json |

**注意**：此 API 一次會回傳單一學習者的版本資訊。 它不會回傳所有版本認證的清單。

**路徑參數**

| **參數** | **必修** | **類型** | **描述** |
|---------------|--------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 低音 | 是的 | 字串 | 學習物件的 ID，特別是被請求適用版本的根憑證。 此需取得標準存取權限。 |

**查詢參數**

| **參數** | **必修** | **類型** | **描述** |
|---------------|--------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 包括 | 不 | 字串 | 一份逗號分隔的相關模型清單，應與已解決的認證一同包含在回應中，例如子貸款組（subLO）或註冊（enrollment）。 使用與其他 Adobe Learning Manager 學習物件端點相同的包含語法。 |

**範例請求**

```
GET /primeapi/v2/learningObjects/certification%3A167658/applicableCertification?include=subLOs
Accept: application/vnd.api+json
Authorization: oauth <access-token>
```

```
curl -X GET --header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
'https://<host>/primeapi/v2/learningObjects/certification%3A167658/applicableCertification?include=subLOs'
```

**注意**：loId值必須以URL編碼。 認證 ID 中的冒號（如 certification：167658）編碼為 %3A。

**範例回應 200 OK**

回應使用與標準學習物件回應相同的結構，回傳已解決的認證。

**重要提示：**&#x200B;回應中的 ID 欄位是已解決&#x200B;**認證**&#x200B;的 ID，即適用於此學習者的具體版本。它通常會和你輸入的 root 認證 ID 不一樣，因為這個 API 的目的就是把 root ID 轉換成正確的目前版本。

```
{
  "data": {
    "id": "string",
    "type": "string",
    "attributes": {
      "authorNames": [
        "string"
      ],
      "bannerUrl": "string",
      "catalogs": [
        ...
      ]
    }
  }
}
```

**回應代碼**

| **現況** | **意義** |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 200 | 相關認證已成功解決，並作為回應被退還。 |
| 400 | 所提供的 loID 要麼不是認證，要麼不是根認證。 把原始認證的 ID，而不是重複版本，當作 loId。 |
| 401 / 403 | 請求缺少有效的學習者憑證，或憑證沒有所需的存取權限。 |
| 404 | 此根憑證無法解決任何有效認證問題。 例如，因為鏈中每個版本都已被退休或刪除，或是該認證根本沒有記錄的根憑證參考。 如果某版本成功解決，但呼叫學習者無法存取該版本，也可能發生 404。 |
| 500 | 在解決認證時發生了意外的伺服器錯誤。 請重試該請求;如果錯誤依舊，請聯絡客服。 |

**錯誤回應範例**

```
{
  "meta": {
    "error": "string",
    "detail": "string"
  }
}
```

**注意：** 此 API 每次呼叫可解析一名學習者的版本。 它不會回傳根憑證所有版本的清單。

**重要重點**

- **非定期認證：如果你**&#x200B;通過的 loId 認證沒有設定為重複認證，API 會自行回傳該認證。

- **跳過中間版本：**&#x200B;如果學習者的有效註冊直接從早期版本移到較新的版本，且中間沒有有效註冊，API 仍會正確解析為學習者的實際當前版本。 學習者未積極參與的中間版本不會影響解決方法。

- **已刪除與退休認證：** 已刪除的認證版本將完全排除在解決方案之外。 已退休的認證仍可能依州不同而被考慮;若您依賴特定版本仍可解決，請確認其現況，而非僅憑退休即排除其考慮資格。

- **解析是確定性的：** 如果學習者的註冊資料處於不一致狀態（例如多個註冊被標記為目前），API 會解析到最近建立的版本，而非回傳不可預測的結果或錯誤。

**注意**：目前尚無管理員權限的 API 等效版本，正在評估未來版本。

### 在你的整合中使用這個 API

一個常見的使用案例是外部頁面或入口網站，列出學習者可存取的認證。 而不是直接連結到特定的認證 ID，因為該認證在重複驗證後可能會過時。 用根認證 ID 連結，並在學習者選擇正確版本時解析。

在你的整合中 1.Store 或參考認證，使用 **根認證 ID，也就是** 認證最初建立時的 ID，且在重複出現之前。

&#x200B;2. 當學習者選擇要查看或執行某項認證時，呼叫 GET /primeapi/v2/learningObjects/{loId}/applicableCertification，並將根認證 ID 傳遞為 loId。

&#x200B;3. 利用回應中回傳的認證版本，引導學習者前往正確的目的地，無論是註冊行動或是目前進度的檢視。

這確保學習者始終會選擇與其實際註冊及進度相符的認證版本，即使認證會隨時間重複出現並產生新版本。

## 報告：學習者成績單中的根訓練 ID

**根訓練 ID** 欄位預設在所有帳號的學習者成績單中可用。

| **行類型** | **根訓練 ID 值** |
|-----------------------------------------------------------------|--------------------------------------------------------------------------------|
| 認證設定為重複發放 | 這個版本追蹤的根認證 ID |
| 認證未設定為重複驗證 | 該列的訓練 ID 值相同 |
| 嵌入證照中的課程 | 是父認證的根認證 ID，不是課程本身的 ID |
| 一個不屬於任何認證的課程或學習路徑 | 該列的訓練 ID 或嵌入式課程 ID 值相同 |

**注意**：對於擁有大量認證的大型帳戶，學習者成績單中的根訓練ID值會分批解析。 這不會影響資料的準確性，但非常龐大的逐字稿產生時間可能會更長。

此欄位讓您能將學習者在每個版本的重複認證中的完整歷史歸類並報告，而非將每次重複視為無關且獨立的紀錄。 每次重複仍會以獨立一列出現在學習者成績單中。 根訓練識別碼欄位僅用來標示哪些列屬於同一底層認證。

**注意：** 當你需要追蹤學習者在重複認證中的完整參與歷史時，請使用根訓練 ID 欄位。

