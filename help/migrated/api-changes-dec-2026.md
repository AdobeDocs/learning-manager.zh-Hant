---
description: 了解如何使用論壇訂閱設定與訂閱者 API 來設定摘要電子郵件並管理論壇訂閱者
jcr-language: en_us
title: 2026 年 11 月的 API 變更
exl-id: 9b2d3856-810c-4352-bf18-667f698d4d70
source-git-commit: d1399781294a58f6ede8461878c979bd8b5edb34
workflow-type: tm+mt
source-wordcount: '5724'
ht-degree: 1%
---

# 2026 年 12 月的 API 變更

## 討論區講師通知的 API

本文說明支援討論區講師通知的新 API。 利用這些資訊訂閱講師和班長討論區，並控制哪些活動出現在他們的摘要郵件中。

### API 序列 {#api-sequence}

這些 API 可分為兩大類。 API `boardSubscriptionSettings` 在帳號層級運作。 訂閱者的 API 則在板上層級運作。 請依照下列順序使用這些 API：

| 步驟 | API | 目的 | 範圍 |
|---|---|---|---|
| 1 | [`POST /boardSubscriptionSettings`](#api-create-settings) | 設定帳戶層級設定。 | `admin:write` |
| 2 | [`PATCH /boardSubscriptionSettings`](#api-update-settings) | 更新帳戶層級設定。 | `admin:write` |
| 3 | [`GET /boardSubscriptionSettings`](#api-get-settings) | 擷取帳戶層級設定。 | `admin:read` |
| 4 | [`GET /boards/{id}/subscribers`](#api-get-subscribers) | 取得已訂閱看板的使用者名單。 | `admin:read` |
| 5 | [`POST /boards/{id}/subscribers`](#api-subscribe-users) | 訂閱使用者加入看板。 | `admin:write` |
| 6 | [`DELETE /boards/{id}/subscribers/{userId}`](#api-unsubscribe-user) | 取消訂閱某個使用者在看板上。 | `admin:write` |

### 驗證與權限

任何使用 OAuth 驗證並擁有 `admin:read` 和 `admin:write` 範圍的人，都可以呼叫這些 API。 這些 API 使用以下 OAuth 範圍：

* `admin:read`：列出訂閱者並讀取通知設定（`GET` 請求）。
* `admin:write`：建立或變更通知設定，並新增或移除訂閱者（`POST`、 `PATCH`、及 `DELETE` 請求）。

>[!NOTE]
>
>通知發送時會再次檢查登板權限。 如果訂閱者失去對某個看板的存取權，該看板的傳送會被跳過，但訂閱會被保留。 如果存取恢復，配送將恢復。

### 限制與考量

* 可新增的訂閱人數有上限。
* 摘要以單一電子郵件形式發送，無分頁，且郵件內容有大小限制。 對於活動頻繁的論壇，選擇一個能讓每封郵件易於管理的摘要頻率，例如每 6 小時一次。
* 摘要連結僅會開啟已登入的使用者的貼文、留言或回覆。

## 建立帳戶層級設定的 API {#api-create-settings}

### API 的目的 {#purpose-create-settings}

使用此 API 首次設定看板訂閱通知的帳戶層級設定。 設定控制通知摘要在帳戶間的產生方式：

* 哪些討論區活動會產生通知。
* 摘要郵件發送頻率。
* 是否包含貼文、留言、回覆和投票。

若要之後更改設定，請使用 [`PATCH /boardSubscriptionSettings`](#api-update-settings)。

### 端點 {#endpoint-create-settings}

```http
POST /primeapi/v2/boardSubscriptionSettings
```

| 物業 | 價值 |
|---|---|
| 範圍 | `admin:write` |
| 請求格式 | `application/vnd.api+json;charset=UTF-8` |
| 回應格式 | `application/vnd.api+json;charset=UTF-8` |

### 請求機構 {#request-body-create-settings}

將設定作為資源的 `boardSubscriptionSettings` 屬性傳送。

| 場地 | 類型 | 說明 |
|---|---|---|
| `notifyNewPost` | 布林值 | 訂閱者在看板新增貼文時是否會收到通知。 |
| `notifyComment` | 布林值 | 訂閱者在文章中新增留言時是否會收到通知。 |
| `notifyReply` | 布林值 | 訂閱者在留言中加入回覆時是否會收到通知。 |
| `digestFrequencyHours` | 整數 | 摘要郵件以小時計的頻率。 有效值範圍為 1 到 168（一週）。 例如，24 發送每日摘要，168 發送每週摘要。 |

### 範例請求 {#example-request-create-settings}

```bash
curl -X POST \
--header 'Content-Type: application/vnd.api+json;charset=UTF-8' \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
-d '{
  "data": {
    "type": "boardSubscriptionSettings",
    "attributes": {
      "notifyNewPost": true,
      "notifyComment": true,
      "notifyReply": true,
      "digestFrequencyHours": 24
    }
  }
}' \
'https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings'
```

### 範例回應 - 201 已建立 {#example-response-create-settings}

```json
{
  "links": {
    "self": "https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings"
  },
  "data": {
    "id": "1010",
    "type": "boardSubscriptionSettings",
    "attributes": {
      "digestFrequencyHours": 24,
      "notifyComment": true,
      "notifyNewPost": true,
      "notifyReply": true
    }
  }
}
```

### 回應代碼 {#response-codes-create-settings}

| 現況 | 意義 |
|---|---|
| 201 | 這個請求成功了。 帳戶層級設定已建立。 |
| 400 | 一個一般的錯誤請求錯誤。 |
| 401 | 請求缺少有效憑證，或因憑證無效而被拒絕存取。 |

## 用於更新帳戶層級設定的 API {#api-update-settings}

### API 的目的 {#purpose-update-settings}

使用此 API 更新您用 [`POST /boardSubscriptionSettings`](#api-create-settings)建立的帳戶層級設定。 例如，變更摘要頻率或開啟或關閉事件類型。

### 端點 {#endpoint-update-settings}

```http
PATCH /primeapi/v2/boardSubscriptionSettings
```

| 物業 | 價值 |
|---|---|
| 範圍 | `admin:write` |
| 請求格式 | `application/vnd.api+json;charset=UTF-8` |
| 回應格式 | `application/vnd.api+json;charset=UTF-8` |

### 請求機構 {#request-body-update-settings}

請以與建立 API 相同的格式傳送您想要變更的屬性：`notifyNewPost`、 `notifyComment`&#x200B;`notifyReply`&#x200B;`digestFrequencyHours`和 。您未傳送的屬性會保留其目前的值。 關於每個屬性的說明，請參閱 [「建立帳戶層級設定](#api-create-settings)的 API」。

### 範例請求 {#example-request-update-settings}

```bash
curl -X PATCH \
--header 'Content-Type: application/vnd.api+json;charset=UTF-8' \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
-d '{
  "data": {
    "type": "boardSubscriptionSettings",
    "attributes": {
      "notifyReply": true,
      "digestFrequencyHours": 12
    }
  }
}' \
'https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings'
```

### 範例回應 - 200 OK {#example-response-update-settings}

```json
{
  "links": {
    "self": "https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings"
  },
  "data": {
    "id": "1010",
    "type": "boardSubscriptionSettings",
    "attributes": {
      "digestFrequencyHours": 12,
      "notifyComment": true,
      "notifyNewPost": true,
      "notifyReply": true
    }
  }
}
```

### 回應代碼 {#response-codes-update-settings}

| 現況 | 意義 |
|---|---|
| 200 | 這個請求成功了。 帳戶層級設定已更新，回應包含目前的設定。 |
| 400 | 一個一般的錯誤請求錯誤。 |
| 401 | 請求缺少有效憑證，或因憑證無效而被拒絕存取。 |

## 用來擷取帳戶層級設定的 API {#api-get-settings}

### API 的目的 {#purpose-get-settings}

當使用者訂閱看板時，Adobe Learning Manager 可以透過摘要電子郵件通知他們該看板的活動。 帳戶層級設定決定哪些活動類型會觸發通知，以及摘要的發送頻率。

此 API 允許您擷取這些設定。 使用它來顯示應用程式中目前的通知設定，或在建置依賴這些設定的功能前驗證設定。

### 端點 {#endpoint-get-settings}

```http
GET /primeapi/v2/boardSubscriptionSettings
```

| 物業 | 價值 |
|---|---|
| 範圍 | `admin:read` |
| 回應格式 | `application/vnd.api+json;charset=UTF-8` |

### 範例請求 {#example-request-get-settings}

```bash
curl -X GET \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
'https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings'
```

### 範例回應 - 200 OK {#example-response-get-settings}

```json
{
  "links": {
    "self": "https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings"
  },
  "data": {
    "id": "1010",
    "type": "boardSubscriptionSettings",
    "attributes": {
      "digestFrequencyHours": 24,
      "notifyComment": true,
      "notifyNewPost": true,
      "notifyReply": true
    }
  }
}
```

### 資源結構 {#resource-schema-get-settings}

**`boardSubscriptionSettings`屬性**

| 場地 | 類型 | 說明 |
|---|---|---|
| `notifyNewPost` | 布林值 | 訂閱者在看板新增貼文時是否會收到通知。 |
| `notifyComment` | 布林值 | 訂閱者在文章中新增留言時是否會收到通知。 |
| `notifyReply` | 布林值 | 訂閱者在留言中加入回覆時是否會收到通知。 |
| `digestFrequencyHours` | 整數 | 摘要郵件以小時計的頻率。 有效值範圍為 1 到 168（一週）。 使用此值告訴使用者預期多久收到摘要郵件。 例如，當值為 24 時顯示「每日」，當值為 168 時顯示「每週」。 |

### 回應代碼 {#response-codes-get-settings}

| 現況 | 意義 |
|---|---|
| 200 | 這個請求成功了。 回應包含帳戶層級的看板訂閱設定。 |
| 400 | 一個一般的錯誤請求錯誤。 |
| 401 | 請求缺少有效憑證，或因憑證無效而被拒絕存取。 |

### 在你的整合中使用這個 API {#integration-get-settings}

常見的使用情境是通知偏好設定畫面，顯示該帳戶如何設定董事會訂閱電子郵件。

1. 當您的應用程式通知偏好設定畫面載入時，請呼叫 `GET /boardSubscriptionSettings`。
1. 使用回覆中的數值顯示哪些類型的活動會觸發通知，以及摘要郵件發送頻率。

## 用來擷取板上訂閱者的 API {#api-get-subscribers}

### API 的目的 {#purpose-get-subscribers}

擷取訂閱特定看板的使用者清單。 訂閱該看板的使用者會收到該看板中新活動的通知。 此 API 會回傳目前訂閱該看板的使用者，以及每個訂閱何時以及由誰創建的詳細資訊。

使用此 API 在您的應用程式中顯示訂閱者清單、稽核誰接收董事會更新，或將董事會訂閱資料與外部系統同步。

回應是分頁的。 使用 `page[offset]` and `page[limit]` 查詢參數來瀏覽大型訂閱者清單。 回傳的資料會依據請求的看板上呼叫使用者的權限而定。

### 端點 {#endpoint-get-subscribers}

```http
GET /primeapi/v2/boards/{id}/subscribers
```

| 物業 | 價值 |
|---|---|
| 範圍 | `admin:read` |
| 回應格式 | `application/vnd.api+json;charset=UTF-8` |

### 參數 {#parameters-get-subscribers}

| 參數 | 在 | 必需 | 預設 | 說明 |
|---|---|---|---|---|
| `id` | 路徑 | 是的 | 無 | 您想要擷取訂閱者的看板 ID。 存取權須經撥號者在看板上的權限。 |
| `page[offset]` | 查詢 | 不 | 0 | 要返回的紀錄起始位置。 |
| `page[limit]` | 查詢 | 不 | 10 | 每頁要回訪的訂閱者數量。 最大允許值為 200。 |

### 範例請求 {#example-request-get-subscribers}

```bash
curl -X GET \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
'https://learningmanager.adobe.com/primeapi/v2/boards/1234/subscribers?page[offset]=0&page[limit]=50'
```

### 範例回應 - 200 OK {#example-response-get-subscribers}

```json
{
  "data": [
    {
      "id": "1234:5678",
      "type": "boardSubscriber",
      "attributes": {
        "boardId": 1234,
        "dateSubscribed": 1757000000000,
        "subscribedByUserId": 5678,
        "user": {
          "id": "5678",
          "name": "Jane Doe",
          "email": "jane.doe@example.com",
          "avatarUrl": "https://example.com/avatars/5678.png",
          "bio": "Learning enthusiast",
          "contentLocale": "en-US",
          "uiLocale": "en-US",
          "timeZoneCode": "PST",
          "userType": "INTERNAL",
          "state": "ACTIVE",
          "profile": "Learner",
          "roles": ["Learner"],
          "gamificationEnabled": true,
          "pointsEarned": 120,
          "pointsRedeemed": 20,
          "enrollOnClick": true,
          "preferredResolution": "720p",
          "lastLoginDate": "2026-09-23T18:12:04.000Z"
        }
      }
    }
  ]
}
```

### 資源結構 {#resource-schema-get-subscribers}

回應包含一個新資源，。 `boardSubscriber`其屬性包括 `boardId`、 `dateSubscribed`、 `subscribedByUserId`和 `user`。 嵌入的使用者物件包含訂閱者資訊，例如使用者 ID、姓名、電子郵件、個人檔案與角色，以及其他使用者的元資料。

**`boardSubscriber`屬性**

| 場地 | 類型 | 說明 |
|---|---|---|
| `id` | string | 不透明訂閱 ID。 |
| `type` | string | 資源類型。 |
| `boardId` | 數量 | 使用者所訂閱的看板 ID。 |
| `dateSubscribed` | 數量 | 使用者訂閱該看板的時間戳記。 |
| `subscribedByUserId` | 數量 | 建立訂閱的使用者 ID。 |
| `user` | 物件 | 已訂閱使用者的詳細資料（嵌入，見下文）。 |

**`user`（嵌入於訂閱者內部）**

| 場地 | 類型 | 說明 |
|---|---|---|
| `id` | string | 不透明的使用者 ID。 |
| `name` | string | 使用者的顯示名稱。 |
| `email` | string | 使用者的電子郵件地址。 |
| `avatarUrl` | string | 使用者個人頭像的網址。 |
| `bio` | string | 使用者簡短簡介。 |
| `binUserId` | string | 使用者的內部識別碼。 |
| `userUniqueId` | string | 帳戶中使用者的唯一識別碼。 |
| `userType` | string | 使用者類型，例如內部或外部。 |
| `state` | string | 使用者帳戶的當前狀態。 |
| `profile` | string | 指派給使用者的設定檔。 |
| `roles` | 字串陣列 | 使用者所擁有的角色。 |
| `contentLocale` | string | 使用者偏好查看內容的語系。 |
| `uiLocale` | string | 使用者介面所使用的語系。 |
| `timeZoneCode` | string | 為使用者設定的時區。 |
| `preferredResolution` | string | 使用者偏好的影片解析度。 |
| `enrollOnClick` | 布林值 | 使用者在選擇學習物件時是否自動註冊。 |
| `gamificationEnabled` | 布林值 | 是否為使用者啟用遊戲化功能。 |
| `pointsEarned` | 數量 | 使用者所獲得的遊戲化點數總數。 |
| `pointsRedeemed` | 數量 | 用戶兌換的遊戲化點數總數。 |
| `lastLoginDate` | string | 使用者最近一次登入的日期與時間。 |
| `fields` | 物件 | 自訂使用者欄位及其值。 |
| `metadata` | 物件 | 與使用者相關聯的額外元資料。 |

### 回應代碼 {#response-codes-get-subscribers}

| 現況 | 意義 |
|---|---|
| 200 | 這個請求成功了。 回應內容包含了董事會的訂閱者。 |
| 400 | 一個一般的錯誤請求錯誤。 例如，看板 ID 或分頁值格式不正確。 |
| 401 | 請求缺少有效憑證，或因憑證無效而被拒絕存取。 |

### 在你的整合中使用這個 API {#integration-get-subscribers}

常見的使用情境是管理員或版主視圖，顯示所有收到該論壇更新的人。

1. 當檢視載入時，呼叫這個端點，並附上看板 ID 和 `page[limit]` 適合你版面配置的值（最多 200）。
1. 顯示 `user.name`每位訂閱者的 、 `user.email`、 及 `dateSubscribed` 值。
1. 如果回傳的記錄數量等 `page[limit]`於 ，可能會有更多訂閱者。 再次呼叫該端點，依頁面大小遞增 `page[offset]` ，直到某頁面回傳的記錄數少於請求。

## 訂閱使用者至看板的 API {#api-subscribe-users}

### API 的目的 {#purpose-subscribe-users}

訂閱一位或多位用戶加入討論區，讓他們收到該討論區的摘要電子郵件。 可依使用者 ID、電子郵件地址（解析為帳戶內的使用者 ID）或兩者皆可識別使用者。 您可以在單一請求中新增多個使用者。 請參閱 [批量訂閱](#bulk-subscriptions)。

### 端點 {#endpoint-subscribe-users}

```http
POST /primeapi/v2/boards/{id}/subscribers
```

| 物業 | 價值 |
|---|---|
| 範圍 | `admin:write` |
| 請求格式 | `application/vnd.api+json;charset=UTF-8` |
| 回應格式 | `application/vnd.api+json;charset=UTF-8` |

### 參數 {#parameters-subscribe-users}

| 參數 | 在 | 必需 | 說明 |
|---|---|---|---|
| `id` | 路徑 | 是的 | 要訂閱使用者的看板 ID。 |

### 請求機構 {#request-body-subscribe-users}

將使用者作為資源的 `boardSubscriberBulkRequest` 屬性傳送。 至少要求其中一項 `userIds` 或 `emails` 。

| 場地 | 類型 | 說明 |
|---|---|---|
| `data.attributes.userIds` | 數字陣列 | 要訂閱的使用者 ID。 |
| `data.attributes.emails` | 字串陣列 | 要訂閱的使用者的電子郵件地址。 每個地址都會解析為帳戶內的使用者 ID。 |

### 範例請求 {#example-request-subscribe-users}

```bash
curl -X POST \
--header 'Content-Type: application/vnd.api+json;charset=UTF-8' \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
-d '{
  "data": {
    "type": "boardSubscriberBulkRequest",
    "attributes": {
      "userIds": [
        1234,
        5678
      ],
      "emails": [
        "abc@xyz.com"
      ]
    }
  }
}' \
'https://learningmanager.adobe.com/primeapi/v2/boards/1010/subscribers'
```

### 範例回應 - 207 多重狀態 {#example-response-subscribe-users}

```json
{
  "added": [
    {
      "userId": "12345",
      "status": "SUCCESS"
    }
  ],
  "failed": [
    {
      "userId": "78910",
      "errorCode": "NO_BOARD_ACCESS"
    }
  ]
}
```

**回應屬性**

| 場地 | 類型 | 說明 |
|---|---|---|
| `added` | 陣列 | 已訂閱的使用者。 每個條目都有 a `userId` 和 `status`。 已訂閱的用戶也在此被報告為成功者。 |
| `failed` | 陣列 | 那些無法訂閱的使用者。 每個條目都有 和 `userId` `errorCode`，例如 `NO_BOARD_ACCESS`。 |

### 回應代碼 {#response-codes-subscribe-users}

| 現況 | 意義 |
|---|---|
| 207 | 多重狀態。 請求已處理，回應中列出每位使用者`added`&#x200B;`failed`的結果。 |
| 400 | 一個一般的錯誤請求錯誤。 |
| 401 | 請求缺少有效憑證，或因憑證無效而被拒絕存取。 |
| 404 | 所要求的資源，例如黑板，卻找不到。 |
| 409 | 該董事會處於非活躍狀態、已刪除或已退休，因此整個申請被拒絕。 |

### 批量訂閱 {#bulk-subscriptions}

使用批量訂閱，在單一請求中新增多個使用者到討論區。 批量訂閱有助於減少管理訂閱者所需的 API 呼叫次數。 當這種情況很有用時：

* 一位講師負責管理多個班級。
* 一個團隊經理需要能接觸到許多討論區。
* 外部系統會以批次方式同步看板訂閱。
* 在創建班級時，必須同時訂閱多位講師。

#### 批量新增行為

批量請求可以包含使用者 ID、電子郵件地址，或兩者的混合。 每位使用者都會獨立處理。

#### 冪等行為

大量加成是冪等的。 如果使用者已經訂閱了看板，請求就會成功，不會建立重複訂閱，且現有訂閱保持不變。 這讓用戶端能安全地重試請求。

#### 部分成功

有些使用者可以訂閱，而有些則無法通過驗證。 操作不會因為有一個或多個使用者無效而失敗。

| 案件 | 結果 |
|---|---|
| 使用者存在且可存取看板 | 成功 |
| 使用者已訂閱 | 成功 |
| 使用者無法存取看板 | 失敗 （`NO_BOARD_ACCESS`） |
| 使用者不存在 | 失敗 |
| 使用者處於非活動狀態 | 失敗 |
| 該使用者已被刪除 | 失敗 |

#### 回應格式

批量訂閱會回傳 HTTP 207 多重狀態，並對每個使用者都有`added`&#x200B;`failed`結果，如範例[回應](#example-response-subscribe-users)所示。

#### 常見的驗證失敗

* **使用者無法存取該板。** 如果使用者無法看到該看板，則 `NO_BOARD_ACCESS` 會為該使用者回傳。 其餘用戶則繼續正常處理。
* **該董事會處於非活躍狀態、已刪除或已停用。** 如果該看板不符合訂閱資格，該請求會以 HTTP 409 衝突拒絕。
* **使用者無效。** 如果使用者帳戶不存在、處於非啟用狀態或已被刪除，該操作會傳回該使用者的失敗項目。

## API 用來取消訂閱使用者的看板 {#api-unsubscribe-user}

### API 的目的 {#purpose-unsubscribe-user}

取消訂閱某個使用者在討論區。 訂閱被移除後，使用者將不再收到該看板的通知與摘要電子郵件。

### 端點 {#endpoint-unsubscribe-user}

```http
DELETE /primeapi/v2/boards/{id}/subscribers/{userId}
```

| 物業 | 價值 |
|---|---|
| 範圍 | `admin:write` |
| 回應格式 | `application/vnd.api+json;charset=UTF-8` |

### 參數 {#parameters-unsubscribe-user}

| 參數 | 在 | 必需 | 說明 |
|---|---|---|---|
| `id` | 路徑 | 是的 | 董事會的識別碼。 |
| `userId` | 路徑 | 是的 | 要取消訂閱的使用者 ID。 |

### 範例請求 {#example-request-unsubscribe-user}

```bash
curl -X DELETE \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
'https://learningmanager.adobe.com/primeapi/v2/boards/1234/subscribers/5678'
```

### 範例回應 - 204 無內容 {#example-response-unsubscribe-user}

回應沒有具體內容。

### 回應代碼 {#response-codes-unsubscribe-user}

| 現況 | 意義 |
|---|---|
| 204 | 這個請求成功了。 該使用者已被取消訂閱。 |
| 400 | 一個一般的錯誤請求錯誤。 |
| 401 | 請求缺少有效憑證，或因憑證無效而被拒絕存取。 |
| 404 | 所請求的資源，例如看板或訂閱，都找不到。 |

## 書籤 API 排序與已退休的內容處理

### API 的目的

學習者會將想要重溫的訓練加入書籤。 在此變更之前，書籤 API 回傳書籤的順序並無特定順序。 整合，尤其是無頭實作，無法先顯示最近儲存的書籤。 擁有許多書籤的學習者必須翻閱舊項目以尋找最近的。

已退休學習物件的書籤也保留在清單中。 選擇其中一個會導致「找不到頁面」錯誤。

此變更從兩個方面改善了書籤 API：

* 書籤會依時間順序回傳，從最新到。
* 已退役學習物件的書籤將不再回傳。

不會引入新的端點、參數或回應屬性。 現有的整合功能仍能在不做任何變更的情況下運作。

### 基礎網址與慣例

書籤 API 使用以下基礎路徑與慣例：

| 商品 | 價值 |
|---|---|
| 基徑 | `/primeapi/v2` |
| 內容類型 | `application/vnd.api+json` |
| Authentication | 具備學習者讀取權限的 OAuth 憑證 |
| 預設順序 | 請先從最新的書籤開始 |
| 新增參數 | 沒有 |
| 反應結構 | 不變 |

### 端點

#### 回傳書籤的端點

以下端點會以新順序回傳書籤：

| 端點 | 回歸 |
|---|---|
| `GET /primeapi/v2/learningObjects?filter.bookmarks=true` | 學習者已加入書籤的學習物件 |
| `GET /primeapi/v2/bookmarks` | 學習者的書籤 |

#### 將學習物件按順序加入書籤

`GET /primeapi/v2/learningObjects?filter.bookmarks=true`

<!-- Content Review by Claude: Please confirm the endpoint list. The dev-to-QE hand-off confirms ordering for GET /learningObjects?filter.bookmarks=true. The PRD (ALMER-442) also lists GET /primeapi/v2/bookmarks. Please also confirm the OAuth scope. -->

回傳呼叫學習者已加入書籤的學習物件。 最近被書籤標記的項目排在第一，最舊的則排在最後。

**範圍：** 學習者讀取權限

端點接受以下查詢參數：

| 參數 | 在 | 必需 | 說明 |
|---|---|---|---|
| `filter.bookmarks` | 查詢 | 是的 | 設定為 ， `true` 僅回傳學習者已書籤的學習物件 |

**範例請求**

```http
GET /primeapi/v2/learningObjects?filter.bookmarks=true
Accept: application/vnd.api+json
Authorization: oauth <access-token>
```

**範例 200 OK 回應**

學習者將「Adobe Analytics 入門」先加入書籤，其次「建立工作區專案」，最後「Adobe Analytics 進階分群」。 回覆依序從最新到最舊排列。 其他屬性為簡潔而省略。

```json
{
  "data": [
    {
      "id": "course:2400162",
      "type": "learningObject",
      "attributes": {
        "name": "Advanced Segmentation in Adobe Analytics"
      }
    },
    {
      "id": "course:2400160",
      "type": "learningObject",
      "attributes": {
        "name": "Building Workspace Projects"
      }
    },
    {
      "id": "course:2400159",
      "type": "learningObject",
      "attributes": {
        "name": "Getting Started with Adobe Analytics"
      }
    }
  ]
}
```

>[!NOTE]
>
>新的排序是預設行為，適用於所有帳戶。

### 書籤排序

#### 書籤的排序方式

書籤依學習者儲存的日期排序，從最新到最舊。 例如，如果學習者將課程A加入書籤，接著是課程B，最後才列出課程C，回應會先列出課程C，課程B排第二，課程A最後。

例如，如果一個書籤固定在第 10 名的 LO 是「未儲存」，之後又重新加入書籤，那麼它會顯示為「最近已書籤」，並且在列表的前列中。

先前在用戶端排序書籤的整合功能可以移除該邏輯，並依回傳順序顯示結果。

### 已停用的內容處理

#### 退休學習物件的處理方式

無論學習者是否已註冊該學習物件，已退休學習物件的書籤都不會在回應中回傳。

已停用且已加入書籤的學習物件，除非學習者已註冊，否則不會顯示。

學習者不再看到導致「頁面未找到」錯誤的書籤。 書籤是隱藏於結果之外，而非刪除。

### 相容性

此變更不會破壞現有的 API 使用者：

* 端點及其參數保持不變。
* 回應結構未曾變更，且不會新增或移除任何屬性。
* 只有結果的順序以及已退役學習對象的排除與先前行為有所不同。

### 在你的整合中使用這個 API

一個常見的使用情境是在無頭學習者體驗中出現「儲存以備後用」清單。 您希望學習者先看到他們最新的書籤，而非連結到已停用的內容。

1. 學習者打開清單時請打電話 `GET /primeapi/v2/learningObjects?filter.bookmarks=true` 。
2. 依照回傳的順序顯示學習物件。 第一個項目是最近被收藏的。
3. 移除您作為變通方法所新增的任何用戶端排序或已退休內容篩選功能。
4. 根據回應中的項目數量顯示書籤數量。 已退休學習物件的書籤不再包含在內。

### 學習者應用程式中 Leaner Compliance Widget 中多註冊實例的 API 支援

公開 API 透過現有註冊端點上的可選查詢參數來支援此行為。 如果你省略這個參數，API 會回傳與先前相同的結果，因此現有的整合系統，包括無頭實作，仍能維持不變的運作方式。

**端點**

取得 /primeapi/v2/enrollments

**查詢參數**

includeMultiInstanceEnrollments（選用）

**查詢**

https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page\[limit\]=10&filter.loTypes=course&includeHierarchicalEnrollments=false&includeMultiInstanceEnrollments=true&sort=dateEnrolled

**價值**

沒錯。 預設為 False。

**回應機構**

&lbrace;

「連結」：&lbrace;

“self”： “[https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page\[limit\]=10&amp;filter.loTypes=course&amp;sort=dateEnrolled&amp;includeHierarchicalEnrollments=false&amp;includeMultiInstanceEnrollments=true](https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page%5blimit%5d=10&filter.loTypes=course&sort=dateEnrolled&includeHierarchicalEnrollments=false&includeMultiInstanceEnrollments=true)”，

“next”： “[https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page\[limit\]=10&amp;filter.loTypes=course&amp;sort=dateEnrolled&amp;includeHierarchicalEnrollments=false&amp;includeMultiInstanceEnrollments=true&amp;page\[cursor\]=eyJjb3Vyc2VNdWx0aSI6MCwiam9iQWlkIjowLCJjb3Vyc2UiOjEwLCJsZWFybmluZ1Byb2dyYW0iOjAsImNlcnRpZmljYXRpb24iOjB9](https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page%5blimit%5d=10&filter.loTypes=course&sort=dateEnrolled&includeHierarchicalEnrollments=false&includeMultiInstanceEnrollments=true&page%5bcursor%5d=eyJjb3Vyc2VNdWx0aSI6MCwiam9iQWlkIjowLCJjb3Vyc2UiOjEwLCJsZWFybmluZ1Byb2dyYW0iOjAsImNlcnRpZmljYXRpb24iOjB9)”

&rbrace;,

“data”： \&lbrack;

&lbrace;

“id”： “course：15067_30122_3400468”，

“type”： “learningObjectInstanceEnrollment”，

“屬性”： &lbrace;

“完成截止日期”：「2026-02-24T10:50:45.000Z」，

“enrollmentSource”： “MGR_APPROVAL”，

“hasPassed”：false，

“progressPercent”： 0，

「分數」：0，

「state」：「PENDING_APPROVAL」

&rbrace;,

「關係」：&lbrace;

「學習者」：&lbrace;

“data”： &lbrace;

“id”： “3400468”，

“type”： “user”

&rbrace;

&rbrace;,

“learningObject”： &lbrace;

“data”： &lbrace;

“id”： “course：15067”，

“type”： “learningObject”

&rbrace;

&rbrace;,

“loInstance”： &lbrace;

“data”： &lbrace;

“id”： “course：15067_30122”，

“type”： “learningObjectInstance”

&rbrace;

&rbrace;,

“loResourceGrades”： &lbrace;

“data”： \&lbrack;

&lbrace;

“id”： “course：15067_30122_41715_1_3400468”，

“type”： “learningObjectResourceGrade”

&rbrace;

\&rbrack;

&rbrace;

&rbrace;

&rbrace;,

&lbrace;

“id”： “course：1108800_1997400_3400468”，

“type”： “learningObjectInstanceEnrollment”，

“屬性”： &lbrace;

“enrollmentSource”： “SELF_ENROLL”，

“hasPassed”：false，

“progressPercent”： 0，

「分數」：0，

「state」：「PENDING_APPROVAL」

&rbrace;,

「關係」：&lbrace;

「學習者」：&lbrace;

“data”： &lbrace;

“id”： “3400468”，

“type”： “user”

&rbrace;

&rbrace;,

“learningObject”： &lbrace;

“data”： &lbrace;

“ID”：「course：1108800」，

“type”： “learningObject”

&rbrace;

&rbrace;,

“loInstance”： &lbrace;

“data”： &lbrace;

“id”： “course：1108800_1997400”，

“type”： “learningObjectInstance”

&rbrace;

&rbrace;,

“loResourceGrades”： &lbrace;

“data”： \&lbrack;

&lbrace;

“id”： “course：1108800_1997400_2174574_0_3400468”，

“type”： “learningObjectResourceGrade”

&rbrace;

\&rbrack;

&rbrace;

&rbrace;

&rbrace;,

&lbrace;

“id”： “course：2027668_3707328_3400468”，

“type”： “learningObjectInstanceEnrollment”，

“屬性”： &lbrace;

“enrollmentSource”： “MGR_APPROVAL”，

“hasPassed”：false，

“progressPercent”： 0，

「分數」：0，

「state」：「PENDING_APPROVAL」

&rbrace;,

「關係」：&lbrace;

「學習者」：&lbrace;

“data”： &lbrace;

“id”： “3400468”，

“type”： “user”

&rbrace;

&rbrace;,

“learningObject”： &lbrace;

“data”： &lbrace;

“id”： “course：2027668”，

“type”： “learningObject”

&rbrace;

&rbrace;,

“loInstance”： &lbrace;

“data”： &lbrace;

“id”： “course：2027668_3707328”，

“type”： “learningObjectInstance”

&rbrace;

&rbrace;,

“loResourceGrades”： &lbrace;

“data”： \&lbrack;

&lbrace;

“id”： “course：2027668_3707328_2665897_0_3400468”，

“type”： “learningObjectResourceGrade”

&rbrace;

\&rbrack;

&rbrace;

&rbrace;

&rbrace;,

&lbrace;

“id”： “course：2030067_3709862_3400468”，

“type”： “learningObjectInstanceEnrollment”，

“屬性”： &lbrace;

“enrollmentSource”： “MGR_APPROVAL”，

“hasPassed”：false，

“progressPercent”： 0，

「分數」：0，

「state」：「PENDING_APPROVAL」

&rbrace;,

「關係」：&lbrace;

「學習者」：&lbrace;

“data”： &lbrace;

“id”： “3400468”，

“type”： “user”

&rbrace;

&rbrace;,

“learningObject”： &lbrace;

“data”： &lbrace;

“id”： “course：2030067”，

“type”： “learningObject”

&rbrace;

&rbrace;,

“loInstance”： &lbrace;

“data”： &lbrace;

“id”： “course：2030067_3709862”，

“type”： “learningObjectInstance”

&rbrace;

&rbrace;,

“loResourceGrades”： &lbrace;

“data”： \&lbrack;

&lbrace;

“id”： “course：2030067_3709862_2668467_0_3400468”，

“type”： “learningObjectResourceGrade”

&rbrace;

\&rbrack;

&rbrace;

&rbrace;

&rbrace;,

&lbrace;

“id”： “course：3081896_5749155_3400468”，

“type”： “learningObjectInstanceEnrollment”，

“屬性”： &lbrace;

“enrollmentSource”： “MGR_APPROVAL”，

“hasPassed”：false，

“progressPercent”： 0，

「分數」：0，

「state」：「PENDING_APPROVAL」

&rbrace;,

「關係」：&lbrace;

「學習者」：&lbrace;

“data”： &lbrace;

“id”： “3400468”，

“type”： “user”

&rbrace;

&rbrace;,

“learningObject”： &lbrace;

“data”： &lbrace;

“id”： “course：3081896”，

“type”： “learningObject”

&rbrace;

&rbrace;,

“loInstance”： &lbrace;

“data”： &lbrace;

“id”： “course：3081896_5749155”，

“type”： “learningObjectInstance”

&rbrace;

&rbrace;,

“loResourceGrades”： &lbrace;

“data”： \&lbrack;

&lbrace;

“id”： “course：3081896_5749155_3737554_0_3400468”，

“type”： “learningObjectResourceGrade”

&rbrace;,

&lbrace;

“id”： “course：3081896_5749155_3737555_0_3400468”，

“type”： “learningObjectResourceGrade”

&rbrace;

\&rbrack;

&rbrace;

&rbrace;

&rbrace;,

&lbrace;

“id”： “course：2037893_3717940_3400468”，

“type”： “learningObjectInstanceEnrollment”，

“屬性”： &lbrace;

“enrollmentSource”： “MGR_APPROVAL”，

“hasPassed”：false，

“progressPercent”： 0，

「分數」：0，

「state」：「PENDING_APPROVAL」

&rbrace;,

「關係」：&lbrace;

「學習者」：&lbrace;

“data”： &lbrace;

“id”： “3400468”，

“type”： “user”

&rbrace;

&rbrace;,

“learningObject”： &lbrace;

“data”： &lbrace;

“id”： “course：2037893”，

“type”： “learningObject”

&rbrace;

&rbrace;,

“loInstance”： &lbrace;

“data”： &lbrace;

“id”： “course：2037893_3717940”，

“type”： “learningObjectInstance”

&rbrace;

&rbrace;,

“loResourceGrades”： &lbrace;

“data”： \&lbrack;

&lbrace;

“id”： “course：2037893_3717940_3676856_0_3400468”，

“type”： “learningObjectResourceGrade”

&rbrace;

\&rbrack;

&rbrace;

&rbrace;

&rbrace;,

&lbrace;

“id”： “course：3049434_5713130_3400468”，

“type”： “learningObjectInstanceEnrollment”，

“屬性”： &lbrace;

“完成截止日期”：「2020-05-05T18:29:59.000Z」，

“enrollmentSource”： “MGR_APPROVAL”，

“hasPassed”：false，

“progressPercent”： 0，

「分數」：0，

「state」：「PENDING_APPROVAL」

&rbrace;,

「關係」：&lbrace;

「學習者」：&lbrace;

“data”： &lbrace;

“id”： “3400468”，

“type”： “user”

&rbrace;

&rbrace;,

“learningObject”： &lbrace;

“data”： &lbrace;

“id”： “course：3049434”，

“type”： “learningObject”

&rbrace;

&rbrace;,

“loInstance”： &lbrace;

“data”： &lbrace;

“id”： “course：3049434_5713130”，

“type”： “learningObjectInstance”

&rbrace;

&rbrace;,

“loResourceGrades”： &lbrace;

“data”： \&lbrack;

&lbrace;

“id”： “course：3049434_5713130_3693595_0_3400468”，

“type”： “learningObjectResourceGrade”

&rbrace;

\&rbrack;

&rbrace;

&rbrace;

&rbrace;,

&lbrace;

“id”： “course：2001397_3679403_3400468”，

“type”： “learningObjectInstanceEnrollment”，

“屬性”： &lbrace;

“enrollmentSource”： “MGR_APPROVAL”，

“hasPassed”：false，

“progressPercent”： 0，

「分數」：0，

「state」：「PENDING_APPROVAL」

&rbrace;,

「關係」：&lbrace;

「學習者」：&lbrace;

“data”： &lbrace;

“id”： “3400468”，

“type”： “user”

&rbrace;

&rbrace;,

“learningObject”： &lbrace;

“data”： &lbrace;

“id”： “course：2001397”，

“type”： “learningObject”

&rbrace;

&rbrace;,

“loInstance”： &lbrace;

“data”： &lbrace;

“id”： “course：2001397_3679403”，

“type”： “learningObjectInstance”

&rbrace;

&rbrace;,

“loResourceGrades”： &lbrace;

“data”： \&lbrack;

&lbrace;

“id”： “course：2001397_3679403_2635974_0_3400468”，

“type”： “learningObjectResourceGrade”

&rbrace;

\&rbrack;

&rbrace;

&rbrace;

&rbrace;,

&lbrace;

“id”： “course：2037862_3717900_3400468”，

“type”： “learningObjectInstanceEnrollment”，

“屬性”： &lbrace;

“enrollmentSource”： “MGR_APPROVAL”，

“hasPassed”：false，

“progressPercent”： 0，

「分數」：0，

「state」：「PENDING_APPROVAL」

&rbrace;,

「關係」：&lbrace;

「學習者」：&lbrace;

“data”： &lbrace;

“id”： “3400468”，

“type”： “user”

&rbrace;

&rbrace;,

“learningObject”： &lbrace;

“data”： &lbrace;

“id”： “course：2037862”，

“type”： “learningObject”

&rbrace;

&rbrace;,

“loInstance”： &lbrace;

“data”： &lbrace;

“id”： “course：2037862_3717900”，

“type”： “learningObjectInstance”

&rbrace;

&rbrace;,

“loResourceGrades”： &lbrace;

“data”： \&lbrack;

&lbrace;

“id”： “course：2037862_3717900_3676816_0_3400468”，

“type”： “learningObjectResourceGrade”

&rbrace;

\&rbrack;

&rbrace;

&rbrace;

&rbrace;,

&lbrace;

“id”： “course：2037837_3717863_3400468”，

“type”： “learningObjectInstanceEnrollment”，

“屬性”： &lbrace;

“完成截止日期”：「2020-02-29T18:29:59.000Z」，

“enrollmentSource”： “SELF_ENROLL”，

“hasPassed”：false，

“progressPercent”： 0，

「分數」：0，

“state”： “其他”

&rbrace;,

「關係」：&lbrace;

「學習者」：&lbrace;

“data”： &lbrace;

“id”： “3400468”，

“type”： “user”

&rbrace;

&rbrace;,

“learningObject”： &lbrace;

“data”： &lbrace;

“id”： “course：2037837”，

“type”： “learningObject”

&rbrace;

&rbrace;,

“loInstance”： &lbrace;

“data”： &lbrace;

“id”： “course：2037837_3717863”，

“type”： “learningObjectInstance”

&rbrace;

&rbrace;,

“loResourceGrades”： &lbrace;

“data”： \&lbrack;

&lbrace;

“id”： “course：2037837_3717863_3597363_0_3400468”，

“type”： “learningObjectResourceGrade”

&rbrace;

\&rbrack;

&rbrace;

&rbrace;

&rbrace;

\&rbrack;

&rbrace;

## 學習路徑註冊的最後存取日期 {#last-access-date-lp-enrollment}

Adobe Learning Manager 允許您在學習路徑註冊時儲存自訂的元資料，例如最後存取日期。 你透過 API 設定並讀取這些元資料。 這有助於您追蹤對所指派學習路徑的限時存取情況。

## 關於學習路徑註冊的中繼資料

您已經可以透過 API 設定課程報名的最後存取日期。 該日期決定學習者可存取課程的時間長短。 學習路徑報名現在支援通用的中繼資料欄位，讓您能儲存最後存取日期或其他想要追蹤的值。

您不需要開啟欄位或傳送特殊的標頭。 欄位在你設定之前是空的。

>[!NOTE]
>
>這些元資料是用來追蹤你的。 Adobe Learning Manager 不會在學習者開啟學習路徑或其課程時更新該資訊，也不會控制對該學習路徑的存取權限。 它也不會傳播到路徑上的各條路徑。 每個課程都會保留自己的最後存取日期，因此同一路徑上的課程可能會有不同的日期。 繼續分別管理課程層級的存取權到期。

### 元資料規則 {#metadata-rules}

* 該值必須是 JSON 物件。 字串、數字、布林值或陣列會回傳 400 錯誤訊息。`metadata must be a JSON object`
* 你可以用任何鑰匙。 Adobe Learning Manager 不會驗證鍵或值，也不會強制執行日期格式。 本文中的範例使用紀元毫秒，格式與課程日期相同。
* PATCH 請求會取代整個中繼資料物件。 它不會與現有值合併，因此你省略的鍵會被移除。
* 設定 `"metadata": null` 會清除所有元資料並回傳 200。
* 請求若物件為空 `attributes` ，或沒有鍵 `metadata` ，則儲存的元資料不會被更改。
* 當未設定元資料，或在你清除後 `metadata` ，該金鑰不在回應中。

## 設定現有註冊的中繼資料

使用管理員令牌。

將 PATCH 請求傳送至下列端點，其中 `{enrollmentId}` 為學習路徑註冊 ID，格式 `learningProgram:<lpId><instanceId><userId>`為：

```
PATCH /primeapi/v2/users/{userId}/enrollments/{enrollmentId}
```

請使用此請求主體：

```json
{
  "data": {
    "id": "<enrollmentId>",
    "type": "learningObjectInstanceEnrollment",
    "attributes": {
      "metadata": {
        "lastAccessDate": 1745337600000
      }
    }
  }
}
```

### 註冊學習者時設定中繼資料

使用管理員令牌。

發送帶有學習路徑與實例 ID 的 POST 請求。 在請求主體中包含一個可選 `metadata` 物件。

```
POST /primeapi/v2/users/{userId}/enrollments?loId=<lpId>&loInstanceId=<instanceId>
```

* 如果 `metadata` 不是 JSON 物件，請求會回傳 400，且使用者未被註冊。
* 如果使用者已經註冊，請求會回傳 200 且不會改變任何資訊。 若要變更現有註冊的元資料，請使用 PATCH 請求。
* 回應中不包含中繼資料。 發送 GET 請求來閱讀。

### 擷取元資料

您可以使用管理員或學習者憑證擷取中繼資料。 請求依 token 類型而異。

| 代幣 | 獲得一次報名 | 列出學習路徑報名 |
|---|---|---|
| 行政 | `GET /primeapi/v2/users/{userId}/enrollments/{enrollmentId}` | `GET /primeapi/v2/users/{userId}/enrollments?filter.loTypes=learningProgram` |
| 學習者 | `GET /primeapi/v2/enrollments/{enrollmentId}`<br>`GET /primeapi/v2/learningObjects/{id}?include=enrollment` | `GET /primeapi/v2/enrollments?filter.loTypes=learningProgram` |

>[!NOTE]
>
>此 `include=enrollment` 參數僅適用於學習者標記。 此功能不支援管理員角色。

回應會回傳 `metadata` 包含學習路徑註冊的物件。

### 在無頭與外部入口網站中使用元資料

外部入口網站與整合使用相同的 API 呼叫。 請使用與你門戶所使用的令牌相符的請求。

* **在入口網站顯示值：** 從上方表格中發送 GET 請求，針對您的令牌類型，並從回應中讀取物件 `metadata` 。
* **從外部系統（例如商務平台）更新值：** 使用管理員權杖傳送 PATCH 請求。

## 作業 API：使用 generateCustomReport 匯出報告建構器報告

Adobe Learning Manager 2026 年 12 月版本在 Job API 中新增了一種新的 `generateCustomReport`工作類型 。 使用它以自動方式匯出您在 Report Builder 中建立的任何報告，方法是傳遞報告 ID。

結合報告建構器中的新 L2 測驗資料集，您現在可以：

* 將跨多個課程與模組的題目層級（L2）測驗資料匯出於單一報告，而非每門課程只執行 `generateQuizReport` 一次。
* 自動化定期匯出，例如每日增量匯出至資料倉儲或 BI 工具。

現有的工作類型（包括 `generateQuizReport`）保持不變。

### 開始之前

* 你必須是管理員。 其他職位無法提供該 `generateCustomReport` 職務類型。
* 先在 Report Builder 中建立並儲存報告。 對於 L2 測驗資料，請從 L2 測驗資料集建立報告，並包含你需要的題目層級欄位，例如題目文本、學習者回答、分數、嘗試次數及答題日期。
* 請注意報告的識別碼。 你在請求中傳達為 `reportId`。

### 建立工作

**端點**

```
POST /primeapi/v2/jobs
```

**請求機構**

```json
{
  "data": {
    "type": "job",
    "attributes": {
      "description": "Daily L2 quiz export",
      "jobType": "generateCustomReport",
      "payload": {
        "reportId": "1478"
      }
    }
  }
}
```

**屬性**

| 屬性 | 必需 | 說明 |
|---|---|---|
| `jobType` | 是的 | 一定是 `generateCustomReport`。 |
| `payload.reportId` | 是的 | 已儲存的 Report Builder 報表的 ID，以字串形式呈現。 必須是正整數，以字串傳入，例如 `"1478"`。 傳送數字 0、負數、小數或空值會回傳錯誤。 |
| `description` | 不 | 你對該職務所選擇的描述。 |
| `callbackUrl` | 不 | 工作完成時要呼叫的 URL。 運作方式和其他工作類型一樣。 |
| `payload.filters` | 不 | 請參見下方章節。 |

### 覆寫日期篩選器（可選） {#override-date-filter}

```json
"payload": {
  "reportId": "1478",
  "filters": [
    { "columnName": "L2 Quiz - Response - Timestamp", "operator": "gte", "val": "2026-11-15T00:00:00.000Z" }
  ]
}
```

* 它僅取代報告中本次執行的儲存日期篩選條件。 匯出 `val` 涵蓋（包含）直到工作執行為止。
* `columnName` 使用格式 `<Dataset name> - <Field name>`。 它必須符合報表中已存在的日期篩選條件。 它不區分大小寫，但間距和連字號必須完全一致。
* `operator` 為選填，且僅 `gte` 允許。
* `val` 是過去 7 天內的 ISO 8601 UTC 時間。 時間被截斷到秒。
* 你可以覆蓋多個欄位。 清單為空表示已儲存的篩選條件已被使用。
* 使用情境：每日增量匯出，從前一次匯出結束處開始。

### 建立工作時回傳的錯誤

| 原因 | 訊息 |
|---|---|
| `reportId` 失蹤 | `reportId is required` |
| `reportId` 不是正整數字串 | `reportId must be a positive integer string` |
| 日期非 ISO 格式 | `filters.val must be in ISO format, e.g. 2020-01-01T18:30:00.000Z` |
| 日期超過 7 天或未來 | `filters.val must be within the last 7 days` |
| 除 `gte` | `filters.operator must be gte` |
| 同一欄位重複出現 | `Duplicate filter column: <column>` |
| 欄位不是報告中的篩選器 | `Unsupported custom report filter column: <column>` |
| 同一報告的作業仍在執行中 | `There exists an similar job with id = <jobId> which has not finished yet` |

只有在執行作業時會偵測到已儲存報表定義的問題。 此時，工作狀態會變成 `Failed`，且不返回任何理由。

### 報告要求

如果報告不符合以下條件，作業會失敗並出現錯誤訊息：

* 報告定義包含相對日期篩選器，例如最近 7 天。
* 報告中的每個日期篩選器必須涵蓋 7 天或更短，而非只有一天。
* 固定日期範圍（包含固定開始與結束日期）不被支援，作業就會失敗。
* 沒有日期篩選器的報告會失敗。 這包括建立在沒有日期欄位的資料集上的報表。

>[!NOTE]
>
>POST 請求會立即驗證。 HTTP 400 拒絕無效請求，原因在 `source.info`中。

### 檢查工作狀態並下載報告

**端點**

```
GET /primeapi/v2/jobs/{jobId}
```

回應使用與其他工作類型的相同結構。 當工作完成時， `status.code` 為 `Completed`，且 `status.data.s3Url` 包含下載連結。

```json
{
  "data": {
    "type": "job",
    "id": "12345",
    "attributes": {
      "jobType": "generateCustomReport",
      "payload": {
        "reportId": "1478"
      },
      "status": {
        "code": "Completed",
        "data": {
          "s3Url": "valid for 7 days"
        }
      }
    }
  }
}
```

API 回傳 `Submitted`、 和 `Completed` `Failed`。 該檔案是一個名為 `report.csv`的單一 CSV 檔案。

>[!NOTE]
>
>下載網址有效期為七天。 工作完成後立即下載檔案。

>[!IMPORTANT]
>
>任何擁有連結的人都可以在不登入的情況下下載檔案。 把連結當作對待其中所包含的資料一樣來處理。

**失敗的工作範例**

```json
"status": { "code": "Failed" }
```

### 限制

同一報告一次只能執行一個 `generateCustomReport` 工作。 第二次請求會被拒絕，直到第一次申請完成。

### L2 測驗報告輸出

當您在 Report Builder 中從 L2 測驗資料集建立報告並以 `generateCustomReport`匯出時，輸出具有以下特性：

* 輸出是一個名為 `report.csv`的單一 CSV 檔案。 模組是檔案中的一個欄位。 如果您選擇課程，報告只會回傳其測驗模組。
* 每一列代表一位學習者在一次嘗試中對同一題目的回應。
* 資料依標準 Report Builder 週期更新一次（約每 15 分鐘一次）。
* 日期與時間值皆為您帳戶的時區。 欄位標題會顯示時區，例如 `L2 Quiz - Response - Timestamp (America/Argentina/Salta)`。

### L2 測驗資料集中的欄位

| 類別 | 欄位 |
|---|---|
| 學習者 | 使用者 ID |
| 河道 | 課程 ID、課程實例 ID、課程名稱 |
| 模組 | 模組 ID、模組名稱、模組版本 |
| 問題 | 問題編號、問題文本、正確答案、互動類型 |
| 回應 | 回應答案、已達成分數、最高可能分數正確、回應時間戳記 |
| 嘗試 | 嘗試次數 |

>[!NOTE]
>
>L2 測驗資料集並未與其他報告建構器資料集連結。 此報告中無法提供學習者姓名、電子郵件、經理及自訂屬性。 若要將一列與學習者匹配，請使用使用者 ID。

您也可以匯出以其他報表建構器資料集建立的報表，並搭配 `generateCustomReport`。 輸出中可用的欄位取決於資料集。

## 建立與管理 Zoom 連接器的 API

使用這些 API 管理 Adobe Learning Manager 中的 Zoom 連線。 您可以擷取現有連線、儲存 Zoom 認證、建立或更新連線、設定使用者群組與自訂角色的存取權限，以及啟用或停用連線。

### 設定 Zoom 連接器 API

設定和管理 Zoom 連接器需要四個 API 呼叫。 按以下順序製作：

| 步驟 | API | 它的功能 |
|---|---|---|
| 1 | `POST /ctr/authcred/uuid/20012` | 儲存 Zoom 憑證。 |
| 2 | `POST /ctr/app/esconnect` | 建立 Zoom 連線，或更新現有連線。 |
| 3 | `PUT /ctr/xtsa/{connectionId}/access` | 設定可以使用該連線的使用者群組與自訂角色。 |
| 4 | `POST /ctr/xtsas/{connectionId}/enable` | 啟用或停用該連線。 |

>[!NOTE]
>
>這些 API 使用已登入的整合管理工作階段。 它們不使用 API 金鑰或 OAuth 令牌。

### 基礎網址與慣例

Zoom 連接器 API 使用以下慣例：

| 商品 | 價值 |
|---|---|
| 基礎網址 | `https://learningmanagerstage1.adobe.com` |
| 內容類型 | `application/json` |
| Authentication | 已登入整合管理員的工作階段 |
| 必填標頭 | `content-type`、、 `accept`、 `x-acap-caller-role: ROLE_INTEGRATIONADMIN`、 `x-csrf-token`、以及 `Cookie` |
| Zoom UUID 整合目錄 | `20012` |
| 連線限制 | 50 個 Zoom 連線 |

該`x-csrf-token`值嵌入於整合管理頁面的 HTML 中。`csrfToken`標 `Cookie` 頭會承載已登入管理員的工作階段 Cookie。

### 開始之前

- 以整合管理員身份登入。
- 建立 Zoom 伺服器對伺服器的 OAuth 應用程式。 記下它的用戶端 ID、用戶端密鑰與帳戶 ID。 你還需要 Zoom 超級管理員的電子郵件地址。
- 打電話 `GET /ctr/xtsas/canCreateAccount/25`。 如果你能建立另一個 Zoom 連線，它會回傳 `true` 。

### 步驟 1：儲存 Zoom 認證 {#save-credentials}

在建立或更新連線之前，請呼叫此 API。 它儲存連接器用來連接 Zoom 的憑證。

```
POST /ctr/authcred/uuid/20012
```

若要更新現有連線，請新增 `connectionId` 查詢參數：

```
POST /ctr/authcred/uuid/20012?connectionId={connectionId}
```

請求主體是以 JSON 文字形式呈現的憑證。 它是包含 JSON 的 JSON 字串，而非巢狀物件。 請附上外側的引號。

| 索引鍵 | 說明 |
|---|---|
| `clientId` | Zoom 應用程式的用戶端 ID。 |
| `clientSecret` | Zoom 應用程式的客戶端祕密。 這個數值很敏感。 |
| `accountId` | Zoom 帳號 ID。 |
| `superAdmin` | Zoom 超級管理員的電子郵件地址。 |

範例請求正文：

```
"{\"clientId\":\"<ZOOM_CLIENT_ID>\", \"clientSecret\":\"<ZOOM_CLIENT_SECRET>\", \"accountId\":\"<ZOOM_ACCOUNT_ID>\", \"superAdmin\":\"<ADMIN_EMAIL>\"}"
```

範例 `200 OK` 回應：

```json
{
  "code": 0,
  "description": "Success"
}
```

`code: 0` 表示憑證已被保存。

### 步驟 2：建立或更新 Zoom 連線 {#create-connection}

此 API 會建立 Zoom 連線。 同一端點也會更新現有連線。

```
POST /ctr/app/esconnect
```

請求主體包含以下欄位：

| 場地 | 必需 | 說明 |
|---|---|---|
| `UUID` | 是的 | 整合型錄 UUID。 用於 `20012` Zoom。 |
| `listOfConnections` | 是的 | 建立連結。 寄一件商品。 |
| `listOfConnections[].name` | 是的 | 連接器的顯示名稱，例如 `Zoom_Partner_X`。 |
| `listOfConnections[].tag` | 是的 | 建立連接器時傳送空字串（`""`）。 更新時省略它。 |
| `listOfConnections[].credentialsJson` | 是的 | 憑證以 JSON 文字形式呈現。 使用你在步驟 1 中寄出的同一個字串。 |
| `listOfConnections[].schedules` | 是的 | 同步排程。 發送 `objectUUID` 10002、 `priority` 1 和 `type` 1。 |
| `listOfConnections[].id` | 僅更新 | 要更新的連線 ID，例如 `3474737`。 |

範例請求正文：

```json
{
  "UUID": 20012,
  "listOfConnections": [
    {
      "name": "Zoom_Example",
      "tag": "",
      "credentialsJson": "{\"clientId\":\"<ZOOM_CLIENT_ID>\", \"clientSecret\":\"<ZOOM_CLIENT_SECRET>\", \"accountId\":\"<ZOOM_ACCOUNT_ID>\", \"superAdmin\":\"<ADMIN_EMAIL>\"}",
      "schedules": [
        { "objectUUID": 10002, "priority": 1, "type": 1 }
      ]
    }
  ]
}
```

範例 `200 OK` 回應：

```json
[3474737]
```

回應是一個包含新連線 ID 的 JSON 陣列。 請在步驟 3 和 4 以及任何後續通話中使用此 ID。

### 建立與更新比較

| 差異 | 創建 | 更新 |
|---|---|---|
| `listOfConnections[].id` | 未寄出 | 連線 ID |
| `listOfConnections[].tag` | `""` | 未寄出 |
| 憑證呼叫步驟 1 | `POST /ctr/authcred/uuid/20012` | `POST /ctr/authcred/uuid/20012?connectionId={id}` |

### 步驟 3：設定誰可以使用此連線 {#set-access}

此 API 定義哪些使用者群組與自訂角色可以使用此連線。

```
PUT /ctr/xtsa/{connectionId}/access
```

路徑使用單數 `xtsa` 作為一個連接。 複數 `xtsas` 是連結的集合。

請求主體是一個 JSON 陣列。 每個項目會授予一個使用者群組或自訂角色的存取權。

| 場地 | 必需 | 說明 |
|---|---|---|
| `accessType` | 是的 | `USER_GROUP` 或 `CUSTOM_ROLE`。 |
| `accessId` | 是的 | 使用者群組或自訂角色的 ID，以字串形式呈現。 |

範例請求正文：

```json
[
  { "accessType": "USER_GROUP", "accessId": "<groupId>" },
  { "accessType": "CUSTOM_ROLE", "accessId": "<roleId>" }
]
```

當存取清單被儲存時，API 會回傳 `204 No Content` 任何實體。

>[!NOTE]
>
>此請求會取代整個存取清單。 它不會附加在它上。 任何不在體內的東西都會失去存取權。 若要移除所有存取，請傳送一個空陣列（`[]`）。

### 步驟 4：啟用或停用連線 {#enable-disable}

此 API 用來開啟或關閉連線。 建立連線後，只要你需要變更狀態，就可以使用它。

```
POST /ctr/xtsas/{connectionId}/enable
```

路徑使用複數形式 `xtsas`，就像 list 和 delete calls 一樣。 步驟 3 中的存取呼叫使用單數 `xtsa`。

| Path 參數 | 類型 | 說明 |
|---|---|---|
| `connectionId` | 編號 | 連線的 ID。 它是 `id` 由 回傳的 `GET /ctr/xtsas`，以及步驟 2 中回傳的 ID。 |

請求主體包含以下欄位：

| 場地 | 類型 | 必需 | 說明 |
|---|---|---|---|
| `objectUUID` | 編號 | 是的 | 連線的同步物件。 使用 `10002`，即您在步驟 2 中輸入 `schedules[].objectUUID` 的相同值。 |
| `operation` | 編號 | 是的 | 發送 `1`。 |
| `val` | 布林 | 是的 | 連線的新狀態。 發送 `false` 以停用連線。 發送 `true` 以啟用它。 |

停用連線的請求主體範例：

```json
{
  "objectUUID": 10002,
  "operation": 1,
  "val": false
}
```

啟用連線的請求主體範例：

```json
{
  "objectUUID": 10002,
  "operation": 1,
  "val": true
}
```

停用連線的範例請求：

```bash
curl -X POST 'https://learningmanagerstage1.adobe.com/ctr/xtsas/<connectionId>/enable' \
  -H 'accept: application/json' \
  -H 'content-type: application/json' \
  -H 'x-acap-caller-role: ROLE_INTEGRATIONADMIN' \
  -H 'x-csrf-token: <CSRF_TOKEN>' \
  -H 'Cookie: <SESSION_COOKIES>' \
  --data '{"objectUUID":10002,"operation":1,"val":false}'
```

要確認新狀態，請撥打 `GET /ctr/xtsas`，透過 找到連線 `id`，並檢查其 `enabled` 旗標。

>[!NOTE]
>
>標 `x-acap-caller-role` 頭必須與活動設定檔的角色相符。 對於這些 API，請使用 `ROLE_INTEGRATIONADMIN`。

### 建立連線後管理連線

您可以使用以下呼叫搭配連線 ID：

| 目的 | 叫聲 |
|---|---|
| 啟用或停用連線 | `POST /ctr/xtsas/{connectionId}/enable` |
| 讀取單一連線的存取清單 | `GET /ctr/xtsa/{connectionId}/access` |
| 所有 Zoom 連線的讀取權限 | `GET /ctr/xtsas/access?UUID=20012` |
| 列出所有連結。 Zoom 連線有 `extsysRefId` 25 個。 | `GET /ctr/xtsas` |
| 檢視連線 | `GET /ctr/app/connection/{id}/object/10002` |
| 永久刪除連線 | `DELETE /ctr/xtsas/{id}` |

>[!NOTE]
>
>檢視呼叫會以明文回傳用戶端密鑰。 將客戶端秘密視為敏感，若被揭露則輪換。 請勿提交或分享工作階段 Cookie、CSRF 權杖或憑證，包括在 HAR 檔案及複製的 cURL 指令中。

### 在您的整合中使用這些 API

常見的使用情境是為新帳戶或合作夥伴自動設定 Zoom 連接器。

1. 請致電 `GET /ctr/xtsas/canCreateAccount/25` 確認您是否能建立另一個連線。
2. 用 Zoom 帳號登入資料打電話 `POST /ctr/authcred/uuid/20012` 。
3. 使用連接器名稱、相同的憑證字串以及同步排程進行呼叫 `POST /ctr/app/esconnect` 。 從回應中讀取連線 ID。
4. 以可以使用該連線的使用者群組和自訂角色進行通話 `PUT /ctr/xtsa/{connectionId}/access` 。
5. 撥打時設定`POST /ctr/xtsas/{connectionId}/enable`&#x200B;`val`為 `true` 或`false`，以啟用或停用連線。接著打電話 `GET /ctr/xtsas` 確認 `enabled` 旗標，確認州份。
6. 若要稍後更改認證，請使用連線 ID 重複步驟 2 和 3。


