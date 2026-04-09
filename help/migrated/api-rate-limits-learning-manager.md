---
jcr-language: en_us
title: Learning Manager 中的 API 速率限制
description: Adobe Learning Manager 展現了一套豐富的 REST API，協助客戶打造與 Learning Manager 整合的應用程式，甚至是客製化的使用者體驗與工作流程擴充，幫助他們的業務。
contentowner: saghosh
preview: true
source-git-commit: 3188d7f5593aeee87978e1e46456f01e1f41d57b
workflow-type: tm+mt
source-wordcount: '1801'
ht-degree: 1%

---



# Learning Manager 中的 API 速率限制

## 速率限制導論 {#introductiontoratelimiting}

Adobe Learning Manager 展現了一套豐富的 REST API，協助客戶打造與 Learning Manager 整合的應用程式，甚至是客製化的使用者體驗與工作流程擴充，幫助他們的業務。

每當呼叫 API 時，Learning Manager 伺服器都會共享計算資源，因此我們必須謹慎且謹慎，確保應用程式運作順暢，不會危及平台的效能與可用性特性。 這是透過對 API 用戶端呼叫方式（頻率與速度）設限來實現的。

例如，應用程式可能試圖取得該帳號中的所有使用者，並可能以快速的速度呼叫多個分頁 API。 而開發者若不小心將此設定成緊密迴圈，導致伺服器負載巨大，應用程式變慢，甚至因消耗超出預期或需求而危及平台安全。

為了解決這個問題，我們引入了單一使用者在特定客戶端應用程式中，能呼叫多少次 API 的速率限制。 我們以每分鐘請求數（Requests Per Minute，簡稱 RPM）來衡量。 例如，當我們說 GET API 呼叫的上限是 600 RPM 時，這只是表示單一使用者在一分鐘內最多只能呼叫 600 次，若超過該限制，使用者將受到速率限制。 請求以毫秒級追蹤，因此此限制相當於每 100 毫秒（ms）有 1 個請求。 還有一個參數叫做 Burst，它也與速率限制一同定義，定義使用者能發出超過指定速率（我們這裡是 600RPM）的請求次數。 例如，若突發參數為 10;這表示最多會分配 10 個時段，當請求「太早」（我們的情況是早於 100 毫秒）到達時，如果隊列中有空位，該請求會立即被處理。 該時段會被標記為「已佔用」，直到適當時間過去（我們的情況是 100 毫秒後）才會釋放給其他請求使用。 現實中的流量通常是爆發，這時爆發參數就派上用場了。 對於 Learning Manager 平台，我們會為特定 API 版本（例如 V2）、角色（學習者/管理員）以及動詞（GET/PUT/POST/DELETE/PATCH）定義限制。 在上述範例中，我們可以說速率上限是 （600， 10）。

雖然我們一直以來在 Learning Manager 中對 Public API 有速率限制;到目前為止，我們對允許非常高轉速的使用相當寬鬆。 然而，隨著您喜愛的學習平台的成長，我們看到 API 的使用量快速成長，因此決定將這些速率限制明確記錄下來，以造福所有客戶並提升平台管理。 在此情境下，我們已升級 API，開始回傳新的 API 回應（HTTP 狀態代碼 429）;而你目前還沒看到。 當速率限制被突破時，此回應會提供給 API 用戶端。 客戶端應用程式現在需要依照其應用程式邏輯來處理這些回應程式碼;而這份文件主要目的是協助開發者在看到此類回應時，獲得必要資訊，以便在程式碼中融入正確的邏輯。

## 如何確認強制的速率限制？ {#howtoconfirmtheenforcedratelimits}

對於每個請求，回應標頭包含以下資訊：

```
x-rate-limit: 600r/m 
x-burst: 10
```

* x-rate-limit 以每分鐘請求數來指定基本請求率門檻。
* X-BURST 指定超過基準請求率的請求數量可立即被接受。

## 如何發現因速率限制引起的錯誤？ {#howtocatcherrorscausedbyratelimits}

對於每個請求，你可以檢查是否已經觸及費率限制。 如果你收到回應代碼 429，「{“message”：“429 太多請求}}”，表示你已達到速率上限。

最佳做法是在腳本中加入能捕捉 429 個回應的程式碼。 如果你的腳本忽略「請求過多」錯誤，繼續嘗試發出請求，你可能會開始出現 null 錯誤。 到那時，錯誤資訊對診斷問題就沒什麼用了。

例如，一個撞到速率限制的 curl 請求可能會回傳以下回應：

```
< HTTP/2 429 
< date: Wed, 04 Nov 2020 06:53:04 GMT 
< content-type: application/json; charset=utf-8 
< server: openresty 
< x-rate-limit: 60r/m 
< x-burst: 10 
< retry-after: 10.752 
< access-control-allow-credentials: true 
< access-control-allow-methods: GET, POST, OPTIONS, PUT, HEAD, DELETE, PATCH 
< access-control-allow-headers: X-acap-all-roles, X-acap-account,X-acap-user,X-acap-caller-role,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type, x-experience-api-version, Authorization, X-CSRF-TOKEN, X-HTTP-Method-Override 
< strict-transport-security: max-age=31536000; includeSubDomains 
< x-frame-options: SAMEORIGIN 
< x-xss-protection: 1 
< x-content-type-options: nosniff 
< x-request-id: gwBBFC9741-58A5-43B1-B1FE-7D14275961E7 
< strict-transport-security: max-age=31536000; includeSubDomains
```

回應包含以下金鑰的資訊：

```
status: 429 
retry-after: 10.752
```

狀態代碼 429 表示「請求過多」，且目前的請求尚未被處理。 retry-after 標頭規定你可以在 10.752 秒內重試 API 呼叫。 你的程式碼應該停止發送額外的 API 請求，直到足夠時間重試。

以下偽代碼展示了一個捕捉速率限制錯誤的簡單方法：

```
response = request.get(url) 
if response.status equals 429: 
    alert('Rate limited. Waiting to retry…') 
    wait(response.retry-after) 
    retry(url)
```

事實上，我們甚至為你打造了一個 Learning Manager 虛擬 API，讓你熟悉並熟悉處理 429 狀態碼。

```
curl -X GET --header 'Accept: application/json' --header 'Authorization: oauth < 
<token>
  >' 'https://learningmanager.adobe.com/learningmanagerapi/v2/dummy 
</token>
```

這個虛擬 API 的限制為：

```
x-rate-limit: 5r/m 
x-burst: 2
```

虛擬 API 的限制刻意設計得很低，讓你能很快撞到速率限制，然後可以更專注於開發程式來捕捉和處理速率限制錯誤。

## 測試虛擬 API {#testingthedummyapi}

我們提供了一個終端，讓你了解速率限制的運作方式。 為此，我們建立了一個名為 GET /dummy 的特殊端點，具有學習者讀取範圍。 此 API 刻意設定為非常嚴格的速率限制，每分鐘 5 次請求，突發限制 = 2。

你可以用轉速低於5轉、高於5轉的頻率來測試這個終點。 根據回應標頭中的資訊，撰寫程式碼來處理 HTTPS 狀態碼 429。

為了讓你更簡單，可以參考這段 JavaCcript 範例程式碼說明這點。 點擊這 [把](https://jsfiddle.net/ACAPJS/9yv8zcmL/) 小提琴，看看程式碼的運作。

此申請需要你提供一個學習者角色申請令牌。 請參閱 [應用程式開發手冊]（https://captivateLearning Manager.adobe.com/docs/Learning Managerapi/v2/）以取得 API 權杖的資訊，您也可以使用學習管理器整合管理應用程式開發資源區的權杖助手來產生權杖。

這個應用程式一次對虛擬 API 進行 10 次迴圈呼叫。 由於虛擬 API 的速率限制為 （5， 2）;當 Learning Manager 接到的前 5+2 通電話成功後，速率上限就會被突破，並且你會看到它們的成功回應。

不過請注意，這個應用程式會尋找並處理 429 狀態碼的回應。 當這個應用程式收到這樣的回應時，會列印出 API 回應中的細節，等待建議的時間，然後重試失敗的嘗試。

## 處理速率限制的最佳實務 {#bestpracticestohandleratelimiting}

很多時候，帳戶裡的資料其實不會經常變動。 例如，帳號裡的課程可能不會經常變動。 與其每次都想收集所有資料，不如試著在需要時取得特定資料，並考慮使用快取機制。 這樣一來，當你的應用程式真的需要打很多電話時，你在費率限制內就有足夠的配額來撥打那些重要的電話。

有些資料可能會更頻繁變動，你可能需要更頻繁地取得。 即使如此，也請問問你的應用程式是否能承受稍微過時的資料（例如你快取中某個幾分鐘前取得的資料），因為這可能對使用者的工作流程沒有影響。 即使你必須從伺服器取得新資料，也可以謹慎地只取得你需要的特定資料，而不必全部取得。

有時你也無法選擇取得大量資料，因為 API 可能不夠靈活，無法用一次呼叫就完全提供你想要的資訊。 看看 API 是否提供篩選器和排序條件，用來減少呼叫次數;你仍然應該考慮快取，因為你帳戶中的許多使用者可能需要相同的資料。

當你在帶有圖形介面的互動應用程式中取得過多資料時，應用程式很可能想做太多事情，導致使用者因資訊或功能而感到壓力，影響應用程式的使用者體驗。

當你在打造非互動式應用程式（例如日常工作）時，可能需要大量資料來取用。 在這種情況下，可以考慮使用 Job API，因為它主要是設計用來回傳 CSV 格式的大量資料。 請注意，Job API 會有配額限制，你可以每天呼叫 N 次。

由於 Learning Manager 實作了 JSONAPI 規範，有些 API 也可以側載部分資料。 這樣可以省下額外 API 呼叫的次數，但你得用太急切的方式取得資料。 由於側載資料有時會非常龐大，在 API 分頁呼叫中，最大頁面大小限制為 10;但對於沒有包含的 API 呼叫，你可能可以指定更大的頁面大小（最多 100）

最終，如果你在短時間內大量提交 API 請求，就會遇到 API 請求速率的限制。 當你達到上限時，學習管理器會停止處理任何請求，直到一定時間過去。

費率限制詳見本文最後一節。 建議你先熟悉這些限制。

## V2 API 端點的速率限制 {#ratelimitsforv2apiendpoints}

下表提供了各種 V2 端點的限制。 目前，這些費率限制尚未對客戶施加，但這些限制將從 DD/MM/YYYY 開始執行。 因此，客戶必須檢視現有應用程式的程式碼，了解如何調整程式碼以了解這些速率限制，並處理 HTTP 狀態碼為 429 的 API 回應。

<table> 
 <tbody>
  <tr> 
   <td><p><b>運作</b></p></td> 
   <td><p><b>管理 API</b></p></td> 
   <td><p><b>學習器 API</b></p></td> 
  </tr> 
  <tr> 
   <td><p>刪除</p></td> 
   <td><p>(25, 10) <br></p></td> 
   <td><p>(20, 10)<br></p></td> 
  </tr> 
  <tr> 
   <td><p>補丁</p></td> 
   <td><p>(60, 20)</p></td> 
   <td><p>(15, 5) <br></p></td> 
  </tr> 
  <tr> 
   <td><p>後期</p></td> 
   <td><p>(30, 10)<br></p></td> 
   <td><p>(30, 10)<br></p></td> 
  </tr> 
  <tr> 
   <td><p>賣權</p></td> 
   <td><p>(20, 10)<br></p></td> 
   <td><p>(20, 10)<br></p></td> 
  </tr> 
  <tr> 
   <td><p>去</p></td> 
   <td><p>(100, 100)<br></p></td> 
   <td><p>(100, 30)<br></p></td> 
  </tr> 
 </tbody>
</table>

