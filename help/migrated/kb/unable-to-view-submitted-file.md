---
jcr-language: en_us
title: 無法在 Adobe Learning Manager 中查看檔案提交
description: 講師無法查看學習者在提交活動模組中上傳的檔案。
contentowner: nluke
exl-id: b4a0af25-14ae-46f1-9afd-0bf2aace7fe2
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%
---
# 無法在 Adobe Learning Manager 中查看檔案提交

## 子嗣

講師無法查看學習者上傳的檔案提交。

## 說明

講師無法查看學習者在提交活動模組&#x200B;**中上傳**&#x200B;的檔案。

例如，一位學習者註冊了一個名為 **Test 實例** 的課程實例，如下所示：

![](assets/test-instance.png)

*檢視實例*

學習者接著開啟課程並在活動模組中上傳檔案。

當講師嘗試批准提交時，卻無法成功。

![](assets/activity.png)

*在活動模組中上傳檔案*

## 成因

如果在學習者註冊的課程實例中沒有講師，問題就會出現。

## 解決方法

要檢查是否有講師加入課程實例，請執行以下步驟：

1. 進入課程設定。
1. 在 **管理** 區塊，點選 **[!UICONTROL Instances]。**
1. 在學習者註冊的情況下，請點擊 **[!UICONTROL Sessions]**。

   ![](assets/check-instructor.png)

   *在實例中選擇會話*

   此課程沒有指定講師。

1. 點擊 **[!UICONTROL Edit]**。 新增批准檔案提交的講師。

   ![](assets/assign-instructor.png)

   *新增教練*
1. 儲存變更。
