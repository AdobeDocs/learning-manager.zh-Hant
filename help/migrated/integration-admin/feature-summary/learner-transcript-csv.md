---
jcr-language: en_us
title: 解讀學習者成績單 CSV
description: 解讀學習者成績單 CSV
contentowner: saghosh
preview: true
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '2996'
ht-degree: 0%
---


# 解讀學習者成績單 CSV

學習者成績單是 Adobe Learning Manager 中最受歡迎的報告之一。 該報告能將幾乎所有可能的細節集中於一份 CSV 格式的報告中。

除了作為使用者可取用以追蹤和分析學習行為的報告外，該報告也可視為學習管理工具的格式，用以將學習行為資料匯出至外部應用程式/系統。

典型的企業情境是定期匯出學習者成績單給學習管理工具，分析以擷取完成重要學習計畫的學習者，並訂購禮券以表彰及獎勵準時完成的學生。

另一個使用情境是將學習行為資料加入企業資料倉儲，屆時可能想將學習資料與其他企業資料結合，以分析學習行為與其他流程資料之間的關聯性。

在文件的其餘部分，我們簡要說明如何從Learning Manager取得學習者成績單;接著說明報告中每一列與每一欄需要如何解釋。

這些資訊對於任何打算透過處理匯出學習者成績單資料來整合 Learning Manager 與其他系統的開發者來說，可能非常有用。

## 從使用者介面取得學習者文字稿 {#fetchlearnertranscriptfromtheuserinterface}

從個人資料設定中，學習者可以下載他的成績單。 欲了解更多資訊，請參閱 ***[下載學習者成績單](/help/migrated/administrators/feature-summary/reports/learner-transcripts.md)。

管理員可以為整個組織、特定使用者組或特定學習物件，或特定使用者與學習物件產生學習者成績單。 他們也能取得一定時間區間內的所有學習紀錄，並指示是否需要模組層級資訊（預設情況下，模組層級資訊會省略）。 更多詳情請參閱 [***下載學習者成績單***](/help/migrated/administrators/feature-summary/reports/learner-transcripts.md)。

<!--Update above link?-->

管理員也可以設定系統定期寄送學習者成績單。

透過介面產生的學習者成績單將是一個 Excel 檔案，裡面同時包含「技能成績單」。 在本文件中，我們將提及以 CSV 格式產生的內容，該報告包含與學習物件註冊、開始、進度或完成相關的學習活動。

## 匯出學習者成績單 {#exportlearnertranscript}

當學習者成績單必須由外部系統使用時，學習管理員提供一個名為「匯出資料」的功能，其中學習者成績單是可匯出的資料類型之一。 如序言所述，這是將 Learning Manager 整合到需要處理學習行為資料的外部系統，或是將企業資料倉儲填入學習行為資料時所必須的。

關於支援匯出學習者成績單的連接器細節，請參閱 [FTP、Box 與 PowerBI 連接器中的匯出資料區](/help/migrated/integration-admin/feature-summary/connectors.md) 塊。

這些連接器的目的是定期（每 N 天一次）將資料匯出到下游應用程式。 因此，這些連接器每次執行只會匯出增量學習行為資料。 請注意，這些連接器不允許擷取特定使用者子集或學習物件的紀錄——資料總是關於該帳戶中所有使用者及所有學習物件的資料。

以 PowerBI 為例，客戶應該提供一個工作空間，讓 Learning Manager 能持續將資料逐步匯出成動態建立的資料集。 這個連接器僅用於匯出資料，客戶必須根據這些資料集自行建立報告或儀表板。

下一節將詳細說明下游系統應如何解讀學習者成績單中的紀錄。

## 解讀學習者成績單 {#interpretthelearnertranscript}

學習者成績單中的每一列，都可以視為在特定時間內被 Learning Manager 捕捉到的某種學習行為。 通常，連接器會匯出「增量資料」，因此列代表連接器最後一次執行與當前執行之間發生的學習活動。

當然，連接器也允許你隨時取得學習者成績單，在這種情況下使用者可以指定開始日期，結束日期則假設是現在。 通常一開始會做一次，然後設定連接器，在一天中某個特定時間匯出增量學習者成績單，每 N 天一次（N 的預設值為 1）。

現在讓我們來定義什麼是增量學習者成績單

在學習者成績單中，每一列代表涉及特定學習者和特定學習對象的活動。 我們主要關心的是學習者對學習對象的狀態—— **已註冊**、 **開始**、 **進行**&#x200B;中及 **完成**。 因此，學習者成績單同時包含四個對應的日期。

目前有三種學習物件類型，學習管理員追蹤學習者的進度;匯出的資料包含模組層級的進度資訊，這是學習者在學習管理工具中能體驗到的最細緻內容單元。

* **課程** - 由一個或多個模組組成
* **學習課程** ——由一門或多門課程組成
* **認證** ——由一門或多門課程組成。

學習者成績單的每一行都可能與特定使用者參與模組、課程、學習計畫或認證相關。 當使用者註冊學習計畫時，成績單會顯示該使用者為

學習者逐字稿的欄位提供與各學習活動相關的各種資訊，以下表格說明每欄的語意。

## 學習者成績單

<table> 
 <tbody> 
  <tr> 
   <th width="158" valign="bottom"><p><b>欄名</b></p></th> 
   <th width="160" valign="bottom"><p><b>價值類型</b></p></th> 
   <th width="306" valign="bottom"><p><b>說明</b></p></th> 
  </tr> 
  <tr> 
   <td><p><b>名稱</b></p></td> 
   <td><p>永遠不會空</p></td> 
   <td><p>學習者姓名</p></td> 
  </tr> 
  <tr> 
   <td><p><b>電子郵件</b></p></td> 
   <td><p>永遠不會空</p></td> 
   <td><p>學習者的電子郵件地址</p></td> 
  </tr> 
  <tr> 
   <td valign="bottom"><b>Adobe ID</b></td> 
   <td valign="bottom">可以是空的</td> 
   <td valign="bottom">學習者的 Adobe ID</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>使用者唯一識別碼</b></td> 
   <td height="19" width="283">可以是空的</td> 
   <td height="19" width="728">學習者的使用者唯一ID。 本欄是根據後端設定，在帳號層級啟用或停用。</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>學習計畫名稱</b></p></td> 
   <td valign="middle"><p>可以是空的</p></td> 
   <td valign="middle">使用者被自動分配到的學習計畫名稱（如有）。</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>LP/認證/課程</b></p></td> 
   <td valign="middle"><p>永遠不會空</p></td> 
   <td valign="middle"><p>學習 pogram、認證或課程名稱</p></td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>類型</b></p></td> 
   <td valign="middle">永不空虛</td> 
   <td valign="middle"><p>使用者所註冊的學習對象類型。</p></td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>河道</b></p></td> 
   <td valign="middle"><p>可以是空的</p></td> 
   <td valign="middle">當然是註冊在哪個使用者的名稱。 當該列為空時，代表認證或學習計畫。 </td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>LO 唯一識別碼</b></td> 
   <td height="19" width="283">可以是空的</td> 
   <td height="19" width="728">學習對象的唯一 ID。 本欄是根據帳號層級啟用或停用的設定而定</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>執行個體  </b></p></td> 
   <td valign="middle">永不空虛</td> 
   <td valign="middle">LO 使用者所註冊實例的名稱。 </td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>納入標準</b></p></td> 
   <td valign="middle"><p>永遠不會空</p></td> 
   <td valign="middle"><p>註冊基礎（這位學員是怎麼被這個LO註冊的）。</p></td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>模組</b></p></td> 
   <td valign="middle"><p>可以是空的</p></td> 
   <td valign="middle">課程內的模組名稱。 當該列為空時，代表課程、學習計畫或認證。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>版本</b></td> 
   <td height="19" width="283">可以是空的</td> 
   <td height="19" width="728">模組版本</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>傳遞類型</b></td> 
   <td height="19" width="283">可以是空的</td> 
   <td height="19" width="728">課程內容類型 - 電子學習、面對面、虛擬學習、活動。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>語言</b></td> 
   <td height="19" width="283">可以是空的</td> 
   <td height="19" width="728">該模組由學習者所使用的語言。 本欄僅顯示電子學習模組的價值。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>留言</b></td> 
   <td height="19" width="283">可以是空的</td> 
   <td height="19" width="728">管理員、講師在記錄使用者出席時新增的留言。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>報名日期（亞洲/加爾各答時區）</b></td> 
   <td height="19" width="283">永不空虛</td> 
   <td height="19" width="728">學習者報名到LO類型的日期。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>開始日期（亞洲/加爾各答時區）</b></td> 
   <td><p>可以是空的</p></td> 
   <td height="19" width="728">學習者開始學習的日期。 空表示學習者尚未開始此步驟。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>完工日期（亞洲/加爾各答時區）</b></td> 
   <td><p>可以是空的</p></td> 
   <td><p>完成此項的學習者日期。 空表示學習者尚未完成此步驟。</p></td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>Deadline（亞洲/加爾各答時區）</b></td> 
   <td><p>可以是空的</p></td> 
   <td height="19" width="728">預計完成此 LO 的學習者日期。 空的意思是沒有截止日期。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>逾期</b></td> 
   <td height="19" width="283">是/不是</td> 
   <td height="19" width="728">已登記於 LO 的學習者目前逾期狀態。 是/不是</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>現況</b></p></td> 
   <td valign="middle">未開始/完成/進行中/未註冊</td> 
   <td valign="middle">目前學習者註冊的進度百分比。</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>進步百分比</b></p></td> 
   <td valign="middle">可以是空的</td> 
   <td valign="middle"><p>表示學習者完成此項工作的程度。</p></td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>花費時間（分鐘）</b></td> 
   <td height="38" width="283">可以是空的</td> 
   <td height="38" width="728">學習者在 LO 中所花費的學習時間，模組層級的列顯示每個模組的學習時間所花費。 課程/課程/證書等級的列顯示累積的學習時間。</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>等級</b></p></td> 
   <td valign="middle">通過/不及格</td> 
   <td valign="middle">表示學習者的成功。 「通過」，如果使用者符合成功標準，則「失敗」。</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>測驗分數</b></p></td> 
   <td valign="middle">可以是空的</td> 
   <td valign="middle">學習者獲得的最新測驗分數。 如果學習者沒嘗試測驗，或內容沒有測驗，或管理員/講師沒有給分數，可能會是空白。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>Quiz_score_max</b></td> 
   <td height="38" width="283">可以是空的</td> 
   <td height="38" width="728">該模組最新的最高測驗分數。 如果學習者沒嘗試過測驗，或內容中沒有測驗，可能會是空白。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>Highest_Quiz_score</b></td> 
   <td height="38" width="283">可以是空的</td> 
   <td height="38" width="728">學習者在多次嘗試中取得的最高測驗分數。 如果學員沒嘗試測驗，或內容沒有測驗，或管理員/講師沒有給分，可能會是空白。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>Highest_Quiz_score_max</b></td> 
   <td height="38" width="283">可以是空的</td> 
   <td height="38" width="728">該模組的最高測驗分數。 如果學習者沒嘗試過測驗，或內容中沒有測驗，可能會是空白。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>嘗試</b></td> 
   <td height="19" width="283">可以是空的</td> 
   <td height="19" width="728">目前學習者在本模組的總嘗試次數。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>最大允許嘗試次數</b></td> 
   <td height="19" width="283">可以是空的</td> 
   <td height="19" width="728">學習者可使用模組的最大嘗試次數。</td> 
  </tr> 
  <tr> 
   <td valign="middle"><p><b>使用者狀態</b></p></td> 
   <td valign="middle">永不空虛</td> 
   <td valign="middle">學習者的使用者狀態：活躍/已刪除/暫停。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>可分組的主動場</b></td> 
   <td height="38" width="283">可以是空的</td> 
   <td height="38" width="728">對於帳戶中每個可分組的活動欄位，都會有一欄，欄位名稱為活動欄位，值則為學習者對該欄位的具體值。</td> 
  </tr> 
  <tr> 
   <td><p><b>經理人姓名</b></p></td> 
   <td><p><i>可以是空的</i></p></td> 
   <td height="19" width="728">學習者經理姓名</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>招生人數</b></td> 
   <td height="38" width="283">1 或 0</td> 
   <td height="38" width="728">學習者的註冊人數。 最高層級的 LO 列顯示值 = '1'。 子訓練顯示的值為 0。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283"><b>先發計數</b></td> 
   <td height="19" width="283">1 或 0</td> 
   <td height="19" width="728">開始為LO點名學習者。 最高層級的 LO 列顯示值 = '1'。 子訓練顯示的值為 0。</td> 
  </tr> 
  <tr> 
   <td height="58" width="283"><b>完成次數</b></td> 
   <td height="58" width="283">1 或 0</td> 
   <td height="58" width="728">學習者完成的總數。 如果學習者在該訓練中尚未完成，最高層級的LO列會顯示值=「1」。 即使處於待處理狀態，子訓練仍顯示0值。 最高層級的 LO 列顯示值 = '0'，若學習者已完成訓練。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>預產期還有N天</b></td> 
   <td height="38" width="283">1 或 0</td> 
   <td height="38" width="728">根據訓練學習者註冊的實例截止日期，會顯示「1」或「0」的值。 這取決於學習摘要I表&gt;「截止日期即將到來」欄位中輸入的數值。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>用戶需在 N 天內繳交</b></td> 
   <td height="38" width="283">1 或 0</td> 
   <td height="38" width="728">根據訓練學習者註冊的實例截止日期，會顯示「1」或「0」的值。 這取決於Learning Sumary II表格&gt;「截止日期即將到來」欄位中輸入的金額。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>（進展大於N）的數量</b></td> 
   <td height="38" width="283">1 或 0</td> 
   <td height="38" width="728">根據學習者在訓練中的進展，這個數值會顯示「1」或「0」。 這取決於學習摘要I表&gt;「進度大於」欄位輸入的數值。</td> 
  </tr> 
  <tr> 
   <td height="38" width="283"><b>使用者的（進度大於 N%）計數</b></td> 
   <td height="38" width="283">1 或 0</td> 
   <td height="38" width="728">根據學習者在訓練中的進展，這個數值會顯示「1」或「0」。 這取決於Learning Sumary II表格&gt;「進度大於」欄位中輸入的數值。</td> 
  </tr> 
  <tr> 
   <td height="19" width="283">T<b>雨 ID</b></td> 
   <td height="19" width="283">永不空虛</td> 
   <td height="19" width="728">訓練的訓練編號。</td> 
  </tr> 
  <tr> 
   <td height="20" width="283"><b>訓練或模組長度（分鐘）</b></td> 
   <td height="20" width="283">永不空虛</td> 
   <td height="20" width="728">預設訓練實例的總訓練或模組時長（分鐘）。</td> 
  </tr> 
 </tbody> 
</table>

### 學習摘要 I

<table cellpadding="1" cellspacing="0" border="1"> 
 <tbody> 
  <tr> 
   <th>柱名<br></th> 
   <th>價值類型</th> 
   <th>說明</th> 
  </tr> 
  <tr> 
   <td height="19" width="264">類型</td> 
   <td height="19" width="253">全部、學習計畫、證書、課程。</td> 
   <td height="19" width="412">學習摘要表應顯示資料的 LO 類型。</td> 
  </tr> 
  <tr> 
   <td height="19" width="264">可分組欄位（輪廓）</td> 
   <td height="19" width="253">永不空虛</td> 
   <td height="19" width="412">學習摘要表應顯示資料的輪廓。</td> 
  </tr> 
  <tr> 
   <td height="38" width="264">經理人姓名</td> 
   <td height="38" width="253">永不空虛</td> 
   <td height="38" width="412">管理者名稱，其下屬的 LO 群組資料將顯示在學習摘要表中。</td> 
  </tr> 
  <tr> 
   <td height="19" width="264">排標籤</td> 
   <td height="19" width="253">永不空虛</td> 
   <td height="19" width="412">LO的名字和已註冊的學習者名單一起。</td> 
  </tr> 
  <tr> 
   <td height="19" width="264">註冊學習人數</td> 
   <td height="19" width="253">永不空虛</td> 
   <td height="19" width="412">報名學習者人數。</td> 
  </tr> 
  <tr> 
   <td height="19" width="264">已開始學習的人數</td> 
   <td height="19" width="253">永不空虛</td> 
   <td height="19" width="412">已開始學習者人數。</td> 
  </tr> 
  <tr> 
   <td height="19" width="264">完成學員人數</td> 
   <td height="19" width="253">永不空虛</td> 
   <td height="19" width="412">完成 LO 的學習人數。</td> 
  </tr> 
  <tr> 
   <td height="38" width="264">進步學習人數 &gt;= N%</td> 
   <td height="38" width="253">永不空虛</td> 
   <td height="38" width="412">進步學習者人數 &gt;= N%（數值）。</td> 
  </tr> 
  <tr> 
   <td height="39" width="264">N天內截止日期的學習人數</td> 
   <td height="39" width="253">永不空虛</td> 
   <td height="39" width="412">N天內有繳交日期的學習者人數（數值）。</td> 
  </tr> 
 </tbody> 
</table>

### 學習摘要 II

| 柱名 | 價值類型 | 說明 |
|---|---|---|
| 類型 | 全部、學習計畫、證書、課程。 | 學習摘要表應顯示資料的 LO 類型。 |
| 可分組欄位（輪廓） | 永不空虛 | 學習摘要表應顯示資料的輪廓。 |
| 經理人姓名 | 永不空虛 | 管理者名稱，其下屬的 LO 群組資料將顯示在學習摘要表中。 |
| 排標籤 | 永不空虛 | 學習者名稱及學習者所註冊的 LO 名單。 |
| 註冊學習對象數量 | 永不空虛 | 學習者註冊的學習對象數量。 |
| 啟動學習對象數量 | 永不空虛 | 學習對象數量已開始。 |
| 完成的學習物件數量 | 永不空虛 | 學習者已完成的學習物件數量。 |
| 已進展的學習對象數量 >= N % | 永不空虛 | 學習者物件數量 學習者已進步 >= N %。 |
| 截止日期為 N 天的學習對象數量 | 永不空虛 | N天內截止日期的學習對象數量。 |

### 合規摘要

| 柱名 | 價值類型 | 說明 |
|---|---|---|
| 類型 | 全部、學習計畫、證書、課程。 | 學習摘要表應顯示資料的 LO 類型。 |
| 列標籤（左側欄） | 永不空虛 | 學習者名稱及學習者所註冊的 LO 名單。 |
| 列標籤（左側欄） | 永不空虛 | 學習者名稱及學習者所註冊的 LO 名單。 |

### 技能記錄

| .柱名 | 價值類型 | 說明 |
|---|---|---|
| 名稱 | 永不空虛 | 學習者姓名 |
| 電子郵件 | 永不空虛 | 學習者的電子郵件地址 |
| Adobe ID | 可以是空的 | 學習者的 Adobe ID |
| 使用者唯一識別碼 | 可以是空的 | 學習者的使用者唯一ID。 本欄是根據後端設定，在帳號層級啟用或停用。 |
| 技巧 | 永不空虛 | 為學習者分配技能名稱。 |
| 技術水準 | 永不空虛 | 為學習者分配技能等級。 |
| 所需學分 | 永不空虛 | 學習者達成此技能所需的總學分。 |
| 已獲得的學分 | 永不空虛 | 學習者為該技能所獲得的總積分。 |
| 完成率 | 永不空虛 | 達成該技能需使用進度百分比。 |
| 指定日期（UTC時區） | 永不空虛 | 技能分配給學習者的日期。 |
| 達成日期（UTC時區） | 永不空虛 | 學習者獲得該技能的日期。 |
| 使用者狀態 | 永不空虛 | 學習者的使用者狀態：活躍/已刪除/暫停。 |
| 可分組的主動場 | 可以是空的 | 對於帳戶中每個可分組的活動欄位，都會有一欄，欄位名稱為活動欄位，值則為學習者對該欄位的具體值。 |
| 經理人姓名 | 可以是空的 | 學員的經理姓名。 |

### 技能摘要 I

| 柱名 | 價值類型 | 說明 |
|---|---|---|
| 之後 | 永不空虛 | 在輸入（價值）前，完成該技能的學習者數量，需更新。 |
| 名稱 | 所有或任何學習者名稱 | 學習者的名字，並指派了一項技能。 |
| 經理人姓名 | 永不空虛 | 經理名稱，其下屬的技能培訓資料會顯示在技能摘要表上。 |
| 排標籤 | 永不空虛 | 技能名稱與分配到該技能的學習者名單。 |
| 應該具備此技能的使用者數量 | 永不空虛 | 分配到技能的學習人數。 |
| 已達成此技能的使用者數量 | 永不空虛 | 已達成此技能的學習者人數。 |
| 需要更新技能的學習者數量 | 永不空虛 | 需要更新技能的學習者數量。 |
| 合規率（依技能達成） | 永不空虛 | 分配技能的進度百分比。 |

### 技能總結 II

| 柱名 | 價值類型 | 說明 |
|---|---|---|
| 之後 | 永不空虛 | 在輸入（價值）天數前完成技能的學習人數，需要複習。 |
| 技巧 | 全部或任何技能名稱 | 分配給學習者的技能名稱。 |
| 經理人姓名 | 永不空虛 | 經理名稱，其下屬的技能培訓資料會顯示在技能摘要表上。 |
| 排標籤 | 永不空虛 | 學習者名稱與分配的技能清單。 |
| 每位使用者應擁有的技能數量 | 永不空虛 | 技能數量分配給學習者。 |
| 每位使用者擁有的技能數量 | 永不空虛 | 學習者所達成的技能數量。 |
| 需要刷新的技能數量 | 永不空虛 | 需要更新技能的學習者數量。 |
| 合規率 | 永不空虛 | 分配技能的進度百分比。 |

* 有時管理員會在課程結束後（尤其是教室課程）手動標記學習物件的完成。 在這種情況下，如果匯出資料設定為每日匯出LT，實際完成日期可能已經過了，匯出時就不會收到那些在課程結束很久後才標記為完成的完成紀錄。 當偵測到這種情況時，請考慮在介面中匯出從指定開始日期到日期（隨需）的逐字稿;然後帶到下游應用程式進行「延遲處理」。 在此過程中，你可能需要忽略已處理的紀錄。
* 模組的多次嘗試取決於該 LO 是否啟用了這個功能。 啟用後，你現在看到的 CSV 列中與模組相關的內容是一次嘗試。 一天內並非所有嘗試都會被報告，因此你可能會看到總嘗試次數增加超過一次。 而且嘗試不一定會提升分數，任何時候你只會拿到最高分。
