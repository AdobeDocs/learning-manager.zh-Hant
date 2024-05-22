---
jcr-language: en_us
title: Adobe Learning Manager不再使用API
description: 隨著Adobe Learning Manager中API的發展，API會定期重新組織或升級。 API進化後，舊的API會遭到取代並最終移除。 本頁包含從已棄用的API版本移轉至較新且較穩定的API版本時，您必須知道的資訊。
contentowner: saghosh
exl-id: 0fe9a3cb-9114-42d6-81ae-1a4f28c984fa
source-git-commit: 670d0477b246af2a0257e41eca799817e391b348
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Adobe Learning Manager中的API淘汰與變更

## 2024年3月發行的Adobe Learning Manager中API的淘汰

<!-- ### Changes in Rate Limits

With the next release of Adobe Learning Manager, we're restructuring API rate limits for new accounts. For existing accounts, only the Admin APIs will be rate-limited. After 90 days (about 3 months), we will restructure rate limits for all APIs, but existing accounts will be whitelisted according to current usage. Existing accounts need to revisit their learner API usage. 

For new accounts, if they want to increase the rate limits, they must contact the Customer Success team of ALM. 

#### Which APIs will be rate limited 

For new accounts, all Admin, Learner, and Search APIs will have rate limits and burst enforced.  

The API burst rate or burst limit refers to the maximum number of requests allowed to be made to an API in a short burst within a limited timeframe. 

The following table lists the rate and burst limits for the APIs.

<table>
    <tr>
        <th>API</th>
        <th>Number of requests-RPM</th>
        <th>Number of requests-Burst</th>
    </tr>
    <tr>
        <td>Admin</td>
        <td>5</td>
        <td>5</td>
    </tr>
    <tr>
        <td>Learner</td>
        <td>20</td>
        <td>5</td>
    </tr>
    <tr>
        <td>Search</td>
        <td>50</td>
        <td>5</td>
    </tr>
</table>
-->

### 位移限制的變更

由於位移值擷取的記錄數量相當多，且整體效能降低，因此我們強制實施 **500** 記錄。 在下一個版本中，管理員和學習者皆須使用 **GET使用者** API最多會傳回 **500** 記錄。

如果您需要擷取更多記錄，請使用 **GET工作** API。

<!--### Exclude paths 

At present, Learning Manager APIs follow a graph data structure, which allows you to fetch data by traversing the API model through includes. Even though you could traverse an API up to seven levels, fetching the data using a single API call is computationally expensive. 

We recommend that all existing and new customers make small calls multiple times instead of one large call. This approach will prevent unwanted data from being loaded in the call. 

We want to enforce these restrictions on new accounts and maintain a whitelist of existing accounts.-->

#### 哪些路徑已過時

已棄用下列路徑：

* /learningObject
   * 已棄用的路徑：
      * enrollment.loInstance.loResources.resources
      * instances.loResources.resources
   * 新路徑：
      * enrollment.loInstance.loResources
      * instances.loResources

* /learningObject/{id}
   * 已棄用的路徑：
      * enrollment.instances.subLoInstances.learningObject
   * 新路徑：
      * enrollment.instances.subLoInstances

* /enrollings
   * 已棄用的路徑：
      * loInstance.learningObject.enrollment
   * 新路徑：
      * loInstance.learningObject

* /learningObject/{id}
   * 已棄用的路徑：
      * instance.subLoInstances.learningObject.enrollment.loResourceGrades
   * 新路徑：
      * instance.subLoInstances

<!--### Instance summary count changes 

Currently, in the LO summary endpoint, you fetch the number of all possible instances. For example, for a course, you can view the number of enrollments and waitlists in the response for **GET /learningObjects/{loId}/instances/{loInstanceId}/summary**. You can then view the completionCount and enrollmentCount in the response. If the course is a VC or classroom, you can also view its seat limit and waitlist limit. 

The process of retrieving the completion and enrollment counts is computationally expensive, therefore the calculation is done on a request basis. If the data is not present in the cache, the data is reloaded, which is computationally intensive. If there are many users enrolling in a course, the counts will be large, and effectively impacts CPU performance. 

In the next release of Adobe Learning Manager, in the LO Instance summary endpoint, the completionCount, enrollmentCount, seatLimit, and waitlistCount are cached. The cached information persists till there are changes in enrollments or unenrollments. For counts exceeding 1000 enrollments, we'll assume the estimated counts, and invalidate the results for all existing and new accounts.

>[!NOTE]
>
>For counts, such as, completionCount, enrollmentCount, seatLimit, and waitlistCount exceeding1000, it's advisable to interpret them as estimates rather than precise figures, as these will be retrieved from cache.-->

### 依名稱排序

在下一個版本的Adobe Learning Manager中，下列API的排序欄位中將不使用name和 — name：

* GET/userGroups/{userGroupId}/users
* GET/users

>[!NOTE]
>
>對於所有現有帳戶與新帳戶，將停止依名稱與名稱排序。


## Adobe Learning Manager 2023年11月版本中的API淘汰

### 覆寫旗標

在2023年11月發行的Adobe Learning Manager中，我們已停止來自API的覆寫標幟。 覆寫旗標並非公用API規格的一部分，且旨在用於後端測試。 此標幟現已停止提供學習者API使用。 不過，標幟對管理員API仍然有效。

我們淘汰學習者API的標幟是因為覆寫標幟透過學習者API擷取大量資料。

下列學習者API日後將停止運作，因為有覆寫標幟。

_/primeapi/v2/users？page[offset]=0&amp;page[limit]=10&amp;sort=id&amp;override=TRUE_

### 技能型新建議的API變更

Adobe Learning Manager改善了針對啟用客戶和合作夥伴的帳戶的建議。 隨著課程、學習路徑和認證的排名演演算法發生變更，建議演演算法的這項改善為內容探索提供了更好的使用者體驗。

演演算法將不再允許對等式建議。 此變更不會影響現有的使用者，但「產業調整」選項將繼續存在。 在「自訂」選項中，Adobe Learning Manager不再允許以自訂對等專案為基礎的選取。

對等群組現在會變成帳戶，而學習者會看到顯示群組中趨勢主題的字串。 所有建議都可解釋。 例如，如果您檢視的是主旨的某件事，分段上的卡片就會顯示課程的原因。

### 通知宣告報告的變更

在舊版Adobe Learning Manager中，「通知公告」報告沒有任何篩選器。 Adobe Learning Manager已下載帳戶中的所有通知。

在2023年11月版本中，我們已新增日期篩選器，讓您在指定期間內下載通知。  不過，您只能下載過去六個月的報表。

### 淘汰GET/使用者端點中的高位移值

為了改善系統效能並更有效地管理資源使用率，Adobe已同時棄用GET/使用者端點中的高位移值 **管理員** 和 **學習者** 範圍。 我們建議使用 **工作API** 以擷取含有位移值的記錄。

