---
description: 瞭解如何管理Learning Manager上的標籤。
jcr-language: en_us
title: 標記
contentowner: dvenkate
exl-id: ea39d2a2-3d2b-43ae-8f8d-b97420b9d008
source-git-commit: a28ac8f57710c118ca4ad02872fd100c6f24beac
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 0%

---

# 標記

管理員現在可以在學習管理器中管理標記。 使用更出色的標籤和可管理資料庫，協助學習者更輕鬆搜尋，並快速取得適當的搜尋結果。 您可以使用此功能管理冗餘、拼寫錯誤和不相關的標籤。 您也可以新增、編輯、刪除、附加或取代標籤。

按一下每個標籤旁提供的計數，即可檢視與該標籤相關聯的學習物件清單。 此清單會顯示課程、學習計畫、憑證、工作輔助和內容群組的數量。 按一下這些選項中的任何一個，即可檢視清單。

您可以使用&#x200B;**[!UICONTROL Sort By]**&#x200B;選項，根據使用方式或字母順序來排序標籤。

## 標籤簡介

此培訓將指導您如何添加、編輯、替換、附加和刪除標籤。 您也會瞭解如何變更許可權設定及使用標籤篩選器。

[![按鈕](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/8318920)

如果您無法啟動訓練，請寫信到<almacademy@adobe.com>。

## 新增/刪除/編輯標籤 {#adddeleteedittags}

1. 以管理員身分，在左側導覽面板上按一下&#x200B;**[!UICONTROL Tags]**。 **[!UICONTROL Tag Management]**&#x200B;頁面隨即開啟。
1. 要新增標記，請按兩下 **[!UICONTROL Add]**。 新增按鈕位於頁面的右上角。 如果沒有現有的標記， **[!UICONTROL Add]** 按鈕也將顯示在頁面中間 **[!UICONTROL Tag Management]** 。

   新增多個標記時，請使用 （，） 或 （;) 分隔。 標記名稱最多可包含 50 個字符。

1. 要刪除現有標記，請按兩下複選框以選擇標記。 您可以選擇多個標籤（最多 50 個）一次刪除。 若要刪除，請遵循此步驟：

   * 選取要刪除的標籤>開啟&#x200B;**[!UICONTROL Action]**&#x200B;下拉式功能表>選取&#x200B;**[!UICONTROL Delete]**。

1. 您一次只能編輯一個標籤。 若要編輯標籤，請遵循此步驟：

   * 選擇要編輯的標記>打開&#x200B;**[!UICONTROL Actions]**&#x200B;下拉功能表>然後按兩下 **[!UICONTROL Edit]**。

   對話框出現 **[!UICONTROL Edit Tag]** 。 輸入新的標記名稱，然後按下 **[!UICONTROL Save]**。

   如果您輸入的標籤名稱已存在，Adobe Learning Manager會顯示警告訊息。 不能存在具有相同名稱的兩個標籤。

## 取代標籤 {#replacetags}

1. 選取您要取代的標籤。 您一次最多可以選取50個標籤。 開啟&#x200B;**[!UICONTROL Actions]**&#x200B;下拉式功能表並選取&#x200B;**[!UICONTROL Replace]**。
1. **[!UICONTROL Replace Tags]**&#x200B;對話方塊出現，顯示選取的標籤。

1. **[!UICONTROL Name for replaced tags]**&#x200B;在該選項中，輸入要用於替換所選標記的新標記的名稱。您可以使用下拉式清單中的現有標籤來取代它們，或新增標籤。

   分號或逗號不能是標籤名稱的一部分。  請注意，移轉案例不會處理沒有分號的標籤，以及在使用這類標籤做為某些LO的一部分時錯誤訊息的顯示。

1. 按一下&#x200B;**[!UICONTROL Replace]**。

## 附加標籤 {#appendtags}

如果對標籤執行追加作，則新的/現有標記將追加到與所選標籤關聯的所有 LO 和內容組清單。

1. 選擇要附加的標記。 您一次最多可選取 50 個標記。 開啟作下拉選單，然後選擇 **[!UICONTROL Append]**。
1. 對話框出現，  **[!UICONTROL Append Tags]** 顯示所選標記。
1. 您可以通過從現有標籤的下拉清單中輸入 或 **[!UICONTROL New Tag]** 的名稱，將額外的標記附加到具有所選標籤的所有學習中。 新標記將追加到學習管理器中的所有關聯學習中。

   分號或逗號不能是標籤名稱的一部分。 若使用，Prime會顯示錯誤訊息。 請注意，移轉案例不會處理沒有分號的標籤，以及在使用這類標籤做為某些LO的一部分時錯誤訊息的顯示。

1. 按一下&#x200B;**[!UICONTROL Append]**。

## 設定 {#settings}

作為管理員，您可以透過按一下「設定」選項來向作者提供建立標籤的許可權。

![](assets/unknown-1.jpeg)

*設定用于建立標記的頁面*

* 當用戶權限創建標記並選擇當前無效的現有標記時，

  將顯示一條錯誤消息，提示所選標記不再有效。 移除不支援的字元即可建立新標籤。 在此情況下，作者在儲存之前，應該能夠看到他的舊標籤被變更為新標籤。

* 如果使用者沒有建立新標籤的許可權，則會出現錯誤訊息，指出所選的標籤已失效。 作者可以聯絡管理員，以修改無效的標籤。

  作者無法建立或儲存無效的標籤。 他們可以刪除無效標記並添加任何其他現有有效標記然後繼續。
