---
description: 瞭解如何管理Learning Manager上的標籤。
jcr-language: en_us
title: 標記
contentowner: dvenkate
source-git-commit: 0534bd52c80b77d985cfe715f74054f3aabac9a2
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 0%

---



# 標記

管理員現在可以管理Learning Manager中的標籤。 使用更出色的標籤和可管理資料庫，協助學習者更輕鬆搜尋，並快速取得適當的搜尋結果。 您可以使用此功能管理冗餘、拼寫錯誤和不相關的標籤。 您也可以新增、編輯、刪除、附加或取代標籤。

按一下每個標籤旁提供的計數，即可檢視與該標籤相關聯的學習物件清單。 此清單會顯示課程、學習計畫、憑證、工作輔助和內容群組的數量。 按一下這些選項中的任何一個，即可檢視清單。

您可以使用來根據使用情形或字母順序來排序標籤 **[!UICONTROL Sort By]** 選項。

## 標籤簡介

此培訓會教您如何新增、編輯、取代、附加和刪除標籤。 您也會瞭解如何變更許可權設定及使用標籤篩選器。

[![按鈕](assets/launch-training-button.png)](https://learningmanager.adobe.com/app/learner?accountId=98632&amp;sdid=5S7K7ZCT&amp;mv=display&amp;mv2=display#/course/8318920)

如果您無法啟動培訓，請寫信至 <almacademy@adobe.com>.

## 新增/刪除/編輯標籤 {#adddeleteedittags}

1. 以管理員身分，在左側導覽面板上按一下 **[!UICONTROL Tags]**. 此 **[!UICONTROL Tag Management]** 頁面隨即開啟。
1. 若要新增標籤，請按一下 **[!UICONTROL Add]**. 新增按鈕位於頁面的右上角。 如果沒有現有標籤， **[!UICONTROL Add]** 按鈕也可在以下內容中間使用： **[!UICONTROL Tag Management]** 頁面。

   新增多個標籤時，請使用(，)或(；)加以分隔。 標籤名稱最多可包含50個字元。

1. 若要刪除現有標籤，請按一下核取方塊以選取標籤。 您可以一次選取多個最多50個數字的標籤進行刪除。 若要刪除，請遵循此步驟：

   * 選取要刪除的標籤>開啟 **[!UICONTROL Action]** 下拉式功能表>選取 **[!UICONTROL Delete]**.

1. 您一次只能編輯一個標籤。 若要編輯標籤，請遵循此步驟：

   * 選取要編輯的標籤>開啟標**[!UICONTROL Actions]**下拉式功能表>按一下 **[!UICONTROL Edit]**.

   此 **[!UICONTROL Edit Tag]** 對話方塊隨即顯示。 輸入新標籤名稱，然後按一下 **[!UICONTROL Save]**.

   如果您輸入的標簽名稱已存在，AdobeLearning Manager會顯示警告訊息。 不能存在具有相同名稱的兩個標籤。

## 取代標籤 {#replacetags}

1. 選取您要取代的標籤。 您一次最多可以選取50個標籤。 開啟 **[!UICONTROL Actions]** 下拉式功能表並選取 **[!UICONTROL Replace]**.
1. 此 **[!UICONTROL Replace Tags]** 隨即顯示對話方塊，其中顯示選取的標籤。

1. 在 **[!UICONTROL Name for replaced tags]** 選項，輸入您想要取代所選標籤的新標籤名稱。 您可以使用下拉式清單中的現有標籤來取代它們，或新增標籤。

   分號或逗號不能是標籤名稱的一部分。  請注意，移轉案例不會處理沒有分號的標籤，以及在使用這類標籤做為某些LO的一部分時錯誤訊息的顯示。

1. 按一下 **[!UICONTROL Replace]**.

## 附加標籤 {#appendtags}

如果對標籤進行「附加」操作，則新/現有標籤將附加到與所選標籤相關聯之所有活頁簿和內容群組的清單中。

1. 選取您要附加的標籤。 您一次最多可以選取50個標籤。 開啟「動作」下拉式功能表，然後選取 **[!UICONTROL Append]**.
1. 此  **[!UICONTROL Append Tags]** 隨即顯示對話方塊，其中顯示選取的標籤。
1. 您可以輸入「 」的名稱，將其他標籤附加至具有所選標籤的所有學習專案。 **[!UICONTROL New Tag]** 或從現有標籤的下拉式清單中選取。 新標籤將會附加至Learning Manager中所有相關的學習專案。

   分號或逗號不能是標籤名稱的一部分。 若使用，Prime會顯示錯誤訊息。 請注意，移轉案例不會處理沒有分號的標籤，以及在使用這類標籤做為某些LO的一部分時錯誤訊息的顯示。

1. 按一下 **[!UICONTROL Append]**.

## 設定 {#settings}

作為管理員，您可以透過按一下「設定」選項來向作者提供建立標籤的許可權。

![](assets/unknown-1.jpeg)

*建立標籤的設定頁面*

* 當使用者有權建立標籤並選取目前無效的現有標籤時，

  系統會顯示錯誤訊息，指出選取的標籤已失效。 移除不支援的字元即可建立新標籤。 在此情況下，作者在儲存之前，應該能夠看到他的舊標籤被變更為新標籤。

* 如果使用者沒有建立新標籤的許可權，則會出現錯誤訊息，指出所選的標籤已失效。 作者可以聯絡管理員，以修改無效的標籤。

  作者無法建立或儲存無效的標籤。 他們可以移除無效的標籤，並新增任何其他現有的有效標籤並繼續。
