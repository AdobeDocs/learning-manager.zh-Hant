---
description: 瞭解2024年11月發行的Adobe Learning Manager中的新功能和增強功能
jcr-language: en_us
title: 新功能摘要
source-git-commit: bfe77d838340f94e072f9d7346576e3034a66a66
workflow-type: tm+mt
source-wordcount: '3052'
ht-degree: 0%

---

# 新功能摘要 {#new-features-summary}

瞭解2024年11月發行的Adobe Learning Manager中的新功能和增強功能。

* **由AI支援的搜尋：**&#x200B;結合辭彙與語意搜尋，以取得更聰明、內容感知的結果。
* **Webhooks**：與Webhooks整合，以將即時資訊傳送至特定URL。
* **學習工具互通性(LTI)**：支援LTI以便與其他LMS平台互通性。
* **Credly整合**：透過Credly管理和共用外部徽章。
* **法規遵循儀表板增強功能**：與其他管理員共用儀表板，並在學習者首頁上設定預設法規遵循小工具。
* **多語言支援**：建立教室和虛擬教室模組的語言特定執行個體。
* **自訂角色**：增強對使用者角色和許可權的控制。
* **完成註解**：將學習者標籤為完成時新增註解。
* **使用者群組報告**：使用詳細報告管理使用者群組。
* **輪候表報告**：下載課程執行個體的輪候表學習者清單。
* **協助工具增強功能**：支援刊頭及公司標誌的替代文字。
* **支援北印度文**：支援北印度文的介面語言。
* **髒話檢查**：封鎖包含禁止字詞的社交貼文。
* **電子郵件範本最佳化**：結合併最佳化講師指派和工作階段取消的電子郵件範本。
* **MS團隊完成條件**：設定VILT工作階段的最短出席時間。
* **新的移轉工作流程**：移轉變更包含課程與模組的完成條件，以及將模組移轉至資料夾。

## Adobe Learning Manager中的AI支援搜尋

Adobe Learning Manager正在改寫學習者搜尋課程或訓練的方式。 它引入了AI支援的搜尋功能，結合了辭彙和語意搜尋。 搜尋現在變得更加聰明，因為它會尋找特定辭彙，並瞭解這些辭彙背後的語境和意圖。 進階搜尋可瞭解您查詢的意義，並提供相關結果。 它會識別搜尋的主要焦點，以提供您最完整的結果集。

如需詳細資訊，請參閱本文[進階搜尋](/help/migrated/learners/feature-summary/advanced-search.md)。

## Webhooks

Adobe Learning Manager允許與Webhook整合，將即時資訊（例如課程註冊、課程建立和其他資訊）傳送至特定URL。

ALM中的webhook可讓一個實體透過HTTP自動傳送資料給另一個應用程式。 如此一來，應用程式便能在不持續要求資訊的情況下，為其他應用程式提供資訊。 例如，如果使用者完成學習管理系統(LMS)課程，webhook可以自動將該資訊傳送到另一個平台，例如CRM或報告工具。 Webhook通常用於整合中，以自動化流程並減少系統之間手動更新的需求。 提供您要傳送資料的回呼URL，以設定Webhook。

如需詳細資訊，請參閱本文[Webhooks](/help/migrated/integration-admin/feature-summary/webhooks.md)。

## 學習工具互通性

Adobe Learning Manager現在支援LTI，以增強Adobe Learning Manager與其他學習管理系統(LMS)之間的互通性。

### 什麼是LTI？

LTI （Learning Tools Interoperability，學習工具互通性）是一種標準，可讓協力廠商工具和內容提供者連線學習管理系統(Learning Management System，LMS)。 使用者可以直接在其LMS內從外部內容提供者存取外部學習內容，而無需登入或導覽至不同的LMS。

LTI作為工具提供者： LTI作為工具提供者，可讓外部系統與LMS整合。 Adobe Learning Manager充當LTI工具提供者，可讓其他LMS平台直接在LMS內從Adobe Learning Manager存取課程、憑證或學習路徑。

LTI作為工具消費者： LTI作為工具消費者，可讓LMS透過學習工具互通性(LTI)整合外部工具。 在此案例中，LMS是外部工具所提供服務的消費者。 Adobe Learning Manager可充當LTI工具消費者，讓他們整合協力廠商學習工具。 這可讓Adobe Learning Manager學習者使用Adobe Learning Manager中協力廠商工具的課程、憑證或學習路徑。

如需詳細資訊，請參閱本文[學習工具互通性](/help/migrated/integration-admin/feature-summary/learning-tools-interoperability.md)。

## 可信

使用Credly時，ALM中的管理員可讓學習者跨各種社群媒體頻道，從平台管理和共用外部徽章。

### 什麼是Credly？

Credly是數位認證平台，可讓學習者和組織贏取、分享及驗證專業成就，例如徽章或認證。 學習者可以透過其在社群媒體和其他位置的Credly設定檔管理和分享徽章。

### 將Credly與Adobe Learning Manager整合

首先，在Adobe Learning Manager (ALM)中新增Credly聯結器。 接下來，將現有徽章從Credly移轉，以確保學習者成就的持續性。 最後，在Adobe Learning Manager中建立適當學習路徑的技能，以增強學習者的發展和認可。

如需詳細資訊，請參閱本文[Credly](/help/migrated/integration-admin/feature-summary/credly-integration.md)

## 合規性儀表板

在此版本中，管理員現在可以與其他管理員、自訂管理員和商店管理員共用控制面板，讓他們立即存取合規性控制面板。 他們現在可以在學習者的首頁上設定預設的合規性Widget，讓學習者追蹤其合規性要求。 如需詳細資訊，請參閱本文[合規性儀表板](/help/migrated/administrators/feature-summary/reports.md#share-compliance-dashboard-with-admins-and-custom-admins)。

## 多語言支援

Adobe Learning Manager (ALM)現在可讓作者使用教室和虛擬教室模組的語言標籤，建立語言專屬的執行個體。 學習者可以使用其偏好語言存取CR/VC模組。 例如，作者可建立具有兩個例項的CR/VC模組：一個使用英文一個使用法文。 學習者可以透過其偏好語言選取執行個體。

如需詳細資訊，請參閱本文[新增不同地區設定的學習物件](/help/migrated/authors/feature-summary/add-new-language-learning-objects.md#multi-language-support-for-crvc-instances-with-language-tagging)。

## 自訂角色

自訂角色可讓管理員為不同的使用者群組定義特定的角色和責任，以確保更好的管理和控制。 在此版本中，ALM藉由提供對以下區段的更詳細控制來增強自訂角色。

* 使用者
* 課程
* 學習路徑
* 認證
* 工作輔助
* 目錄

管理員可以根據使用者職責指派精確許可權，確保每個群組只能存取相關功能和內容。 這些增強型控制項可讓您更精細地管理重要區段。

以管理員身分登入，並導覽至「**[!UICONTROL Users]** > **[!UICONTROL Custom Roles]**」以建立和管理自訂角色。

如需詳細資訊，請參閱本文[自訂角色](/help/migrated/administrators/feature-summary/custom-role.md)。

## 完成註解

管理員現在可以在課程、學習路徑或認證中將學習者標示為完成時新增註解。 管理員可以同時為一個或多個學習者新增註解，且註解會顯示在[學習者成績單](/help/migrated/administrators/feature-summary/reports.md#learner-transcripts)報告中。

如需詳細資訊，請參閱本文[完成註解](/help/migrated/administrators/feature-summary/courses.md#completion-comments)。

## 使用者群組報表

Adobe Learning Manager的新&#x200B;**[!UICONTROL User Group Report]**&#x200B;可顯示管理員離開時未受管理的群組，有助於管理使用者群組。 管理員可以存取「**[!UICONTROL Users]** > **[!UICONTROL User Group]**」區段下的報告。 它提供每個群組的詳細資訊，包括：

* 使用者群組型別
* 群組名稱
* 說明
* 建立者（名稱）
* 建立者（電子郵件）
* 建立時間（UTC時區）
* 使用者人數

如需詳細資訊，請參閱本文[使用者群組報告](/help/migrated/administrators/feature-summary/add-users-user-groups.md#user-group-report)。

## 輪候表報告

Adobe Learning Manager的新&#x200B;**[!UICONTROL Waitlist Report]**&#x200B;可讓管理員下載課程所有執行個體的輪候學習者清單。 管理員和講師可以從&#x200B;**[!UICONTROL Course]**&#x200B;或&#x200B;**[!UICONTROL Session Overview]**&#x200B;頁面上的&#x200B;**[!UICONTROL Waitlist]**&#x200B;區段存取此報告。 輪候表報告可從「管理員」和「講師」區段下載。

依照輪候表報表中的可用欄執行：

* 課程名稱
* 執行個體名稱
* 執行個體ID
* 執行個體狀態
* 使用者名稱
* 電子郵件
* 使用者唯一ID
* 註冊日期（UTC時區）
* 狀態
* 輪候表編號
* 輪候表限制
* 名額限制

請參閱此文章[輪候表報告](/help/migrated/administrators/feature-summary/courses.md#waitlist-report)和[輪候表報告](/help/migrated/instructors/feature-summary/learners.md#waitlist-report)，以從管理員和講師區段下載報告。

## 學習者首頁的協助工具

Adobe Learning Manager現在支援所有刊頭的替代文字，以改善學習者的協助工具。 這項功能可讓有特殊需求的學習者使用熒幕助讀程式來閱讀替代文字及瞭解影像。 您可以選取多種語言，並為每種語言提供替代文字。 請確定在個別語言中新增替代文字。 確定您帳戶中的公司標誌也包含公司名稱的替代文字。
如需詳細資訊，請參閱本文[宣告](/help/migrated/administrators/feature-summary/announcements.md#masthead)。

## 支援北印度文

Adobe Learning Manager現在推出印地語作為平台的介面語言之一，並支援平台在印度成長。 對印地語母語喇叭的支援可確保使用者完全存取所有功能、報告和整體使用者體驗。

若要變更介面語言，請遵循下列步驟：

1. 以&#x200B;**[!UICONTROL Admin]**&#x200B;登入。
2. 前往&#x200B;**[!UICONTROL Profile Settings]** > **[!UICONTROL Interface Language]**。
3. 選取&#x200B;**[!UICONTROL Hindi]**&#x200B;作為介面語言。


## 社交貼文的髒話檢查

Adobe Learning Manager現在會封鎖學習者應用程式中包含禁止字詞的社交貼文。 這有助於讓事情保持專業性和合規性，尤其是在醫療保健等敏感領域。

## 電子郵件範本最佳化

### 指派講師時傳送電子郵件給學習者

現有的電子郵件&#x200B;**[!UICONTROL You have been added as an Instructor]**&#x200B;和&#x200B;**[!UICONTROL VCProvider Session Details]**&#x200B;已合併為一個電子郵件&#x200B;**[!UICONTROL You have been added as a UserType]**。 根據使用者的角色，**[!UICONTROL UserType]**&#x200B;將為&#x200B;**[!UICONTROL Instructor]**&#x200B;或&#x200B;**[!UICONTROL Organizer]**。 這些電子郵件以前在UI中無法使用。 兩者現在已合併至單一電子郵件，並新增至UI。 管理員可以在&#x200B;**[!UICONTROL Email Template]**&#x200B;區段中存取此範本。 依預設，所有新帳戶和現有帳戶都會啟用此功能，但管理員可以從相同區段停用或啟用此功能。 每當建立工作階段並指派講師時，就會傳送此電子郵件，不論是針對工作階段，例如Zoom、Teams、Connect或其他服務。

### 工作階段取消時傳送電子郵件給學習者

從工作階段移除的講師現在只會收到工作階段取消電子郵件。 之前，他們同時收到取消和更新電子郵件。 停留在工作階段的講師將會收到工作階段更新電子郵件，以及工作階段的新邀請。

## MS Teams完成條件

目前，學習者即使加入虛擬講師引導的訓練(VILT)課程僅幾秒鐘，仍會標示為已參加。 在此版本中，我們已引入團隊模組的完成條件，以確保更準確的出席。 作者現在可以設定學習者在VILT工作階段中必須花費的最短時間，以計算其出席次數。

這是後端功能，預設為停用。 請連絡您的CSM以啟用它。

## 移轉變更

移轉工作流程中進行下列變更：

* 將模組移轉至特定資料夾。
* 已新增模組的完成條件。
* 已新增課程的完成條件

### 模組移轉中的變更

當您將模組移轉至ALM時，預設會將模組儲存在公用資料夾中。 在這個版本中，我們在[module_version.csv](assets/module_version.csv)檔案中新增了一個名為`folder`的新欄。 管理員可以使用此欄來指定移轉後模組應該移至的資料夾名稱。 管理員也可以將單一模組放入多個資料夾中，方法是列出資料夾名稱，並以逗號分隔。

資料夾欄使用字串資料型別，並且是選用欄。 以下是資料夾資料行的條件：

* 您新增的資料夾名稱應該是ALM帳戶中的現有內容資料夾。
* 值應以逗號分隔的字串。
* 如果您為已存在於不同資料夾中的模組新增資料夾名稱，新值將不會覆寫或取代指派的資料夾。 模組將新增至新資料夾，並仍可在現有資料夾中使用。
* 如果值為空白，資料夾將預設為&#x200B;**[!UICONTROL Public]**。

如需詳細資訊，請參閱[module_version csv spec](assets/4-module_version.xlsx)檔案。

### 模組移轉變更 — 完成條件

管理員可在模組移轉期間指定模組的完成條件。 在此版本中，我們已在[module_version.csv](assets/module_version.csv)中新增欄`completionCriteria`、`viewPercent`和`quizData`。

以下是新欄的條件：

1. `completionCriteria`：

   * 資料型別應為字串值，且支援的值有：
      * `LAUNCH_CONTENT`
      * `VIEW_PERCENT`
      * `QUIZ`
      * `MARK_COMPLETE`
   * 僅針對自控進度模組型別，在模組層級新增完成條件。
   * 支援的靜態內容值為`LAUNCH_CONTENT`和`VIEW_PERCENT`。
   * 互動式內容的支援值為`LAUNCH_CONTENT`、`VIEW_PERCENT`和`QUIZ`。
   * HTML5內容的支援值為`LAUNCH_CONTENT`和`MARK_COMPLETE`。

2. `viewPercent`：

   * 此欄的資料型別應為整數，值必須介於0到100之間。
   * 當completionCriteria設定為`VIEW_PERCENT`時，請在此欄中輸入必要的檢視百分比，或將其留空。

3. `quizData`：

   * 資料型別應為字串值，且支援的值是`QUIZ_ATTEMPTED`、`QUIZ_PASSED`和`QUIZPASSED_OR_LIMITREACHED`。
   * 當`completionCriteria`設定為`QUIZ`時，請在`quizData`欄中輸入適當的測驗值。

如需詳細資訊，請參閱[module_version csv spec](assets/4-module_version.xlsx)檔案。

### 課程移轉 — 完成條件變更

管理員可在課程移轉期間指定課程的完成條件。 在這個版本中，我們在[course.csv](assets/course.csv)中新增了一個名為`completionCriteria`的新欄。

`completionCriteria`欄的條件如下：

* 資料型別應為字串或數字，且為選用欄位。
* 值應該是`ALL`、`X`和`SELECTEDMODULES`。
* X是大於0且小於模組總數的整數值。
* 如果您將`completionCriteria`設為`SELECTEDMODULES`，則需要在[course_module.csv](assets/course_module.csv)檔案中標示必要的模組。
* 在`optionalCriteria`欄中輸入`TRUE`或`FALSE`。 如果您將值設為`TRUE`，則會讓模組成為必要。

如需詳細資訊，請參閱[課程csv規格](assets/3-course.xlsx)和[課程_模組csv規格](assets/6-course_module.xlsx)檔案。

## API變更

以下是API變更：

* **搜尋API**：
   * 新的模式篩選器，包含下列選項： classicSearch和advanceSearch。
   * snippetTypes的新增loMetadata選項。
* **宣告API**：
   * 包含刊頭說明的altText屬性。
* **執行個體API**：
   * 新的地區設定屬性，可擷取地區設定詳細資訊。
* **粗俗檢查**：
   * 更新API以檢查社群貼文的評論和回覆中禁止使用的字詞：
* **RPM與高載限制**：
   * 新增所有API的RPM （每分鐘要求數）和突發限制。
* **徽章API**：
   * 新屬性externalProvider，可擷取外部徽章的相關資訊。
* **工作API**：
   * 使用工作API下載「使用者群組報表」和「自訂角色稽核報表」 。

### 搜尋API中的變更

搜尋API現在具有包含兩個選項的新模式篩選器： `classicSearch`和`advanceSearch`。 `snippetTypes`也有新的`loMetadata`選項。 若要取得最佳結果，請在使用`advanceSearch`模式時於`snippetTypes`中加入`loMetadata`。

### 公告API變更

`GET /announcements API`現在包含`altText`屬性，以提供刊頭說明。

#### 使用cURL的範例要求：

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

### 執行個體API中的變更

新的`locale`屬性已新增到下列API以擷取地區設定詳細資料。

* `GET /learningObjects/{loId}/instances/{loInstanceId}`
* `GET /learningObjects/{id}?include=instances,enrollment.loInstance`
* `GET /learningObjects?include=instances,enrollment.loInstance`
* `GET /learningObjects/{id}/relatedLOs?include=instances,enrollment.loInstance`
* `POST /learningObjects/query?include=instances,enrollment.loInstance`
* `POST /search/query?include=model.instances`
* `GET /search?include=model.instances`

#### 使用cURL的範例要求：

```
curl --location 'http://abcd.com/primeapi/v2/learningObjects/course:1234567/instances/course:1234567_1234567' \
```

#### 範例要求：

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

### 褻瀆檢查的公用API變更

下列API已更新，以對社交貼文的評論和回覆執行褻瀆檢查。

* `POST /boards/{id}/posts `
* `PATCH /posts/{id}`
* `POST /posts/{id}/comments`
* `PATCH /comments/{id}`
* `POST /comments/{id}/replies`
* `PATCH /replies/{id}`

如果在貼文中找到限制字詞，將傳送以下回應。

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

### RPM和成組分解限制的變更

在此版本中，已針對所有API新增RPM （每分鐘要求數）和高載限制。 您可以在「Swagger」頁面上檢查每個API的RPM上限。

RPM是一分鐘內可傳送至API伺服器的要求數目。 高載限制允許在短時間內傳送較多的要求，超出一般的速率限制。 例如，`learningObject` API允許每分鐘最多15個請求。 如果超過此限制，API會傳回錯誤訊息。

### 徽章API中的變更

已將新屬性`externalProvider`新增到下列API，以擷取有關外部徽章的資訊，包括徽章ID和提供者名稱。

* `GET /badges `
* `GET /badges/{id}`
* `GET /skills?include=levels.badge`
* `GET /skills/{id}?include=levels.badge`
* `GET /learningObjects/{loId}/instances/{loInstanceId}?include=badge`
* `GET /users/{userId}/userBadges`
* `GET /users/{userId}/userBadges/{id}`

#### 使用cURL的範例要求：

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

### 透過工作API下載使用者群組和自訂角色稽核報告

使用者可以使用`Job API`下載&#x200B;**[!UICONTROL User Group Report]**&#x200B;和&#x200B;**[!UICONTROL Custom Role Audit Report]**。

#### 下載使用者群組報表的範例要求：

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

#### 自訂角色稽核報告下載的範例要求：

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

### 無要求內文的錯誤訊息

我們針對要求內文為必填欄位，但API未提供情形匯入了特定錯誤訊息。

#### 錯誤訊息範例：

```
{
    "status": "BAD_REQUEST",
    "title": "Generic Error"
}
```

## 報告增強功能

管理員可以在&#x200B;**管理員** > **報表**&#x200B;區段中找到這些報表變更。

### 學習成績單報告

**[!UICONTROL Learning Transcripts]**&#x200B;報告將包含兩個新欄：

* **[!UICONTROL Module ID]**：顯示每個模組的唯一識別碼。 此新欄已新增至現有&#x200B;**[!UICONTROL Module]**&#x200B;欄之後。
* **[!UICONTROL Course Instance ID]**：顯示每個課程執行個體的唯一識別碼。此新欄已新增到現有&#x200B;**[!UICONTROL Instance]**&#x200B;欄之後。
* **[!UICONTROL Completion Comment]**：此欄會擷取管理員在標示使用者完成時輸入的註解。 此新欄已在報告結尾新增。


### 工作階段摘要報告

**[!UICONTROL Session Summary]**&#x200B;報告將包含三個新欄：

* 已在&#x200B;**[!UICONTROL Session Name]**&#x200B;欄之前新增&#x200B;**[!UICONTROL Module ID]**&#x200B;欄。
* 已在&#x200B;**[!UICONTROL Session Name]**&#x200B;欄之前新增&#x200B;**[!UICONTROL Session ID]**&#x200B;欄。
* 已在&#x200B;**[!UICONTROL Instance Name]**&#x200B;欄之後新增&#x200B;**[!UICONTROL Course Instance ID]**&#x200B;欄。
* 已在&#x200B;**[!UICONTROL Enrollment Count]**&#x200B;欄之後新增&#x200B;**[!UICONTROL Completion Count]**&#x200B;欄。

## 此更新中修正的錯誤

* 修正在Android和iOS裝置上提交檔案期間，從活動模組上傳視訊時發生的錯誤。
* 修正了在行動應用程式中開啟課程的問題；網頁版本正常運作。
* 修正在Safari中檢視工作輔助和其他資源的問題。
* 修正使用者無法在行動應用程式下載工作輔助的問題。
* 修正修補程式使用者API檔案中的錯誤。
* 修正從課程刪除工作階段時，組織者未收到電子郵件通知的問題。
* 修正將模組從課程移除並重新發佈時，組織者未收到工作階段取消電子郵件的問題。
* 新增在外部使用者建立期間，在電子郵件地址中包含特殊字元「+」和「 — 」的支援。
* 修正CSV記錄值中使用者技能報告包含雙引號時，Marketo聯結器統一報告同步失敗的問題
* 修正`/skills`端點為Admin API傳回正確狀態，但學習者API一致顯示不正確或快取資料的問題。
* 修正帳戶未設定Go1聯結器時，免費課程的Go1上線失敗的問題。
* 若學習者已完成學習路徑(LP)，則無法透過移轉存取學習路徑(LP)中的課程，此問題已獲修正。
* 修正當使用者的管理員和略過層級管理員都設為SU （超級使用者）而不是管理員時，增量使用者CSV失敗的問題，並且未包含在CSV中。
* 修正控制面板報表中存放區管理員的範圍問題。
* 修正刪除草稿課程時xapi_iri未移除的問題。
* 已修正在某些情況下無法新增唯一識別碼(LO ID)的問題。
* 已修正學習計畫中的IsEmbeddable屬性未正確更新共用學習計畫的問題。
* 已修正影響學習者檢視中學習路徑顯示總期間的問題。
* 修正在刪除學習者的帳戶後，仍可透過自助註冊連結進行註冊或註冊的問題。
* 修正在建立課程期間，在課程說明中新增連結時，`www`遭到移除的問題。
* 修正隱藏資訊和下載工作輔助未正常作用的問題。
* 修正透過具有IP ID的自我註冊連結新增的新使用者無法執行單一登入(SSO)功能的問題。
* 修正刪除宣告後未擷取通知訊息資料的問題。
* 修正當透過電子郵件搜尋使用者時，搜尋結果不足的問題。

## 系統需求

檢視[Adobe Learning Manager系統需求](/help/migrated/system-requirements.md)。

## Adobe Learning Manager舊版

* [2024年7月發行版本](/help/migrated/whats-new-july-2024.md)
* [2024年3月發行版本](/help/migrated/whats-new-march-2024.md)
