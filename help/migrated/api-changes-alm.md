---
description: ALM 中的 API 變更
jcr-language: en_us
title: 四月發布時的 API 變更
source-git-commit: 3b35c16d74c83329cee24ee9ad007a53ccbd8cf3
workflow-type: tm+mt
source-wordcount: '4093'
ht-degree: 0%

---


# 2026 年 4 月版本中的 API 變更

2026 年 4 月的 Adobe Learning Manager 版本針對公開 API 進行了針對替代方案與等效功能的專注強化，包括內容時窗存取、內容導向測驗嘗試、非登入體驗，以及職業輔助處理。 這些變更設計上大致向下相容，同時允許更精確的整合。

## 學習路徑的自適應學習

此版本新增了完整的公開 API 支援，以支援自適應學習路徑。 學習路徑（Learning Paths，LP）現在可以定義自適應規則，控制哪些區段與子學習物件（sub LO）對不同學習者群組可見，而公共 API 也反映了此行為。

以下終點受影響：

- GET /primeapi/v2/learningObjects？filter.loTypes=learningPath
- 取得 /primeapi/v2/learningObjects/{loId}

一個新的布林屬性 attributes.isAdaptive，表示學習程式使用自適應規則。 當此旗標為真時，該區段屬性會被自適應地解釋。

對於學習者呼叫，僅回傳目前學習者可見的區段。 每個區段包含學習物件 ID（loId）、一個強制旗標和一個強制的 LOCount，這些都是根據該學習者的自適應配置計算出來的，還有 sectionId。 relationships.subLOs 的關係現在也經過過濾，只包含該學習者可見的子學習物件。

對於管理員呼叫，區塊還可以同時暴露 adaptiveConfig 陣列。 此說明了各使用者群組的自適應規則，包括 userGroupId、userGroupName 以及該區塊是否為該群組的強制性。 面向管理的工具可以利用此點來視覺化和管理自適應規則。

學習計畫的重置完成

此版本引入了一套 API，用於 __刷新（重置）學習物件的完成__ ，包括自適應學習程式。 這支援了如再訓練、定期合規更新或計畫重啟等情境。

新增端點：

```
POST /primeapi/v2/learningObjects/{loId}/instances/{loInstanceId}/refreshCompletion
```

此操作需要適當的寫入權限，並在指定使用者情境中重置指定學習物件實例的完成狀態。 它主要供管理端自動化或精心設計的學習工具使用。

此功能計畫透過 Jobs API 推出批量版本。 請求表單設計用來依電子郵件、使用者 ID 或使用者群組 ID 來鎖定使用者，例如：

```
{  
  "emails": ["[user1@example.com](mailto:user1@example.com)", "[user2@example.com](mailto:user2@example.com)"],  
  "userIds": ["12345", "67890"],  
  "userGroupIds": ["ug1", "ug2"]  
}  
```

整合者在需要重新啟動每個課程或課程的學習者時，應該使用這個 API。 用戶端必須優雅地處理錯誤回應：API 可能會拒絕不適用重置的刷新請求（例如當沒有完成功能或不支援學習物件類型時）。

## 等價與替代完備化

為了支援多個學習物件能滿足相同需求的實作，本版本引入了等價與替代完成作為公開 API。

學習物件端點現在包含以下資訊：

```
- GET /primeapi/v2/learningObjects
- GET /primeapi/v2/learningObjects/{loId}
```

新的布林屬性 attributes.isAlternateComplete 顯示學習者對某個學習對象的完成是否來自另一個或等價的學習對象，而非該物件本身。 當此情況成立時，relationships.alternateCompletions 關係會列出作為替代角色的學習物件。 這使得下游報告與儀表板能區分直接完成與替代完成，並顯示哪個替代完成符合需求。

此外，相關學習對象視角允許發現可能滿足學習對象的替代方案。 此現象可透過以下方式曝光：

```
GET /primeapi/v2/learningObjects/{loId}/relatedLOs?type=sourceAlternateLOs&limit={n}
```

回應回傳可作為替代物件的學習對象，並包含一個meta.count欄位，顯示此類替代物件的總數，與當前限制無關。 整合系統可利用此方法呈現推薦的對應版本，或建立替代映射的管理視圖。

## 報告與分析的應用案例

產生報告或分析的使用者應更新邏輯，將 isAlternateComplete 和 alternateCompletions 加入報告工作流程。

使用完成資料的報告整合（例如，LT 匯出、自訂資料倉儲串流或 BI 儀表板）應擴展其邏輯，從 LO API 讀取並持久化屬性 .isAlternateComplete 與 relationships.alternateCompletions：

- 當 isAlternateComplete == false：\
  把這張唱片當作 __LO 的直接完成__，就像現在一樣。
- 當 isAlternateComplete == 真：
   - 在報告中標記該紀錄為&#x200B;__替代完成__（例如，「完成方法」欄位，值為 DIRECT 與 ALTERNATE）。
   - 使用 relationships.alternateCompletions.data[*].id 來記錄&#x200B;__哪個來源 LO__ 給予了這個完成（例如：「Course B completed via alternate course A」）。

典型使用案例：

- _合規報告_——顯示合規課程已透過核准等效課程完成，並列出符合要求的來源課程。
- _計畫進度儀表板_——區分直接&#x200B;_完成路徑_&#x200B;的學習者與透過替代路徑達成的學習者，以獲得更準確的進度與補救視圖。
- _稽核追蹤_——對於標示為 isAlternateComplete = true 的任何 LO，稽核員可以精確看到哪些替代訓練被用於完成該完成。

若不納入這兩個欄位，下游報告將將替代完成視為一般完成，無法&#x200B;_解釋_ *為*&#x200B;何學習者顯示完成了他從未直接接受的培訓。

## 學習者與管理員 LO API 行為

多語言工作輔助的結構在學習者與行政 LO API 中都是相同的。 學習者範圍只會回傳學習者可見的工作輔助，但對每個可見的工作輔助工具，它會透過多個資源實體（每個區域一個）及多區域本地化元資料，揭露所有已設定的區域。 管理範圍會回傳管理員能管理的所有工作輔助工具，使用相同的 LO 模型和區域特定資源 ID。 具有學習者範圍的客戶應選擇與學習者內容語言最匹配的 attributes.locale 資源，而管理工具則可列舉所有區域以便報告和管理。

## 具備註解功能的檢查清單

為了支援審核員能對檢查清單活動分享結構化回饋的工作流程，本版本透過學習物件資源 API 呈現&#x200B;*檢查清單評論*&#x200B;與審查者可見性控制。

與檢查清單相關的元資料會暴露在 learningObjectResource 實體（JApiLOResource，「類型」：「learningObjectResource」）上，這些實體代表課程或其他學習物件中的檢查清單資源。

相關資訊可透過以下管道取得：

```
GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources
```

當學習物件實例包含檢查清單類型的資源時，包含陣列中對應的 learningObjectResource 條目會在屬性下暴露評論與審查者可見性屬性，並在關係下顯示審查者身份。

### 新的檢查清單評論屬性

對於檢查清單資源，learningObjectResource 可能包含以下屬性：

- attributes.checklistComment\
  例如，審閱者對學習者留下的自由文字評論：\
  「checklistComment」：「表現優異！ 所有安全規範都正確遵守。」\
  此屬性僅&#x200B;_在以下情況下被_&#x200B;填入：
   - showChecklistComment 為真，且
   - 清單設定已啟用enable_reviewer_remarks。
- attributes.showchecklistComment\
  一個布林旗標示是否應該向學習者展示審稿人意見：\
  “showChecklistComment”： true\
  此屬性僅在&#x200B;_檢查清單設定中啟用 enable_ reviewer_remarks 時才會存在_。\
  客戶應使用此標記來決定是否在學習者經驗中呈現檢查清單評論。
- attributes.showReviewerNameToLearner\
  一個布林旗標，控制學習者是否應該看到審閱者的身份：\
  “showReviewerNameToLearner”： true\
  當為真時，客戶端可使用 checklistReviewedBy 關係（見下文）來解析並顯示審查者名稱（例如透過使用者查詢 API）。

其他針對檢查清單的上下文，如 checklistEvaluationStatus、isChecklistMandatory、resourceSubType：「CHECKLIST」及 submissionDate，也在同一 learningObjectResource 中提供，以支援更豐富的檢查清單使用者介面與報告功能。

### 審稿人身份關係

當審稿人名稱是要顯示時，learningObjectResource 包含一個指向審稿人使用者的關聯：

```
"relationships": {
  "checklistReviewedBy": {
    "data": {
      "id": "user_id",
      "type": "user"
    }
  }
}
```

此關係僅在以下&#x200B;_情況下被_&#x200B;填入：

- showReviewerNameToLearner 是真的，且
- checklistReviewedBy 並非空（即檢查清單已被審查過）。

用戶端應用程式應：

1. 請查看 attributes.showReviewerNameToLearner。
2. 如果 true，且 relationships.checklistReviewedBy.data 存在，請呼叫適當的使用者 API，將「id」：「user_id」解析成顯示名稱。
3. 請將審核者姓名放在檢查清單旁，視情況而定。

### 存取清單資源與評論

要取得檢查清單資源及其對特定學習物件的註解，客戶端應：

- 叫聲

```
GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources
```

- 回應如下：
   - 使用 mainingObject 中的 relationships.instances 來找到包含中相關的 learningObjectInstance 條目。
   - 從每個 learningObjectInstance 中，依照 relationships.loResources 尋找 learningObjectResource 條目。
   - 篩選 learningObjectResource 條目，其中：
      - attributes.resourceSubType == “CHECKLIST”（用於檢查清單資源），以及
      - 可選擇性地 attributes.showChecklistComment == true 來尋找有學習者可見註解的檢查清單。

- 對於每個檢查清單 learningObjectResource，請消耗：
   - attributes.checklistComment（如果存在且 showChecklistComment 為真）
   - attributes.checklistEvaluationStatus（例如：「PASSED」）
   - attributes.showReviewerNameToLearner
   - relationships.checklistReviewedBy （在存在時）用以識別審查者。

此模式允許無頭或自訂客戶端直接從 Prime API 呈現完整的檢查清單體驗，包括狀態、強制/可選標誌，以及審核者回饋。

### 報告與使用者體驗考量

- _報告與分析_&#x200B;追蹤學習者在清單上的表現的整合可以包含：
   - checklistEvaluationStatus，用於通過/不通過或其他狀態指標。
   - isCheckList 必須區分必需與可選的檢查清單活動。
   - 檢視回饋覆蓋度的檢查清單與顯示清單評論。
- _學習者體驗_&#x200B;使用者介面實作應：
   - 在顯示評論前請尊重 showChecklistComment。
   - 請使用 showReviewerNameToLearner 和 checklistReviewedBy 來決定是否顯示評論者姓名或保持匿名。
   - 當評論被停用或不存在時，請優雅地退回，仍顯示評估狀態和提交資訊。

## 多語言就業援助支援

為支援需同時以多種語言提供工作輔助給學習者與管理員的實作，本版本將工作輔助處理擴展為每個地區&#x200B;*回傳*&#x200B;一個資源，而非單一硬編碼的美國英語資源。

多語言工作輔助工具仍沿用現有的階層制度：

_learning Object_ （lo） → _learningObjectResource_（loResource） → _資源_

API 合約無需更改。 任何在地化的工作輔助工具自然都符合此結構，每個區域有獨立的資源實體，並在 learningObject / learningObjectResource 層級共享本地化元資料。

工作援助資料透過以下方式公開：

```
GET /primeapi/v2/learningObjects/jobAid:{jobAidId}?include=instances.loResources.resources
```

當工作輔助工具有多種語言變體時，所包含的陣列包含多個「類型」：「資源」條目——分別對應每個地區（例如 en-US、fr-FR、es-ES），全部由單一 learningObjectResource 連結。

### 多語言就業輔助結構

多語言工作輔助工具的用途：

- _learningObject（類型：learningObject）_
   - 包含多條目（例如en-us、fr-fr）的在地化元資料，讓客戶能以適當語言呈現工作協助標題/描述。
- _learningObjectInstance（類型：learningObjectInstance）_
   - 指的是透過 relationships.loResources 的一個或多個 learningObjectResource 條目。
- _learningObjectResource（類型：learningObjectResource）_
   - 包含常見設定（內容類型、版本等） 以及多地點在地元資料。
   - 透過 relationships.resources 連結到一個或多個資源實體。
- _資源（類型：資源）_
   - *每個地區*&#x200B;有一個，每個區域都有自己的 ID、地點、名稱和網址（位置/下載網址）。

對於多語言工作輔助工具，典型的模式是：

- learningObjectResource 提供 en-US 與 fr-FR 的 localizedMetadata
- 指向：
   - 資源附地點：「en-us」
   - 資源附帶地點：「FR-FR」

用戶端可透過將學習者的所在地與 resource.attributes.locale 欄位匹配來選擇合適的資源。

### 工作輔助工具的新資源 ID 格式

為了正確區分多個在地化的工作輔助資源變體，_資源識別碼格式已改變_。

_舊的（舊有）資源 ID 格式_

過去，工作協助資源使用的是不透明的識別格式，例如：

jobAid:131032_-1_-1_2_resource

此格式不編碼區域，API 實際上只會暴露單一資源（通常是美國）。

_新的資源識別格式（多語言感知）_

新格式如下：

```
jobAid:<jobAidId>_<version>_<localeCode>
```

舉例：

- jobAid:131032_2_en-US
- jobAid:131032_2_fr_FR
- jobAid:131032_2_es_ES

視覺解析：

```
jobAid:131032_2_fr_FR

        │      │ │ │

        │      │ │ └──► Locale Code (fr_FR, en_US, es_ES, etc.)

        │      │ └────► Version (2)

        │      └──────► JobAid ID (131032)

        └─────────────► Resource Type Prefix ("jobAid:")
```

此結構使客戶能：

- 快速辨識該資源屬於哪個工作說明工具和版本。
- 需要時直接從資源 ID 推斷出所在位置。

### 向下相容性：

```/resources/{resourceId}```

舊有資源端點仍可使用：

```GET /primeapi/v2/resources/{resourceId}

```

它現在&#x200B;_同時向下相容_&#x200B;舊有與新 ID 格式：

- _舊的身分證格式_（例如，jobAid:131032_-1_-1_2_resource）
   - 持續有效。
   - 回傳&#x200B;_與該舊有識別碼相關的第一個建立資源_（通常是原始的美國資源）。
- _新的 ID 格式_（例如 jobAid:131032_2_fr_FR）
   - 回傳&#x200B;_與該 ID 對應的精確區域資源_。
   - 這使得能精確檢索並操作局部工作輔助變體。

目前儲存或參考舊資源 ID 的整合系統可繼續運作且不需更改，而較新的實作則鼓勵採用新的 ID 格式以執行區域特定操作。

### 整合與使用者體驗考量

- _學習者/管理員使用者介面_
   - 請使用 learningObject.localizedMetadata 和 learningObjectResource.localizedMetadata，以適當語言呈現標題與描述。
   - 使用 resource.attributes.locale 選擇學習者所在位置的正確網址（location/downloadUrl）。
   - 如果無法取得學習者的確切所在地，請實作備援行為（例如退回 en-US）。
- _API 與儲存_
   - 對於新的整合，請儲存&#x200B;_新格式的資源 ID（_```jobAid:<jobAidId>_<version>_<localeCode>```），以實現明確的區域特定檢索。
   - 舊有 ID 仍可搭配 /resources/{resourceId} 使用，但無法區分不同地區。

## 起始模組的時間槽限制

有些學習經驗必須只在限定的時間範圍內提供。 該版本顯示學習對象資源的時間槽資訊，並引入驗證端點，檢查學習者是否能在當前時間啟動資源。

時隙元資料可透過端點取得：

```GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources```

在學習物件資源層級，timeSlot 物件現在可能存在於屬性中，且 startTime 與 endTime 的值以 UTC 表示。 這指定了資源可啟動的視窗。

在啟動模組前，整合可以呼叫新的驗證端點：

```GET /primeapi/v2/learningObjects/{loId}/instances/{loInstanceId}/loResources/{loResourceId}/canStart```

此端點用於學習者-讀取情境，會回傳學習者是否目前被允許啟動該資源，並考量已設定的時間時隙、交付類型及其他後端規則。

自訂播放器與用戶端應用程式應使用 canStart 強制時間存取，並利用 timeSlot 元資料清楚顯示內容何時可用或過期。 canStart 的負面回應應明確處理，告知學習者為何該內容尚未或無法開始。

## 多重嘗試、內容導向測驗

有些內容套件會自行執行嘗試追蹤，而非僅依賴 Adobe Learning Manager。 該發布會引入一個標誌，指示何時嘗試是由內容本身驅動。

透過：

```GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources```

學習物件資源現在可能會暴露一個布林屬性 hasContentDrivenAttemptTracking。 當情況成立時，測驗或模組會內部管理嘗試次數（例如透過 SCORM 或 xAPI 邏輯），而平台的標準嘗試計數器可能無法完全反映學習者的經驗。

顯示嘗試次數或控制重試行為的整合應該會檢查這個標記。 啟用後，不應僅從平台元資料推斷嘗試次數限制，應準備依賴內容端報告（例如透過 xAPI 語句）或業務專用規則。

## 工作援助資源ID格式中的行為改變

本版本引入了工作輔助資源 ID 格式的重要 __行為變更__ 。 雖然沒有新的端點，但這會直接影響儲存或解析這些 ID 的系統。

過去，職業援助資源ID的格式如下：

```jobAid:<jobAidId>_-1_-1_2_resource```

在 2026 年 4 月版本中，此格式被簡化且更明確的格式取代：

```jobAid:<jobAidId>_<version>_<localeCode>```

例如：

jobAid:131032_2_fr_FR

組成部分包括：

- ```<jobAidId>```： 數字的就業援助識別碼（例如 131032），
- ```<version>```：工作輔助工具的版本號（例如，2），
- ```<localeCode>```：區域代碼（例如en_US、fr_FR、es_ES）。

任何索引資源或持續存在 Job Aid 資源 ID 的整合，都必須更新其解析與儲存邏輯以識別新格式。 由於識別碼本身會變動，強烈建議您在升級至 2026 年 4 月版本後，重建任何以 Job Aid 資源 ID 為關鍵的本地索引。

## 透過遷移設定航向橫幅圖片

你現在可以在 Adobe Learning Manager 中設定或更新課程橫幅影像，作為標準遷移工作流程的一部分。 這有助於你啟動或整理大型目錄，同時保持課程頁面的視覺一致性，無需手動編輯

### 橫幅圖片定義的地點

橫幅影像會在course.csv _遷移檔案中設定_，你已經用來提供課程的元資料，例如：

- 身分證
- 賽道名稱
- 課程創建日期
- 州
- 作家
- 縮圖網址

透過此強化，course.csv規範新增了 _課程橫幅圖片的選用欄位_ 。 精確的標頭名稱會在你從 Learning Manager 帳號下載的 CSV 規格中定義（例如，可能看起來像 bannerUrl 或 bannerImageUrl）。

橫幅欄：

- 指向你想用作 _課程橫幅_&#x200B;的圖片檔。
- 它的運作方式和 thumbnailURL 一樣，使用你設定的內容庫（Box/FTP）中可用的圖片。

### 準備遷移用的橫幅圖片

1. 上傳橫幅圖片：將橫幅圖片檔案放在你用來處理其他遷移資產的同一個 Box 或 FTP 位置，依照你現有的目錄結構。
2. 檢查檔案格式：請使用系統需求中所述的支援圖片格式之一（例如 png、jpg、jpeg、gif）：
   1. [*系統需求*](/help/migrated/system-requirements.md)
3. 更新course.csv：在新的橫幅欄位中，請參考橫幅圖片的相對路徑或識別碼。 一個概念性範例：

```
id,courseName,courseCreationDate,state,author,thumbnailUrl,bannerUrl  
12345,DEMO1,2018-05-05T08:56:21.000Z,Published,Sudheer,pic1.png,banners/banner1.png  
45678,DEMO2,2018-05-05T08:56:21.000Z,Published,Sudheer,pic2.png,banners/banner2.png  
```

### 遷移時套用橫幅

一旦你的course.csv更新，流程就和其他遷移一樣：

1. _上傳 CSV 檔_&#x200B;將更新後的course.csv（以及其他相關檔案）上傳到已設定為遷移的 Box/FTP 資料夾。 檔案名稱必須與csv_specifications.zip中指定的名稱完全一致（這些名稱具有大小寫區分）。
2. _開始衝刺跑_&#x200B;在 Adobe Learning Manager 中，作為整合管理員，啟動包含 course.csv 的遷移 _衝刺執行_ 。\
   遷移引擎會讀取橫幅欄位，並將橫幅影像套用到每個課程。
3. _檢視結果與錯誤日誌_&#x200B;衝刺結束後：
   1. 在作者&#x200B;_和_&#x200B;學習者&#x200B;_應用程式中驗證橫幅_。
   2. 如果某些資料列失敗（例如因檔案路徑無效或格式不支援），請從遷移執行中下載錯誤 CSV 並修正資料。

### 新課程與現有課程的比較

橫幅欄位在兩種情況下都適用：

- _透過遷移建立的新課程_&#x200B;當賽道首次從course.csv建立且橫幅欄被填滿時，該橫幅會立即設定。
- _現有課程（改裝/修正）_&#x200B;如果你用相同的課程 ID 和新的橫幅值重新執行遷移：
   - 學習經理會找到現有課程。
   - 橫幅映像會 _更新_ 為 CSV 中指定的新圖片。

您的實際欄位名稱和路徑必須與下載的 CSV 規格&#x200B;_及內容庫配置相符_。

## 移除 LearningProgramCourse 中的順序欄位

Adobe Learning Manager 現在支援在遷移過程中，學習路徑（學習程式&#x200B;_）內簡化的課程排序模型_。作為此變更的一部分， _learning_ program_course.csv遷移檔案中的排序欄位被移除_ 。

過去，learning_program_course.csv 檔案包含一個欄位（通常稱為 order 或類似欄位），用於：

- 根據該欄位的數值，明確設定 _每門課程在學習程式中的位置_ 。
- 要求管理員或腳本手動維護此數字序列，尤其是在插入或重新排序課程時。

現在，Adobe Learning Manager 不再使用 learning_program_course.csv 的排序欄來決定課程順序。 遷移 CSV 著重 _於哪些課程屬於哪個學習計畫_，而非它們的數字排序。

## 對遷移CSVs的影響

### learning_program_course.csv

你應該將舊有訂單欄位視為已移除或忽略：

- 遷移期間，不要依賴命令來控制學習計畫中的課程順序。
- 如果你還有舊模板的訂單欄位：
   - 學習管理器會忽略它來處理訂單。
   - 你可以安全地隨著時間從 CSV 中移除，以簡化遷移檔案。
- 核心所需的映射仍為：
   - 學習程式識別碼↔課程識別碼（以及其他仍被記錄的欄位，如 id、learningProgramId、courseId、日期）。

請務必參考 Learning Manager 帳號（透過 csv _specifications.zip）最新的[_ CSV 規格_](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/migration-manual) ，以確認目前的標頭集和需求。

## timeZoneCode 在球場實例

從本版本起，課程實例模型（learningObjectInstance）揭露了一個新屬性：

timeZoneCode ——一個字串欄位，明確將課程實例連結到帳號設定的時區之一。

這讓客戶能夠：

- 以一致且由 API 驅動的方式解析課程實例的時區。
- 正確解讀並顯示該實例的所有實例層級日期/時間，不論使用者的時區為何。

### timeZoneCode 出現的地方

該欄位會被加入 learningObjectInstance 模型的屬性中僅限於課程實例。

範例：

```
{
  "id": "course:1262748_1359228",
  "type": "learningObjectInstance",
  "attributes": {
    "dateCreated": "2019-08-06T13:50:39.000Z",
    "isAET": false,
    "isDefault": true,
    "timeZoneCode": "356",
    "isFlexible": false,
    "state": "Active",
    "localizedMetadata": [
      {
        "locale": "en-US",
        "name": "Default instance"
      }
    ]
  }
}
```

### 如何解析 timeZoneCode

數值 timeZoneCode 是帳號時區目錄的查詢金鑰，透過帳號 API 公開：

```http
GET /primeapi/v2/account
Authorization: Bearer <access_token>
```

回應中列出的時區如下：

```
"data": {
  "attributes": {
    "timeZones": [
      {
        "name": "Etc/GMT+12",
        "timeZoneCode": "356",
        "utcOffset": -720,
        "utcOffsetCode": "UTC-12:00(Etc/GMT+12)",
        "zoneId": "Etc/GMT+12"
      },
      "..."
    ]
  }
}
```

### 推薦客戶流程：

1. 呼叫一次 GET /account，為租戶設 attributes.timeZones。
2. 針對每個課程實例：
   - 閱讀 attributes.timeZoneCode。
   - 在 timeZones 中找到 timeZoneCode 匹配的對應條目。
   - 使用該條目的 zoneId、utcOffset、utcOffsetCode 來顯示和排程邏輯。

## 使用者群組成員資格的非同步公開 API

### 簡介

Adobe Learning Manager 提供兩個 _管理非同步 API_ 來管理使用者群組（UG）成員資格：

- POST /async/userGroups/{userGroupId}/users – 非同步地將使用者加入 UG
- 刪除 /async/userGroups/{userGroupId}/users – 非同步移除使用者

這些 API 不會在同一請求中更新成員身份，而是接受你的批次並回傳事件 _ID_。 實際結果則會透過 webhook 後續傳送。

在以下情況下使用：

- 你要管理大型群組或頻繁的批次更新。
- 延遲不如可靠性和吞吐量重要。
- 你是在建立整合功能（人力資源、客戶關係管理、LXP），而不是介面點擊。

對於小型互動式的管理操作，你可以繼續使用同步 `/userGroups/{id}/users` API。

### 認證與基礎網址

這些 API 是標準 __v2 管理 API__ 表面的一部分。

- [基礎網址（生產環境）](https://learningmanager.adobe.com/docs/primeapi/v2/)
- 認證：OAuth 2.0 存取權杖，具有 `admin:write` 範圍
- 必填標頭：
   - 授權：持有者 &lt;access_token>
   - Content-Type： application/json
   - Accept： application/json

關於一般的管理員 API 行為與範圍，請參見：

- [開發者手冊](/help/migrated/integration-admin/feature-summary/developer-manual.md)
- [API 參考指南](https://learningmanager.adobe.com/docs/primeapi/v2/)

### 請求格式

兩者加&#x200B;__減______&#x200B;都使用完全相同的身形。

#### 車身

```
{
  "metadata": {
    "event_id": "my-optional-correlation-id",
    "sourceSystem": "HRIS",
    "batchId": "hr_2026_03_30_0001"
  },
  "data": [
    { "type": "user", "id": "11101219" },
    { "type": "user", "id": "11101220" }
  ]
}
```

#### 資料（必需）

資料是該批次的使用者資源識別碼清單。

- `type` 一定是「使用者」。
- `id` 是 _ALM 中的數字使用者 ID_ （非電子郵件，也非 UUID）。

#### 限制條件

- `data` 必須存在且非空。
- 至少需要一位使用者。
- 每個請求的最大有效載荷大小為 20 位使用者。
- 所有識別碼必須為數字，且必須指向有效使用者。

若上述任何條件失敗，API 會回傳錯誤，且不會被排隊。

#### 元資料（可選）

`metadata` 你是否希望在 Webhook 中回傳任何額外的相關資料？

典型用法：

- `event_id` – 你產生的相關性識別。
- `sourceSystem` —— 你上游系統的名稱。
- `batchId` – 批次或工作識別碼。

服務在 Webhook 回應中回傳這個物件時，保持不變，所以你可以將回調與你的內部工作匹配。

限制條件：

- 選修;可完全省略。
- 所有鍵與值的總長度不得超過 1000 字元。

### 回應格式

兩個端點同步回應事件 ID：

```
{ "event_id": "cd2972c8-cb15-47a0-a23f-e4a16cb720f5" }
```

行為：

- 若 `metadata.event_id` 傳遞，則使用該值。
- 否則，服務會產生 UUID。

你應該時刻：

- 將此 `event_id` 儲存為批次的主要識別碼。
- 預期在 Webhook 回撥中也會收到相同的值。

查看 [Webhook 以新增或移除使用者群組成員](/help/migrated/integration-admin/feature-summary/webhooks.md#webhooks-for-adding-and-removing-user-group-membership) ，以便更多組織化。

## 常見問題

_2026 年 4 月的版本將如何改變 learningObjects API 用於自適應學習程式？_

此版本在學習程式上新增了 isAdaptive 旗標，並使區段與子語言組（subLO）對學習者有感知能力。 在自適應程式中，學習者只能看到根據自適應規則可見的區段和子學習物件，而管理員則可以看到使用者群組底層的自適應配置。

_如果我的整合假設所有區段和子 LO 都會回傳，我需要更新嗎？_

是的。 對於自適應學習程式，API 現在只會回傳目前學習者可見的段落和子 LO。 用戶端程式碼應將回應視為權威且可能經過過濾的視圖，而非假設完整清單。

_我該如何以程式方式重置學習者完成課程或學習計畫的成績？_

使用新的端點：

```POST /primeapi/v2/learningObjects/{loId}/instances/{loInstanceId}/refreshCompletion```當權限與狀態允許時，這會重置目標實例的完成。

_我如何判斷學習者是否透過替代或等效的學習物件完成了某件事？_

檢查學習物件上的 isAlternateComplete 屬性。 如果是真的，alternateCompletions 關係列出了作為該學習者完成替代方案的學習物件。

_我該如何找到所有能滿足特定學習對象的替代方案？_

請使用以下端點：

```GET /primeapi/v2/learningObjects/{loId}/relatedLOs?type=sourceAlternateLOs&limit={n}```

並使用 data array（用於替代節點）和 meta.count（用於替代節點總數）。

_我怎麼知道學習者此刻是否被允許開始一個模組？_

首先，從以下處取得該資源的時間槽：

```GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources```然後使用：

```GET /primeapi/v2/learningObjects/{loId}/instances/{loInstanceId}/loResources/{loResourceId}/canStart```

_hasContentDrivenAttemptTracking 在資源上是什麼意思？_

這表示嘗試追蹤是由內容本身控制（例如透過 SCORM/xAPI 邏輯），而不僅僅是平台計數器。 如果是真的，不要只依賴平台的嘗試次數或限制來做你的 UX 和報告。

_我要如何取得適合未登入用戶（公開體驗）的選單？_

用途：

```GET /primeapi/v2/templates/menus?include=pages,subMenus.pages&isNonLoggedIn=true```

此時會回傳篩選給匿名使用者的選單與頁面結構，適合 Experience Builder 或其他無頭網站。

_effectiveModifiedDate 在工作協助篩選功能上有什麼改變？_

將 filter.effectiveModifiedDate 與 filter.loTypes=jobAid 合併的請求，現在只會正確回傳指定日期視窗內的工作輔助資料。

_工作援助資源識別碼格式有什麼改變？我該如何處理？_

ID 格式從以下數值變更：

```jobAid:<jobAidId>_-1_-1_2_resource```

收件人：

```jobAid:<jobAidId>_<version>_<localeCode>```

例如JobAid:131032_2_fr_FR。 任何儲存或解析 Job Aid 資源 ID 的系統都必須更新，且你應計劃在升級至 2026 年 4 月版本後重建以這些 ID 為關鍵的本地索引。
