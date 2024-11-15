---
jcr-language: en_us
title: Webhooks使用指南
description: 瞭解Webhook使用方式、最佳實務和限制
contentowner: chandrum
exl-id: e6a63ffb-7fdd-46e4-b5e6-20ce36861cef
source-git-commit: 4b26eddf1285651a13ee9c71fdf677e8b92e6dc3
workflow-type: tm+mt
source-wordcount: '3360'
ht-degree: 0%

---

# Webhooks使用指南

Webhook是網頁應用程式之間自動且即時通訊的一種方式。

傳統API會等待使用者要求資訊，而即時API則會在事件發生時共用資料。 Webhook可作為即時API，每當指定事件發生時，都有助於立即共用資料。

## 實體

若要瞭解Webhook事件，我們首先需要瞭解這些事件的相關實體和觸發條件。

### 學習物件

以下是學習物件（課程、學習路徑或認證）的「支援」事件。

#### 草稿

每當從UI建立學習物件時，它都會以&#x200B;**草稿**&#x200B;模式啟動。 這表示學習物件尚未發佈，因此不適用於學習者。 只要學習物件仍是草稿，就會觸發&#x200B;**LEARNING_OBJECT_DRAFT**&#x200B;事件。 草稿的任何後續更新也將觸發此事件。

#### 更新

學習物件發佈後，其狀態會從&#x200B;**草稿**&#x200B;變更為&#x200B;**已發佈**。 在此轉換期間，Webhook會產生&#x200B;**LEARNING_OBJECT_MODIFICATION**&#x200B;事件，因為學習物件正在從&#x200B;**草稿**&#x200B;修改為&#x200B;**已發佈**。 學習對象的所有後續修改與更新也會觸發&#x200B;**LEARNING_OBJECT_MODIFICATION**&#x200B;事件。

學習物件淘汰時，也會觸發&#x200B;**LEARNING_OBJECT_MODIFICATION**&#x200B;事件。 此已淘汰作業會將基礎執行環境標示為已更新，因為一旦父級學習物件處於已淘汰狀態，這些執行環境就會被淘汰。

#### 刪除

刪除學習物件時，會產生&#x200B;**LEARNING_OBJECT_DELETION**&#x200B;事件。 此事件表示學習物件已遭刪除，學習者無法再存取。

除了即時事件之外，學習物件事件也有批次（非即時）對應專案，這會在&#x200B;**LEARNING_OBJECT_MODIFICATION_BATCH**&#x200B;事件中觸發。 此事件會在透過移轉工作流程建立或修改學習物件期間發生。 由於學習物件不支援透過移轉進行的草稿和刪除操作，因此這些動作沒有對應的草稿或刪除事件。

### 學習物件例項

以下是學習物件例項支援的事件。

#### 更新

建立執行個體後，即會產生&#x200B;**LEARNING_OBJECT_INSTANCE_MODIFICATION**&#x200B;事件。 Adobe Learning Manager中的學習物件執行個體沒有&#x200B;**草稿**&#x200B;狀態，因此Adobe Learning Manager不支援&#x200B;**LEARNING_OBJECT_INSTANCE_DRAFT事件**。 每當建立、修改或淘汰執行個體時，就會產生此事件。

除了在建立、更新或淘汰執行個體時產生之外，當其父級學習物件標示為&#x200B;**已淘汰**&#x200B;時，也會自動產生此事件。 這是因為當學習物件淘汰時，基礎執行個體也需要標示為&#x200B;**已淘汰**。

#### 刪除

刪除執行個體時，會產生&#x200B;**LEARNING_OBJECT_INSTANCE_DELETION**&#x200B;事件。 此事件僅適用於包含自訂進度模組的課程例項，因為Adobe Learning Manager只允許管理員刪除模組型別為自訂進度模組的課程例項。 Adobe Learning Manager不支援明確刪除其他型別的課程模組，這些模組不適用於學習路徑例項或認證例項。

學習物件執行個體也有非即時對應專案，在&#x200B;**LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH**&#x200B;事件中公開。 此事件是在透過移轉工作流程建立或修改學習物件例項時觸發。 由於移轉不支援學習物件執行個體的草稿或刪除操作，因此無法使用對應的草稿或刪除事件。

### 註冊

學習者執行註冊動作後，就會觸發即時註冊事件。 根據學習物件型別，即時註冊事件可能屬於以下類別之一：

* COURSE_ENROLLMENT
* LEARNING_PATH_ENROLLMENT
* CERTIFICATION_ENROLLMENT

除了這些即時事件之外，註冊事件還有批次對應專案。 每當管理員、管理員或平台觸發註冊時，就會觸發非即時註冊事件。 根據學習物件型別，批次註冊事件可以是下列其中一項：

* COURSE_ENROLLMENT_BATCH
* LEARNING_PATH_ENROLLMENT_BATCH
* CERTIFICATION_ENROLLMENT_BATCH

### 取消註冊

當學習者執行取消註冊動作時，會觸發即時取消註冊事件。 根據學習物件型別，即時取消註冊事件可能屬於以下類別之一：

* COURSE_UNENROLLMENT
* LEARNING_PATH_UNENROLLMENT
* CERTIFICATION_UNENROLLMENT

除了這些事件，還有批次取消註冊事件。 每當管理員、管理員或平台標示取消註冊時，就會觸發非即時取消註冊事件。 根據學習物件型別，批次取消註冊事件可以是下列其中一項：

* COURSE_UNENROLLMENT_BATCH
* LEARNING_PATH_UNENROLLMENT_BATCH
* CERTIFICATION_UNENROLLMENT_BATCH

### 完成

當學習者完成學習物件時，就會觸發即時完成事件。 根據學習物件型別，即時完成事件可能屬於以下類別之一：

* COURSE_COMPLETED
* LEARNING_PATH_COMPLETED
* CERTIFICATION_COMPLETED

除了這些即時事件之外，還有批次完成事件。 例如，當管理員、經理或平台將學習物件標示為完成時，即會觸發非即時完成事件。 根據學習物件型別，批次完成事件可能屬於下列類別之一：

* COURSE_COMPLETED_BATCH
* LEARNING_PATH_COMPLETED_BATCH
* CERTIFICATION_COMPLETED_BATCH

### 學習者進度

每當學習者註冊學習物件並開始模組時，就會追蹤其進度。 此資料包含在&#x200B;**LEARNER_PROGRESS**&#x200B;事件中。 事件最多可延遲15分鐘，因為進度追蹤需仰賴複雜的彙總邏輯（非即時）。

### CI統計資料

每當課程執行個體的名額或輪候表可用性發生變更時，就會觸發&#x200B;**CI_STATS**&#x200B;即時事件。 此資料僅在執行個體層級擷取。 此外，由於座位和輪候表可用性是課程及其例項的特定屬性，因此此事件是為課程而觸發，而非為其他學習路徑或認證而觸發。

## 事件順序

Adobe Learning Manager可確保為每個帳戶排序事件。 但是，在關聯註冊或完成與進度事件之間的訊息時，可能會出現不一致。 發生此情況是因為學習者進度事件最多可延遲15分鐘，因為進度追蹤仰賴複雜的彙總邏輯，而此邏輯並非即時。 此外，進度事件來自不同的資料來源，因此在註冊和完成事件方面，無法保證其順序。 因此，Adobe Learning Manager在客戶聆聽這些事件時提供最佳實務。

如果完成事件發生在學習者進度事件之前，使用者端可以忽略學習者進度事件。 這是因為學習者進度事件最多可延遲15分鐘，而完成事件可能在收到進度事件之前觸發。 由於收到完成事件表示學習物件已完成，因此表示進度已達100%。

在註冊事件發生在學習者進度事件之後的罕見情況下，使用者端可以忽略註冊事件。 這是因為進度只能在學習者註冊學習物件後追蹤。 換言之，接收進度事件表示學習物件已開始，這只有在成功註冊後才會發生。

## 即時事件與批次事件

如上所述，某些事件具有即時和非即時對應專案。 訂閱即時事件的時間與訂閱非即時事件的時間可能會造成問題。 根據上述實體，以下是可遵循的准則。

### 即時事件

| S.No | Webhook活動 | 說明 |
|---|---|---|
| 1 | CI_STATS | 當課程執行個體的名額或輪候表可用性發生變更時觸發。 |
| 2 | COURSE_ENROLLMENT | 學習者註冊課程時觸發。 |
| 3 | COURSE_COMPLETED | 於學習者完成課程時觸發。 |
| 4 | LEARNING_PATH_ENROLLMENT | 學習者註冊學習路徑時觸發。 |
| 5 | LEARNING_PATH_COMPLETED | 學習者完成學習路徑時觸發。 |
| 6 | CERTIFICATION_ENROLLMENT | 學習者註冊認證時觸發。 |
| 7 | CERTIFICATION_COMPLETED | 學習者完成認證時觸發。 |
| 8 | COURSE_UNENROLLMENT | 於學習者取消課程註冊時觸發。 |
| 9 | LEARNING_PATH_UNENROLLMENT | 當學習者取消註冊學習路徑時觸發。 |
| 10 | CERTIFICATION_UNENROLLMENT | 當學習者取消註冊認證時觸發。 |
| 11 | LEARNING_OBJECT_DRAFT | 在建立處於草稿狀態的學習物件期間觸發。 |
| 12 | LEARNING_OBJECT_DELETION | 在刪除學習物件期間觸發。 |
| 13 | LEARNING_OBJECT_MODIFY | 在修改學習物件期間觸發。 |
| 14 | LEARNING_OBJECT_INSTANCE_MODIFICATION | 在建立或修改學習物件例項期間觸發。<div><b>注意：</b>建議只在發佈課程之後才使用課程執行個體。</div> |
| 15 | LEARNING_OBJECT_INSTANCE_DELETION | 在刪除學習物件例項期間觸發。 |

### 非即時事件

| S.No | Webhook活動 | 說明 |
|---|---|---|
| 1 | COURSE_ENROLLMENT_BATCH | 管理員/經理/平台註冊課程學習者時觸發。 |
| 2 | COURSE_COMPLETED_BATCH | 在管理員/管理員/平台將課程標示為完成時觸發。 |
| 3 | LEARNING_PATH_ENROLLMENT_BATCH | 當管理員/經理/平台在學習路徑中註冊學習者時觸發。 |
| 4 | LEARNING_PATH_COMPLETED_BATCH | 當管理員/管理員將學習路徑標示為完成時觸發。 |
| 5 | CERTIFICATION_ENROLLMENT_BATCH | 管理員/經理/平台註冊認證中的學習者時觸發。 |
| 6 | CERTIFICATION_COMPLETED_BATCH | 當管理員/經理/平台將認證標示為完成時觸發。 |
| 7 | 學習者進度 | 完成模組時追蹤學習者的進度。 |
| 8 | COURSE_UNENROLLMENT_BATCH | 當管理員/經理/平台取消課程學習者的註冊時觸發。 |
| 9 | LEARNING_PATH_UNENROLLMENT_BATCH | 當管理員/經理/平台從學習路徑取消註冊學習者時觸發。 |
| 10 | CERTIFICATION_UNENROLLMENT_BATCH | 當管理員/經理/平台取消註冊認證的學習者時觸發。 |
| 11 | LEARNING_OBJECT_MODIFICATION_BATCH | 透過移轉工作流程修改學習物件時觸發。 |
| 12 | LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH | 透過移轉工作流程建立或修改學習物件例項時觸發。 |

### 學習物件及其執行個體

* 當您想要接聽透過管理員、作者等角色的UI動作所進行的學習物件變更時，請訂閱即時事件。
* 當您想要接聽透過移轉工作流程對學習物件進行的變更時，請訂閱非即時或批次事件。

### 註冊、取消註冊及完成

* 每當您想要接聽學習者執行的註冊、取消註冊或完成時，請訂閱即時事件。
* 每當您想要接聽以管理員、管理員、平台等標示的註冊、取消註冊或完成時，請訂閱非即時或批次事件。

### 學習者進度

* 每當您想要接聽學習者的進度變更時，請訂閱事件。

>[!NOTE]
>
>在上述情境中（註冊、取消註冊、完成和進度），包含userId和loInstanceId的屬性複合可以唯一識別記錄。

### 課程執行個體統計資料

* 每當您想要接聽座位或輪候表可用性變更時，請訂閱即時&#x200B;**CI_STATS**&#x200B;事件。

## Webhook事件裝載

在Webhooks回應裝載中，Adobe Learning Manager會發出唯一識別實體所需的屬性。 這些將會以相同的格式發出，並根據公用API使用的標準，確保webhook資料與公用API資料同步。 檢視[裝載範例](/help/migrated/integration-admin/feature-summary/webhooks-usage-guide.md#sample-payloads-for-the-events)，瞭解各種事件的裝載。

## 使用Webhook建立外部DB或通知服務

我們聽說過Webhook可能很實用的使用案例之一，就是在客戶端建立資料庫。 Adobe Learning Manager有自己的資料庫和結構描述，但客戶無權存取。

問題是：客戶如何能使用來自webhook的事件來建立資料庫？

由於Adobe Learning Manager不會直接公開表格記錄和結構描述，客戶可以依賴Webhooks解決方案，透過使用事件來填入外部資料庫。 在此版本中，我們提供學習物件、學習物件例項、註冊、取消註冊、完成、進度和課程例項統計資料等事件。

### 從學習物件事件建置資料庫

學習物件事件公開`loId`和`loType`以識別實體。 然而，僅憑這些屬性並不足以建置外部學習物件資料庫。 客戶將需要其他欄位以進一步說明學習物件。
有兩種方式可擷取其他資料：

#### 產生訓練資料報表以擷取所有資料

若學習物件是透過移轉等工作流程大量建立的，應使用此方法。 目標是使用所有內嵌為移轉工作流程一部分的學習物件來產生&#x200B;**[!UICONTROL Training Data]**&#x200B;報表。 若要最佳化匯入程式，建議將匯出開始時間設為觸發移轉的時間。 這將確保報表中只會匯出透過移轉傳入的學習物件，因為客戶的資料庫中已有歷史資料。

#### 從公用APIGET/learningObjects — 管理員範圍查詢資訊

透過即時工作流程建立學習物件時，應使用此方法。 客戶應擁有自己的快取層，以批次處理透過事件發出的學習物件，然後傳遞這些學習物件ID以查詢`GET /learningObjects` API。 具有快取層的原因是為了確保不會超過公用API速率限制。 目前，我們將` GET /learningObject` API的管理員速率限制設為每小時500個請求。 如果超過此限制，公用API服務將會回應&#x200B;**HTTP 429太多要求訊息**。

### 從學習物件執行個體和CI_STATS事件建置資料庫

學習物件執行個體事件會針對課程和學習路徑發出`loInstanceId`、`loId`和`loType`屬性。 同樣地，**CI_STATS**&#x200B;事件只適用於課程，因為`seatLimit`、`seatAvailability`、`waitListLimit`、`waitlistAvailability`等只適用於課程。

在某些情況下，需要執行個體名稱、狀態等額外的執行個體資料。 若要擷取其他執行個體資料，請遵循以下方法：

#### 從public-apiGET/learningobjects — 管理範圍查詢資訊

客戶可使用如上所述的`GET /learningObjects` API，以及包含以擷取執行個體相關資訊的執行個體。 他們仍應遵循[區段](/help/migrated/integration-admin/feature-summary/webhooks-usage-guide.md#query-the-information-from-the-public-api-get-learningobjects-admin-scope)中提及的方法，以確保未違反速率限制。


>[!NOTE]
>
>1. 認證在ALM中沒有執行個體的概念。
>2. 不需要擷取CI_STATS的其他資料，因為系統原本會擷取相同的資訊做為學習物件例項事件的一部分。

### 正在從註冊、取消註冊、完成和進度事件建置資料庫

學習者註冊、取消註冊、完成和進度會在Adobe Learning Manager中作為單獨事件發出。 學習者由`userId`屬性識別。 但在某些情況下，客戶端的下游工作流程可能需要額外的學習者資訊，例如名稱、電子郵件等。 若要擷取此資料，客戶可遵循下列方法：

#### 從管理員或聯結器匯出使用者報告

每當涉及大量工作流程時（例如大量註冊、大量取消註冊等），都應遵循此方法。 Adobe Learning Manager的使用者報表包含與使用者相關的所有資訊。 透過將從webhook事件取得的`userId`建立關聯，客戶可以查詢此報告（可能在客戶端公開為資料庫、快取或API端點）以擷取其他詳細資訊，例如名稱、電子郵件、UUID等。 此方法可用來每週或每天同步使用者。

#### 從公用APIGET/users — 管理範圍查詢資訊

當使用者無法在上述報告中使用時，可遵循此方法。 方法1和2的組合可確保過去建立的所有現有使用者都可由&#x200B;**[!UICONTROL User Report]**&#x200B;涵蓋，同時仍可從API擷取新建立的使用者。 如果&#x200B;**[!UICONTROL User Report]**&#x200B;沒有資料，客戶可以將userIds作為輸入引數傳送至`GET /users` API以擷取使用者資訊。 這些資訊應在客戶端快取，以防止同一組使用者重複叫用公開API。 請注意，我們目前將GET/使用者API的管理員速率限制設定為每小時500個請求。 超過此限制的任何請求都將導致&#x200B;**HTTP 429太多請求**&#x200B;回應。

## 容錯

ALM Webhook系統的容錯為訂閱者提供建議，以處理潛在問題，例如事件遺失、重複事件和順序錯亂。

ALM的連線逾時設定為10秒，通訊端逾時設定為5秒。 預期使用者端一收到訊息，就會立即確認訊息。 這是為了確保使用者端在處理訊息時不會延遲。 如果有一些下游處理很耗時，使用者端仍應立即確認事件，然後在其末端處理下游處理。

### 資料保留

事件會保留7天。 如果在此時間內未處理這些檔案，則會永久遺失。 如果復原是在最後一天，而且需要更多時間，則系統不會延長保留期間。
如果產生事件的速度快於使用的速度，則某些事件可能會遺失。 雖然這種情況不常見，但訂閱者應進行監控以避免其成為長期問題。

### Webhook停用

當訂閱者無法回應webhook事件時，ALM系統會使用指數輪詢重試webhook，以避免讓訂閱者不知所措。

重試程式會以5秒的初始間隔開始。 如果訂閱者沒有回應，等候時間會加倍為10、20、40和80秒，最後會增加到5分鐘的上限。 一旦達到5分鐘，系統將繼續每5分鐘重試一次，直到7天的保留期結束。 如果訂閱者在此期間仍未回應，webhook將會自動停用。 系統會定期傳送提醒電子郵件給訂閱者。

### 重複事件

如果訂閱者在處理事件後需要5秒以上的時間回應，系統可能會嘗試再次處理相同事件。 建議使用事件ID來追蹤哪些事件已處理。 此外，如果webhook在傳送事件後但在儲存之前因已處理而當機，則可能會重試相同的事件群組。 建議使用批次ID或個別事件ID來識別和忽略任何重複專案。

### 容錯建議

為避免這些錯誤，訂閱者應主動監控webhook事件，並針對錯過事件、重複傳送或順序錯亂等問題設定警報。

## webhook事件的特定准則

1. 如果您先收到LEARNER_PROGRESS事件，請忽略下列事件：

   * COURSE_ENROLLMENT
   * COURSE_ENROLLMENT_BATCH
   * LEARNING_PATH_ENROLLMENT
   * LEARNING_PATH_ENROLLMENT_BATCH
   * CERTIFICATION_ENROLLMENT
   * CERTIFICATION_ENROLLMENT_BATCH

2. 如果LEARNER_PROGRESS事件在下列事件之後，請忽略該事件：

   * COURSE_COMPLETED
   * COURSE_COMPLETED_BATCH
   * LEARNING_PATH_COMPLETED
   * LEARNING_PATH_COMPLETED_BATCH
   * CERTIFICATION_COMPLETED
   * CERTIFICATION_COMPLETED_BATCH

3. 使用時間戳記欄位來判斷要忽略或處理事件（LEARNER_PROGRESS事件除外）。

## Webhooks活動使用量最佳實務

* webhook解決方案用於處理必須具備速度和低延遲的高輸送量系統。 因此，客戶應確保事件在收到後立即獲得確認。 即使客戶端需要其他處理（例如從報告、API擷取資料或執行其他動作），收到事件時應立即傳送確認，之後由使用者端負責處理事件。
* 若未儘快認可事件，可能會影響事件的即時性質，因為後續事件只有在收到先前的認可後才會發出。
* 使用者端可以使用HTTP 202 Accepted狀態代碼回應，以確認事件已接受。

## 限制

* 工作輔助不屬於LO類別下的Webhook事件，因為它們通常用於協助學習者完成其他學習物件。
* 學習物件例項處分會視為更新事件。 例項不會有刪除事件，因為它只能淘汰，不能刪除。
* 工作階段變更將會擷取為執行個體更新事件的一部分。 這僅適用於課程。 學習路徑例項或認證例項不會從較低層級實體向上傳播。
* 如果學習路徑包含課程，且學習者透過學習路徑完成課程，則會產生兩個&#x200B;**LearnerProgress**&#x200B;事件 — 一個用於課程，一個用於學習路徑。
* 某些工作流程會以非同步方式計算學習物件的屬性，例如持續時間和傳遞型別。 因此，當cron工作完成處理時，將會產生這些學習物件的事件。
* 如果透過家長學習計畫或認證註冊了課程，則註冊、取消註冊和完成事件只會觸發家長學習計畫或認證。 由於註冊是間接發生，因此這些事件不會觸發子課程。
* 只有&#x200B;**[!UICONTROL ACTIVE]**&#x200B;狀態的帳戶才支援Webhook。 **[!UICONTROL TRIAL]**&#x200B;或&#x200B;**[!UICONTROL INACTIVE]**&#x200B;帳戶無法使用。

## 事件的裝載範例

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
      "eventName": "COURSE_ENROLLMENT_BATCH",
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

+++LEARNING_OBJECT_MODIFY

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
