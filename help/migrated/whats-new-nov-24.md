---
description: 了解 2024 年 11 月版 Adobe Learning Manager 中的新功能與增強內容
jcr-language: en_us
title: 新功能摘要 2024 年 11 月
exl-id: 4dfe0e31-d202-4a6e-8c4f-43851218699f
source-git-commit: 7b84a4565ccf109ed4789f4963d6e250f5d0a852
workflow-type: tm+mt
source-wordcount: '3226'
ht-degree: 0%

---

# 新功能摘要 2024 年 11 月 {#new-features-summary}

了解 2024 年 11 月版本 Adobe Learning Manager 的新功能與增強內容。

* **AI 驅動搜尋：** 結合詞彙與語意搜尋，提供更智慧且具上下文感知的結果。
* **Webhooks**：與 Webhooks 整合，將即時資訊傳送到特定網址。
* **學習工具互通性（LTI）：**&#x200B;支援與其他學習管理系統平台的互通性LTI。
* **Credly 整合**：透過 Credly 管理並分享外部徽章。
* **合規儀表板強化**：與其他管理員共享儀表板，並在學習者首頁設定預設合規小工具。
* **多語言支援**：為教室與虛擬教室模組建立語言專屬實例。
* **自訂角色**：強化對使用者角色與權限的控制。
* **完成評論：在標記學習者為完成時，請**&#x200B;加入註解。
* **使用者群組報告**：管理詳細報告的使用者群組。
* **候補名單報告**：下載課程實例的候補學習者名單。
* **無障礙功能提升**：支援報頭與公司標誌上的替代文字。
* **支援印地語**：介面語言支援印地語。
* **髒話檢查**：封鎖含有禁忌詞彙的社群貼文。
* **電子郵件範本優化**：結合並優化教師分配及課程取消的電子郵件範本。
* **MS Teams 完成標準**：設定 VILT 課程的最低出席時間。
* **新的遷移工作流程**：遷移變更包括課程與模組的完成標準，以及將模組遷移到資料夾中。

>[!NOTE]
>
>請觀看這場 [線上研討會](https://cdn.content.adobelearningmanageracademy.com/public/newlearner/newlearner_0dc0f1e8.html#/overviewPage?instanceId=11932477&loId=11231360&loType=course) ，了解更多本版本的新功能。

## Adobe Learning Manager 中的 AI 驅動搜尋

Adobe Learning Manager 正在革新學習者搜尋課程或培訓的方式。 它引入了結合詞彙與語意搜尋的 AI 驅動搜尋功能。 搜尋變得更聰明，因為它尋找特定詞彙，並理解其背後的脈絡與意圖。 進階搜尋能理解你的查詢意義，並提供相關結果。 它會明確搜尋的主要重點，給你最完整的結果。

>[!NOTE]
>
>AI 驅動的搜尋僅提供給學習者。

請參閱此條目 [：進階搜尋](/help/migrated/learners/feature-summary/advanced-search.md) 以獲取更多資訊。

## Webhook

Adobe Learning Manager 允許與 Webhooks 整合，將即時資訊（如課程註冊、課程建立及其他資訊）傳送到特定網址。

ALM 中的 webhook 允許一個實體透過 HTTP 自動將資料傳送給另一個應用程式。 它將使應用程式能夠在不持續請求的情況下，提供其他應用程式資訊。 例如，若使用者完成學習管理系統（LMS）課程，webhook 可自動將該資訊傳送至其他平台，如 CRM 或報告工具。 Webhook 常用於整合，以自動化流程並減少系統間手動更新的需求。 設置 webhook，提供一個回調 URL，然後把資料傳送過去。

詳情請參閱本文 [Webhooks](/help/migrated/integration-admin/feature-summary/webhooks.md) 。

## 學習工具互通性

Adobe Learning Manager 現已支援 LTI，以提升 Adobe Learning Manager 與其他學習管理系統（LMS）之間的互通性。

### 什麼是長期性情（LTI）？

LTI（學習工具互通性）是一項標準，允許第三方工具與內容提供者與學習管理系統（LMS）連接。 使用者可直接在其 LMS 內存取外部內容提供者的外部學習內容，無需登入或切換至其他 LMS。

**LTI 作為工具提供者**：LTI 作為工具提供者，允許外部系統與學習管理系統（LMS）整合。 Adobe Learning Manager 作為 LTI 工具提供者，讓其他 LMS 平台能直接在其 LMS 中存取 Adobe Learning Manager 的課程、證書或學習路徑。

**LTI 作為工具使用者**：LTI 作為工具消費者允許 LMS 透過學習工具互通性（LTI）整合外部工具。 在這種情況下，LMS 是外部工具所提供的服務的消費者。 Adobe Learning Manager 作為 LTI 工具使用者，允許整合第三方學習工具。 這讓 Adobe Learning Manager 的學習者能夠在 Adobe Learning Manager 內，透過第三方工具學習課程、證書或學習路徑。

更多資訊請參閱本文 [《學習工具互通性](/help/migrated/integration-admin/feature-summary/learning-tools-interoperability.md) 》。

## Credly

使用 Credly，ALM 中的管理員讓學習者能管理並分享平台的外部徽章，跨越各種社群媒體管道。

### 什麼是 Credly？

Credly 是一個數位認證平台，讓學習者和組織能夠獲得、分享並驗證專業成就，例如徽章或證照。 學習者可以透過 Credly 個人檔案在社群媒體及其他平台管理並分享徽章。

### 將 Credly 與 Adobe Learning Manager 整合

首先，在 Adobe Learning Manager （ALM） 中加入 Credly 連接器。 接著，將現有徽章從 Credly 遷移，以確保學習者成就的連續性。 最後，在 Adobe Learning Manager 中建立一項技能，並選擇適合的學習路徑，以提升學習者的發展與認可度。

欲了解更多資訊，請參閱此條目 [Credly](/help/migrated/integration-admin/feature-summary/credly-integration.md)

## 合規儀表板

在此版本中，管理員現在可以與其他管理員、自訂管理員及店經理共享儀表板，讓他們能即時存取合規儀表板。 他們現在可以在學習者首頁設定預設的合規小工具，讓學習者能追蹤自己的合規需求。 更多資訊請參閱本文 [《合規儀表板](/help/migrated/administrators/feature-summary/reports.md#share-compliance-dashboard-with-admins-and-custom-admins) 》。

## 多語言支援

Adobe Learning Manager （ALM） 現在允許作者利用語言標籤建立針對教室與虛擬教室模組的語言專屬實例。 學習者可使用偏好語言的CR/VC模組。 例如，作者可以建立一個包含兩個實例的 CR/VC 模組：一個為英文，一個為法文。 學習者可以選擇自己偏好的語言實例。

更多資訊請參閱本文 [「在不同地區](/help/migrated/authors/feature-summary/add-new-language-learning-objects.md#multi-language-support-for-crvc-instances-with-language-tagging) 新增學習物件」。

## 自訂角色

自訂角色允許管理員為不同使用者群組定義特定角色與責任，確保更好的管理與控制。 在此版本中，ALM 透過對後續章節提供更細緻的控制，強化了自訂角色。

* 使用者
* 課程
* 學習路徑
* 認證
* 工作輔助工具
* 目錄

管理員可根據使用者職責分配精確權限，確保每個群組僅能存取相關功能與內容。 這些強化控制讓關鍵區段能更細緻地管理。

以管理員身份登入，並前往 **[!UICONTROL Users]** > **[!UICONTROL Custom Roles]** 建立和管理自訂角色。

更多資訊請參閱本文 [《自訂角色](/help/migrated/administrators/feature-summary/custom-role.md) 》。

## 完成評論

管理員現在可以在標記學習者為完成課程、學習路徑或認證時加入註解。 管理員可以同時為一位或多位學習者新增評論，這些評論會出現在 [學習者成績單](/help/migrated/administrators/feature-summary/reports.md#learner-transcripts) 報告中。

請參閱此條目 [完成評論](/help/migrated/administrators/feature-summary/courses.md#completion-comments) 以獲取更多資訊。

## 使用者群組報告

Adobe Learning Manager 的新功能 **[!UICONTROL User Group Report]** 透過管理員離開時，提供未管理群組的可視性，幫助管理使用者群組。 管理員可以在>**[!UICONTROL User Group]**&#x200B;區查看報告&#x200B;**[!UICONTROL Users]**。它提供了關於每個團體的詳細資訊，包括：

* 使用者群組類型
* 集團名稱
* 說明
* 由（姓名）創建
* 由（電子郵件）製作
* 創建於（UTC時區）
* 使用者人數

詳情請參閱此條目 [User Group 報告](/help/migrated/administrators/feature-summary/add-users-user-groups.md#user-group-report) 。

## 候補名單報告

Adobe Learning Manager 的新功能 **[!UICONTROL Waitlist Report]** 允許管理員下載所有課程實例的候補學習者名單。 管理員與講師可從 **[!UICONTROL Waitlist]** OR **[!UICONTROL Session Overview]** 頁面的章節&#x200B;**[!UICONTROL Course]**&#x200B;存取此報告。候補名單報告可從行政區和講師區下載。

以下是候補名單報告中的欄位：

* 課程名稱
* 實例名稱
* 實例識別碼
* 實例狀態
* 使用者名稱
* 電子郵件
* 使用者唯一識別碼
* 註冊日期（UTC時區）
* 現況
* 候補名單號碼
* 候補名單限制
* 席次限制

請參閱本文 [的候補名單報告（行政）](/help/migrated/administrators/feature-summary/courses.md#waitlist-report) 及 [候補名單報告（講師](/help/migrated/instructors/feature-summary/learners.md#waitlist-report) ）以下載管理員與講師部分的報告。

## 學習者首頁的無障礙功能

Adobe Learning Manager 現在支援所有主頁的替代文字，以提升學習者的無障礙性。 這讓有特殊需求的學習者能使用螢幕閱讀器閱讀替代文字並理解圖片。 你可以選擇多種語言，並為每種語言提供替代文字。 記得要把對應語言的替代文字加進去。 確保你帳號中的公司標誌也包含包含公司名稱的替代文字。詳情請參閱此條目 [公告](/help/migrated/administrators/feature-summary/announcements.md#masthead) 。

## 支持印地語

Adobe Learning Manager 現已將印地語引入平台介面語言之一，並支持平台在印度的成長。 對印地語母語者的支援確保所有功能、報告及整體使用者體驗都能完全開放給使用者。

>[!NOTE]
>
>系統產生的 PDF 格式徽章證書不支援印地語。

要更改介面語言，請依照以下步驟操作：

1. 以 . 登入。**[!UICONTROL Admin]**
2. 去 **[!UICONTROL Profile Settings]** > **[!UICONTROL Interface Language]**。
3. 選擇 **[!UICONTROL Hindi]** 為介面語言。


## 社群貼文的髒話檢查

Adobe Learning Manager 現在會封鎖 Learners 應用程式中包含禁止詞彙的社交貼文。 這有助於保持專業且合規，尤其是在像醫療這類敏感領域。

## 電子郵件範本優化

### 當有老師指派時，請透過電子郵件通知學習者

現有的電子郵件 和 **[!UICONTROL VCProvider Session Details]** 已被合併成一封&#x200B;**[!UICONTROL You have been added as an Instructor]**&#x200B;電子郵件&#x200B;**[!UICONTROL You have been added as a UserType]**。根據使用者的角色，該 **[!UICONTROL UserType]** 會是 **[!UICONTROL Instructor]** 或 **[!UICONTROL Organizer]**。 這些郵件之前在介面中是無法提供的。 現在這些郵件已經合併成一封郵件，並加入了介面。 管理員可以在該 **[!UICONTROL Email Template]** 區塊中存取此範本。 預設情況下，所有新舊帳號都會啟用，但管理員可以在同一區塊中啟用或停用。 無論課程內容為 Zoom、Teams、Connect 或其他服務，每當課程建立並指派教師時，都會發送此電子郵件。

### 課程取消時，請透過電子郵件通知學習者

被移除的講師現在只會收到取消課程的電子郵件。 之前，他們收到了取消通知和更新郵件。 留在課程中的講師將收到課程更新電子郵件及新的邀請函。

## MS Teams 完成標準

目前，即使學習者只參加了幾秒鐘的虛擬講師主導訓練（VILT）課程，也會被標記為已出席。 這次釋出後，我們為 Teams 模組引入了完成標準，以確保更準確的出席率。 作者現在可以設定學習者在VILT課程中必須花費的最低時間，才能計算出勤時間。

這是預設關閉的後端功能。 請聯絡你的客服經理啟用。

## 更新電子郵件投遞所需的新 IP 位址

為了提升電子郵件傳遞的可靠性，我們正在現有的 IP 池中新增 IP 位址。 為確保電子郵件通訊不中斷，請根據需要更新組織的電子郵件設定。

我們目前使用以下 IP 位址來發送電子郵件：

* 149.72.162.66
* 167.89.5.155

以下 IP 位址將加入我們的電子郵件投遞池：

* 159.183.228.93
* 159.183.225.26
* 159.183.218.22
* 168.245.57.144

>[!NOTE]
>
>如有需要，建議與 IT 團隊合作，將 IP 位址加入允許的 URL 清單。

## 遷徙變動

遷移工作流程中會進行以下變更：

* 將模組遷移到特定資料夾。
* 新增模組的完成標準。
* 課程的額外完成標準

### 模組遷移的變更

當你將模組遷移到 ALM 時，它們預設會儲存在 public 資料夾中。 在這個版本中，我們在 module_version.csv[&#128279;](assets/module_version.csv) 檔案中新增了一個欄位。`folder` 管理員可以使用此欄位指定遷移後模組應該放置的資料夾名稱。 管理員也可以透過以逗號分隔資料夾名稱，將單一模組放入多個資料夾中。

資料夾欄位使用字串資料型別，且是可選欄位。 以下是資料夾欄位的條件：

* 你新增的資料夾名稱應該是 ALM 帳號中已有的內容資料夾。
* 這些值應該是逗號分隔的字串。
* 如果你為已存在於其他資料夾的模組新增資料夾名稱，該新值不會覆蓋或取代已分配的資料夾。 該模組會被加入新資料夾，並且在現有資料夾中也能使用。
* 若值為空，資料夾預設為 **[!UICONTROL Public]**。

更多資訊請參考 [module_version csv 規格](assets/4-module_version.xlsx) 檔。

### 模組遷移變更 - 完成標準

管理員可在模組遷移時指定模組的完成標準。 在這個版本中，我們新增了欄位 `completionCriteria`， `viewPercent` 以及 `quizData` [module_version.csv](assets/module_version.csv)。

以下是新欄位的條件：

1. `completionCriteria`:

   * 資料型態應為字串，值與支援值為：
      * `LAUNCH_CONTENT`
      * `VIEW_PERCENT`
      * `QUIZ`
      * `MARK_COMPLETE`
   * 僅在模組層級為自學模組類型設置完成標準。
   * 靜態內容的支援值為 `LAUNCH_CONTENT` 和 `VIEW_PERCENT`。
   * 互動內容的支援值為 `LAUNCH_CONTENT`、 `VIEW_PERCENT`、 `QUIZ`和 。
   * HTML5 內容的支援值為 `LAUNCH_CONTENT` 和 `MARK_COMPLETE`。

2. `viewPercent`:

   * 此欄位的資料型態應為整數，值介於 0 到 100 之間。
   * 當 completionCriteria 設定為 `VIEW_PERCENT`時，請在此欄輸入所需的瀏覽百分比或留空。

3. `quizData`:

   * 資料型別應為字串，支援的值為 `QUIZ_ATTEMPTED`、 、 `QUIZ_PASSED`&#x200B;`QUIZPASSED_OR_LIMITREACHED`和 。
   * 當 `completionCriteria` 設定為 `QUIZ`時，在欄位中輸入相應的測驗值 `quizData` 。

更多資訊請參考 [module_version csv 規格](assets/4-module_version.xlsx) 檔。

### 課程遷移變更-完成標準

管理員可在課程遷移時指定課程的完成標準。 在這個版本中，我們新增了一個名為 `completionCriteria` in the [course.csv](assets/course.csv) 的新欄位。

以下是該 `completionCriteria` 欄位的條件：

* 資料型別應為字串或數字，且為可選欄位。
* 這些值應該是 `ALL`、 `X`、 `SELECTEDMODULES`和 。
* X 是一個整數值，應該大於 0，且小於模數總數。
* 如果你設定`completionCriteria`為 `SELECTEDMODULES`，你需要在 course_module.csv[&#128279;](assets/course_module.csv) 檔案中標記必須的模組。
* 在欄位 `optionalCriteria` 中輸入 `TRUE` 或 `FALSE`。 如果你設定了 ， `TRUE` 那模組就會變成必修。

詳情請參閱 [課程 csv spec](assets/3-course.xlsx) 及 [course_module csv spec](assets/6-course_module.xlsx) 檔案。

## API 變更

以下是 API 的變更：

* **搜尋API**：
   * 新增模式篩選器，選項包括：classicSearch 和 advanceSearch。
   * snippetTypes 的新 loMetadata 選項。
* **公告 API**：
   * 包含用於報頭描述的altText屬性。
* **實例 API**：
   * 新增 locale 屬性以取得 locale 詳細資訊。
* **髒話檢查**：
   * 更新的 API 以檢查社群貼文留言與回覆中禁止用詞：
* **轉速與爆發限制**：
   * 新增了每分鐘請求數（RPM）和所有 API 的突發限制。
* **徽章 API**：
   * 新增屬性 externalProvider，用以檢索外部徽章的資訊。
* **職缺 API**：
   * 使用工作 API 下載使用者群組報告與自訂角色稽核報告。

### 搜尋 API 變更

搜尋 API 現在新增了兩個模式篩選器： `classicSearch` 和 `advanceSearch`。 還有一個新的`loMetadata`選項。`snippetTypes`為了獲得最佳效果，請在使用`advanceSearch`時加入。`loMetadata` `snippetTypes`

### 公告 API 變更

現在包含`GET /announcements API`&#x200B;`altText`屬性以提供報頭描述。

#### 使用 cURL 的範例請求：

```
curl -X GET --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 12345678' 'https://abcd.adobe.com/primeapi/v2/announcements/123456'
```

#### 範例回應：

```
{
  "links": {
    "self": "https://abcd.adobe.com/primeapi/v2/announcements/123456"
  },
  "data": {
    "id": "12345",
    "type": "adminAnnouncement",
    "attributes": {
      "actionUrl": "google.com",
      "announcementType": "MASTHEAD",
      "expiryDate": "2038-01-19T03:14:07.000Z",
      "liveDate": "2024-07-31T11:11:30.000Z",
      "contentMetaData": [
        {
          "contentType": "IMAGE",
          "contentUrl": "https://abcd.adobe.com",
          "locale": "en-US",
          "altText": "Moonlight - english changed new",
          "thumbnailUrl": "https://abcd.adobe.com/"
        },      ]
    }
  }
}
```

### 實例 API 的變更

這個新 `locale` 屬性已被加入以下 API 中，用以取得區域細節。

* `GET /learningObjects/{loId}/instances/{loInstanceId}`
* `GET /learningObjects/{id}?include=instances,enrollment.loInstance`
* `GET /learningObjects?include=instances,enrollment.loInstance`
* `GET /learningObjects/{id}/relatedLOs?include=instances,enrollment.loInstance`
* `POST /learningObjects/query?include=instances,enrollment.loInstance`
* `POST /search/query?include=model.instances`
* `GET /search?include=model.instances`

#### 使用 cURL 的範例請求：

```
curl --location 'http://abcd.com/primeapi/v2/learningObjects/course:1234567/instances/course:1234567_1234567' \
```

#### 範例請求：

```
{
    "links": {
        "self": "http://abcd.com/primeapi/v2/learningObjects/course:1234567/instances/course:1234567_1234567"
    },
    "data": {
        "id": "course:1234567_1234567",
        "type": "learningObjectInstance",
        "attributes": {
            "dateCreated": "2024-02-27T09:21:25.000Z",
            "isAET": false,
            "isDefault": true,
            "isFlexible": false,
            "locale": "en-US",
            "state": "Active",
            "localizedMetadata": [
                {
                    "locale": "en-US",
                    "name": "Default instance"
                }
            ]
        },
        "relationships": {
            "learningObject": {
                "data": {
                    "id": "course:1234567",
                    "type": "learningObject"
                }
            },
            "loResources": {
                "data": [
                    {
                        "id": "course:123456_1234567_1234567_1",
                        "type": "learningObjectResource"
                    }
                ]
            }
        }
    }
}
```

### 公開 API 變更用於髒話檢查

以下 API 已更新，可對社群貼文的留言與回覆進行髒話檢查。

* `POST /boards/{id}/posts `
* `PATCH /posts/{id}`
* `POST /posts/{id}/comments`
* `PATCH /comments/{id}`
* `POST /comments/{id}/replies`
* `PATCH /replies/{id}`

若貼文中發現限制詞彙，將發送以下回覆。

#### 範例回應：

```
{
  "status": "FORBIDDEN",
  "title": "BAD_WORD_FOUND",
  "source": {
    "info": "Unacceptable word found in post"
  }
}
```

### 轉速與爆發限制的變化

在此版本中，所有 API 都新增了 RPM（每分鐘請求數）和突發限制。 每個 API 的最大轉速可在 Swagger 頁面查詢。

RPM 是你在一分鐘內能發送給 API 伺服器的請求數量。 突發限制允許在短時間內處理更多請求，超越一般速率限制。 例如，API 允許 `learningObject` 每分鐘最多 15 次請求。 若超過此限制，API 將回傳錯誤訊息。

### 徽章 API 變更

此新屬性 `externalProvider` 已加入以下 API 中，用以取得外部徽章的資訊，包括徽章 ID 與提供者名稱。

* `GET /badges `
* `GET /badges/{id}`
* `GET /skills?include=levels.badge`
* `GET /skills/{id}?include=levels.badge`
* `GET /learningObjects/{loId}/instances/{loInstanceId}?include=badge`
* `GET /users/{userId}/userBadges`
* `GET /users/{userId}/userBadges/{id}`

#### 使用 cURL 的範例請求：

```
curl -X GET --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 123456789' 'https://abcd.adobe.com/primeapi/v2/badges/44'
```

#### 範例回應：

```
{
  "links": {
    "self": "https://abcd.adobe.com/primeapi/v2/badges/44"
  },
  "data": {
    "id": "44",
    "type": "badge",
    "attributes": {
      "imageUrl": "https://abcd.com/accountassets/1/badges/download.png",
      "name": "external badge",
      "state": "Active",
      "externalProvider": {
        "id": "1234sjd-b272-4de1-9b60-1234567",
        "provider": "credly"
      }
    }
  }
}
```

### 透過工作 API 下載使用者群組及自訂角色稽核報告

使用者可透過 .and 下載&#x200B;**[!UICONTROL User Group Report]**&#x200B;**[!UICONTROL Custom Role Audit Report]**。`Job API`

#### 用戶群組報告下載範例請求：

```
curl -X POST --header 'Content-Type: application/vnd.api+json;charset=UTF-8' --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 12345678' -d '{ \ 
     "data": { \ 
         "type": "job", \ 
         "attributes": { \ 
             "jobType": "generateUserGroupReport" \ 
         } \ 
    } \ 
 }' 'https://abcd.adobe.com/primeapi/v2/jobs'
```

#### 自訂角色稽核報告下載範例請求：

```
curl -X POST --header 'Content-Type: application/vnd.api+json;charset=UTF-8' --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 1234567' -d '{
    "data": {
        "type": "job",
        "attributes": {
            "description": "description of your choice",
            "jobType": "generateCustomRoleAuditReport",
            "payload":{
                 "fromDate": "2020-01-01T18:30:00.000Z",
                 "toDate": "2024-09-31T18:30:00.000Z",
                 "locale":  "en-US"
            }
        }
   }
}
```

### 無請求主體的錯誤訊息

我們針對請求主體是強制但未在 API 中提供的特殊錯誤訊息。

#### 範例錯誤訊息：

```
{
    "status": "BAD_REQUEST",
    "title": "Generic Error"
}
```

## 報告強化

管理員可以在管理員&#x200B;**>**&#x200B;報告&#x200B;**區塊找到這些報告**&#x200B;變更。

### 學習成績單報告

報告 **[!UICONTROL Learning Transcripts]** 將新增兩個專欄：

* **[!UICONTROL Module ID]**： 顯示每個模組的唯一識別碼。 這根新柱是在現有 **[!UICONTROL Module]** 柱子之後新增的。
* **[!UICONTROL Course Instance ID]**： 顯示每個課程實例的唯一識別碼。這根新柱是在現有 **[!UICONTROL Instance]** 柱子之後新增的。
* **[!UICONTROL Completion Comment]**： 本欄記錄管理員在標記用戶完成時所輸入的評論。 這欄新增於報告末尾。


### 會期總結報告

報告 **[!UICONTROL Session Summary]** 將新增三個專欄：

* **[!UICONTROL Module ID]** 欄位已在欄位前 **[!UICONTROL Session Name]** 加。
* **[!UICONTROL Session ID]** 欄位已在欄位前 **[!UICONTROL Session Name]** 加。
* **[!UICONTROL Course Instance ID]** 欄位已在欄位後 **[!UICONTROL Instance Name]** 面新增。
* **[!UICONTROL Completion Count]** 欄位已在欄位後 **[!UICONTROL Enrollment Count]** 面新增。

## 本次更新修正的錯誤

* 已修正在 Android 和 iOS 裝置上傳影片時，從活動模組上傳影片時發生的錯誤。
* 已修正手機應用程式開啟課程的問題;網頁版運作正常。
* 修正了在 Safari 中查看工作輔助工具及其他資源的問題。
* 已修正用戶無法在行動應用程式下載工作輔助工具的問題。
* 已修正 Patch User API 文件中的錯誤。
* 修正了主辦方在課程刪除時無法收到電子郵件通知的問題。
* 修正了主辦方在模組從課程中移除並重新發布時，無法收到取消課程通知的問題。
* 新增支援在外部使用者建立時，在電子郵件地址中加入特殊字元「+」與「-」。
* 修正了 Marketo 連接器統一報表同步失敗的問題，如果使用者技能報告的 CSV 記錄值中有雙引號
* 修正 `/skills` 了端點回傳 Admin API 正確狀態，但 Learner API 卻持續顯示錯誤或快取資料的問題。
* 修正了當帳號沒有設定 Go1 連接器時，免費增值課程的 Go1 入門失敗問題。
* 修正了學習路徑（LP）課程無法透過遷移存取的問題，尤其是學習者已完成 LP。
* 修正了增量使用者 CSV 失敗的問題，當使用者的管理員和跳過層級的管理者都設為 SU（超級使用者）而非管理員，且不包含在 CSV 中時。
* 修正了儀表板報告中店經理範圍的問題。
* 修正了刪除草稿課程時xapi_iri沒有被移除的問題。
* 修正了某些情境下無法新增唯一 LO ID 的問題。
* 已修正學習計畫中 IsEmbeddable 屬性在共享學習計畫中無法正確更新的問題。
* 已修正學習者檢視中學習路徑總持續時間顯示的問題。
* 已修正讓學習者即使帳號被刪除後，仍可透過自助註冊連結註冊或註冊的問題。
* 修正 `www`了在課程建立時新增連結時被移除的問題。
* 修正了隱藏資訊和下載工作輔助工具無法正常運作的問題。
* 已修正單一登入（SSO）無法正常運作的問題，因為新用戶透過自註冊連結與 IP ID 加入。
* 修正了公告刪除後通知訊息資料無法取得的問題。
* 已修正電子郵件搜尋用戶時搜尋結果不足的問題。

## 系統需求

查看 [Adobe Learning Manager 系統需求](/help/migrated/system-requirements.md)。

## 發行說明

請 [查看最新發行公告](/help/migrated/release-note/release-notes.md) 。

## Adobe Learning Manager 先前版本

* [2024年7月發行](/help/migrated/whats-new-july-2024.md)
* [2024年3月發行](/help/migrated/whats-new-march-2024.md)
