---
title: 原生擴充性
description: 在AdobeLearning Manager的原生版本中設定自訂體驗，可讓您在不太複雜的案例中使用Headless。
source-git-commit: 86c80607e2f50e6abf6d64fd7a916ef5b024b837
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 0%

---

# 原生擴充性

您可以在AdobeLearning Manager的原生版本中設定自訂體驗，如此一來，您將不會將Headless用於不太複雜的案例。 您也可以建立自訂應用程式，並將其放置在學習者、經理、管理員、作者或講師工作流程的原生版本中的不同位置。

Adobe Learning Manager可在管理員、作者、學習者、經理和講師應用程式中支援15個叫用點。

## 建立擴充功能

1. 以管理員身分，在左側面板中選取 **[!UICONTROL Native Extensions]**.
1. 選取「新增擴充功能」。
1. 在中輸入擴充功能的名稱 **[!UICONTROL Name]** 欄位。
1. 在「 」中輸入擴充功能的說明 **[!UICONTROL Description]** 欄位。
1. 選取引動點。 引動點是Adobe Learning Manager中可在自訂應用程式中插入連結或按鈕的任何位置。 可以使用下列引動點：

   在此範例中，選取 **[!UICONTROL Admin]**， **[!UICONTROL Author: Course]**， **[!UICONTROL Learning Path]** - **[!UICONTROL Instances]** - **[!UICONTROL Instance row]**.

   ![延伸模組影像](assets/list-native-extensions.png)
   *選取啟動點*

1. 輸入將顯示在中UI的擴充功能標籤 **[!UICONTROL Extension Label]** 欄位。
1. 在「 」中輸入您要託管擴充功能的URL **[!UICONTROL URL]** 欄位。
1. 在「開啟位置」下拉式清單中，選取要在強制回應視窗或新標籤中啟動擴充功能。
1. 選取強制回應視窗的大小。 如果您已選取「 」，便可使用選項 *應用程式內* 強制回應視窗。

   若要維持快顯視窗內的協助工具，當擴充功能應用程式位於網站上的最後一個可聚焦元素時，必須將其傳送至事件，然後使用者選取TAB鍵。 需要將焦點保持在快顯視窗內，以支援協助工具。

   ```
   window.parent.postMessage({*}
   
   { type: 'ALM_EXTENSION_APP', eventType: 'trapFocusInModal' }
   
   ,{}'');
   ```

1. 設定擴充功能的範圍。 下列範圍可供使用：

   * **[!UICONTROL All Courses, Learning Paths and Certifications]**：此擴充功能已針對所有課程、學習路徑及認證啟用。 與管理員一樣，作者可為部分課程、學習路徑及認證停用此功能。
   * **[!UICONTROL Selected Courses, Learning Paths and Certifications]**：此擴充功能已針對所有課程、學習路徑及認證停用。 作者可與管理員一起為某些課程、學習路徑和認證啟用此功能。

1. 選取 **[!UICONTROL Activate]** 切換即可啟用擴充功能。 啟動後，擴充功能會根據範圍顯示在指定的引動點上。
1. 選取 **[!UICONTROL Save]** 建立擴充功能的頁面。

## 以管理員身分存取擴充功能

1. 身為管理員，請選取「 」 **[!UICONTROL Learning Paths]** 在左側工具列中。
1. 選取課程> **[!UICONTROL View Learning Path]**.
1. 選取 **[!UICONTROL Instances]** 在左側面板中。
1. 選取 **[!UICONTROL More]** （在例項區段中）。 擴充功能會顯示在「例項」區段中。

   ![例項影像](assets/instances-extension.png)
   *選取擴充功能*

   選取擴充功能時，擴充功能會出現在強制回應視窗中。

## 以作者身分存取擴充功能

1. 身為管理員，請選取「 」 **[!UICONTROL Learning Paths]** 在左側工具列中。
1. 選取課程> **[!UICONTROL View Learning Path]**.
1. 選取 **[!UICONTROL Instances]** 在左側面板中。
1. 選取 **[!UICONTROL More]** （在例項區段中）。 擴充功能會顯示在「例項」區段中。

   ![例項影像](assets/instances-extension.png)
   *以作者身分存取擴充功能*

   選取擴充功能時，擴充功能會出現在強制回應視窗中。

## 檢視所有擴充功能

身為管理員，您可以在「原生擴充功能」頁面上檢視所有擴充功能。 若要檢視清單，請選取應用程式左側面板中的「原生擴充功能」 。

![檢視擴充功能影像](assets/view-extensions.png)
*檢視所有擴充功能*

## 啟用或停用擴充功能

身為作者，您可以在課程的「設定」頁面上啟用或停用課程、認證或學習路徑的擴充功能。

![啟用擴充功能影像](assets/activate-extension.png)
*啟用擴充功能*

## 共用存取金鑰

如果您要設定註冊擴充功能，則必須共用存取金鑰。

這點很重要，因為如果此金鑰未產生並跨平台共用，註冊驗證將會失敗，且學習者無法自行註冊課程。

必須共用存取金鑰才能註冊課程或學習路徑及憑證。

在「設定」標籤中，產生金鑰。

![共用重要影像](assets/share-extension.png)
*共用存取金鑰*

## 下載擴充功能報表

有兩種方式下載此報表。

**擴充功能組態報告**

1. 在「原生擴充功能」頁面中，選取 **[!UICONTROL Extension Configuration Report]**.

   ![報表影像](assets/extension-config-report.png)
   *下載擴充功能報表*

   報表隨即產生。

1. 選取「確定」。

   ![產生報表影像](assets/generating-report.png)
   *產生報表*

   報告包含下列欄位：

   * 擴充功能名稱
   * 引動點
   * 標籤
   * 在URL中開啟
   * 範圍
   * 啟動
   * 學習對象唯一識別碼
   * 訓練ID
   * 訓練型別
   * 訓練名稱

**報表頁面**

1. 在 **[!UICONTROL Reports]** > **[!UICONTROL Custom Reports]**，選取 **[!UICONTROL Extension Configuration Report]**.

   ![報表頁面影像](assets/extension-report-page.png)
   *從報告頁面下載報告*

狀態必須在範圍內 **0 - 4294967295**，則在設定註冊狀態時。
