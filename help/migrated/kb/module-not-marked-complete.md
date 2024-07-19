---
jcr-language: en_us
title: 在Adobe Learning Manager中完成課程時模組被標籤為未完成
description: 即使學習者在Adobe Learning Manager中完成課程後，模組仍會標籤為未完成。
contentowner: nluke
exl-id: c0f14f2e-733a-4b4f-a2c2-4c0b33a15fa1
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# 在Adobe Learning Manager中完成課程時模組被標籤為未完成

## 問題

即使學習者在Adobe Learning Manager中完成課程後，模組仍會標籤為未完成。

## 原因

SCORM 2004定義了成功和完成標準，並分別傳送兩者的陳述式。

例如，讓內容集包含100%投影片檢視的&#x200B;**完成條件**，以及設為「通過測驗」的&#x200B;**成功條件**。

學習者，完成課程但未能通過測驗。 在此情況下，進度為100%，但學習者未符合&#x200B;**成功標準**，模組被標籤為未完成。

## 解決方案

此問題與專案設定的報告&#x200B;**偏好設定**&#x200B;有關。 作者必須確認課程完成和成功所設定的條件。

如果需要進行任何變更，作者可使用內容製作工具(例如Adobe Captivate Classic)進行此作業。 然後，作者可以據此更新模組。

![](assets/scorm.png)

*檢視Captivate Classic報表偏好設定*
