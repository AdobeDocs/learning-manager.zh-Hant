---
description: 學習如何使用 iframe 將學習助理嵌入應用程式，包括設定、設定與事件處理
jcr-language: en_us
title: 透過嵌入 iFrame 整合學習助理
source-git-commit: 1549a4592b7a930631dcff6b2e75ec3a3d4f5592
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---


# 使用 iframe 的學習助理嵌入

## 概觀

Adobe Learning Manager （ALM） 使用者可直接將 **學習者助理** 嵌入他們面向學習者的應用程式中（例如自訂入口網站、學習管理系統前端、學習中心等） 使用標準 HTML `<iframe>`。

透過 iFrame 嵌入時，學習助理提供所有學習助理功能，包括：

* 配器
* 答覆代理人
* 知識代理
* 學習路徑代理

>[!IMPORTANT]
>
>iFrame 嵌入讓您的應用程式能完整存取學習助理底層代理。 然而，你的應用程式（「父應用程式」）負責處理助理發出的任何事件。 例如，當學習者點擊助理回應中的引用或課程連結時，助理會發出事件，而你的父應用程式必須處理該事件並執行實際導航。 學習助理不會代表你的申請進行導航。

## 先決條件

開始前，請確保你具備：

* 一個啟用學習助理的 ALM 租戶。 請從管理員設定頁面設定所需的目錄。
* 一個有效的 accessToken 用於驗證學習者（或管理員）會話。 要產生存取權杖，請依照使用 OAuth 2.0](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/developer-manual#authentication-using-oauth-20) 認證頁面上的[指示操作。該頁面包含驗證及產生存取權杖所需的步驟。
* 能夠將 嵌入 `<iframe>` 應用程式，並透過瀏覽器的 postMessage API 與之溝通。
* 前端程式碼擁有父應用程式，因為你的應用程式必須監聽並回應來自嵌入 iFrame 的訊息。

## 學習助理設定參數

| 參數名稱 | 價值 | 說明 |
|---|---|---|
| 主機名稱 | learningmanager.adobe.com | 指定應用程式的宿主網域。 |
| 存取令牌 | token123（實際存取權杖） | 用於驗證並授權使用者會話的令牌。 |

## 初始化 iFrame

透過 postMessage API 將設定傳送給學習助理，並使用嵌入的 iFrame 配置握手。

1. 父應用程式將學習助理嵌入為 `<iframe>`.
2. 若未找到基於 URL 的設定，學習助理會向母應用程式發送ALM_CHAT_REQUEST_CONFIG事件。
3. 父應用程式會以包含組態有效載荷的ALM_CHAT_CONFIG事件回應。 例如：

   ```json
   {
     "hostName": "learningmanager.adobe.com",
     "accessToken": "token123",
     "openByDefault": false,
     "isAdmin": false
   }
   ```

4. 成功初始化後，學習助理會進行影像並準備使用。

## iFrame 事件摘要

學習助理與家長應用程式透過 postMessage 事件雙向溝通。

### 外出事件（學習助理 iFrame 到 Parent App）

| 活動名稱 | 說明 | 通過參數 |
|---|---|---|
| ALM_CHAT_OPENED | 聊天開啟時就被解雇。 | -- |
| ALM_CHAT_CLOSED | 聊天結束後被解雇。 | -- |
| ALM_CHAT_LO_REDIRECT | 請前往個人化學習路徑總覽頁面。 | loId， loType， instanceId |
| ALM_CHAT_URL_REDIRECT | 當聊天訊息中點擊外部連結時，會被觸發。 | 網址 |
| ALM_CHAT_REQUEST_CONFIG | 請求從父應用程式設定。 | -- |
| ALM_CHAT_WAITING_FOR_REPLY | 表示助理正在處理請求或等待回應。 | isWaitingForReply |
| ALM_CHAT_PERSONALIZED_PATH_CREATED | 當學習路徑被儲存時觸發。 | -- |

### 即將進入的事件（從家長應用程式到學習助理）

| 活動名稱 | 說明 | 有效載荷 |
|---|---|---|
| ALM_CHAT_CONFIG | 傳送初始化助理所需的設定有效載荷。 | 配置物件 |
| ALM_CHAT_OPEN | 打開學習助理。 | 沒有 |
| ALM_CHAT_CLOSE | 學習助理關閉。 | 沒有 |
| ASK_AI_ASSISTANT_QUERY | 打開聊天視窗，向助理提交查詢。 | { 查詢：「問題文本」 } |

## 父應用程式中的事件處理需求

透過 iFrame 嵌入學習助理並不代表它是完全獨立的小工具。 家長申請必須積極聆聽外發事件並採取適當行動。 至少，您的申請應具備：

* 聆聽ALM_CHAT_REQUEST_CONFIG並回應ALM_CHAT_CONFIG讓助理能啟動。
* 處理ALM_CHAT_LO_REDIRECT：當學習者在助理回覆中點擊引用或來源時，你的應用程式會接收 loId、loType 和 instanceId，並負責引導學習者前往正確的課程或學習對象。
* 處理ALM_CHAT_URL_REDIRECT：當學習者點擊聊天訊息中的外部連結時，你的應用程式會接收該網址，並負責開啟或導覽（例如在新分頁中）。
* 可選擇性地追蹤 ALM_CHAT_OPENED / ALM_CHAT_CLOSED / ALM_CHAT_WAITING_FOR_REPLY，以反映助理的狀態（例如，當 isWaitingForReply 為真時顯示載入指示）。
* 可選擇使用 ALM_CHAT_OPEN / ALM_CHAT_CLOSE / ASK_AI_ASSISTANT_QUERY 來程式化控制助理。 例如，打開助理，從應用程式其他地方的說明&#x200B;**按鈕預先填寫查詢**。

## 需要幫忙嗎？

聯絡你的 Adobe 客戶成功經理，安排技術導覽。
