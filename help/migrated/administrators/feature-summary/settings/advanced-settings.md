---
description: 了解更多關於如何在 Adobe Learning Manager 中設定進階設定
jcr-language: en_us
title: Adobe Learning Manager 的進階設定
source-git-commit: 03123dcd8d9066cdfcb0fe97e61acb3df625a23e
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 0%

---


# Adobe Learning Manager 的進階設定

## 目錄標籤

Adobe Learning Manager 中的目錄標籤用於標註學習對象（課程、認證、學習路徑等） 具有特定的欄位和數值。 這些標籤幫助你和作者有效分類與組織內容，促進更好的篩選、追蹤與報告。

更多資訊請參閱 [Adobe Learning Manager](/help/migrated/administrators/feature-summary/catalog-labels.md) 中的目錄標籤。


>[!NOTE]
>
>* 強制標籤：你可以選擇在課程創建時強制作者使用目錄標籤。
>* 作者工作流程：作者在建立或編輯課程時必須加上合規標籤，以確保分類正確。

## 內容資料夾

內容資料夾允許你透過建立私人或公開資料夾來組織和管理內容。 此功能確保內容僅對特定作者或團體開放，提供對內容可見性與管理的更好控制。

**重點：**

資料夾是內容的儲存庫，內容是擁有以下屬性的帳號中整個內容庫的子集：

* 只有你（管理員）可以建立、編輯或刪除資料夾。
* 你可以在自訂管理員角色定義時，控制資料夾存取權。
* 內容必須始終與至少一個資料夾相關聯。 一開始，所有內容都會綁定到公開資料夾，之後可以更改。
* 內容可在建立時綁定多個資料夾，這也可以透過複製操作實現
* 所有資料夾名稱必須在帳號內唯一，否則命名資料夾時會出現錯誤。

資料夾只控制內容的可見性，並不會產生內容的複製品。 因此，編輯內容會在所有相關的資料夾中反映。

**公用資料夾**

帳號中始終存在一個公開資料夾，起初所有內容都會屬於這個資料夾。 之後，作者可以將內容從這個資料夾移到其他資料夾。 公共資料夾具有以下屬性：

* 所有與此資料夾相關的內容預設都會對所有類型的作者開放。
* 任何屬於公開資料夾的內容，都不能屬於其他資料夾。 反之亦然。

這個資料夾不能成為可設定角色定義的一部分。 因此，沒有在可設定的角色定義中放置公共資料夾，並不會限制對公共資料夾的存取。

**私人資料夾**

你建立的任何資料夾都是私人資料夾。

**新增內容資料夾**

要新增內容資料夾，請依照以下步驟操作：

1. 選擇 **[!UICONTROL Settings]** > **[!UICONTROL Content Folder]**。
2. 選擇 **[!UICONTROL Add]** 建立新資料夾。
3. 輸入要建立資料夾的名稱和描述。

   ![替代文字](assets/advanced-settings-picture1.png)

4. 選擇 **[!UICONTROL Save]** 建立該資料夾。

**資料夾操作**

* **[!UICONTROL Add a folder]**： 要新增資料夾，請選擇該資料夾，然後在畫面右上角選擇 **[!UICONTROL Add]** 。
* **[!UICONTROL Delete a folder]**： 要刪除資料夾，請選擇要刪除的資料夾，選擇 **[!UICONTROL Actions]** 選單，然後選擇 **[!UICONTROL Delete Folder]**。

## 教室地點

建立並管理實體或虛擬教室的圖書館。 這些地點可供作者與管理者使用，舉辦由講師主導的訓練（ILT）活動。 此功能確保教室細節如座位限制與地點資訊皆預先設定且易於存取。

更多資訊請參閱 [Adobe Learning Manager](/help/migrated/administrators/feature-summary/classroom.md) 中的「新增教室地點」。

## 報表

此區塊允許您設定合規與群組成功儀表板。

![替代文字](assets/advanced-settings-picture2.png)

更多資訊請參見以下內容：

* [合規儀表板](/help/migrated/administrators/feature-summary/reports.md#compliance-dashboard)
* [團體成功儀表板](/help/migrated/administrators/feature-summary/group-success-dashboard.md)


