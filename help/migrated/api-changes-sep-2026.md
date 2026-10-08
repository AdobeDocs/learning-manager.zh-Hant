---
description: 公開且面向學習者的 API 端點，用於在 Adobe Learning Manager 中列出、檢索、註冊及刪除個人化學習路徑，以及 API 端點，用以檢查是否透過指派給學習者的目錄直接存取一個或多個學習物件。
jcr-language: en_us
title: 2026 年 9 月的 API 變更
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '1374'
ht-degree: 1%
---

# 2026 年 9 月 Adobe Learning Manager 版本中的 API 變更

## 用於檢查學習物件目錄存取的 API

判斷目前學習者是否擁有直接目錄存取一個或多個學習物件的權限，無論學習者是否透過學習路徑或認證取得該內容。

### API 的目的

當學習者開啟學習路徑或認證時，他們可以瀏覽其中的各個課程，即使特定課程並非透過目錄直接分配給他們。 這有助於內容發現：學習者可以在決定是否繼續前，先探索學習路徑的內容。

然而，能夠以這種方式查看課程，並不代表學習者可以自動註冊。 報名應依學習者是否擁有該特定課程的直接目錄存取權，而非僅透過包含學習路徑的間接存取權。

這個 API 讓你能檢查特定學習者是否能直接透過指派給他們的目錄存取一個或多個學習物件。 利用結果控制與註冊相關的使用者介面，例如只有在確認直接目錄存取時才顯示註冊選項，同時在兩種情況下都保持課程頁面本身可瀏覽。

### 終點

`GET /primeapi/v2/learningObjects/isMemberOfVisibleCatalogs`

| 財產 | 價值 |
|---|---|
| **範圍** | 學習者閱讀存取 |
| **回應格式** | application/vnd.api+json |

### 查詢參數

| 參數 | 必修 | 類型 | 說明 |
|---|---|---|---|
| 識別碼 | 是的 | 字串或陣列 | 一個或多個學習物件 ID 需要檢查。 接受單一 ID 或逗號分隔清單。 每個請求最多可輸入 10 個 ID。 |

### 範例請求

```
GET /primeapi/v2/learningObjects/isMemberOfVisibleCatalogs?ids=course%3A2400159%2Ccourse%3A2400160%2Ccourse%3A2400161%2Ccourse%3A2400162
Accept: application/vnd.api+json
Authorization: oauth <access-token>
```

>[!NOTE]
>
>學習物件 ID 必須以 URL 編碼。 像 course：2400159 這類 ID 中的冒號編碼為 %3A，多個 ID 之間的逗號編碼為 %2C。

### 範例回應 - 200 OK

```json
{
  "course:2400162": false,
  "course:2400161": false,
  "course:2400160": true,
  "course:2400159": true
}
```

| 價值 | 意義 |
|---|---|
| 沒錯 | 呼叫學習者可直接存取此學習物件的目錄。 |
| 錯誤 | 學習對象並不會直接透過目錄直接提供給呼叫的學習者。 如果學習者能透過他們所取得的學習路徑或認證取得，仍可能查看該資訊。 |

### 回應代碼

| 現況 | 意義 |
|---|---|
| 200 | 這個請求成功了。 回應包含每個請求 ID 的結果。 |
| 400 | 一個通用的錯誤請求錯誤。 例如，提供超過10份身分證，或有身分證出現畸形。 |
| 401 | 請求缺少有效的學習者憑證，或因憑證無效而被拒絕存取。 |

### 錯誤回應範例

```json
{
  "status": "BAD_REQUEST",
  "title": "Bad request. Check url, params and headers",
  "source": {
    "info": "Either LO id is blank or not as per public api specification"
  }
}
```

### 在你的整合中使用這個 API

一個常見的使用案例是學習者透過從學習路徑導航到的課程頁面。 你希望課程頁面本身保持可開啟，只有在學習者擁有該課程目錄的直接存取權時才顯示 **「註冊** 」操作。

1. 當課程頁面載入時，呼叫這個端點並使用課程的學習物件 ID。
2. 如果該 ID 的回應為真，請顯示 **「註冊** 」選項。
3. 如果回覆是 false，請保留課程頁面、標題、描述和課程細節可看，但請隱藏「 **註冊** 」選項。

## 行政審計追蹤報告職缺 API {#apiaudittrailreport}

### API 的目的

管理員稽核追蹤報告列出對Adobe Learning Manager 帳號。 例如，對基礎、整合的變更，或在特定日期範圍內的進階帳號設定。 產生稽核追蹤報告需要查詢並彙整所請求日期範圍與設定類型的設定變更紀錄。 根據範圍大小及變更量，這可能超過同步 HTTP 請求的時間限制，可能導致用戶端或閘道逾時。

為避免此問題，報告透過通用的工作 API 非同步產生：

1. **創造一份工作。** 管理員會提交請求，指定報告類型、日期範圍及設定類型。 API 會立即回傳工作 ID，無需等待報告編譯完成。

2. **調查工作內容。** 管理員會定期透過 ID 檢索工作以檢查狀態。 當工作完成時，回應會包含結果，或是對其的參考。

### 基礎網址與慣例

| 項目 | 價值 |
|---|---|
| 基底路徑 | `/primeapi/v2` |
| 內容類型 | `application/vnd.api+json;charset=UTF-8`（JSON）:API |
| Authentication | 持有人 OAuth 代幣，範圍限定給帳戶管理員 |
| 帳號背景 | `x-acap-account` 標頭識別呼叫管理員的帳號 |
| 民調 | 不強制執行固定間隔;輪詢取得工作狀態端點直到`status`不再或`QUEUED`&#x200B;`IN_PROGRESS` |

### 身分證

當建立工作時， `id` 回傳的工作是一個不透明的字串（例如，
`4593`). 務必將你從創作中獲得的確切 `id` 金額回傳在查詢狀態時的回應。 永遠不要建構或解析它。

### 認證範圍

每個端點都需要一個帶有以下範圍的 OAuth 標記，且撥打電話的使用者必須持有帳戶管理員角色：

- `admin:write` 建立一份報告工作（`ROLE_ADMIN` 必須）
- `admin:read` 閱讀工作狀態與結果（`ROLE_ADMIN` 必讀）

來電者未持有 `ROLE_ADMIN` 該帳戶的請求包括被拒絕;參見 [錯誤處理](/help/migrated/api-changes-sep-2026.md#error-handling)

### 終點

#### 建立審計追蹤報告工作

`POST /primeapi/v2/jobs`

建立一個非同步工作，產生設定變更稽核追蹤報告針對給定的日期範圍和場景類型。 回應立刻回來在狀態下有工作資源 `QUEUED` ;報告本身則以背景。

範圍： `admin:write`

| 參數 | 在 | 必修 | 說明 |
|---|---|---|---|
| `jobType` | 身體 | 是的 | 一定是 `generateConfigChangeAuditReport` 為了這份報告 |
| `payload.fromDate` | 身體 | 是的 | 例如，報表視窗的開始，ISO-8601 帶有偏移 `2026-09-15T00:00:00.000+05:30` |
| `payload.toDate` | 身體 | 是的 | 舉例來說，報表視窗結束時，ISO-8601 帶有偏移量 `2026-09-23T23:59:59.000+05:30` |
| `payload.settingTypes` | 身體 | 是的 | 一個或多個設定類別的陣列，包含：支援的值為 `Basics`、 `Integrations`、 `Advanced` |

範例請求主體

```json
{
  "data": {
    "type": "job",
    "attributes": {
      "jobType": "generateConfigChangeAuditReport",
      "payload": {
        "fromDate": "2026-09-15T00:00:00.000+05:30",
        "toDate": "2026-09-23T23:59:59.000+05:30",
        "settingTypes": ["Basics", "Integrations", "Advanced"]
      }
    }
  }
}
```

回應： `202 Created`。 回應體是工作資源的初始化
`QUEUED` 州。

```json
{
  "data": {
    "id": "4593",
    "type": "job",
    "attributes": {
      "jobType": "generateConfigChangeAuditReport",
      "status": "QUEUED",
      "dateCreated": "2026-09-23T18:12:04.000+05:30"
    }
  }
}
```

>[!NOTE]
>
>一個 `fromDate`跨越非常大日期範圍的 /`toDate` 視窗，或者說
>請求所有設定類型，若帳戶有長期變更歷史，可以
>處理時間比較長。 查詢「取得工作狀態」端點，而不是
>假設報告在固定延遲後已準備好。

#### 取得審計追蹤報告（Audit Trail Report）職缺的狀態

`GET /primeapi/v2/jobs/{id}`

回傳先前建立工作的工作狀態。 雖然工作是仍在運行， `attributes.status` 為 `QUEUED` 或 `IN_PROGRESS` 且
`attributes.result` 不存在。 工作完成後， `attributes.status`或 `COMPLETED`為 ，報告位置為 `attributes.result`，或
`FAILED`，故障細節在 `attributes.error`。

範圍： `admin:read`

| 參數 | 在 | 必修 | 說明 |
|---|---|---|---|
| `id` | 路徑 | 是的 | 工作 ID 在建立工作時會回傳 |

工作仍在執行時的範例回應

```json
{
  "data": {
    "id": "4593",
    "type": "job",
    "attributes": {
      "jobType": "generateConfigChangeAuditReport",
      "status": "IN_PROGRESS",
      "dateCreated": "2026-09-23T18:12:04.000+05:30"
    }
  }
}
```

工作完成後的範例回應

```json
{
  "data": {
    "id": "4593",
    "type": "job",
    "attributes": {
      "jobType": "generateConfigChangeAuditReport",
      "status": "COMPLETED",
      "dateCreated": "2026-09-23T18:12:04.000+05:30",
      "dateCompleted": "2026-09-23T18:12:41.000+05:30",
      "result": {
        "downloadUrl": "https://learningmanager.adobe.com/primeapi/v2/jobs/4593/download",
        "expiresAt": "2026-09-24T18:12:41.000+05:30"
      }
    }
  }
}
```

### 資源結構

#### 工作屬性

| 場地 | 類型 | 說明 |
|---|---|---|
| `id` | 字串 | 不透明的工作識別碼 |
| `jobType` | 字串 | `generateConfigChangeAuditReport` 本報告 |
| `status` | 字串 | `QUEUED`、、 `IN_PROGRESS`、 `COMPLETED`或 `FAILED` |
| `dateCreated` | 字串（ISO-8601） | 職位創立時 |
| `dateCompleted` | 字串（ISO-8601） | 當工作完成時;出現一次`status`即為`COMPLETED`&#x200B;`FAILED` |
| `payload` | 目的 | 工作所建立的請求參數（嵌入 – 見下文） |
| `result` | 目的 | 完成報告下載地點;僅在 `status` 時 `COMPLETED` 呈現（嵌入 – 見下文） |
| `error` | 目的 | 失效細節;僅在 `status` 時才出現 `FAILED` |

#### 有效載荷（嵌入於建立請求中）

| 場地 | 說明 |
|---|---|
| `fromDate` | 報告視窗開始 |
| `toDate` | 報告視窗結束 |
| `settingTypes` | 報告中包含的設定類別： `Basics`， `Integrations`， `Advanced` |

#### 結果（嵌入，嵌入於已完成的工作中）

| 場地 | 說明 |
|---|---|
| `downloadUrl` | 可下載產生報告的簽名網址 |
| `expiresAt` | 當 `downloadUrl` 不再有效時;請求重新檢查狀態以取得新連結 |

### 錯誤處理 {#audit-trail-report-error-handling}

以下代碼適用於這些端點：

| HTTP 狀態 | 錯誤代碼 | 當它發生時 |
|---|---|---|
| 400 | `BAD_REQUEST` | `toDate` 是早 `fromDate`於 ， `settingTypes` 為空或包含不支援的值，或日期無效 ISO-8601 – 僅建立端點 |
| 401 | `UNAUTHORIZED_ACCESS` | 該令牌遺失、無效或過期 |
| 403 | `FORBIDDEN` | 來電者不會持有 `ROLE_ADMIN` 該帳戶 |
| 400 | `OBJECT_DOESNT_EXIST` | Get by id：工作不存在或ID畸形——兩種情況都歸結為同一個反應 |

錯誤回應範例

```json
{
  "status": "BAD_REQUEST",
  "title": "Bad request. Check url, params and headers",
  "source": {
    "info": "toDate must be on or after fromDate"
  }
}
```

### 在你的整合中使用這個 API

一個常見的使用案例是面向管理員的「下載稽核追蹤」動作，在帳號設定畫面。

1. 當管理員選擇日期範圍和一種或多種設定類型時，確認後，用這些值呼叫 create-job 端點。
2. 儲存回來的工作 `id` ，並在合理的間隔（例如每隔幾秒）。
3. 雖然 `status` 是 `QUEUED` 或 `IN_PROGRESS`，但持續顯示進度狀態在使用者介面中。
4. 當 `status` 變為 `COMPLETED`時，用 `result.downloadUrl` 來讓管理員在通過前 `expiresAt` 下載報告。
5. 當 `status` 變成 `FAILED`時， `error` 出現在管理員面前，讓他們重試。
