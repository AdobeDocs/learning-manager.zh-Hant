---
jcr-language: en_us
title: RTF編輯器的CSS範本
description: RTF編輯器的CSS範本
contentowner: saghosh
preview: true
source-git-commit: 9325abb9cda8c8a019c9d72c1944a8284f38f83e
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---



# RTF編輯器的CSS範本

## 為何需要CSS？

RTF文字是由HTML標籤所組成。 以原樣呈現標籤會導致瀏覽器套用預設樣式。 這通常與公司的風格指引不符。 需要CSS才能符合准則。

## 預設樣式

附加的CSS樣式表包含Learning Manager套用的樣式。 考量到大多數使用案例，樣式已有所調整。 下載附加的CSS檔案，並根據您的慣例和建置系統將其匯入您的Webapp。 所定義的CSS類別會在ql-editor類別下名稱空間，且不會干擾您現有的樣式。

## 自訂樣式

預設樣式可能不符合每個人的需求。 自訂可藉由覆寫提供的CSS來完成。 所有樣式都會包裝在ql編輯器下，作為子系選取器。 使用下列類別：

* **縮排**： li.ql-indent-$number。 $number從1到9不等
* **size**： ql-size-small， ql-size-large， ql-size-great
* **alignment**： ql-align-center、ql-align-justify、ql-align-right
* **color**： ql-color-$color。 $color =白色，紅色，橙色，黃色，綠色，藍色，紫色
* **背景**： ql-bg-$color。 $color =黑色，紅色，橙色，黃色，綠色，藍色，紫色
* **html標籤**： p， ol， ul， pre， blockquote， h1， h2， h3， h4， h5， h6

[用於自訂的CSS檔案。](assets/ql-headless.css)
