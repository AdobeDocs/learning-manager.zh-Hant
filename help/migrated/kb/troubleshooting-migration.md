---
description: 本檔案包含基本疑難排解提示，可解決您在將資料和內容從現有LMS移轉至Learning Manager時可能遇到的一些典型問題。
jcr-language: en_us
title: 疑難排解移轉問題
contentowner: jayakarr
source-git-commit: 6abc118c6ad7e66e3ded5bd26b9167c3a0b99e4b
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 0%

---



# 疑難排解移轉問題

本檔案包含基本疑難排解提示，可解決您在將資料和內容從現有LMS移轉至Learning Manager時可能遇到的一些典型問題。

## 一般移轉問題 {#genericmigrationissues}

### 無法登入FTP資料夾或內容資料夾 {#unabletologintoftpfolderorcontentfolder}

確認已在FTP和Box服務中建立您的帳戶。 當您建立移轉專案時，會要求設定這兩個服務。 當您建立服務後，就會收到Exavault和Box的電子郵件，要求您重設或設定密碼。 如果您不記得密碼，可以造訪Exavault和Box網站來重設密碼。

### 即使按一下「重新整理」按鈕，工作也不會反映出來 {#jobsarenotreflectedevenafterclickingrefreshbutton}

* 請確定CSV檔案已上傳至Exavault FTP中的正確資料夾。 路徑結構應如下所示：

`code Account>Project>Sprint location`

* 請確定CSV檔案的檔案名稱與CSV規格名稱一致：

   * course.csv
   * course_instance.csv
   * course_module.csv
   * enrollment.csv
   * module.csv
   * module_version.csv
   * user_course_grade.csv

### 會顯示含有錯誤記錄之作業的失敗 {#failuresareshownforjobswitherrorrecords}

1. 按一下以下載錯誤記錄檔 **下載錯誤記錄** 連結
1. 根據報告的錯誤更正原始CSV，並且
1. 使用修改過的CSV重新執行Sprint。

最佳實務是在變更數少於記錄總數時，在新的Sprint中執行修改過的CSV。

### 即使在停止Sprint移轉後也無法登入Learning Manager應用程式 {#unabletologintocaptivateprimeapplicationevenafterstoppingthesprintmigration}

一旦Sprint執行停止或完成，解鎖帳戶可能需要10至15分鐘。 15分鐘後嘗試存取應用程式。

### 即使觸發「停止」，部分移轉工作仍會顯示「進行中」狀態。 {#someofthemigrationjobsdisplayinprogressstatusevenafterstopistriggered}

當工作處於「進行中」狀態時，可能需要10-15分鐘才能停止執行所有工作。 請在10分鐘後重新檢查狀態。

### 無法建立Sprint，因為按鈕已停用 {#unabletocreateasprintasthebuttonisdisabled}

在建立衝刺(Sprint)之前，請確定目前的Sprint已標示為完成。 按一下 **[!UICONTROL Mark Sprint Complete]** ，以完成Sprint移轉。

### 按鈕已停用，無法將移轉專案標示為完成 {#unabletomarkamigrationprojectascompleteasthebuttonisdisabled}

在標示移轉專案完成之前，請確定目前的Sprint已標示為完成。 按一下 **[!UICONTROL Mark Sprint Complete]** ，以完成Sprint移轉。

## CSV問題 {#csvissues}

### module_version.csv檔案遷移失敗，內容尚未遷移 {#moduleversioncsvfilemigrationisfailingandcontentisnotmigratedyet}

確保內容可在「內容」資料夾（指定移轉專案、快速連結路徑下的Box帳戶）中使用。 此外，請確定您已選取選項 **是** 的 **您要移轉此Sprint的內容嗎？** 在Sprint建立頁面中的問題。

如果您忘記選取 **是**，並在此衝刺中繼續進行，然後您必須等到完成此衝刺為止。 建立另一個衝刺，並確保按一下 **[!UICONTROL Yes]**.

### enrollment.csv或user_course_grade.csv記錄失敗，並出現錯誤訊息「不是有效的Learning Manager ID」 {#enrollmentcsvorusercoursegradecsvrecordsfailwithanerrormessagenotavalidprimeid}

確保作為userId， assignedByUserID欄位一部分的電子郵件ID屬於有效的Learning Manager使用者。 如果沒有，請新增使用者，並使用建立新的Sprint **同步使用者** 已選取選項。 如果使用者不屬於組織，請使用「新增使用者CSV規格」，在Learning Manager中將使用者新增為已刪除使用者。 以下提供用於新增已刪除使用者的CSV規格範例，以供您參考。

[Users.csv](assets/users.zip) 請參閱 **CSV規格和範例CSV** 中的區段 [移轉手冊](../integration-admin/feature-summary/migration-manual.md) 以下載完整的CSV規格集和範例CSV檔案。

### 課程顯示為空白或移轉的課程播放不正確的模組 {#coursesappearblankorincorrectmodulesplayforamigratedcourse}

確保 **moduleOrderInCourse** 課程的關鍵值開頭為 **0** 而且是連續順序。 courseModuleType的順序應為PRETEST、TESTOUT、CONTENT

此外，請確定Activity、Classroom和VC這兩個版本未連結至現有的課程。

### 接收訊息為「模組已連結至現有的課程」 {#receivingamessageasmoduleisalreadylinkedwithanexistingcourse}

Learning Manager不允許將活動/VC/教室模組連結至多個課程。 確認模組未連結至任何其他課程。

### 所有課程都會顯示最新版的Activity/VC/Classroom模組，即使這些課程連結了不同的模組版本 {#allthecoursesshowthelatestversionofactivityvcclassroommoduleseventhoughthecoursesarelinkedwithdifferentmoduleversions}

Learning Manager不支援活動、教室和虛擬教室模組的版本設定。 如果您透過moduleVersion.csv檔案提供版本，它會更新現有檔案而不是建立新版本。

### 已移轉的Activity/VC/Classroom模組未顯示所需的持續時間 {#desireddurationdoesnotappearforamigratedactivityvcclassroommodule}

所需的期間不是Activity/VC/Classroom模組的有效專案。

### 超連結URL未在Learning Manager中開啟 {#hyperlinkurldoesntopenupincaptivateprime}

請確認所提供的連結已預先加上「http://&#39;」或「https://&#39;」

### moduleVersion移轉因「找不到檔案」錯誤而失敗 {#moduleversionmigrationfailswithfilenotfounderrors}

確保內容資料夾中存在參照的檔案，並且檔案已成功移轉。

### moduleVersion移轉失敗，並出現錯誤訊息，指出「發生內部錯誤 — 適用於模組：x和moduleVersion：y」 {#moduleversionmigrationfailswithanerrormessageasaninternalerrorhasoccurredformodulexandmoduleversiony}

重新執行Sprint以解決問題。
