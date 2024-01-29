---
jcr-language: en_us
title: Learning Manager中的社交登入
description: Learning Manager中的社交登入
contentowner: saghosh
preview: true
source-git-commit: ccdb222228f76fdae63ebb0a808824ad6ac1db7f
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---



# Learning Manager中的社交登入

您可以使用您的Facebook、LinkedIn或Twitter憑證登入Learning Manager。

## 設定社交登入 {#setupsociallogin}

1. 如果您希望客戶成功經理設定帳戶，請洽詢他/她。

   否則，請遵循以下步驟。

1. 搜尋您要設定社交登入的帳戶。
1. 將登入變更為SSO。
1. 按一下「進階」。 指定下列JSON。

   ```
   \{"linkedIn":true,"microsoft":true,"twitter":true,"facebook":true,"editingAllowed":true
   ```

   如果JSON不正確，則會出現例外狀況。

   此社交登入功能僅適用於INTERNAL使用者。

