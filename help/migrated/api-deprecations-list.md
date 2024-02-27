---
jcr-language: en_us
title: Adobe Learning Manager中的API淘汰
description: 隨著Adobe Learning Manager中API的發展，API會定期重新組織或升級。 API進化後，舊的API會遭到取代並最終移除。 本頁包含從已棄用的API版本移轉至較新且較穩定的API版本時，您必須知道的資訊。
contentowner: saghosh
source-git-commit: 24c886fcd9448b7f1d71526794a3c46a0f91d017
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 0%

---


# Adobe Learning Manager中的API淘汰與變更

## 2024年3月版AdobeLearning Manager中的API淘汰

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

位移限制的變更適用於所有新客戶。 若為現有客戶，則適用90天規則。

### 排除路徑

目前，Learning Manager API會遵循圖表資料結構，可讓您透過include遍歷API模型來擷取資料。 即使您最多可周遊7個層級的API，使用單一API呼叫擷取資料的計算成本很高。

我們建議所有現有客戶和新客戶進行多次小型通話，而非一次大型通話。 此方法可防止在呼叫中載入不需要的資料。

我們想要對新帳戶強制執行這些限制，並維護現有帳戶的白名單。

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

### 執行個體摘要計數變更

目前，在LO摘要端點中，您會擷取所有可能例項的數目。 例如，對於課程，您可以在回應中檢視註冊和輪候表的數目 **GET/learningObjects/{loId}/instances/{loInstanceId}/摘要**. 然後，您可以在回應中檢視completionCount和enrollmentCount。 如果課程是虛擬教室或教室，您也可以檢視其名額限制和輪候表限制。

擷取完成與註冊計數的程式在計算上非常昂貴，因此計算是以請求為基礎進行的。 如果資料不存在快取中，則會重新載入資料，這將會耗費大量計算時間。 如果有許多使用者註冊課程，則次數會很大，並有效影響CPU效能。

在AdobeLearning Manager的下一個版本中，在LO執行個體摘要端點中，會快取completionCount、enrollmentCount、seatLimit和waitlistCount。 快取的資訊會持續存在，直到註冊或取消註冊發生變更為止。 對於超過1000個註冊的計數，我們會假設預估計數，並讓所有現有帳戶和新帳戶的結果失效。

>[!NOTE]
>
>對於超過1000的計數（例如completionCount、enrollmentCount、seatLimit和waitlistCount），建議將其解譯為預估值，而非精確的數字，因為這些將會從快取中擷取。

### 依名稱排序

在下一版AdobeLearning Manager中，以下API的排序欄位中不建議使用名稱和 — name：

* GET/userGroups/{userGroupId}/users
* GET/users

>[!NOTE]
>
>對於所有現有帳戶與新帳戶，將停止依名稱與名稱排序。


## 2023年11月發行的Adobe Learning Manager中API淘汰

### 覆寫旗標

在2023年11月發行的Adobe Learning Manager中，我們已停止來自API的覆寫標幟。 覆寫旗標並非公用API規格的一部分，且旨在用於後端測試。 此標幟現已停止提供學習者API使用。 不過，標幟對管理員API仍然有效。

我們淘汰學習者API的標幟是因為覆寫標幟透過學習者API擷取大量資料。

下列學習者API日後將停止運作，因為有覆寫標幟。

<code>https://captivateprime.adobe.com/primeapi/v2/users?page[offset]=0&amp;page[limit]=10&amp;sort=id&amp;override=TRUE</code>

### 技能型新建議的API變更

Adobe Learning Manager能改善客戶和合作夥伴啟用帳戶的建議。 隨著課程、學習路徑和認證的排名演演算法發生變更，建議演演算法的這項改善為內容探索提供了更好的使用者體驗。

演演算法將不再允許對等式建議。 此變更不會影響現有的使用者，但「產業調整」選項將繼續存在。 在「自訂」選項中，AdobeLearning Manager將不再允許自訂對等選取。

對等群組現在會變成帳戶，而學習者會看到顯示群組中趨勢主題的字串。 所有建議都可解釋。 例如，如果您檢視的是主旨的某件事，分段上的卡片就會顯示課程的原因。

### 通知宣告報告的變更

在舊版AdobeLearning Manager中，通知宣告報告沒有任何篩選器。 Adobe Learning Manager已下載帳戶中的所有通知。

在2023年11月版本中，我們已新增日期篩選器，讓您在指定期間內下載通知。  不過，您只能下載過去六個月的報表。