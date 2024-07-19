---
jcr-language: en_us
title: 解譯學習者成績單CSV
description: 解譯學習者成績單CSV
contentowner: saghosh
preview: true
source-git-commit: fba5e5ddc1964b485be473bf356806f234688cf4
workflow-type: tm+mt
source-wordcount: '2997'
ht-degree: 0%

---



# 解譯學習者成績單CSV

學習者成績單是Adobe Learning Manager中最常用的報告之一。 該報告可讓您以CSV格式在單一報告中取得幾乎每個可能的詳細資訊。

除了作為使用者可擷取以追蹤和分析學習行為的報告之外，該報告也可視為一種格式，在其中可設定Learning Manager將學習行為的相關資料匯出至外部應用程式/系統。

典型的企業情境是定期匯出Learning Manager的學習者成績單，加以分析以擷取完成重要學習計畫的學習者，並下訂單購買禮品憑單以辨識及獎勵及時完成。

另一個使用案例是將學習行為資料新增到企業資料倉儲，其中使用者可能想要將學習資料與其他企業資料結合，以分析學習行為與其他流程資料之間的關聯。

在檔案的其餘部分，我們會簡單說明如何從Learning Manager擷取學習者成績單；然後繼續提供報告每一列和每一欄需要如何解譯的詳細資訊。

對於任何打算透過處理匯出的學習者成績單資料的方式將Learning Manager與其他系統整合的開發人員而言，此資訊可能會很有用。

## 從使用者介面擷取學習者成績單 {#fetchlearnertranscriptfromtheuserinterface}

學習者可從「設定檔設定」下載其成績單。 如需詳細資訊，請參***[下載學習者成績單](../../administrators/feature-summary/learner-transcripts.md)***。

管理員可以產生整個組織的學習者成績單、一組特定使用者或一組特定學習物件，或一組特定使用者和學習物件。 他們還可以取得一段時間間隔內的所有學習記錄，並指出是否需要模組層級資訊（預設會省略模組層級資訊）。 如需詳細資訊，請參閱&#x200B;[***下載學習者成績單***](../../administrators/feature-summary/learner-transcripts.md)。

<!--Update above link?-->

管理員也可以設定系統以定期透過電子郵件傳送學習者成績單。

透過UI產生的學習者成績單將是一個Excel檔案，其中也包含「技能成績單」。 在本檔案中，我們將參照以CSV格式產生的內容，其中包含與註冊、開始、進度或完成學習物件相關的學習活動。

## 匯出學習者成績單 {#exportlearnertranscript}

當學習者成績單必須由外部系統使用時，Learning Manager會提供稱為匯出資料的功能，其中學習者成績單是可匯出的資料型別之一。 如序言中所述，將Learning Manager與需要處理學習行為資料的外部系統整合，或向Enterprise Data Warehouse填入學習行為資料時，需要用到此屬性。

如需支援匯出學習者成績單的聯結器方式的詳細資訊，請參閱FTP、Box和PowerBI聯結器中的[匯出資料區段](/help/migrated/integration-admin/feature-summary/connectors.md)。

這些聯結器提供的目的是定期（N天一次）將資料匯出至下游應用程式。 因此，這些聯結器只會在每次執行中匯出增量學習行為資料。 請注意，這些聯結器不允許擷取使用者或學習物件特定子集的記錄，此記錄一律是該帳戶中所有使用者和所有學習物件的相關資料。

至於PowerBI，客戶應提供工作區，讓Learning Manager可繼續將此資料逐步匯出至動態建立的資料集中。 此聯結器只會匯出資料，客戶必須視需要根據此資料集建立自己的報告/控制面板。

下一節會詳細說明下游系統應如何解譯學習者成績單中的記錄。

## 解讀學習者成績單 {#interpretthelearnertranscript}

學習者成績單中的每一列都可視為一段特定時間內Learning Manager擷取的學習行為。 聯結器通常會匯出「增量資料」，因此列會代表上次執行聯結器與目前執行之間發生的學習活動。

當然，聯結器也可讓您隨選擷取學習者成績單，在這種情況下，使用者可以指定開始日期，而結束日期假設為現在。 通常，使用者一開始會執行此動作一次，然後設定聯結器以在特定時間匯出增量學習者成績單，每N天一次（預設值N，為1）。

現在，讓我們定義增量學習者成績單的涵義

在學習者成績單中，每一列代表特定活動，包含特定學習者和特定學習物件。 我們主要關心學習者對於學習物件的狀態 — **已註冊**、**已開始**、**進行中**&#x200B;和&#x200B;**已完成**。 因此，學習者成績單會擷取四個對應的日期。

現在有三種學習物件型別，其中Learning Manager會追蹤學習者進度，匯出的資料包含模組層級的進度資訊，這是學習者在Learning Manager中可體驗到的最細微內容單位。

* **課程** — 一或多個模組的組合
* **學習計畫** — 一或多個課程的組合
* **認證** — 一或多個課程的組合。

學習者成績單中的每一列可能都和特定使用者對模組、課程、學習計畫或認證的參與有關。 當使用者註冊學習計畫時，成績單將指出使用者是

「學習者成績單」欄提供與每個學習活動相關的各種資訊，下表說明每個欄的語意。

## 學習者成績單

<table> 
 <tbody> 
  <tr> 
   <th width="158" valign="bottom"><p><b>欄名稱</b></p></th> 
   <th width="160" valign="bottom"><p><b>值的型別</b></p></th> 
   <th width="306" valign="bottom"><p><b>說明</b></p></th> 
  </tr> 
  <tr> 
   <td><p><b>名稱</b></p></td> 
   <td><p>從不空白</p></td> 
   <td><p>學習者姓名</p></td> 
  </tr> 
  <tr> 
   <td><p><b>電子郵件</b></p></td> 
   <td><p>從不空白</p></td> 
   <td><p>學習者的電子郵件地址</p></td> 
  </tr> 
  <tr> 
   <td valign="bottom"><b>Adobe ID</b></td> 
   <td valign="bottom">可為空白</td> 
   <td valign="bottom">學習者的Adobe ID</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>使用者唯一ID</b></td> 
   <td height="19" width="283">可為空白</td> 
   <td height="19" width="728">學習者的使用者唯一ID。 此欄以帳戶層級是否啟用/停用的後端設定為基礎。</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>學習方案名稱</b></p></td> 
   <td valign="middle"><p>可為空白</p></td> 
   <td valign="middle">自動指派使用者的學習計畫名稱（若有）。</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>LP/認證/課程</b></p></td> 
   <td valign="middle"><p>從不空白</p></td> 
   <td valign="middle"><p>學習計畫、認證或課程的名稱</p></td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>型別</b></p></td> 
   <td valign="middle">從不空白</td> 
   <td valign="middle"><p>學習物件的型別，使用者已註冊。</p></td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>課程</b></p></td> 
   <td valign="middle"><p>可為空白</p></td> 
   <td valign="middle">使用者註冊的課程名稱。 當它空白時，該列表示認證或學習計畫。 </td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>學習對象唯一識別碼</b></td> 
   <td height="19" width="283">可為空白</td> 
   <td height="19" width="728">學習對象的物件唯一ID。 此欄是根據帳戶層級是否啟用/停用的設定</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>例項  </b></p></td> 
   <td valign="middle">從不空白</td> 
   <td valign="middle">已註冊的LO使用者執行個體名稱。 </td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>選取條件</b></p></td> 
   <td valign="middle"><p>從不空白</p></td> 
   <td valign="middle"><p>註冊基礎（此學習者如何註冊此學習對象）。</p></td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>模組</b></p></td> 
   <td valign="middle"><p>可為空白</p></td> 
   <td valign="middle">課程內的模組名稱。 如果留空，此列代表課程、學習計畫或認證。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>版本</b></td> 
   <td height="19" width="283">可為空白</td> 
   <td height="19" width="728">模組版本</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>傳遞型別</b></td> 
   <td height="19" width="283">可為空白</td> 
   <td height="19" width="728">模組的傳遞型別 — 電子學習、F2F、VC、活動。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>語言</b></td> 
   <td height="19" width="283">可為空白</td> 
   <td height="19" width="728">學習者使用模組所用的語言。 此欄僅顯示電子學習模組的值。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>註解</b></td> 
   <td height="19" width="283">可為空白</td> 
   <td height="19" width="728">管理員（學習者的講師）在標示使用者出席時為其新增註解。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>註冊日期（亞洲/加爾各答時區）</b></td> 
   <td height="19" width="283">從不空白</td> 
   <td height="19" width="728">學習者註冊學習對象型別的日期。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>開始日期（亞洲/加爾各答時區）</b></td> 
   <td><p>可為空白</p></td> 
   <td height="19" width="728">學習者開始學習課程的日期。 空白表示學習者尚未開始此專案。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>完成日期（亞洲/加爾各答時區）</b></td> 
   <td><p>可為空白</p></td> 
   <td><p>學習者完成此作業的日期。 空白表示學習者尚未完成此作業。</p></td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>截止日期（亞洲/加爾各答時區）</b></td> 
   <td><p>可為空白</p></td> 
   <td height="19" width="728">學習者預計完成此學習課程的日期。 空白表示此專案沒有期限。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>過期</b></td> 
   <td height="19" width="283">是/否</td> 
   <td height="19" width="728">已註冊學習課程的學習者目前逾期狀態。 是/否</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>狀態</b></p></td> 
   <td valign="middle">未開始/完成/進行中/未註冊</td> 
   <td valign="middle">學習者註冊到學習對象的最新進度百分比。</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>進度%</b></p></td> 
   <td valign="middle">可為空白</td> 
   <td valign="middle"><p>表示學習者完成此作業的範圍。</p></td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>逗留時間（分鐘）</b></td> 
   <td height="38" width="283">可為空白</td> 
   <td height="38" width="728">學習者在LO中所花費的學習時間，模組層級列會顯示個別模組Wise學習時間。 課程/方案/憑證層級列會顯示彙總的學習時間。</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>等級</b></p></td> 
   <td valign="middle">通過/失敗</td> 
   <td valign="middle">表示學習者成功。 「通過」，如果使用者符合此專案的成功標準，則設為「失敗」。</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>測驗分數</b></p></td> 
   <td valign="middle">可為空白</td> 
   <td valign="middle">學習者取得的最新測驗分數。 如果學習者未嘗試測驗或內容中沒有任何測驗或管理員/講師未指派任何分數，則此區段可為空白。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>測驗_分數_最大值</b></td> 
   <td height="38" width="283">可為空白</td> 
   <td height="38" width="728">此模組可取得的最新最高測驗分數。 如果學習者未嘗試該測驗或內容不含任何測驗，則該測驗可為空白。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>最高_測試_分數</b></td> 
   <td height="38" width="283">可為空白</td> 
   <td height="38" width="728">學習者嘗試多次後獲得的最高測驗分數。 如果學習者未嘗試測驗或內容中沒有任何測驗或管理員/講師未指派任何分數，則此區段可為空白。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>最高_測試_分數_最大值</b></td> 
   <td height="38" width="283">可為空白</td> 
   <td height="38" width="728">模組的最高測驗分數。 如果學習者未嘗試該測驗或內容不含任何測驗，則該測驗可為空白。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>嘗試次數</b></td> 
   <td height="19" width="283">可為空白</td> 
   <td height="19" width="728">學習者到目前為止針對此模組嘗試的總次數。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>允許嘗試次數上限</b></td> 
   <td height="19" width="283">可為空白</td> 
   <td height="19" width="728">學習者嘗試使用模組的最大次數。</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>userState</b></p></td> 
   <td valign="middle">從不空白</td> 
   <td valign="middle">學習者的使用者狀態：作用中/已刪除/已暫停。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>可分組活動欄位</b></td> 
   <td height="38" width="283">可為空白</td> 
   <td height="38" width="728">對於帳戶中的每個可分組作用中欄位，都會有一個欄，其中欄名稱是作用中欄位的名稱，值將是學習者對該欄位的特定值。</td> 
  </tr> 
  <tr> 
   <td><p><b>管理員名稱</b></p></td> 
   <td><p><i>可為空白</i></p></td> 
   <td height="19" width="728">學習者的經理名稱</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>註冊計數</b></td> 
   <td height="38" width="283">1或0</td> 
   <td height="38" width="728">學習者的學習對象註冊計數。 最高層級的LO列會顯示值= '1'。 小數部分會顯示值0。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>開始計數</b></td> 
   <td height="19" width="283">1或0</td> 
   <td height="19" width="728">已開始計算學習者的學習對象數。 最高層級的LO列會顯示值= '1'。 小數部分會顯示值0。</td> 
  </tr> 
  <tr> 
   <td height="58" width="283"><b>完成計數</b></td> 
   <td height="58" width="283">1或0</td> 
   <td height="58" width="728">學習者的學習對象完成計數。 如果學習者在該訓練中擱置完成，則最高層級學習對象資料列會顯示值= '1'。 即使處於「擱置中」狀態，訓練仍會顯示0值。 如果學習者已完成訓練，最高層級學習對象資料列會顯示值= '0'。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>N天后截止</b></td> 
   <td height="38" width="283">1或0</td> 
   <td height="38" width="728">這會根據培訓學習者註冊的執行個體截止日期，顯示「1」或「0」的值。 這取決於在學習摘要I表&gt;「到期日即將到來」欄位中輸入的值。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>使用者N天后截止</b></td> 
   <td height="38" width="283">1或0</td> 
   <td height="38" width="728">這會根據培訓學習者註冊的執行個體截止日期，顯示「1」或「0」的值。 這取決於在學習摘要II工作表&gt; 「到期日即將到來」欄位中輸入的值。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>計數（進度大於N %）</b></td> 
   <td height="38" width="283">1或0</td> 
   <td height="38" width="728">這會根據學習者在訓練中的進度顯示「1」或「0」的值。 這取決於在「學習摘要I」工作表&gt;「進度大於」欄位中輸入的值。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>使用者的計數（進度大於N %）</b></td> 
   <td height="38" width="283">1或0</td> 
   <td height="38" width="728">這會根據學習者在訓練中的進度顯示「1」或「0」的值。 這取決於在學習摘要II工作表&gt; 「進度大於」欄位中輸入的值。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283">T<b>下雨ID</b></td> 
   <td height="19" width="283">從不空白</td> 
   <td height="19" width="728">培訓的培訓ID。</td> 
  </tr> 
  <tr> 
   <td height="20" width="283"><b>訓練或模組持續時間（分鐘）</b></td> 
   <td height="20" width="283">從不空白</td> 
   <td height="20" width="728">訓練預設執行個體的訓練總計或模組持續時間（分鐘）。</td> 
  </tr> 
 </tbody> 
</table>

### 學習摘要I

<table cellpadding="1" cellspacing="0" border="1"> 
 <tbody> 
  <tr> 
   <th>欄名稱<br></th> 
   <th>值的型別</th> 
   <th>說明</th> 
  </tr> 
  <tr> 
   <td height="19" width="264">型別</td> 
   <td height="19" width="253">全部，學習計畫，證書，課程。</td> 
   <td height="19" width="412">學習摘要表格應顯示其資料的LO型別。</td> 
  </tr> 
  <tr> 
   <td height="19" width="264">可分組欄位（設定檔）</td> 
   <td height="19" width="253">從不空白</td> 
   <td height="19" width="412">學習摘要表格應顯示其資料的設定檔。</td> 
  </tr> 
  <tr> 
   <td height="38" width="264">管理員名稱</td> 
   <td height="38" width="253">從不空白</td> 
   <td height="38" width="412">經理名稱，其下屬的LO engangement資料將顯示在「學習摘要」表格中。</td> 
  </tr> 
  <tr> 
   <td height="19" width="264">列標籤</td> 
   <td height="19" width="253">從不空白</td> 
   <td height="19" width="412">具有已註冊學習者的學習者清單的學習者名稱。</td> 
  </tr> 
  <tr> 
   <td height="19" width="264">已註冊的學習者數</td> 
   <td height="19" width="253">從不空白</td> 
   <td height="19" width="412">註冊學習者的數量。</td> 
  </tr> 
  <tr> 
   <td height="19" width="264">已開始的學習者數</td> 
   <td height="19" width="253">從不空白</td> 
   <td height="19" width="412">已開始學習課程的學習者數。</td> 
  </tr> 
  <tr> 
   <td height="19" width="264">已完成的學習者數</td> 
   <td height="19" width="253">從不空白</td> 
   <td height="19" width="412">已完成學習者名單的學習者人數。</td> 
  </tr> 
  <tr> 
   <td height="38" width="264">進度&gt;= N %的學習者數</td> 
   <td height="38" width="253">從不空白</td> 
   <td height="38" width="412">進度&gt;= N %的學習者數（值）。</td> 
  </tr> 
  <tr> 
   <td height="39" width="264">到期日期在N天的學習者數</td> 
   <td height="39" width="253">從不空白</td> 
   <td height="39" width="412">到期日期為N天（值）的學習者數。</td> 
  </tr> 
 </tbody> 
</table>

### 學習摘要II

| 欄名稱 | 值的型別 | 說明 |
|---|---|---|
| 型別 | 全部，學習計畫，證書，課程。 | 學習摘要表格應顯示其資料的LO型別。 |
| 可分組欄位（設定檔） | 從不空白 | 學習摘要表格應顯示其資料的設定檔。 |
| 管理員名稱 | 從不空白 | 經理名稱，其下屬的LO engangement資料將顯示在「學習摘要」表格中。 |
| 列標籤 | 從不空白 | 具有學習者清單的學習者名稱已註冊。 |
| 已註冊的學習物件數 | 從不空白 | 學習者註冊的學習物件數。 |
| 已開始的學習物件數 | 從不空白 | 學習物件學習者已開始的數量。 |
| 完成的學習物件數 | 從不空白 | 學習物件學習者完成的數目。 |
| 進度>= N %的學習物件數目 | 從不空白 | 學習者物件數（學習者進度>= N %）。 |
| 到期日期在N天后的學習物件數 | 從不空白 | 到期日期在N天后的學習物件數。 |

### 合規性摘要

| 欄名稱 | 值的型別 | 說明 |
|---|---|---|
| 型別 | 全部，學習計畫，證書，課程。 | 學習摘要表格應顯示其資料的LO型別。 |
| 列標籤（左側欄） | 從不空白 | 具有學習者清單的學習者名稱已註冊。 |
| 列標籤（左側欄） | 從不空白 | 具有學習者清單的學習者名稱已註冊。 |

### 技能成績單

| .Column名稱 | 值的型別 | 說明 |
|---|---|---|
| 名稱 | 從不空白 | 學習者姓名 |
| 電子郵件 | 從不空白 | 學習者的電子郵件地址 |
| Adobe ID | 可為空白 | 學習者的Adobe ID |
| 使用者唯一ID | 可為空白 | 學習者的使用者唯一ID。 此欄以帳戶層級是否啟用/停用的後端設定為基礎。 |
| 技能 | 從不空白 | 已將技能名稱指派給學習者。 |
| 技能等級 | 從不空白 | 已指派技能層級給學習者。 |
| 需要積分 | 從不空白 | 學習者獲得技能所需的總積分。 |
| 已獲取的積分 | 從不空白 | 學習者技能獲得的積分總數。 |
| 完成百分比 | 從不空白 | 完成技能的進度百分比。 |
| 指定日期（UTC時區） | 從不空白 | 將技能指派給學習者的日期。 |
| 習得日期（UTC時區） | 從不空白 | 學習者習得技能。 |
| userState | 從不空白 | 學習者的使用者狀態：作用中/已刪除/已暫停。 |
| 可分組活動欄位 | 可為空白 | 對於帳戶中的每個可分組作用中欄位，都會有一個欄，其中欄名稱是作用中欄位的名稱，值將是學習者對該欄位的特定值。 |
| 管理員名稱 | 可為空白 | 經理學習者的名稱。 |

### 技能摘要I

| 欄名稱 | 值的型別 | 說明 |
|---|---|---|
| 晚於 | 從不空白 | 在輸入（值）需要重新整理的天數前已習得技能的學習者數。 |
| 名稱 | 所有或任何學習者名稱 | 已指派技能的學習者名稱。 |
| 管理員名稱 | 從不空白 | 經理名稱，其下屬技能範圍資料將顯示在「技能摘要」表格上。 |
| 列標籤 | 從不空白 | 具有已指派該技能的學習者清單的技能名稱。 |
| 應具備此技能的使用者人數 | 從不空白 | 指派給技能的學習者數。 |
| 已習得該技能的使用者人數 | 從不空白 | 已習得該技能的學習者數。 |
| 技能需要重新整理的學習者數 | 從不空白 | 技能需要重新整理的學習者數。 |
| 合規性百分比（根據已習得的技能） | 從不空白 | 已指派技能的進度百分比。 |

### 技能摘要II

| 欄名稱 | 值的型別 | 說明 |
|---|---|---|
| 晚於 | 從不空白 | 在輸入的（值）天數前已習得技能，且需要重新整理的學習者人數。 |
| 技能 | 所有或任何技能名稱 | 指派給學習者的技能名稱。 |
| 管理員名稱 | 從不空白 | 經理名稱，其下屬技能範圍資料將顯示在「技能摘要」表格上。 |
| 列標籤 | 從不空白 | 具有已指派技能清單的學習者名稱。 |
| 每位使用者應具備的技能數 | 從不空白 | 指派給學習者的技能數。 |
| 每位使用者擁有的技能數 | 從不空白 | 學習者習得的技能數。 |
| 需要重新整理的技能數 | 從不空白 | 技能需要重新整理的學習者數。 |
| 合規性百分比 | 從不空白 | 已指派技能的進度百分比。 |

* 有時管理員可能會在課程結束後很長時間手動標示學習物件的完成（尤其是教室課程）。 在這種情況下，如果「匯出資料」設定為每日匯出LT，則實際的完成日期可能已經過去，因此匯出在類別發生後很長時間內，永遠不會收到標示為完成的完成記錄。 偵測到這個專案時，請考慮從UI中的指定開始日期起匯出成績單（依需求），然後將其帶往下游應用程式以進行「延遲處理」。 在執行此操作時，您可能需要忽略已經處理的記錄。
* 模組的多次嘗試取決於是否為該學習對象啟用。 啟用後，您現在會在CSV列中看見與模組相關的專案，即是一次嘗試。 並非一天中的所有嘗試都會報告，因此您可能會看到嘗試總數增加一個以上。 同樣地，嘗試不一定能改善分數，在任何指定點上您只會得到最佳分數。
