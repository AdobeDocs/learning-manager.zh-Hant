---
jcr-language: en_us
title: 選擇按鈕不會出現在學習管理員中
description: 由於缺少單一按鈕，管理員無法 ssign 或移除角色、發送歡迎信或刪除使用者。
contentowner: nluke
exl-id: d2c86f9f-3e79-4f1f-992e-f92873940061
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%
---
# 選擇按鈕不會出現在學習管理員中

## 子嗣

由於缺少單選按鈕，管理員無法執行以下操作（非完整清單）：

* 指派或移除角色。
* 寄出歡迎信。
* 刪除使用者。

## 成因

問題發生在帳號中出現了錯誤的主題。

![](assets/radio-buttons.png)

*單選按鈕不見*

## 解決方法

重新載入主題並修正單選按鈕的外觀。 請執行以下步驟：

1. 作為管理員，請點擊 **[!UICONTROL Branding]**。
1. 在 **主題** 區，點擊 **[!UICONTROL Edit]。**
1. 隨意選一個主題並儲存更改。

   ![](assets/set-themes.png)

   *選擇任何主題*

1. 還原到之前的主題並儲存更改。
1. 登出 Adobe Learning Manager 並重新登入。
