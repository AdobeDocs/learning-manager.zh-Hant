---
jcr-language: en_us
title: 內嵌式播放器互動API檔案
description: 瞭解各種API，用於監聽內嵌播放器中的事件及觸發動作
contentowner: chandrum
exl-id: 4734ecc1-cc8a-40b0-8997-32a31ec661ec
source-git-commit: 3d183dc40e4d1962d25160b74d8cf6cfa26e3171
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 3%

---

# 內嵌式播放器互動API檔案

Adobe Learning Manager提供程式庫，可整合至應用程式。 此程式庫提供各種API，監聽內嵌播放器中的事件並觸發動作。

使用提供的API，您可以在播放器上播放、暫停及執行其他動作。

## 載入程式庫

資料庫可在此[位置](https://cpcontents.adobe.com/public/publiccdn/playerInteractionLib.min.js)使用。

若要載入程式庫，請遵循下列步驟：

1. 在消費者應用程式中載入js檔案。
2. 載入程式庫時，將會填入window.cpPlayerLib。

>[!NOTE]
>
>如果您未使用prod US，請根據您的環境設定params cpPlayerLib.env和cpPlayerLib.sourceOrigin。

預設值為：

* window.cpPlayerLib.env = [https://learningmanager.adobe.com/app/player](https://learningmanager.adobe.com/app/player)；
* window.cpPlayerLib.sourceOrigin = &quot;[https://cpcontents.adobe.com](https://cpcontents.adobe.com/)&quot;；

### 可用方法

cpPlayerLib程式庫包含下列函式：

**startPlayer**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>startPlayer</td>
</tr>
<tr>
<td>說明</td>
<td>在應用程式中載入播放器。</td>
</tr>
<tr>
<td>引數</td>
<td><li>loId ：學習物件ID。</li><li>accountId ：ALM帳戶的帳戶ID。</li><li>userId ：使用者ID。</li><li>accessToken ：存取權杖。</li><li>domRefId：必須轉譯播放器的div容器ID。</li><li>onModuleLoaded：載入具有下列詳細資訊的模組時，將會叫用此函式。</li><br><li>contenttype</li><li>loId</li><li>moduleId</li><li>已完成</li><li>currentlanguage</li><li>availablelanguages</li><li>isCCAvailable</li><li>已啟用</li></br></td>
</tr>
<tr>
<td>傳回</td>
<td>傳回Promise。 在Promise解析時，將會傳遞playerObj。</td>
</tr>
<tr>
<td>例外</td>
<td>Promise會產生例外狀況。</td>
</tr>
<tr>
<td>程式碼範例</td>
<td>cpPlayerLib.startPlayer(loId、accountId、userId、accessToken、domRefId、onModuleLoaded)。then((playerObj) =&gt; {//playerObj具有與播放器互動的api}) &gt;</td>
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
<td>傳回目前頁面上的所有播放器物件。</td>
</tr>
<tr>
<td>引數</td>
<td>無</td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>cpPlayerLib.getAllPlayers()</td>
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
<td>傳回具有指定學習物件ID的播放器物件。</td>
</tr>
<tr>
<td>引數</td>
<td><li>loId ：學習物件ID。</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>cpPlayerLib.getPlayer(loId)</td>
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
<td>導覽至下一個模組。</td>
</tr>
<tr>
<td>引數</td>
<td><li>moduleId：模組識別碼。</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.navigateToModule(moduleID)</td>
</tr>
</tbody>
</table>

**下一個**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>下一個</td>
</tr>
<tr>
<td>說明</td>
<td>導覽至下一個模組。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.next()</td>
</tr>
</tbody>
</table>

**上一個**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>上一個</td>
</tr>
<tr>
<td>說明</td>
<td>導覽至上一個模組。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.previous()</td>
</tr>
</tbody>
</table>

**toggleTOC**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>toggleToc</td>
</tr>
<tr>
<td>說明</td>
<td>切換播放器上的目錄面板。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.toggleTOC()</td>
</tr>
</tbody>
</table>

**toggleNotes**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>toggleNotes</td>
</tr>
<tr>
<td>說明</td>
<td>切換播放器上的附註面板。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.toggleNotes()</td>
</tr>
</tbody>
</table>

**toggleClosedCaption**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>toggleClosedCaption</td>
</tr>
<tr>
<td>說明</td>
<td>切換隱藏式字幕在播放器上的顯示。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.toggleClosedCaption()</td>
</tr>
</tbody>
</table>

**changeLanguage**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>changeLanguage</td>
</tr>
<tr>
<td>說明</td>
<td>變更播放器上的內容語言。</td>
</tr>
<tr>
<td>引數</td>
<td><li>language：要指定的語言代碼。</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.changeLanguage("es")</td>
</tr>
</tbody>
</table>

**closePlayer**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>closePlay</td>
</tr>
<tr>
<td>說明</td>
<td>關閉播放器，並從頁面中移除播放器。 </td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.closePlayer()</td>
</tr>
</tbody>
</table>

**togglePlayPause**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>togglePlayPause</td>
</tr>
<tr>
<td>說明</td>
<td>在播放器上的播放和暫停內容之間切換。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.togglePlayPause()</td>
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
<td>設定播放器的音量。 值必須介於0到1之間。</td>
</tr>
<tr>
<td>引數</td>
<td><li>volume：磁碟區的值。 有效範圍為0至1。 </li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.setVolume(0.5)</td>
</tr>
</tbody>
</table>

**setPlayBackSpeed**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>setPlayBackSpeed</td>
</tr>
<tr>
<td>說明</td>
<td>設定播放器中的播放速度。</td>
</tr>
<tr>
<td>引數</td>
<td><li>speed：要指定的速度值。 有效值為。25、.5、.75、1、1.25、1.5、1.75、2。</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.setPlayBackSpeed(1.25)</td>
</tr>
</tbody>
</table>

**搜尋**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>搜尋</td>
</tr>
<tr>
<td>說明</td>
<td>跳至視訊上的任何時間。</td>
</tr>
<tr>
<td>引數</td>
<td><li>時間：跳至的時間。 時間以秒為單位。</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.seek(50)</td>
</tr>
</tbody>
</table>

**轉寄**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>轉寄</td>
</tr>
<tr>
<td>說明</td>
<td>在視訊中往前跳10秒。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.forward()</td>
</tr>
</tbody>
</table>

**向後**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>後退</td>
</tr>
<tr>
<td>說明</td>
<td>在視訊中向後跳轉10秒。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.backward()</td>
</tr>
</tbody>
</table>

**navigateToPage**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>navigateToPage</td>
</tr>
<tr>
<td>說明</td>
<td>跳至PPT/PDF上的指定頁面。</td>
</tr>
<tr>
<td>引數</td>
<td><li>pageNumber：要跳轉到的頁碼。</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.navigateToPage (5)</td>
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
<td>跳至PPT/PDF上的下一頁。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.nextPage()</td>
</tr>
</tbody>
</table>

**previousPage**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>上一頁</td>
</tr>
<tr>
<td>說明</td>
<td>跳至PPT/PDF的上一頁。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.previousPage()</td>
</tr>
</tbody>
</table>

**zoomIn**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>zoomIn</td>
</tr>
<tr>
<td>說明</td>
<td>放大PPT/PDF上的內容。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.zoomIn()</td>
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
<td>縮小PPT/PDF上的內容。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.zoomOut()</td>
</tr>
</tbody>
</table>

**下載工作輔助**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>downloadJobAid</td>
</tr>
<tr>
<td>說明</td>
<td>從課程下載工作輔助。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.downloadJobAid()</td>
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
<td>您是否要下載工作輔助。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.toggleJobAidPullout()</td>
</tr>
</tbody>
</table>

**全熒幕**

<table>
<tbody>
<tr>
<td>方法名稱</td>
<td>全熒幕</td>
</tr>
<tr>
<td>說明</td>
<td>將播放器設為全熒幕模式。</td>
</tr>
<tr>
<td>引數</td>
<td><li>無</li></td>
</tr>
</tr>
<tr>
<td>程式碼範例</td>
<td>playerObj.fullScreen()</td>
</tr>
</tbody>
</table>

## 事件清單

**onPlayerEvents(callBack)**

註冊時，將會在所有播放器事件上叫用回呼函式。 事件名稱如下：

* 播放（視訊/音訊/CP）
* 暫停（視訊/音訊/CP）
* TIMEUPDATE （視訊/音訊/CP）
* 頁面變更(PPT/PDF)
* NOTEADDED （所有內容）
* 已啟動（所有內容）
* 已開始（所有內容）
* 已完成（所有內容）
* 通過（所有內容）
* 失敗（所有內容）

**onStreamingEvents(callBack)**

註冊時，將會在為了追蹤使用者活動而傳送的所有播放器陳述式上叫用回呼函式。
