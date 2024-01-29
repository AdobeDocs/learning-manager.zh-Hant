---
jcr-language: en_us
title: Learning Manager中的API速率限制
contentowner: saghosh
preview: true
source-git-commit: 544c695a77c21dd9162b9b943b6119d27aa373dc
workflow-type: tm+mt
source-wordcount: '1757'
ht-degree: 0%

---



# Learning Manager中的API速率限制

## 速率限制簡介 {#introductiontoratelimiting}

Adobe Learning Manager公開豐富的REST API套件，可協助客戶建立與Learning Manager整合的應用程式，或甚至是自訂使用者體驗和工作流程擴充功能以協助其業務。

每當呼叫API時，Learning Manager伺服器就會使用共用的運算資源，因此我們必須謹慎行事，以確保應用程式能正常運作，不會危及平台的效能和可用性特徵。 這是透過引進對API使用者端進行呼叫的方式（頻率和速度）的限制來實現的。

例如，應用程式可能會嘗試取得該帳戶中的所有使用者，並且可能會以快速的速度發出多個分頁API呼叫。 開發人員誤會將此稱為緊密回圈，導致伺服器負載過重，並造成應用程式緩慢，甚至因消耗超出預期或所需的資源而危及平台。

為了解決此問題，我們針對單一使用者在特定帳戶的特定使用者端應用程式中可進行API呼叫的數量引入速率限制。 我們以每分鐘要求數來測量此值，縮寫為RPM。 例如，當我們說GETAPI呼叫的限制是600 RPM，這僅表示單一使用者不能超過一分鐘內最多600次呼叫，並且如果使用者超過該限制，則使用者將獲得速率限制。 系統以毫秒的粒度追蹤請求，因此此限制對應至每100毫秒(ms)1個請求。 還有一個稱為Burst的引數，它也和速率限制一起定義，它定義使用者可以提出多少個超出指定速率（在我們的案例中為600RPM）的請求。 例如，如果「高載」引數為10；這表示在佇列中最多可分配10個位置，而且當要求「來得太早」（在此例中是小於100毫秒）時，如果佇列中有一個位置可供使用，就會立即處理要求。 接著，該位置會標示為「已佔用」，並在適當時間過後（在此案例中為100毫秒後）才會釋出供其他請求使用。 真實世界的流量通常具有突發，這就是「突發」引數有幫助的地方。 對於Learning Manager平台，我們為特定API版本（例如V2）、角色（學習者/管理員）和動詞(GET/PUT/POST/DELETE/PATCH)定義限制。 在以上說明的範例中，我們假設速率限製為(600， 10)。

雖然我們在Learning Manager中一律對Public API設有速率限制，但到目前為止，我們還是相當自由地允許使用非常高的RPM。 然而，隨著您喜愛的學習平台不斷成長，我們的API使用量也迅速增加，我們決定明文記錄這些速率限制，以利所有客戶及平台管理。 在此內容中，我們已升級API，開始傳回新的API回應（HTTP狀態代碼429）；您目前尚未看見。 當超過速率限制時，此回應會提供給API使用者端。 使用者端應用程式現在需要處理此回應程式碼，以符合其應用程式的邏輯；本檔案主要旨在協助開發人員瞭解當他們看到這類回應時，如何將正確的邏輯整合到程式碼中所需的資訊。

## 如何確認強制的速率限制？ {#howtoconfirmtheenforcedratelimits}

對於每個請求，回應標頭都包含下列資訊：

```
x-rate-limit: 600r/m 
x-burst: 10
```

* x-rate-limit會根據每分鐘的請求數，指定基本請求速率臨界值。
* x-burst指定系統接受多少個超出基本要求速率的要求立即處理。

## 如何擷取由速率限制引起的錯誤？ {#howtocatcherrorscausedbyratelimits}

對於每個請求，您可以檢視您是否受限於速率限制。 如果您收到429的回應代碼「{&quot;message&quot;：&quot;429太多請求&quot;}&quot;，表示您已達到速率限制。

最佳實務是在可擷取429回應的指令碼中包含程式碼。 如果您的指令碼忽略了「太多請求」錯誤並繼續嘗試提出請求，您可能會開始收到null錯誤。 此時，錯誤資訊在診斷問題時並不實用。

例如，碰撞至速率限制的curl請求可能會傳回以下回應：

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

回應包含下列索引鍵的相關資訊：

```
status: 429 
retry-after: 10.752
```

狀態代碼429表示「請求數太多」，且目前請求未處理。 retry-after標頭指定您可以在10.752秒後重試API呼叫。 您的程式碼應停止提出其他API要求，直到超過足夠的時間再重試。

下列偽程式碼顯示擷取速率限制錯誤的簡單方法：

```
response = request.get(url) 
if response.status equals 429: 
    alert('Rate limited. Waiting to retry…') 
    wait(response.retry-after) 
    retry(url)
```

事實上，我們甚至已建立一個Learning Manager虛擬API，讓您在遊戲中輕鬆處理429狀態代碼。

```
curl -X GET --header 'Accept: application/json' --header 'Authorization: oauth < 
<token>
  >' 'https://learningmanager.adobe.com/learningmanagerapi/v2/dummy 
</token>
```

此虛擬API的限製為：

```
x-rate-limit: 5r/m 
x-burst: 2
```

虛擬API的限制刻意偏低，因此您很快就會遇到速率限制，然後可以更專注於開發程式碼以擷取和處理速率限制錯誤。

## 測試虛擬API {#testingthedummyapi}

我們提供了端點，讓您瞭解速率限制的運作方式。 為此，我們已建立名為GET/dummy的特殊端點，其具有學習者讀取範圍。 此API經過刻意設定，具有非常嚴格的速率限制，每分鐘5個請求，高載限制= 2。

只要以低於5 RPM和高於5 RPM的速率達到此端點，您就可以輕鬆測試此結果。 撰寫程式碼以處理HTTPS狀態程式碼429並根據回應標頭中的資訊。

為了方便您檢視，您可以檢視此範例JavaCript程式碼，其中說明這一點。 按一下此 [小提琴](https://jsfiddle.net/ACAPJS/9yv8zcmL/) 並檢視程式碼的實際運作情況。

此應用程式需要您提供帳戶的學習者角色應用程式權杖。 請參閱 [應用程式開發人員手冊](https://captivateLearning Manager.adobe.com/docs/Learning Managerapi/v2/)以取得API權杖的相關資訊，且您可以使用Learning Manager整合管理員應用程式之開發人員資源區段中的權杖協助程式來產生權杖。

此應用程式會一次對回圈中的虛擬API進行10次呼叫。 由於虛擬API的速率限製為(5， 2)；在Learning Manager收到的前5+2個呼叫將成功後，就會違反速率限制，因此您會看到這些呼叫的成功回應。

不過，請注意此應用程式在回應中會如何尋找429狀態代碼並加以處理。 當此應用程式取得這類回應時，會列印API回應中的詳細資料、等待建議的時間量並重試失敗的嘗試。

## 處理速率限制的最佳實務 {#bestpracticestohandleratelimiting}

很多時候，帳戶中的資料不會經常變更。 例如，帳戶中的課程可能不會經常變更。 與其每次都嘗試取得所有資料，不如考慮使用快取機制，看看您能否在需要時取得特定資料。 如此一來，當您的應用程式確實需要撥打許多電話時，您就擁有在費率限制內足夠的配額，可以撥打這些重要的電話。

有些資料變更的頻率可能更高，而您可能需要更頻繁地取得這些資料。 即使如此，請自問您的應用程式是否負擔得起稍微過時的資料（可能位於您的快取中，而您已於幾分鐘前擷取），因為它可能對使用者的工作流程沒有影響。 即使您必須從伺服器取得最新資料，再次謹慎地擷取所需的特定資料，而不是取得所有資料。

有時候，您也可能無法取得大量資料，因為API的彈性不足，無法只透過一次呼叫就為您提供您想要的確切資料。 檢視API是否提供篩選器和排序條件，可用將呼叫數降到最低；您仍應考慮快取，因為您帳戶中的許多使用者可能需要相同的資料。

當您在具有GUI的互動式應用程式環境中取得太多資料時，該應用程式可能會嘗試執行太多工作，而且可能會因為大量資訊/功能而讓使用者不知所措，進而影響您應用程式的使用者體驗。

當您建置非互動式應用程式（可能像是每日工作）時，可能需要大量擷取大量資料。 在這種情況下，請考慮使用工作API，其主要設計旨在以CSV格式傳回大量資料。 請注意，工作API會有配額限制，您可以每天N次叫用它們。

由於Learning Manager已實施JSONAPI規格，因此有API可讓您側載部分資料。 這可協助您節省進行額外API呼叫的時間，但您必須以過於急切地取得資料的方式來權衡這個問題。 由於側載資料有時可能非常大，在API分頁呼叫中，您設定的頁面大小上限為10；但對於不包含的API呼叫，您或許可以指定較大的頁面大小（上限為100）

最終，如果您在短時間內提出許多API請求，將會觸及API請求速率限制。 當您達到上限時，Learning Manager將停止處理任何其他請求，直到超過特定時間為止。

速率限制概述於本文的最後一節。 建議您熟悉限制。

## V2 API端點的速率限制 {#ratelimitsforv2apiendpoints}

下表提供各種V2端點的限制。 目前並未對客戶施加速率限制，但這些限制將從DD/MM/YYYY開始執行。 因此，客戶應檢閱其現有應用程式的程式碼，以瞭解如何調整程式碼以留意這些速率限制，並使用HTTP狀態碼429處理API回應，這點極為重要。

<table> 
 <tbody>
  <tr> 
   <td><p><b>作業</b></p></td> 
   <td><p><b>管理API</b></p></td> 
   <td><p><b>學習者API</b></p></td> 
  </tr> 
  <tr> 
   <td><p>DELETE</p></td> 
   <td><p>(25， 10) <br></p></td> 
   <td><p>(20， 10)<br></p></td> 
  </tr> 
  <tr> 
   <td><p>PATCH</p></td> 
   <td><p>(60， 20)</p></td> 
   <td><p>(15， 5) <br></p></td> 
  </tr> 
  <tr> 
   <td><p>POST</p></td> 
   <td><p>(30， 10)<br></p></td> 
   <td><p>(30， 10)<br></p></td> 
  </tr> 
  <tr> 
   <td><p>PUT</p></td> 
   <td><p>(20， 10)<br></p></td> 
   <td><p>(20， 10)<br></p></td> 
  </tr> 
  <tr> 
   <td><p>GET</p></td> 
   <td><p>(100， 100)<br></p></td> 
   <td><p>(100， 30)<br></p></td> 
  </tr> 
 </tbody>
</table>

