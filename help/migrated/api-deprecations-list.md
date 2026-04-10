---
jcr-language: en_us
title: Adobe Learning Manager 中的 API 棄用
description: 隨著 Adobe Learning Manager 的 API 演進，API 會定期重組或升級。 當 API 演進時，舊的 API 會被棄用並最終移除。 本頁包含你在從棄用 API 版本遷移到更新且更穩定 API 版本時需要知道的資訊。
contentowner: saghosh
exl-id: 0fe9a3cb-9114-42d6-81ae-1a4f28c984fa
source-git-commit: 864c3a4e60cf1bf1c049838fb2ba46ebbcb28ddf
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Adobe Learning Manager 中的 API 棄用與變更

## 2024 年 3 月 Adobe Learning Manager 版本中的 API 棄用

<!--
 ### Changes in Rate Limits

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

### 抵消限額的變更

由於偏移值會取得大量紀錄，導致整體效能變慢，我們強制執行最多 **500** 筆紀錄。 在下一個版本中，對於管理員和學習者 **，GET Users** API 最多可回傳 **500** 筆紀錄。

如果你需要更多紀錄來取得，可以使用 **GET Jobs** API。

<!--
### Exclude paths 

At present, Learning Manager APIs follow a graph data structure, which allows you to fetch data by traversing the API model through includes. Even though you could traverse an API up to seven levels, fetching the data using a single API call is computationally expensive. 

We recommend that all existing and new customers make small calls multiple times instead of one large call. This approach will prevent unwanted data from being loaded in the call. 

We want to enforce these restrictions on new accounts and maintain a whitelist of existing accounts.
-->

#### 哪些路徑會被棄用

以下路徑已被棄用：

* /learningObjects
   * 已棄用路徑：
      * enrollment.loInstance.loResources.resources
      * instances.loResources.resources
   * 新路線：
      * enrollment.loInstance.loResources
      * instances.loResources

* /learningObjects/{id}
   * 已棄用路徑：
      * enrollment.instances.subLoInstances.learningObject
   * 新路線：
      * enrollment.instances.subLoInstances

* /註冊人數
   * 已棄用路徑：
      * loInstance.learningObject.enrollment
   * 新路線：
      * loInstance.learningObject

* /learningObjects/{id}
   * 已棄用路徑：
      * instance.subLoInstances.learningObject.enrollment.loResourceGrades
   * 新路線：
      * instance.subLoInstances

<!--
### Instance summary count changes 

Currently, in the LO summary endpoint, you fetch the number of all possible instances. For example, for a course, you can view the number of enrollments and waitlists in the response for **GET /learningObjects/{loId}/instances/{loInstanceId}/summary**. You can then view the completionCount and enrollmentCount in the response. If the course is a VC or classroom, you can also view its seat limit and waitlist limit. 

The process of retrieving the completion and enrollment counts is computationally expensive, therefore the calculation is done on a request basis. If the data is not present in the cache, the data is reloaded, which is computationally intensive. If there are many users enrolling in a course, the counts will be large, and effectively impacts CPU performance. 

In the next release of Adobe Learning Manager, in the LO Instance summary endpoint, the completionCount, enrollmentCount, seatLimit, and waitlistCount are cached. The cached information persists till there are changes in enrollments or unenrollments. For counts exceeding 1000 enrollments, we'll assume the estimated counts, and invalidate the results for all existing and new accounts.

>[!NOTE]
>
>For counts, such as, completionCount, enrollmentCount, seatLimit, and waitlistCount exceeding1000, it's advisable to interpret them as estimates rather than precise figures, as these will be retrieved from cache.
-->

### 依名稱排序

在 Adobe Learning Manager 的下一版本中，以下 API 的排序欄位中已不再使用 name 和 –name：

* 取得 /userGroups/{userGroupId}/users
* 取得 /users

>[!NOTE]
>
>對於所有現有及新帳號，依名稱排序和 –name 將被棄用。


## 2023 年 11 月 Adobe Learning Manager 版本中的 API 棄用

### 覆寫旗標

在 2023 年 11 月的 Adobe Learning Manager 版本中，我們已停止對 API 的覆寫標記。 覆寫旗標並非公開 API 規範的一部分，主要用於後端測試。 該旗標現已停止用於學習者 API。 不過，該旗標對於管理 API 仍然有效。

我們之所以棄用 Learner API 的旗標，是因為覆蓋旗標透過 Learner API 取得大量資料。

未來，以下的 Learner API 將因覆蓋標誌而停止運作。

_/primeapi/v2/users？page[offset]=0&amp;page[limit]=10&amp;sort=id&amp;override=TRUE_

### 基於技能的新建議 API 變更

Adobe Learning Manager 改善了客戶與合作夥伴啟用帳號的建議。 推薦演算法的改進，加上課程、學習路徑與認證排名演算法的改變，為使用者在內容發現上提供了更佳的體驗。

演算法將不再允許基於同儕的推薦。 此變更不會影響現有用戶，但產業整合選項仍將持續存在。 自訂選項中，Adobe Learning Manager 將不再允許自訂同儕選擇。

同儕群組現在變成一個帳號，學習者會看到一串顯示群組中熱門主題的串。 所有建議都是可以解釋的。 例如，如果你正在觀看某個主題的內容，條帶上的卡片會顯示該課程的理由。

### 通知公告報告變更

在早期的 Adobe Learning Manager 版本中，通知公告報告沒有任何篩選功能。 Adobe Learning Manager 下載了帳號內的所有通知。

在 2023 年 11 月的版本中，我們新增了日期篩選器，您可以透過此在指定期間內下載通知。  不過，你只能下載過去六個月的報告。

### GET /users 端點中高偏移值的棄用

為了提升系統效能並更有效管理資源利用率，Adobe 已棄用 GET /users 端&#x200B;**點中 ADMIN 與** LEARNER **&#x200B;**&#x200B;範圍的高偏移值。我們建議使用 **Jobs API** 來取得帶有偏移值的紀錄。

