---
jcr-language: en_us
title: 在 Adobe Learning Manager 完成課程時，模組會被標記為未完成
description: 即使學習者完成 Adobe Learning Manager 課程後，該模組仍被標記為未完成。
contentowner: nluke
exl-id: c0f14f2e-733a-4b4f-a2c2-4c0b33a15fa1
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%
---
# 在 Adobe Learning Manager 完成課程時，模組會被標記為未完成

## 子嗣

即使學習者完成 Adobe Learning Manager 課程後，該模組仍被標記為未完成。

## 成因

SCORM 2004 定義了成功與完成標準，並分別傳送兩者的聲明。

例如，假設有一個內容集， **完成標準** 為100%投影片視圖，成功 **標準** 為「測驗通過」。

一名學習者完成課程，但小考不及格。 此時進度為100%，但因學習者未達 **成功標準**，模組仍被標記為未完成。

## 解法

問題與專案的報告 **偏好設定** 有關。 作者必須核實課程完成與成功的標準。

若需要任何變更，作者可使用內容創作工具（如 Adobe Captivate Classic）進行。 作者可以相應地更新模組。

![](assets/scorm.png)

*查看 Captivate Classic 報告偏好設定*
