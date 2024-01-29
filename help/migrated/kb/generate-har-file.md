---
description: 請閱讀下文，瞭解如何在Google Chrome上產生HAR檔案。
jcr-language: en_us
title: 產生HAR檔案
contentowner: dvenkate
source-git-commit: ec79aa3dd6225cc424721afb50702963c1b125eb
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 0%

---



# 產生HAR檔案

請閱讀下文，瞭解如何在Google Chrome上產生HAR檔案。

若要產生HAR檔案，請執行下列步驟：

1. 開啟Google Chrome視窗並開啟新標籤。
1. 開啟頁面的開發人員工具，按一下右鍵> Inspect。
1. 開啟 **[!UICONTROL Network]** 標籤。 確定紅色記錄按鈕為作用中。 啟用 **[!UICONTROL Preserve Log]** 核取方塊。

   ![](assets/preserve-log-checkbox.png)

   *選取「網路」標籤中的「保留日誌」核取方塊*

1. 登入 [Learning Manager](https://learningmanager.adobe.com/acapindex.html) 使用您的憑證並參加課程。 執行所有會導致問題的操作。
1. 在開發人員工具中，按一下右鍵並選取 **將所有內容儲存為HAR**.

   在某些Google Chrome版本中，您可能必須選取 **[!UICONTROL Copy]** > **[!UICONTROL Copy all as HAR]**.

   ![](assets/copy-hra.png)

   *複製所有HAR檔案*

1. 將複製的內容貼到記事本檔案中。 儲存至案頭作為 **logs.har** 並透過電子郵件傳送給Adobe。
