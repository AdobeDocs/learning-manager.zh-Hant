---
jcr-language: en_us
title: 使用者在Learning Manager中自動刪除
description: 使用者會從Learning Manager中刪除，但管理員不會執行任何此類動作。
contentowner: nluke
source-git-commit: 3242a293fc4b2707044e11c342c984cbfb2fc434
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---



# 使用者在Learning Manager中自動刪除 {#user-gets-auto-deleted-in-learning-manager}

## 問題

A **使用者** 會從Learning Manager中刪除，但管理員從未執行任何此類動作。

## 原因

在Adobe Learning Manager中，有一個選項可讓您在使用者特定時間未登入系統時刪除該使用者。

## 如何變更/套用設定？

### 內部學習者

1. 登入身份 **管理員**.
1. 在 **設定**，按一下 **設定** > **一般**.
1. 在一般設定頁面中，請參閱以取得選項 **自動刪除內部使用者**.
1. 按一下 **[!UICONTROL Edit]** 若要在欄位中輸入天數，若要在學習者未存取系統時自動將其刪除。

   ![](assets/cp-autodelete-internal.png)

   *編輯天數*

>[!NOTE]
>
>   如果您不想自動刪除使用者，請將此欄位保留空白。


1. 按一下 **[!UICONTROL Save]** 以保留所做的設定。

### 對於外部學習者：

1. 登入身份 **管理員**.
1. 在 **管理**，按一下 **[!UICONTROL Users]** > **[!UICONTROL External]**.
1. 按一下需要套用設定的外部使用者名稱。

   如此將可開啟 **編輯外部註冊設定檔** 視窗。

1. 按一下 **[!UICONTROL Advanced Settings]** 左下角。

   ![](assets/cp-autodelete-external.png)

   *選取進階設定選項*

1. 在 **登入要求** 欄位中，輸入學習者尚未存取系統時自動刪除的天數。
1. 按一下 **[!UICONTROL Save]** 以保留所做的設定。
