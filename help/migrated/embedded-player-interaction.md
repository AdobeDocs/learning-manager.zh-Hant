---
jcr-language: en_us
title: 嵌入式玩家互動 API 文件
description: 了解各種 API 來聆聽 Adobe Learning Manager 內建播放器中的事件並觸發動作
contentowner: chandrum
exl-id: 4734ecc1-cc8a-40b0-8997-32a31ec661ec
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 5%
---
# 嵌入式玩家互動 API 文件

Adobe Learning Manager 提供一個函式庫，可整合進應用程式中。 此函式庫提供多種 API，用於監聽事件並觸發嵌入播放器中的動作。

利用提供的 API，你可以播放、暫停，並對玩家執行其他操作。

## 載入函式庫

圖書館可在此 [地點](https://cpcontents.adobe.com/public/publiccdn/playerInteractionLib.min.js)使用。

要載入資料庫，請依照以下步驟操作：

1. 在消費者應用程式中載入 js 檔案。
2. 載入函式庫時，會自動填充 window.cpPlayerLib。

>[!NOTE]
>
>如果你沒有使用 prod US，請根據你的環境設定參數 cpPlayerLib.env 和 cpPlayerLib.sourceOrigin。

預設值如下：

* window.cpPlayerLib.env = [https://learningmanager.adobe.com/app/player](https://learningmanager.adobe.com/app/player);
* window.cpPlayerLib.sourceOrigin = “[https://cpcontents.adobe.com](https://cpcontents.adobe.com/)”;

### 可用方法

cpPlayerLib 函式庫包含以下函式：

**startPlayer（開始球員）**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>startPlayer（開始球員）</td>
</tr>
<tr>
<td>說明</td>
<td>在應用程式中載入播放器。</td>
</tr>
<tr>
<td>參數</td>
<td><li>loId：學習物件識別碼。</li><li>accountId：ALM 帳戶的帳戶 ID。</li><li>用戶ID：使用者ID。</li><li>accessToken：存取權杖。</li><li>domRefId：玩家必須被渲染的 div 容器的 ID。</li><li>onModuleLoaded：當載入包含以下細節的模組時，此函式會被呼叫。</li><br><li>內容類型</li><li>低音</li><li>moduleID</li><li>完工</li><li>當前語言</li><li>可用語言</li><li>isCCAvailable</li><li>ccEnabled</li></br></td>
</tr>
<tr>
<td>回歸</td>
<td>回報承諾。 當承諾被解決時，玩家會被通過。</td>
</tr>
<tr>
<td>例外</td>
<td>該承諾將導致例外。</td>
</tr>
<tr>
<td>範例程式碼</td>
<td>cpPlayerLib.startPlayer（loId， accountId， userId， accessToken， domRefId， onModuleLoaded）.then（（playerObj） =&gt; {//playerObj 擁有與玩家互動的 API}） &gt;</td>
</tr>
</tbody>
</table>

**getAllPlayers**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>getAllPlayers</td>
</tr>
<tr>
<td>說明</td>
<td>回傳目前頁面上的所有玩家物件。</td>
</tr>
<tr>
<td>參數</td>
<td>沒有</td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>cpPlayerLib.getAllPlayers（）</td>
</tr>
</tbody>
</table>

**getPlayer**


<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>getPlayer</td>
</tr>
<tr>
<td>說明</td>
<td>回傳一個玩家物件，並指定為學習物件 ID。</td>
</tr>
<tr>
<td>參數</td>
<td><li>loId：學習物件識別碼。</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>cpPlayerLib.getPlayer（loId）</td>
</tr>
</tbody>
</table>

**navigateToModule**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>navigateToModule</td>
</tr>
<tr>
<td>說明</td>
<td>切換到下一個模組。</td>
</tr>
<tr>
<td>參數</td>
<td><li>moduleId：模組 ID。</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.navigateToModule（moduleID）</td>
</tr>
</tbody>
</table>

**下一篇**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>下一篇</td>
</tr>
<tr>
<td>說明</td>
<td>切換到下一個模組。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.next（）</td>
</tr>
</tbody>
</table>

**先前**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>先前</td>
</tr>
<tr>
<td>說明</td>
<td>前往前一個模組。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.previous（）</td>
</tr>
</tbody>
</table>

**toggleTOC**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>toggleTOC</td>
</tr>
<tr>
<td>說明</td>
<td>切換播放器上的目錄面板。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.toggleTOC（）</td>
</tr>
</tbody>
</table>

**切換備註**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>切換備註</td>
</tr>
<tr>
<td>說明</td>
<td>切換播放器的筆記面板。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.toggleNotes（）</td>
</tr>
</tbody>
</table>

**切換關閉字幕**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>切換關閉字幕</td>
</tr>
<tr>
<td>說明</td>
<td>切換播放器的隱藏字幕顯示。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.toggleClosedCaption（）</td>
</tr>
</tbody>
</table>

**變化語言**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>變化語言</td>
</tr>
<tr>
<td>說明</td>
<td>更改播放器的內容語言。</td>
</tr>
<tr>
<td>參數</td>
<td><li>語言：待指定的語言代碼。</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.changeLanguage（“es”）</td>
</tr>
</tbody>
</table>

**近距離球員**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>近距離球員</td>
</tr>
<tr>
<td>說明</td>
<td>關閉播放器並將該播放器從頁面中移除。 </td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.closePlayer（）</td>
</tr>
</tbody>
</table>

**切換播放暫停**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>切換播放暫停</td>
</tr>
<tr>
<td>說明</td>
<td>在播放器上切換播放與暫停內容。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.togglePlayPause（）</td>
</tr>
</tbody>
</table>

**setVolume**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>setVolume</td>
</tr>
<tr>
<td>說明</td>
<td>設定播放器的音量。 數值必須介於0到1之間。</td>
</tr>
<tr>
<td>參數</td>
<td><li>體積：該體積的價值。 有效範圍是 0-1。 </li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.setVolume（0.5）</td>
</tr>
</tbody>
</table>

**set播放速度**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>set播放速度</td>
</tr>
<tr>
<td>說明</td>
<td>在播放器中設定播放速度。</td>
</tr>
<tr>
<td>參數</td>
<td><li>速度：指待指定的速度值。 有效數值為 .25、0.5、0.75、1、1.25、1.5、1.75、2。</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.setPlayBackSpeed（1.25）</td>
</tr>
</tbody>
</table>

**尋找**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>尋找</td>
</tr>
<tr>
<td>說明</td>
<td>跳到影片中的任何時間點。</td>
</tr>
<tr>
<td>參數</td>
<td><li>時間：跳躍的時機。 時間是秒數。</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.seek（50）</td>
</tr>
</tbody>
</table>

**前進**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>前進</td>
</tr>
<tr>
<td>說明</td>
<td>影片快轉10秒。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.前鋒（）</td>
</tr>
</tbody>
</table>

**倒退**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>倒退</td>
</tr>
<tr>
<td>說明</td>
<td>在影片中往後跳10秒。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.backward（）</td>
</tr>
</tbody>
</table>

**導航至頁面**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>導航至頁面</td>
</tr>
<tr>
<td>說明</td>
<td>跳到PPT/PDF指定的頁面。</td>
</tr>
<tr>
<td>參數</td>
<td><li>pageNumber：要跳轉到的頁碼。</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.navigateToPage （5）</td>
</tr>
</tbody>
</table>

**下一頁**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>下一頁</td>
</tr>
<tr>
<td>說明</td>
<td>跳到PPT/PDF的下一頁。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.nextPage（）</td>
</tr>
</tbody>
</table>

**前一頁**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>前一頁</td>
</tr>
<tr>
<td>說明</td>
<td>跳到PPT/PDF的上一頁。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.previousPage（）</td>
</tr>
</tbody>
</table>

**放大**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>放大</td>
</tr>
<tr>
<td>說明</td>
<td>放大PPT/PDF內容。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.zoomIn（）</td>
</tr>
</tbody>
</table>

**縮小**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>縮小</td>
</tr>
<tr>
<td>說明</td>
<td>在PPT/PDF上放大內容。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.zoomOut（）</td>
</tr>
</tbody>
</table>

**下載工作援助**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>下載工作援助</td>
</tr>
<tr>
<td>說明</td>
<td>從課程下載就業輔助工具。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.downloadJobAid（）</td>
</tr>
</tbody>
</table>

**toggleJobAidPullout**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>toggleJobAidPullout</td>
</tr>
<tr>
<td>說明</td>
<td>無論你是否想下載工作輔助工具。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.toggleJobAid Pullout（）</td>
</tr>
</tbody>
</table>

**全螢幕**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>全螢幕</td>
</tr>
<tr>
<td>說明</td>
<td>將玩家設定為全螢幕模式。</td>
</tr>
<tr>
<td>參數</td>
<td><li>沒有</li></td>
</tr>
</tr>
<tr>
<td>範例程式碼</td>
<td>playerObj.fullScreen（）</td>
</tr>
</tbody>
</table>

## 活動列表

**onPlayerEvents（回調）**

註冊時，所有玩家事件都會啟動回調函式。 活動名稱如下：

* 播放（影片/音訊/電腦）
* 暫停（影片/音訊/CP）
* TIMEUPDATE（影片/音訊/CP）
* 頁面變更（PPT/PDF）
* 備註新增（所有內容）
* 已啟動（所有內容）
* START（所有內容）
* 已完成（所有內容）
* 已通過（所有內容）
* 失敗（所有內容）

**onStreamingEvents（回撥）**

註冊時，所有用於追蹤用戶活動的玩家語句都會啟動回調功能。
