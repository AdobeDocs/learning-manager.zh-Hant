---
jcr-language: en_us
title: 富文字編輯器的 CSS 範本
description: 富文字編輯器的 CSS 範本
contentowner: saghosh
preview: true
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%
---


# 富文字編輯器的 CSS 範本

## 為什麼需要 CSS？

富文本由 HTML 標記組成。 若依照原樣渲染標記，瀏覽器會套用預設樣式。 這通常與公司的風格規範不符。 符合指引是必須有CSS的。

## 預設風格

附上的 CSS 樣式表包含由 Learning Manager 套用的樣式。 外觀設計會根據大多數使用情境做調整。 下載附帶的 CSS 檔案，並依照你的慣例和建置系統匯入到你的網頁應用程式。 CSS 定義的類別會以 ql-editor 類別命名空間，且不會干擾你現有的樣式。

## 自訂風格

預設的造型可能無法滿足每個人的需求。 自訂可以透過覆蓋提供的 CSS 來完成。 所有樣式都包裹在 QL-editor 裡，作為後代選擇器。 使用以下類別：

* **縮排：** li.ql-indent-$number。 $number範圍從1到9
* **尺寸**：QL尺寸-小、QL-尺寸-大、QL-尺寸-巨大
* **對齊**&#x200B;方式：QL-對齊-中心，QL-對齊-對齊，QL-對齊-右
* **顏色**：QL-color-$color。 $color = 白色、紅色、橙色、黃色、綠色、藍色、紫色
* **背景**：QL-BG-$color。 $color = 黑色、紅色、橘色、黃色、綠色、藍色、紫色
* **HTML 標籤：** P、OL、UL、PRE、BLOCKQUOTE、H1、H2、H3、H4、H5、H6

[CSS 檔案用於自訂。](assets/ql-headless.css)
