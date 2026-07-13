---
jcr-language: en_us
title: Webhooks 使用指南
description: 了解 Webhook 的使用、最佳實務與限制
contentowner: chandrum
exl-id: e6a63ffb-7fdd-46e4-b5e6-20ce36861cef
source-git-commit: 4c04757d78d599ca30e3cd26257a967d5b9e3fdc
workflow-type: tm+mt
source-wordcount: '3412'
ht-degree: 0%

---

# Webhooks 使用指南

Webhook 是一種讓網頁應用程式能自動且即時地彼此通訊的方式。

與傳統 API 等待使用者請求資訊不同，即時 API 在資料發生的瞬間即刻共享。 Webhook 作為即時 API，並在指定事件發生時立即協助分享資料。

## 實體

要理解 webhook 事件，首先需要了解相關實體及觸發條件。

### 學習物件

以下是支援的學習對象（課程、學習路徑或認證）事件。

#### 選秀

每當從 UI 建立學習物件時，它會以 **草稿** 模式開始。 這表示學習對象尚未公開，且無法提供給學習者使用。 **只要學習對象仍為草稿，LEARNING_OBJECT_DRAFT**&#x200B;事件就會被觸發。任何後續的草稿更新也會觸發此事件。

#### 更新

一旦學習對象被發佈，其狀態會從&#x200B;**草稿（Draft）變**&#x200B;為已發佈（Published ****）。在此轉換期間，Webhook 會&#x200B;**產生 LEARNING_OBJECT_MODIFICATION** 事件，因為學習物件正從草稿（Draft **）被修改**&#x200B;為&#x200B;**發佈（Published**）。所有後續對 LO 的修改與更新也會觸發 **LEARNING_OBJECT_MODIFICATION** 事件。

**當學習對象被退休時，LEARNING_OBJECT_MODIFICATION**&#x200B;事件也會被觸發。此退休操作標記底層實例為已更新，因為當父學習物件處於退休狀態時，這些實例會被退休。

#### 刪除

刪除學習對象後， **會產生LEARNING_OBJECT_DELETION** 事件。 此事件表示該學習對象已被刪除，且不再可供學習者存取。

除了即時事件外，學習物件事件還有一個批次（非即時）對應事件，作為LEARNING_OBJECT_MODIFICATION_BATCH **事件的一部分**&#x200B;被觸發。此事件發生在遷移工作流程中建立或修改學習物件時。 由於遷移不支援學習物件草圖與刪除操作，因此這些動作沒有對應的草稿或刪除事件。

### 學習物件實例

以下是用於學習物件實例所支援的事件。

#### 更新

一旦建立 **實例，LEARNING_OBJECT_INSTANCE_MODIFICATION** 事件就會產生。 Adobe Learning Manager 中的學習物件實例沒有 **草稿** 狀態;因此 Adobe Learning Manager 不支援 **LEARNING_OBJECT_INSTANCE_DRAFT 事件**。 此事件會在實例被建立、修改或退休時產生。

除了在實例建立、更新或退休時產生，當父學習物件被標記為 **退休**&#x200B;時，此事件也會自動產生。 這是因為當學習物件被退休時，底層實例也必須標記為 **已退休** 。

#### 刪除

當實例被刪除時， **會產生LEARNING_OBJECT_INSTANCE_DELETION** 事件。 此事件僅適用於包含自定進度模組的課程實例，因為 Adobe Learning Manager 僅允許管理員刪除模組類型為自定進度的課程實例。 Adobe Learning Manager 不支援其他類型的課程模組明確刪除，不支援學習路徑實例或認證實例。

學習物件實例還有一個非即時的對應物，作為LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH **事件的一部分**&#x200B;被揭露。此事件會在遷移工作流程中建立或修改學習物件實例時觸發。 由於遷移中不支援學習物件實例的草稿或刪除操作，因此無法提供相應的草稿或刪除事件。

### 招生情況

一旦學習者執行註冊操作，就會觸發即時註冊事件。 根據學習物件類型，即時註冊事件可分為以下類別之一：

* COURSE_ENROLLMENT
* LEARNING_PATH_ENROLLMENT
* CERTIFICATION_ENROLLMENT

註冊活動除了這些即時事件外，還有批次對應活動。 每當管理員、經理或平台觸發註冊時，就會觸發非即時的註冊事件。 根據學習物件類型，批次註冊事件可以是以下其中一種：

* COURSE_ENROLLMENT_BATCH
* LEARNING_PATH_ENROLLMENT_BATCH
* CERTIFICATION_ENROLLMENT_BATCH

### 退學

當學習者執行退學動作時，會觸發即時退選事件。 根據學習對象類型，即時退學事件可分為以下類別之一：

* COURSE_UNENROLLMENT
* LEARNING_PATH_UNENROLLMENT
* CERTIFICATION_UNENROLLMENT

除了這些活動外，還有批次退學活動。 每當管理員、經理或平台標記退名時，會觸發非即時退選事件。 根據學習物件類型，批次取消註冊事件可以是以下其中一種：

* COURSE_UNENROLLMENT_BATCH
* LEARNING_PATH_UNENROLLMENT_BATCH
* CERTIFICATION_UNENROLLMENT_BATCH

### 完工

當學習者完成學習對象時，即時完成事件會被觸發。 根據學習物件類型，即時完成事件可分為以下類別之一：

* COURSE_COMPLETED
* LEARNING_PATH_COMPLETED
* CERTIFICATION_COMPLETED

除了這些即時事件外，還有批次完成事件。 例如，當管理員、管理者或平台標記學習對象為完成時，非即時完成事件會被觸發。 根據學習物件類型，批次完成事件可分為以下類別之一：

* COURSE_COMPLETED_BATCH
* LEARNING_PATH_COMPLETED_BATCH
* CERTIFICATION_COMPLETED_BATCH

### 學習者進展

每當學習者註冊學習對象並開始模組時，都會追蹤其進度。 這些數據包含在 **LEARNER_PROGRESS** 事件中。 由於進度追蹤依賴複雜的聚合邏輯，且非即時，活動可能會延遲最多15分鐘。

### CI 統計

**CI_STATS**&#x200B;即時事件會在課程實例的名額或候補名單有變動時觸發。這些資料僅在實例層級被捕捉。 此外，此事件僅針對課程觸發，其他學習路徑或證照則不觸發，因為名額與候補名單是課程及其實例特有的屬性。

## 事件順序

Adobe Learning Manager 確保每個帳號的事件順序皆有排序。 然而，在報名或完成與進度事件之間的訊息關聯時，可能會存在差異。 這是因為學習者進度事件可能延遲最多15分鐘，因為進度追蹤依賴複雜的彙整邏輯，而非即時進行。 此外，進度事件來自不同的資料來源，因此其順序無法保證與註冊及完成事件的關聯。 因此，Adobe Learning Manager 在聆聽這些活動時，為客戶提供最佳實務。

如果完成事件發生在學習者進度事件之前，客戶可以忽略學習者進度事件。 這是因為學習者進度事件可能延遲最多 15 分鐘，而完成事件則可能在收到進度事件前觸發。 由於收到完成事件表示學習對象已完成，表示進度已達到 100%。

在少數情況下，註冊事件發生在學習者進度事件之後，客戶可以忽略該註冊事件。 這是因為學習者註冊學習對象後，進度才能被追蹤。 換句話說，收到進度事件表示學習對象已被啟動，而這只會在成功註冊後發生。

## 即時事件與批次事件

如前所述，某些事件有即時與非即時對應。 可能會有人問什麼時候該訂閱即時事件，什麼時候訂閱非即時事件。 以下是根據上述實體可遵循的指引。

### 即時事件

| S.No | Webhook 活動 | 說明 |
|---|---|---|
| 1 | CI_STATS | 當課程實例有座位變動或候補名單可用時會觸發。 |
| 2 | COURSE_ENROLLMENT | 當學習者報名課程時觸發。 |
| 3 | COURSE_COMPLETED | 當學習者完成課程時觸發。 |
| 4 | LEARNING_PATH_ENROLLMENT | 當學習者註冊學習路徑時觸發。 |
| 5 | LEARNING_PATH_COMPLETED | 當學習者完成學習路徑時會觸發。 |
| 6 | CERTIFICATION_ENROLLMENT | 當學習者報名認證時會觸發。 |
| 7 | CERTIFICATION_COMPLETED | 當學習者完成認證時會觸發。 |
| 8 | COURSE_UNENROLLMENT | 當學習者退選課程時觸發此機制。 |
| 9 | LEARNING_PATH_UNENROLLMENT | 當學習者從學習路徑退選時觸發。 |
| 10 | CERTIFICATION_UNENROLLMENT | 當學習者退辦認證時會觸發此機制。 |
| 11 | LEARNING_OBJECT_DRAFT | 在建立學習物件於草稿狀態時觸發。 |
| 12 | LEARNING_OBJECT_DELETION | 在刪除學習物件時觸發。 |
| 13 | LEARNING_OBJECT_MODIFICATION | 在修改學習對象時觸發。 |
| 14 | LEARNING_OBJECT_INSTANCE_MODIFICATION | 在建立或修改學習物件實例時觸發。<div><b>注意：</b> 建議僅在課程發布後使用課程實例。</div> |
| 15 | LEARNING_OBJECT_INSTANCE_DELETION | 在刪除學習物件實例時觸發。 |

### 非即時事件

| S.No | Webhook 活動 | 說明 |
|---|---|---|
| 1 | COURSE_ENROLLMENT_BATCH | 當管理員/經理/平台註冊學習者參加課程時，會觸發此功能。 |
| 2 | COURSE_COMPLETED_BATCH | 當管理員/經理/平台標記課程為已完成時會觸發。 |
| 3 | LEARNING_PATH_ENROLLMENT_BATCH | 當管理員/經理/平台將學習者註冊到學習路徑時會觸發。 |
| 4 | LEARNING_PATH_COMPLETED_BATCH | 當管理員/經理標記學習路徑為完成時會觸發。 |
| 5 | CERTIFICATION_ENROLLMENT_BATCH | 當管理員/經理/平台為學習者報名認證時會觸發。 |
| 6 | CERTIFICATION_COMPLETED_BATCH | 當管理員/經理/平台標記認證為完成時會觸發。 |
| 7 | LEARNER_PROGRESS | 追蹤學習者完成模組後的進度。 |
| 8 | COURSE_UNENROLLMENT_BATCH | 當管理員/經理/平台取消課程學習者的報名時會觸發。 |
| 9 | LEARNING_PATH_UNENROLLMENT_BATCH | 當管理員/經理/平台將學習者從學習路徑中退役時觸發。 |
| 10 | CERTIFICATION_UNENROLLMENT_BATCH | 當管理員/經理/平台取消學習者認證註冊時會觸發。 |
| 11 | LEARNING_OBJECT_MODIFICATION_BATCH | 在透過遷移工作流程修改學習物件時觸發。 |
| 12 | LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH | 在透過遷移工作流程建立或修改學習物件實例時觸發。 |

### 學習對象及其實例

* 隨時訂閱即時事件，隨時聆聽管理員、作者等角色透過 UI 動作對學習物件所做的變更。
* 只要想收聽遷移工作流程中學習物件的變更，隨時訂閱非即時或批次事件。

### 報名、退選與完成

* 隨時訂閱即時活動，聆聽學習者報名、退選或完成的活動。
* 只要你想收聽管理員、管理員、平台等標記的註冊、取消或完成，都可以訂閱非即時或批次事件。

### 學習者進展

* 想收聽學生進度時，歡迎訂閱活動。

>[!NOTE]
>
>在上述情境（註冊、取消註冊、完成與進度）中，由 userId 與 loInstanceId 組成的屬性合成可以唯一識別記錄。

### 球場實例統計

* **隨時訂閱即時CI_STATS**&#x200B;活動，隨時掌握座位或候補名單變動。

## Webhook 事件有效載荷

作為 Webhooks 回應有效載荷的一部分，Adobe Learning Manager 會發出唯一識別實體所需的屬性。 這些資料將以相同格式並依據公開 API 使用的標準發布，確保 webhook 資料與公開 API 資料同步。 查看 [範例有效載荷](/help/migrated/integration-admin/feature-summary/webhooks-usage-guide.md#sample-payloads-for-the-events) ，以查看各事件的有效載荷。

## 利用 webhook 建立外部資料庫或通知服務

我們聽說 Webhooks 可能有用的一個應用場景是用來建立客戶端的資料庫。 Adobe Learning Manager 有自己的資料庫和架構，但客戶無法存取。

問題是：客戶如何利用 webhook 事件建立資料庫？

由於 Adobe Learning Manager 不會直接揭露資料表記錄與結構，客戶可依賴 Webhooks 解決方案，透過消費事件來建立外部資料庫。 在本版本中，我們提供學習物件、學習物件實例、註冊、退辦、完成、進度及課程實例統計等事件。

### 從學習物件事件建立資料庫

學習物件事件會揭 `loId` 露並 `loType` 識別一個實體。 然而，僅憑這些屬性不足以建立外部學習物件資料庫。 客戶需要額外欄位來進一步描述學習物件。取得額外資料有兩種方法：

#### 產生一個訓練資料報告來擷取所有資料

這種方法應該用於透過遷移等工作流程大量建立學習物件時。 這裡的目標是產生 **[!UICONTROL Training Data]** 包含所有學習物件的報告，作為遷移工作流程的一部分。 為了優化匯入流程，建議將匯出開始時間設定為遷移觸發的時間。 這將確保只有透過遷移帶來的學習物件會匯出到報告中，因為歷史資料已經存在於客戶的資料庫中。

#### 查詢公開 API 的資訊 GET /learningObjects - 管理員範圍

當透過即時工作流程建立學習物件時，應採用此方法。 客戶應該有自己的快取層，來批次處理事件中發出的學習物件，然後透過傳遞這些學習物件 ID 來 `GET /learningObjects` 查詢 API。 設有快取層的原因是為了確保不會超過公開 API 的速率限制。 目前，我們的管理員速率限制是每小時` GET /learningObject` 500 個 API 請求。 若超過此限制，公共 API 服務將回應 **HTTP 429 請求過多**&#x200B;訊息。

### 從學習物件實例與CI_STATS事件建立資料庫

學習物件實例事件會 `loInstanceId`為課程與學習路徑發出 、 `loId`、 `loType` 及屬性。 同樣地，**CI_STATS**&#x200B;事件僅適用於課程，因為 `seatLimit`、 `waitListLimit``seatAvailability`、 、 `waitlistAvailability`等 僅適用於課程。

在某些使用情境中，需要額外的實例資料，如實例名稱、狀態等。 要取得額外的實例資料，應遵循以下方法：

#### 查詢 public-api GET /learningobjects - 管理員範圍的資訊

客戶可如前所述使用 `GET /learningObjects` 該 API，並附帶實例以取得實例資訊。 他們仍應遵循該 [條文](/help/migrated/integration-admin/feature-summary/webhooks-usage-guide.md#query-the-information-from-the-public-api-get-learningobjects-admin-scope) 所述的做法，以確保費率限制不會被違反。


>[!NOTE]
>
>1. 認證在 ALM 裡沒有實例的概念。
>2. 不需要額外擷取資料CI_STATS因為相同的資訊已經作為學習物件實例事件的一部分被擷取。

### 從註冊、退選、完成及進度事件建立資料庫

學習者註冊、退選、完成及進度會以獨立事件形式在 Adobe Learning Manager 中發布。 學習者以 `userId` 屬性來識別。 然而，在某些情況下，客戶端的下游工作流程可能需要額外的學習者資訊，如姓名、電子郵件等。 要取得這些資料，客戶可以依照以下方法進行：

#### 從管理員或連接器匯出使用者報告

當涉及大量登記工作流程時，如大量註冊、大量退團等，都應遵循此方法。Adobe Learning Manager 的使用者報告包含所有與使用者相關的資訊。 透過將 webhook 事件所得的資訊 `userId` 關聯起來，客戶可以查詢這個報告（可能在客戶端以資料庫、快取或 API 端點的形式呈現），以取得更多細節，如名稱、電子郵件、UUID 等。這種方法可以用來每週或每日同步使用者。

#### 來自公開 API 的查詢資訊 GET /users - 管理員範圍

當上述報告中使用者無法使用時，可採用此方法。 方法1與方法2的結合確保所有過去建立的現有使用者都能被覆蓋 **[!UICONTROL User Report]**，而新創建的使用者仍可從API中擷取。 如果沒有 **[!UICONTROL User Report]** 資料，客戶可以將 userID 作為輸入參數傳送到 `GET /users` API，以取得使用者資訊。 這些資訊應在客戶端快取，以防止同一組使用者重複呼叫公開 API。 請注意，我們目前對 GET /users API 的管理員速率限制為每小時 500 筆請求。 超過此限制的任何請求都會導致 **HTTP 429 過多請求** 回應。

## 容錯性

ALM webhook 系統的容錯系統會建議用戶處理潛在問題，例如事件遺失、重複事件及傳輸順序錯亂。

ALM 將連線逾時設定為 10 秒，socket 逾時為 5 秒。 預期客戶端在收到訊息後立即確認訊息。 這是為了確保用戶端在處理訊息時不會延遲。 若有耗時的下游處理，客戶端仍應立即確認事件，然後在端端處理下游處理。

### 資料保留

活動持續7天。 如果在這段時間內沒有被處理，這些資料就會永久遺失。 如果恢復發生在最後一天，且需要更多時間，系統不會延長保留期。如果事件產生速度快於消費速度，有些事件可能會遺失。 雖然這種情況不常見，但訂閱者應持續關注，避免成為長期問題。

### Webhook 會使 Webhook 失效

當訂閱者未能回應 webhook 事件時，ALM 系統會以指數回退重試 webhook，以避免讓訂閱者負荷過重。

重試流程從初始間隔5秒開始。 若用戶未回應，等待時間會翻倍至 10、20、40 及 80 秒，最終增加至最多 5 分鐘。 一旦累積到 5 分鐘，系統將持續每 5 分鐘重試一次，直到 7 天的保留期結束。 如果訂閱者在整個期間都沒有回應，webhook 將自動被停用。 訂閱者將定期發送提醒電子郵件。

### 重複事件

如果用戶在處理事件後回應超過 5 秒，系統可能會嘗試再次處理同一事件。 建議使用事件 ID 來追蹤哪些事件已經處理完畢。 另外，如果 webhook 在發送事件後但尚未儲存已處理時當機，同樣的事件群組可能會被重試。 建議使用批次 ID 或個別事件 ID 來辨識並忽略重複。

### 容錯建議

為防止這些錯誤，訂閱者應積極監控 webhook 事件，並設置警示以偵測漏接事件、重複配送或順序錯亂等問題。

## Webhook 事件的具體指引

1. 如果你先有LEARNER_PROGRESS事件，請忽略以下列出的事件：

   * COURSE_ENROLLMENT
   * COURSE_ENROLLMENT_BATCH
   * LEARNING_PATH_ENROLLMENT
   * LEARNING_PATH_ENROLLMENT_BATCH
   * CERTIFICATION_ENROLLMENT
   * CERTIFICATION_ENROLLMENT_BATCH

2. 如果LEARNER_PROGRESS事件發生在以下事件之後，請忽略：

   * COURSE_COMPLETED
   * COURSE_COMPLETED_BATCH
   * LEARNING_PATH_COMPLETED
   * LEARNING_PATH_COMPLETED_BATCH
   * CERTIFICATION_COMPLETED
   * CERTIFICATION_COMPLETED_BATCH

3. 使用時間戳欄位判斷是忽略事件還是處理事件，除了LEARNER_PROGRESS事件。

## Webhooks 活動消費最佳實務

* webhook 解決方案用於處理需要速度與低延遲的高吞吐量系統。 因此，客戶應確保事件一收到即予確認。 即使客戶端需要額外處理（例如從報告、API 取資料或執行其他操作），事件一收到就應該立即發送確認，事件處理則由客戶端自行處理。
* 若未盡快確認事件，可能會影響事件的即時性質，因為後續事件只會在收到先前確認後才會被發出。
* 用戶端可回覆 HTTP 202 已接受狀態碼，以確認事件已被接受。

## 限制

* 工作輔助工具不被納入 Webhook 事件的 LO 類別，因為它們通常用於協助學習者完成其他學習物件。
* 學習物件實例的退休會被視為更新事件。 因為某個實例只能被退休，不會有刪除事件。
* 會話變更會被記錄為實例更新事件的一部分。 這只適用於課程。 學習路徑實例或認證實例不會有較低階實體的向上傳播。
* 若學習路徑包含課程，且學習者透過該學習路徑完成課程，則會產生兩個 **LearnerProgress** 事件——一個針對該課程，一個針對學習路徑。
* 某些工作流程會非同步計算學習物件的屬性，如持續時間與交付類型。 因此，當 cron 工作完成處理後，這些學習對象的事件會被產生。
* 若課程是透過家長學習計畫或認證註冊，註冊、退選及完成事件僅會觸發家長學習計畫或認證。 這些事件不會觸發兒童課程，因為註冊是間接發生的。
* Webhook 只支援有 **[!UICONTROL ACTIVE]** 狀態的帳號。 這些帳戶無法使用&#x200B;**[!UICONTROL TRIAL]**。**[!UICONTROL INACTIVE]**

## 事件範例有效載荷

+++CI_STATS

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12345-0458-4450-b5dd-6bc1ef4f8b50",
      "eventName": "CI_STATS",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123456785-LoSt",
      "data": {
        "loInstanceId": "course:12345678_14448475",
        "waitlistCount": 0,
        "enrollmentCount": 10,
        "seatLimit": 30
      }
    }
  ]
}
```

+++

+++COURSE_ENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12345c1-4576-4ec5-a057-3a6f078cc9d6",
      "eventName": "COURSE_ENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123424713000-040366-10488-0",
      "data": {
        "userId": 12345678,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14450088",
        "loType": "course",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++COURSE_ENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1234ec1-4576-4ec5-a057-3a6f078cc9d6",
      "eventName": "COURSE_ENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123424713000-040366-10488-0",
      "data": {
        "userId": 12345678,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14450088",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++COURSE_COMPLETED

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "c2345c-6c98-4ed3-b0b0-ba3da5087c1c",
      "eventName": "COURSE_COMPLETED",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "12345823000-040363-12018-0",
      "data": {
        "userId": 11080928,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14448484",
        "loType": "course",
        "enrollmentSource": "SELF_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z",
        "hasPassed": true
      }
    }
  ]
}
```

+++

+++COURSE_COMPLETED_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "c23458c-6c98-4ed3-b0b0-ba3da5087c1c",
      "eventName": "COURSE_COMPLETED_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123456823000-040363-12018-0",
      "data": {
        "userId": 12345678,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14448484",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z",
        "hasPassed": true
      }
    }
    ]
}
```

+++

+++LEARNING_PATH_ENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1234791-338f-4c4c-83bc-9f73ea794965",
      "eventName": "LEARNING_PATH_ENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123404248000-040653-71396-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:1234567",
        "loInstanceId": "learningProgram:1234567_109139",
        "loType": "learningProgram",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++LEARNING_PATH_ENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12340791-338f-4c4c-83bc-9f73ea794965",
      "eventName": "LEARNING_PATH_ENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123404248000-040653-71396-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:1234557",
        "loInstanceId": "learningProgram:1234557_109139",
        "loType": "learningProgram",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++LEARNING_PATH_COMPLETED

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "123404e-d554-4027-944b-086debefdddf",
      "eventName": "LEARNING_PATH_COMPLETED",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1234604391000-040653-314618-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:92348",
        "loInstanceId": "learningProgram:92348_95662",
        "loType": "learningProgram",
        "enrollmentSource": "SELF_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z",
        "hasPassed": true
      }
    }
  ]
  }
```

+++

+++LEARNING_PATH_COMPLETED_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12344e-d554-4027-944b-086debefdddf",
      "eventName": "LEARNING_PATH_COMPLETED_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123404391000-040653-314618-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:92348",
        "loInstanceId": "learningProgram:92348_95662",
        "loType": "learningProgram",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z",
        "hasPassed": true
      }
    } 
    ]
    }
```

+++

+++CERTIFICATION_ENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1234e776-148e-4128-80e9-b896a460b655",
      "eventName": "CERTIFICATION_ENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "12344672000-040654-559128-0",
      "data": {
        "userId": 12345678,
        "loId": "certification:123418",
        "loInstanceId": "certification:123418_160299",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
}
```

+++

+++CERTIFICATION_ENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "123472ec1-4576-4ec5-a057-3a6f078cc9d6",
      "eventName": "CERTIFICATION_ENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1234524713000-040366-10488-0",
      "data": {
        "userId": 12345678,
        "loId": "course:123456798",
        "loInstanceId": "course:12345678_14450088",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++CERTIFICATION_COMPLETED

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1234bf8-7521-4bc0-bc51-7f951ff63ea9",
      "eventName": "CERTIFICATION_COMPLETED",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123454768000-040654-756257-0",
      "data": {
        "userId": 123456728,
        "loId": "certification:123418",
        "loInstanceId": "certification:134518_160299",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++CERTIFICATION_COMPLETED_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "123453bf8-7521-4bc0-bc51-7f951ff63ea9",
      "eventName": "CERTIFICATION_COMPLETED_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1234604768000-040654-756257-0",
      "data": {
        "userId": 12345678,
        "loId": "certification:123418",
        "loInstanceId": "certification:123418_160299",
        "loType": "certification",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++LEARNER_PROGRESS

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "d1234d3a4-c3df-44fa-a1cf-7edd6e3d2075",
      "eventName": "LEARNER_PROGRESS",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235604551000-297002-5823-0",
      "data": {
        "loId": "course:7542090",
        "loType": "course",
        "userId": 12380928,
        "loInstanceId": "course:7232090_10423047",
        "dateStarted": "2024-11-08T03:49:52.000Z",
        "progressPercent": 50
      }
}
]
}
```

+++

+++COURSE_UNENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "f3237817-8cb8-40ea-a441-813bec1c7724",
      "eventName": "COURSE_UNENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1345506253000-040298-24078-0",
      "data": {
        "userId": 12311591,
        "loId": "course:12324298",
        "loInstanceId": "course:12324298_14450088",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
      }
    }
  ]
}
```

+++

+++COURSE_UNENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "f2317817-8cb8-40ea-a441-813bec1c7724",
      "eventName": "COURSE_UNENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "17235506253000-040298-24078-0",
      "data": {
        "userId": 12311591,
        "loId": "course:12324298",
        "loInstanceId": "course:12324298_14450088",
        "loType": "course",
        "enrollmentSource": "SELF_ENROLL"
    }
   }
  ]
}
```

+++

+++LEARNING_PATH_UNENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "823df878-1dfd-47ac-9bfe-7d4952e3edd1",
      "eventName": "LEARNING_PATH_UNENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235506667000-040299-28209-0",
      "data": {
        "userId": 12311591,
        "loId": "learning_program:123157",
        "loInstanceId": "learning_program:123157_109139",
        "loType": "learning_program",
        "enrollmentSource": "SELF_ENROLL",
      }
    }
]
}
```

+++

+++LEARNING_PATH_UNENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "8e23f878-1dfd-47ac-9bfe-7d4952e3edd1",
      "eventName": "LEARNING_PATH_UNENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235506667000-040299-28209-0",
      "data": {
        "userId": 12311591,
        "loId": "learning_program:123157",
        "loInstanceId": "learning_program:123157_109139",
        "loType": "learning_program",
        "enrollmentSource": "ADMIN_ENROLL"
      }
    }
]
}
```

+++

+++CERTIFICATION_UNENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "7232766b-54d8-472d-b933-7e89d1b75ef8",
      "eventName": "CERTIFICATION_UNENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235507900000-040304-1065-0",
      "data": {
        "userId": 12311591,
        "loId": "certification:123199",
        "loInstanceId": "certification:123199_162078",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL"
      }
    }
  ]
}
```

+++

+++CERTIFICATION_UNENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "7202766b-54d8-472d-b933-7e89d1b75ef8",
      "eventName": "CERTIFICATION_UNENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1735507900000-040304-1065-0",
      "data": {
        "userId": 12511591,
        "loId": "certification:139199",
        "loInstanceId": "certification:139199_162078",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL"
      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_DRAFT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12345da9f-26ec-453c-b56a-cdf18a841948",
      "eventName": "LEARNING_OBJECT_DRAFT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1234519188000-040344-48604-0",
      "data": {
        "loId": "course:1234091",
        "loType": "course"
      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_DELETION

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1234a690-5517-4c09-9cde-d953cdd8582c",
      "eventName": "LEARNING_OBJECT_DELETION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235605296000-040656-662792-0",
      "data": {
        "loId": "course:12319716",
        "loType": "course"
      }
    }
   ]
}
```

+++

+++LEARNING_OBJECT_MODIFICATION

```
{
  "accountId": 8308,
  "events": [
    {
      "eventId": "223e068-af3e-4dd3-a515-ce19d7234873",
      "eventName": "LEARNING_OBJECT_MODIFICATION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123350842000-039736-54153-0",
      "data": {
        "loId": "learningProgram:123836",
        "loType": "learningProgram"
      }
    }
   ]
}
```

+++

+++LEARNING_OBJECT_MODIFICATION_BATCH

```
{
  "accountId": 8308,
  "events": [
    {
      "eventId": "1234e068-af3e-4dd3-a515-ce19d7234873",
      "eventName": "LEARNING_OBJECT_MODIFICATION_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235350842000-039736-54153-0",
      "data": {
        "loId": "learningProgram:123836",
        "loType": "learningProgram"
      }
    }
   ]
}
```

+++

+++LEARNING_OBJECT_INSTANCE_MODIFICATION

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "121da98-ab8d-43e9-b671-e79131cd69dc",
      "eventName": "LEARNING_OBJECT_INSTANCE_MODIFICATION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235603297000-040649-741781-0",
      "data": {
        "loInstanceId": "course:12324298_14453691",
        "loId": "course:12324298",
        "loType": "course"
      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1231da98-ab8d-43e9-b671-e79131cd69dc",
      "eventName": "LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123603297000-040649-741781-0",
      "data": {
        "loInstanceId": "course:12324298_14453691",
        "loId": "course:12324298",
        "loType": "course"
      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_INSTANCE_DELETION

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12d16e90-d73a-457b-83f3-666ba9654edb",
      "eventName": "LEARNING_OBJECT_INSTANCE_DELETION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235605491000-040657-236307-0",
      "data": {
        "loInstanceId": "course:12319674_14453849",
        "loId": "course:12319674",
        "loType": "course"
      }
    }
  ]
}
```

+++
