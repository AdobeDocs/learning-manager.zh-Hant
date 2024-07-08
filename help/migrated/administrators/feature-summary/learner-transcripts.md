---
description: 使用學習管理器下載學習者成績單和管理報告。
jcr-language: en_us
title: 學習者成績單
contentowner: jayakarr
exl-id: f88ad02c-6d36-41e7-9d83-0ebc70d98d63
source-git-commit: de57d96488851c31c380b34672767a803379842e
workflow-type: tm+mt
source-wordcount: '1824'
ht-degree: 0%

---

# 學習者成績單

使用學習管理器下載學習者成績單和管理報告。

Adobe Systems學習管理員使組織的管理員能夠生成與學習者關聯的成績單。

## 生成學習者成績單 {#generatelearnertranscripts}

1. 要生成學習者成績單，請按兩下 **[!UICONTROL Reports]** 管理員登入中的左側窗格。

   管理員&#x200B;**[!UICONTROL Custom Reports]**&#x200B;導航到頁面內的&#x200B;**[!UICONTROL Reports]**>**[!UICONTROL Excel Reports]**&#x200B;標籤。

1. 按兩下連結 **[!UICONTROL Learner Transcripts]**。

   **[!UICONTROL Learner Transcript]**&#x200B;歷史記錄頁面將顯示消息 - **尚未**&#x200B;生成學習者成績單或已觸發貼文學習成績單歷史記錄頁面 實施清單下載。

   <!--[](assets/learner-transcripts.png)-->

   此時將顯示「學習者成績單」對話框。 選擇需要為其生成成績單的日期範圍。

   >[!NOTE]
   >
   >默認情況下，開始起始日期是學習者的註冊日期，結束日期始終是當前日期。 您僅可修改自需要数据起的開始日期。

1. 從 **[!UICONTROL Select Learners]** 欄位選擇學習者姓名，然後按下 **[!UICONTROL Generate]。**
1. 您可以選擇單個學習者或學習者組。 要添加多個學習者，請按兩下 **[!UICONTROL Add More Learners]**。

   ![](assets/add-learners-lt.png)

   *添加更多學習者*

1. 您可以透過啟用該選項選擇特定目錄。 僅為指定的目錄下載文本。 您可以從下拉式清單選擇 **[!UICONTROL Select Catalogs]** 目錄，以選擇特定目錄。

   ![](assets/select-catalogs-lt.png)

1. 匯出學習者成績單時，有一個選項， **[!UICONTROL Enrollment Status]**. 這個下拉式清單包含下列選項：

   * 全選
   * 完成
   * 進行中
   * 未開始
   * 未註冊

   ![](assets/add-enrollment-status-lt.png)

   *選擇目錄*

1. 您還可以為已從帳戶中刪除的學習者下載成績單。

   要下載已刪除使用者的學習者成績單，請按兩下 **[!UICONTROL Advanced Options]** 箭頭，然後選中複選框 **[!UICONTROL Include data of Deleted Learners]**。

   ![](assets/data-deleted-learners.png)

   *下載已刪除學習者的學習者成績單*

1. 您可以通過啟用“**[!UICONTROL Enable module level information]**”複選框來選擇在學習者成績單中下載 模組級別資訊。 在這種情況下，如果啟用了此選項，則模組名稱和在每個模組上花費的時間將作為腳本的一部分進行提取。
1. 您可以選擇通過啟用選項“**[!UICONTROL Include skills data and summary sheets]**”複選框來下載技能數據和摘要表。

   當不包括技能數據時，成績單將生成並作為.zip檔下載到您的計算機。 如果啟用了「技能數據」複選框，則會生成成績單並將其下載到檔中.xls。

## 使用複製粘貼生成學習者成績單

獲取學習者成績單成為一個繁瑣的過程，因為它只能為學習者獲取或一次消費者群組一個。 在這裡，使用複製粘貼功能，您可以複製學習者電子郵件ID的清單並一次粘貼。

1. 以或&#x200B;**[!UICONTROL Manager]** ID登&#x200B;**[!UICONTROL Administrator]**&#x200B;入。
1. 轉到 **[!UICONTROL Reports]** 下面 **[!UICONTROL Manage]**，它會載入 **[!UICONTROL User Activity]** 頁面。
1. 按兩下 **[!UICONTROL Custom Reports]** 左窗格並從清單中選擇 **[!UICONTROL Learner Transcripts]** 。
1. 在 **[!UICONTROL Learner Transcripts]** 頁面上，按兩下 **[!UICONTROL Generate New]** 左上角的按鈕。
1. 按下 **[!UICONTROL Select date range]** 拉清單中，選擇首選日期。 按下標籤， **[!UICONTROL Email IDs]** 輸入唯一電子郵件 ID 的複製清單。

   ![](assets/cp-copy-paste-feature.png)

   *複製貼貼電子郵件ID*

1. 用來 **[!UICONTROL Validate Email Ids]** 驗證輸入的id是否正確。

   ![](assets/cp-learnertran-gdpr.png)

   *驗證電子郵件ID*

   如果輸入的電子郵件ID不正確，它將以紅色突出顯示，並帶有上述驗證消息。

   **[!UICONTROL Generate]** 除非輸入的所有電子郵件 ID 都正確，否則按鈕將不可用。

   ![](assets/cp-copy-paste-generate.png)

   *生成學習者成績單*

1. 按兩下 **[!UICONTROL Generate]** 按鈕為所有提到的電子郵件ID生成學習者成績單。 您將收到一條確認消息，說明報告生成。

   ![](assets/cp-copy-paste-gmessage.png)

   *正在生成的報表的確認消息*

   對於在兩者和&#x200B;**[!UICONTROL Email IDs]**&#x200B;標籤&#x200B;**[!UICONTROL Users]**&#x200B;下輸入的電子郵件 ID，可以合併生成學習者成績單。

## 學習者成績單下載的歷史 {#ltdownload}

在下載 頁面 **[!UICONTROL Learner Transcript]** 上，要生成報告，按兩下按鈕時 **[!UICONTROL Generate New]** ，將顯示“學習者成績單”對話框。

![](assets/history-lt.png)

*生成所有學習者成績單的報告*

按兩下 **[!UICONTROL Advanced Options]** 並展開面板。

選擇使用者及其所屬的目錄。 按兩下 **[!UICONTROL Generate]** 按鈕後，將顯示一個對話框，其中提及下載報表的大致時間。 要產生報表，請按兩下 **[!UICONTROL Generate]**。

![](assets/download-learnertranscripts.png)

*選擇“生成”按鈕*

腳本在後台生成，您可以在學習管理器中繼續執行任務。 生成腳本后，您可以從清單下載腳本。

作為管理員，您可以視圖系統中任何人生成的所有成績單。

![](assets/download-history.png)

*檢視下載歷史記錄*

下載 清單显示下列屬性：

* **學習者：** 要下載成績單的學習者/學習者組。
* **包含的其他數據：** 取決於管理員要從“添加學習者成績單”模式中的進階選項下載的其他數據
* **狀態：** 已下載、已佇列或進行中。
* **寄件者** 和 **收件者**：要下載的成績單的持續時間。
* **應用的篩選器：** 是否已對註冊狀態應用了篩選器。
* **生成者：** 請求下載的學習管理器用戶的用戶 ID。
* **狀態：** 已下載、已佇列或進行中。

您可以隨時取消下載。 如果管理員取消了作業，學習管理器會向觸發學習者成績單的用戶發送應用程式內通知。

![](assets/queued-status.png)

*學習者成績單下載 佇列*

您可以隨時 **取消** 下載。 如果作業被取消，學習管理器會向已取消作業的用戶發送應用內通知。

## 已刪除學習者的數據 {#dataofdeletedlearners}

您可以在學習者成績單清單中包含已刪除學習者的數據。 在「學習者成績單」對話框中，啟用選項 **[!UICONTROL Include data of Deleted Learners]**。

啟用該選項並按兩下 **[!UICONTROL Generate]**&#x200B;後，已刪除的學習者數據將在學習者成績單下載 頁面中顯示，如下所示：

![](assets/deleted-learnersondownloadpage.png)

*檢視已刪除的 learber 數據*

## 自定義欄 {#customize-columns-lt}

管理員可以自定義在學習者成績單報告中導出的列。 管理員、自定義管理員及管理員可在導出報表前設定欄。

在 **[!UICONTROL Learner Transcripts]** 對話框中，按兩下 **[!UICONTROL Advanced Options]**。 **[!UICONTROL Configure Export Format]**&#x200B;在該部分中，選擇要導出的列。

![](assets/image024.png)

*自訂要導出的欄*

僅當用戶在 中下載學習者成績單時，才允許自定義。CSV 格式。 在中下載時。XLSX 格式，將不接受列首選項選擇，並將匯出所有預設列。

## 學習者成績單文件內容 {#learnertranscriptfilecontent}

典型的學習者成績單檔由單個檔中的六個Excel工作表組成。 學習者成績單表提供了對數據的總體分析，包括每門課程涉及的學習者數量、他們的技能、基於課程或學習者的完成百分比以及合規性儀錶板。 以下是學習者成績單中可用的儀錶板：

**學習者成績單**

在學習者成績單 excel 表中，除了有關學習者設定檔詳細資訊外，還提供了學習物件明智的消費詳細資訊，例如註冊日期、開始日期、達到的成績、獲得的測驗分數。 如果課程是任何學習方案的一部分，則除了單個課程消耗詳細資訊外，它們將單獨列出。

**1-學習活動儀錶板**

在這個特定於 LO 的儀錶板中，您可以視圖每門課程、學習方案或認證的學習者數量。 您可以為特定學習對象的學習者視圖進度表。 此表顯示按讚已完成課程或學習方案的學習者人數、正在進行的學習者以及學習者的截止日期的數據。

特定課程的使用者進度是根據您在其中指定截止日期和進度百分比閾值的輸入字段計算的。 例如，如果您在輸入字段中指定 7 天和 70% 作為值，則會顯示 7 天后到期的課程以及進度超過 70% 的課程的課程進度。 您還可以更改此工作表中的時段，修改後的數據將自動顯示在此儀錶板中。

**2 - 學習活動控制面板**

此學習儀錶板顯示特定用戶的數據。 在此儀錶板中，您可以查看特定用戶已註冊的課程、學習計劃或認證。 該表還顯示有關用戶已完成的學習物件、正在進行的學習物件以及用戶即將到來的截止日期的數據。

每個課程的使用者進度是根據您指定的輸入計算的。 即截止日期和進度百分比值。 例如，如果將 7 天和 70% 指定為輸入欄位中的值，則會顯示 7 天后到期的不同課程以及進度超過 70% 的課程的用戶進度。

**技能**

在技能表中，提供了技能名稱、技能級別、所需學分、獲得的學分、完成百分比和其他設定檔詳細資訊。 下面提供了技能 Excel 工作表的示例快照以供參考。

![](assets/skills-learner-transcript.png)

*技能 Excel 工作表示例*

**1-技能儀錶板**

在此儀錶板中，您可以查看您的組織是否具備各種技能。 對於特定技能，您可以檢查組織中應具有此技能的用戶數與實際擁有該技能的用戶數。 此儀錶板還指定必須刷新其技能的使用者。 此值是根據您在輸入欄位中輸入的輸入計算的。 例如，如果輸入 50 天作為輸入，儀錶板將提供有關需要在 50 天后刷新其技能的用戶的數據。

**2-技能儀錶板**

此技能儀錶板更特定於用戶。 您可以篩選特定用戶或多個使用者，並將其技能水平視圖為儀錶板。 此表可以幫助經理和管理員跟蹤每個學習者的技能與預期技能的比較。 技能儀錶板還揭示了必須刷新技能的學習者。 學習者刷新清單是根據您在輸入字段中輸入的天數計算的。

**合規性儀錶板**

合規性儀錶板有兩個部分 - 每個用戶的合規性報告和每個培訓的合規性報告。 對於基於用戶的報表，可以使用合規性儀錶板跟蹤重要合規性計劃即將到期的使用者。 對於基於培訓的報表，可以按學習方案或認證進行篩選。

對於這兩種合規性報告，請按截止日期進行篩選，以視圖相應的數據。

### 文稿中的時間和日期列 {#datetime}

以下列中的值將分鐘四捨五入到最接近的分鐘，將秒捨入為 00：

* 註冊日期（UTC 時區）
* 開始日期 （UTC 時區）
* 完成日期 （UTC 時區）

![](assets/time-columns-in-thetranscript.png)

*Excel 工作表中的時間和日期列*

### 文本中的模組持續時間和ID列 {#moduledurationandidcolumnsinthetranscript}

學習者成績單還顯示列 **[!UICONTROL Module Duration]** 和 **[!UICONTROL ID]**。

![](assets/lt-id-duration.png)

*文本中的模組持續時間和ID列*

### 成績單中的其他列 {#ModuledurationandIDcolumnsinthetranscript-1}

| **列** | **描述** |
|---|---|
| 後 | 在輸入的（值）需要刷新的天數之前獲得技能的學習者人數 |
| 技能 | 分配給學習者的技能名稱 |
| 經理姓名 | 其下屬技能管理數據將顯示在技能匯總表上的經理名稱 |
| 行標籤 | 分配有技能清單的學習者姓名 |
| 每個用戶應具備的技能數量 | 分配給學習者的技能數量 |
| 每個用戶擁有的技能數量 | 學習者達到的技能數量 |
| 需要重新整理的技能數量 | 技能需要刷新的學習者人數 |
| 合規百分比 | 已分配技能的進度百分比 |
| 內嵌路徑 | 這些行將顯示嵌入式學習計劃的名稱。 |
| 內嵌路徑ID | 這些行將顯示嵌入式學習計劃的ID |
| 内嵌路徑語言 | 這些行將顯示創建學習計劃時使用的語言。 |
