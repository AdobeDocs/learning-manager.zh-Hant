---
jcr-language: en_us
title: Learning Manager 中的社交登入
description: Learning Manager 中的社交登入
contentowner: saghosh
preview: true
source-git-commit: ccdb222228f76fdae63ebb0a808824ad6ac1db7f
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%
---


# Learning Manager 中的社交登入

你可以使用Facebook、LinkedIn或Twitter的帳號登入學習管理員。

## 建立社群登入 {#setupsociallogin}

1. 如果你想讓客戶成功經理幫你設立帳號，可以聯絡他/她。

   否則，請依照以下步驟操作。

1. 搜尋你想設定社群登入的帳號。
1. 把登入資料改成 SSO。
1. 點選進階。 請指定以下 JSON。

   ```
   \{"linkedIn":true,"microsoft":true,"twitter":true,"facebook":true,"editingAllowed":true
   ```

   如果是錯誤的 JSON，會有例外。

   此社交登入功能僅用於內部使用者。

