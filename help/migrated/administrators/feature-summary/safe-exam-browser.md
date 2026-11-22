---
title: 安全檢查瀏覽器
description: 在 Adobe Learning Manager 的帳戶層級啟用安全考試瀏覽器整合，讓作者能要求為原生測驗提供安全的瀏覽器環境。
source-git-commit: 8f23f95cd81e5b64932281c990d27be0c390850b
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%
---

# 安全檢查瀏覽器

安全考試瀏覽器透過限制在評量期間使用其他瀏覽器和應用程式，為學習者提供一個安全的環境，讓他們能進行原生的 Adobe Learning Manager 測驗。

管理員可以在帳戶層級啟用安全考試瀏覽器整合，並上傳設定檔（.seb）以定義測驗限制。 啟用整合後，作者可設定個別測驗要求使用安全考試瀏覽器。

本文說明如何為您的帳戶啟用安全考試瀏覽器的整合。

## 啟用安全考試瀏覽器整合

設定安全考試瀏覽器整合，讓作者在設定測驗時提供此選項。 開始之前，請確認您已擁有帳戶的安全考試瀏覽器檔案。

啟用安全考試瀏覽器整合的方法：

1. 以管理員&#x200B;**身分登入 ALM**。
1. 選擇 **「設定** 」> **「一般**」。
1. 前往 **「安全考試瀏覽器」整合**&#x200B;頁面。
1. 選擇 **「編輯**」。

   這擴充 **了安全考試瀏覽器的整合**&#x200B;功能。

1. 選擇 **啟用**。
1. 選擇 **「瀏覽** 並從系統上傳安全考試瀏覽器檔案」。 請參閱 [「設定安全檢查瀏覽器檔案](#configure-the-seb-file-for-macos) 設定」以取得更多資訊。

   ![一般設定](assets/safe-exam-browser-integration-settings.png "中的安全考試瀏覽器整合設定一般設定中的安全考試瀏覽器整合設定")

1. 選擇「 **儲存**」。

   現已開放「安全考試瀏覽器」，供作者在設定支援測驗時啟用。

請參閱[「使用 SEB](../../authors/feature-summary/create-a-course-with-safe-exam-browser.md) 建立課程」以取得更多關於以作者&#x200B;**身分設定安全考試瀏覽器**&#x200B;的資訊。

### 為 macOS 設定 .seb 檔案 {#configure-the-seb-file-for-macos}

使用 SEB 設定工具建立 .seb 檔案，以定義測驗限制、安全性設定及允許的應用程式。 在使用安全考試瀏覽器（SEB）之前，請確保 .seb 檔案符合以下要求：

1. 將 browserWindowWebView 參數設為 3（整數）以啟用 SEB。
1. 將 startURL 設定為對應於目標環境的 URL。
1. 請確保 .seb 檔案包含所需的 quitURL 資訊。
