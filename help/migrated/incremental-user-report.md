---
description: 增量用戶回報工作 API 允許管理員匯出資料變更於指定日期範圍內的使用者。 這消除了完整使用者匯出的需求，並能更有效率地同步新或更新的使用者紀錄。
jcr-language: en_us
title: 增量使用者報告（工作 API）
source-git-commit: d61e81b0df6a6043b938c65adaabecb5699c2ce9
workflow-type: tm+mt
source-wordcount: '1602'
ht-degree: 0%

---


# 增量使用者報告（工作 API）

## 概觀

Adobe Learning Manager 的增量用戶報告是一項新的職缺 API 功能，允許管理員與整合開發者匯出在指定日期與時間內資料變更的使用者。 你不必每次都拉取完整使用者名單，而是可以請求一個只涵蓋新用戶或修改過使用者的目標切片。

本文件涵蓋：

- 為什麼存在增量報告以及何時使用它
- 此功能運作方式——包括變更追蹤模型
- 新增的 Job API 用於增量使用者報告（payload、參數、分頁）
- 如何管理大型帳號（5,00,000+ 用戶）
- 有軌跡與非有軌磁場的比較
- 限制與非目標

## 為什麼要使用增量報告

本節說明此功能的動機，並幫助你決定增量匯出還是完整匯出更適合你的整合。

## 完整使用者匯出的問題

目前的完整使用者匯出（生成用戶工作類型）會回傳帳號中每個使用者的每次執行。 對於大型企業帳戶，這造成兩個重大問題：

| 客戶 | 使用者量 |
|----------|-------------|
| 客戶A | 210萬用戶 |
| 客戶B | 700萬用戶 |
| 客戶C | 100萬+ 用戶 |
| 客戶D | 770萬用戶（遷移） |


* 在這些規模下，匯出管線在擷取、處理及儲存資料時，CPU 使用率約為 90%。
* 下游儀表板（PowerBI、Salesforce、自訂整合）每次執行都會重新匯入未更改的使用者紀錄，浪費頻寬和處理時間。
* 沒有辦法問「自從我上次匯出後，哪些使用者有變動？」 使用目前的 API。

## 何時使用增量報告

當你需要讓外部系統與 Adobe Learning Manager 使用者資料同步時，可以使用增量匯出功能。 典型使用案例：

* 保持企業儀表板（PowerBI、Tableau、SFDC）隨時更新使用者設定檔的變動。
* 將角色、狀態或元資料變更餵給下游的身份管理系統。
* 而是每晚或每小時執行 delta-sync 管線，而不是完全重新載入。
* 降低擁有數百萬用戶帳戶的 API 負載與資料傳輸成本。

當你需要權威基準時，例如首次設定或長時間同步間隔後，請使用完整匯出（生成用戶）。

| 匯出模式 | 當...... |
|-------------|-----------|
| 完整匯出（產生用戶） | 初始啟動;用戶數少於 5 萬的帳號;錯過同步視窗後的恢復。 |
| 增量匯出（生成UserIncrementalReport） | 定期的 delta 同步;大型帳號;只需更改紀錄的管線 |

## 目前完整用戶報告

（生成使用者）本節記錄現有的 Job API 使用者報告供參考。 如果你已經熟悉，請跳到下一節。

## 運作原理

目前使用者的 CSV 報告是透過 Jobs API 以工作形式提交的。 Snaplogic 管線會接手這個任務，對 CAPTIVATE 資料庫（使用者、使用者群組、usergroup_user資料表）執行 MySQL 查詢，然後產生 CSV 檔案。

## 可用濾鏡

有效載荷支援三種可選濾波器：

* `expandMetadata` – 傳真以匯出中繼資料作為獨立欄位。
* `fetchActiveUsers` – 通過真實以匯出僅匯出活躍用戶。
* `peerAccountId` – 產生對等帳號的用戶報告。

## CSV 欄位

匯出後的 CSV 包含以下欄位：

```
internalUserID, userEmail, customerDefinedUniqueUserId, name, managerEmail,

userType, state, excludedFromGamification, pointsEarned, profile, roles,

dateCreated, lastLoginDate, dateDeleted, uiLocale, contentLocale,

timeZoneCode, userSource, group, AF_location, AF_login, AF_externalaf,

lastSocialActivityDate
```

## 請求有效載荷

工作類型：生成使用者。 僅執行行政職務。

```
{

  "data": {

    "type": "job",

    "attributes": {

      "description": "<description of your choice>",

      "jobType": "generateUsers",

      "payload": {

        "expandMetadata": "<true to export metadata as separate column>",

        "fetchActiveUsers": "<true to export ACTIVE users only>",

        "peerAccountId": "<peerAccountId for peer account report>"

      }

    }

  }

}
```

## 限制

* 沒有基於日期的篩選——每次執行都會匯出所有使用者。
* 對於大型帳號來說不可行——超過 ~100 萬用戶，管線資源會耗盡。
* 沒有增量或三角能力。

## 增量使用者報告（生成 UserIncrementalReport）

本節記錄了 M46 新增的增量用戶回報功能。 這是本文件的主要主題。

## 什麼是增量出口？

增量匯出僅回傳在指定開始與結束日期-時間窗口內已變更的追蹤資料使用者。 後端會儲存每個使用者追蹤欄位的最後修改時間戳。 當你為某個視窗申請報告時，只有最近一次變更落在該視窗內的使用者才會被納入。

## 變更追蹤模型的運作原理

Adobe Learning Manager 維護一個最後修改的時間戳，當使用者追蹤欄位變更時，該時間戳記會更新。

當你請求帶有start_date_time和end_date_time的增量報告時，系統會回傳那些最後修改時間戳記落在start_date_time、 [end_date_time]內的使用者。 若使用者在視窗內及視窗後都被修改（即在end_date_time後再次更改），該使用者不會被包含在報告中——因為其最後修改的時間戳記已超出視窗範圍。

>[!NOTE]
>
>這表示增量匯出會捕捉最近變更在指定視窗內的使用者，而非所有在該視窗中任何時刻被觸及的使用者。

## 追蹤變化欄位

若以下任何欄位變更，該使用者將被納入增量報告：

| 場地 | 筆記 |
|---|---|
| 用戶電子郵件 | 使用者的電子郵件地址 |
| 名稱 | 使用者名字 |
| 經理身份 | 使用者資料表儲存 managerId。 如果 managerID 改變，該欄位會被標記為更改。 如果只有經理的電子郵件（同一 managerID）有變動，這個欄位就不會被視為更改。 |
| 類型 | 內部或外部使用者分類 |
| 州 | 活躍或刪除 |
| 簡介 | 使用者設定檔指派 |
| 角色 | 角色新增或刪除 |
| uiLocale | 使用者介面區域 |
| 內容地點 | 內容地點 |
| 時區代碼 | 使用者時區 |
| 主動場域（AF_*） | 所有已設定的活動欄位，例如 AF_location、AF_login |
| 元資料 | 所有已設定的元資料欄位 |

## 欄位未被追蹤以進行變更

以下欄位會出現在 CSV 輸出中，但當它們變更時，並不會觸發納入增量匯出：

* 排除於遊戲化之外
* 積分獲得
* 最後登入日期
* 日期已刪除
* 日期已創建
* 使用者來源
* 最後社交活動日期

## 輸出格式

增量式 CSV 報告的欄位與格式與完整使用者的 CSV 報告相同。 所有欄位的出現順序相同，包括所有活躍欄位與元資料欄位——不論匯出使用者更換了哪些欄位。

>[!NOTE]
>
>若新增活躍欄位或移除現有欄位，所有受該變更影響的使用者將出現在下一次增量匯出中。 來自新活躍欄位的新欄位會附加在報告末尾，以避免以欄位位置為關鍵的現有整合中斷。

## 新增增量使用者報告職缺 API

增量使用者報告使用 Job API 產生一個 CSV 檔案，該檔案包含在指定日期與時間期間內被追蹤資料變更的使用者。 對於大型結果集，請使用本文件後述的分頁模型：在每個請求中提交相同的日期視窗，並將上一個回應中收到的最後一個 userID 傳達為 fromUserId，以取得下一個區塊。

## 工作類型

工作類型：生成UserIncrementalReport

## 請求有效載荷

```
{

    "data": {

        "type": "job",

        "attributes": {

            "description": "description of your choice",

            "jobType": "generateUserIncrementalReport",

            "payload":{

                 "fullExport": <Pass true to export all users. If fullExport is true, fromDate and toDate are ignored>,

                 "expandMetadata": <Pass true to export metadata as separate columns>,

                 "fromDate": <Start of the change window in ISO format, for example 2020-01-01T18:30:00.000Z>,

                 "toDate": <End of the change window in ISO format, for example 2020-01-31T18:30:00.000Z>,

                 "fromUserId": <For paginated requests, pass the last userId received in the previous response>

            }

        }

   }

}
```

## 有效載荷參數

| 參數 | 類型 | 說明 |
|---|---|---|
| 出自日期 | 弦（ISO 8601） | 這是增量出口的必要條件。 變更視窗開始。 請使用ISO 8601格式。 |
| 至今 | 弦（ISO 8601） | 這是增量出口的必要條件。 變動窗口結束。 請使用ISO 8601格式。 |
| fromUserID | 弦 | 選填。 對於分頁請求，將上一個回應中最後收到的 userID 傳給 fromUserId。 第一個請求省略這個參數。 |
| 擴展元資料 | 布林值 | 選填。 如果屬實，則會將元資料匯出為獨立欄位。 |

對於增量匯出，通過 `fromDate` 並 `toDate` 定義變更視窗。 若結果集大於一個區塊，繼續分頁，發送相同 `fromDate` 區塊， `toDate` 並將前一個回應的最後 `userId` 一個傳遞為 `fromUserId`。 如果 fullExport 為真，則忽略日期視窗，API 會產生完整的使用者匯出。

## 處理大型帳號（500k+ 用戶）

使用者報告透過資料平台管道產生，輸出則分段回傳，以支援大型帳號。 若增量出口涵蓋超過 50 萬用戶，報告會被分頁。

## 分頁模型

若要取得所有頁面以進行大型增量匯出，請在每個請求中傳遞相同的 startDateTime 與 endDateTime，並額外將上一區塊中最後收到的使用者的 UserID 作為 fromUserId。 API 會回傳下一組最多 500,000 位使用者 ID 大於傳送的 fromUserId。

## 分頁工作流程

步驟 1：提交第一個請求，不包含 fromUserID。

```
// First request – no fromUserId

{

  "payload": {

    "startDateTime": "2026-05-01T00:00:00Z",

    "endDateTime": "2026-05-31T23:59:59Z"

  }

}
```

步驟二：接收第一批（最多 500,000 名使用者）。 請注意回覆中最後的使用者 ID。

步驟 3：提交下一個請求，經過相同日期視窗及上一次回應的最後使用者 ID，作為 fromUserId。

```
// Subsequent request – pass last userId from previous response as fromUserId

{

  "payload": {

    "startDateTime": "2026-05-01T00:00:00Z",

    "endDateTime": "2026-05-31T23:59:59Z",

    "fromUserId": "<last userId from previous response>"

  }

}
```

步驟四：重複此步驟，直到回應回傳少於50萬筆紀錄，表示已瀏覽最後一頁。

| 請求 | fromUserID 參數 |
|---|---|
| 第一頁 | 省略 fromUserID |
| 第二頁 | 將第一頁的最後一個使用者 ID 傳入 fromUserID |
| 第三頁 | 將第二個頁面的最後一個使用者 ID 傳入 fromUserID |
| …（繼續） | … |
| 最後一頁 | 回應記錄少於50萬筆 |

>[!NOTE]
>
>確保你`startDateTime``endDateTime`在所有分頁請求中保持相同，針對單一匯出執行。在分頁中途更改日期視窗會產生不一致的結果。

## 限制

增量用戶回報是刻意設定範圍的。 以下能力不在範圍內：

* 不是使用者稽核報告——它沒有列出哪些欄位被更改。
* 沒有舊值/新值比較——報告僅顯示目前欄位值。
* 沒有每次變更的時間戳記——個別欄位修改的時間不會顯示。
* 沒有顯示變更次數——一個修改一次的使用者和修改十次的使用者在匯出中會完全相同。
* 現有的報表格式未變——CSV 欄位結構與完整使用者報表相同。

## 連接器整合

增量使用者報告設計用於 Adobe Learning Manager 連接器（PowerBI、Salesforce 等），作為一般同步管線中完整使用者報告的直接替代。 這使得現今使用 generateUsers 的連接器能夠遷移到增量模型，而無需更改下游資料結構。

* 輸出的 CSV 與完整使用者報告欄位相容。
* 連接器可以使用增量報告進行差異同步，並回退完整報告以進行自舉或恢復。
* 支援連接器整合（PowerBI、SFDC）
