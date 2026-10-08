---
jcr-language: en_us
title: Learning Manager 的登入問題
description: Adobe Learning Manager 的登入問題
contentowner: nluke
exl-id: 516c1a20-f185-4ace-a1e7-2cd89644863c
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%
---
# Learning Manager 的登入問題

## 子嗣

無法登入 Adobe Learning Manager。

## 錯誤

嘗試登入 Adobe Learning Manager 時，以下顯示錯誤訊息：

![](assets/cp-error.png)

*會話過期錯誤訊息*

## 原因

當使用者透過 SSO 登入時，會建立一個會話 Cookie，並儲存在瀏覽器中。 它也讓使用者能夠登入其他應用程式。 大多數 SSO 設定為 24 小時後登出。 使用者必須重新驗證才能開啟新的會話。

在某些情況下，使用者因 SSO cookie 過期而無法存取系統。 這些 Cookie 會轉發至 Adobe Learning Manager 進行驗證。 如果使用者長時間未關閉瀏覽器或未登出，該會話不會結束。

Adobe Learning Manager 會拒絕這些過期的 Cookie，導致錯誤。

## 解決方法

如果 Adobe Learning Manager 拒絕了過期的 cookie，請嘗試以下選項：

1. 清除瀏覽器的 Cookie 和快取。 欲了解更多資訊，請參閱此 [文件](unable-log-in-learning-manager.md)。

   或者，IDP 管理員可以在特定時間後定義強制登出。 此步驟再次驗證使用者以開始新會話。

這個錯誤發生還有其他原因，但上述情況很常見。

## 參考連結：

[Microsoft：終身條件存取會話](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)
