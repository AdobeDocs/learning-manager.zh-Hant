---
description: 本文件包含基本的故障排除建議，幫助你解決在將資料與內容從現有學習管理系統遷移到學習管理員時可能遇到的一些典型問題。
jcr-language: en_us
title: 遷移問題故障排除
contentowner: jayakarr
exl-id: b9f17644-f237-4701-86e9-8496db941920
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# 遷移問題故障排除

本文件包含基本的故障排除建議，幫助你解決在將資料與內容從現有學習管理系統遷移到學習管理員時可能遇到的一些典型問題。

## 通用遷移問題 {#genericmigrationissues}

### 無法登入 FTP 資料夾或內容資料夾 {#unabletologintoftpfolderorcontentfolder}

請確保您的帳號已在 FTP 和 Box 服務中建立。 當你建立遷移專案時，你會要求設定這兩個服務。 一旦你建立服務，就會收到 Exavault 和 Box 的電子郵件，要求你重設或設定密碼。 如果你不記得密碼，可以透過 Exavault 和 Box 網站重設密碼。

### 即使點擊刷新按鈕，職缺也不會被反映出來 {#jobsarenotreflectedevenafterclickingrefreshbutton}

* 請確保 CSV 檔案已上傳到 Exavault FTP 的正確資料夾。 路徑結構應如下：

`code Account>Project>Sprint location`

* 確保 CSV 檔案的檔名依照 CSV 規範名稱：

  * course.csv
  * course_instance.csv
  * course_module.csv
  * enrollment.csv
  * module.csv
  * module_version.csv
  * user_course_grade.csv

### 有錯誤紀錄的工作會顯示失敗 {#failuresareshownforjobswitherrorrecords}

1. 點擊 **「下載錯誤紀錄** 」連結下載錯誤日誌
1. 根據報告錯誤修正原始 CSV 檔，然後
1. 用修改過的 CSV 重新執行 Sprint。

最佳實務是在變更次數相較於總記錄數較少時，在新的衝刺中執行修改過的 CSV 檔。

### 即使停止 Sprint 遷移，仍無法登入 Learning Manager 應用程式 {#unabletologintocaptivateprimeapplicationevenafterstoppingthesprintmigration}

一旦停止或完成 Sprint 跑關，解鎖帳號可能需要 10-15 分鐘。 15分鐘後嘗試進入應用程式。

### 即使觸發「停止」，部分遷移工作仍顯示「進行中」狀態。 {#someofthemigrationjobsdisplayinprogressstatusevenafterstopistriggered}

一旦進入「進行中」狀態，可能需要 10 到 15 分鐘才能停止執行所有工作。 請在10分鐘後重新確認狀態。

### 因為按鈕被停用，無法建立衝刺 {#unabletocreateasprintasthebuttonisdisabled}

在建立衝刺前，請確保目前的 Sprint 已被標記為完成。 點擊 **[!UICONTROL Mark Sprint Complete]** 頁面頂端即可完成 Sprint 遷移。

### 無法將遷移專案標記為完成，因為按鈕被關閉 {#unabletomarkamigrationprojectascompleteasthebuttonisdisabled}

在標記遷移專案完成前，請確保目前的 Sprint 已標記為完成。 點擊 **[!UICONTROL Mark Sprint Complete]** 頁面頂端即可完成 Sprint 遷移。

## CSV 問題 {#csvissues}

### module_version.csv檔案遷移失敗，內容尚未遷移 {#moduleversioncsvfilemigrationisfailingandcontentisnotmigratedyet}

確保內容在 Content 資料夾中可用（Box 帳號在指定的遷移專案下，衝刺路徑下）。 另外，請確保你已選擇「是&#x200B;**」選項，該**&#x200B;選項「你會為此 Sprint 遷移內容嗎？」**。** 在 Sprint 建立頁面提出問題。

如果你忘了選擇 **「是**」並繼續這個衝刺，那你就得等完成這個衝刺。 建立另一個衝刺，並確保點擊 **[!UICONTROL Yes]**。

### enrollment.csv或user_course_grade.csv紀錄會因錯誤訊息「Not a valid Learning Manager ID」而失敗 {#enrollmentcsvorusercoursegradecsvrecordsfailwithanerrormessagenotavalidprimeid}

請確保 userID 所提供的電子郵件 ID，assignedByUserID 欄位屬於有效的 Learning Manager 使用者。 如果沒有，請新增該使用者，並建立一個新的衝刺並選擇 **同步使用者** 選項。 若使用者不屬於組織，請透過 Add users CSV 規格在 Learning Manager 中將該使用者新增為已刪除的使用者。 以下提供一份用於新增已刪除使用者的 CSV 範例規範供參考。

[Users.csv](assets/users.zip) 請參閱&#x200B;**遷移手冊[&#128279;](../integration-admin/feature-summary/migration-manual.md)中的 CSV 規格與範例 CSV** 章節，下載完整的 CSV 規格與範例 CSV 檔案。

### 課程顯示為空白或模組錯誤，為遷移的課程進行 {#coursesappearblankorincorrectmodulesplayforamigratedcourse}

確保&#x200B;**課程的 moduleOrderInCourse** 鍵值以 0 **開頭**&#x200B;且連續順序。以 courseModuleType 為單位的順序應該是 PRETEST、TESTOUT、CONTENT

另外，請確保活動、教室和虛擬課程的兩個版本沒有與現有課程連結。

### 收到訊息顯示「模組已與現有課程連結」 {#receivingamessageasmoduleisalreadylinkedwithanexistingcourse}

學習管理員不允許將活動/虛擬學習/教室模組連結到多門課程。 確保該模組不與其他課程有關聯。

### 所有課程都顯示活動/虛擬學習/教室模組的最新版本，儘管課程連結了不同模組版本 {#allthecoursesshowthelatestversionofactivityvcclassroommoduleseventhoughthecoursesarelinkedwithdifferentmoduleversions}

學習管理員不支援活動模組、教室模組及虛擬教室模組的版本管理。 如果你透過moduleVersion.csv檔案提供版本，它會更新現有檔案，而不是建立新的版本。

### 遷移後的活動/虛擬學習/教室模組不會出現期望時長 {#desireddurationdoesnotappearforamigratedactivityvcclassroommodule}

期望時長不適用於活動/虛擬學習/教室模組。

### 超連結網址在 Learning Manager 裡無法開啟 {#hyperlinkurldoesntopenupincaptivateprime}

請確保所提供的連結前綴為「http://」或「https://」。

### moduleVersion 遷移失敗，出現「檔案未找到」錯誤 {#moduleversionmigrationfailswithfilenotfounderrors}

確保該參考檔案存在於內容資料夾中，且成功遷移。

### moduleVersion 遷移失敗時會跳出錯誤訊息，表示「內部錯誤發生 - 針對模組 ： x 與 moduleVersion ： y」 {#moduleversionmigrationfailswithanerrormessageasaninternalerrorhasoccurredformodulexandmoduleversiony}

重新執行 Sprint 以解決問題。
