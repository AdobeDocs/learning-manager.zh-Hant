---
description: 將 Adobe Learning Manager MCP 伺服器新增至您的企業 AI 用戶端，例如 Claude 或 ChatGPT Enterprise，讓學習者能連接它
jcr-language: en_us
title: 將 Adobe Learning Manager 新增至您的企業 AI 客戶端
exl-id: d893efb7-dc0d-4a3a-88d6-b315340e5daa
source-git-commit: 05691364449234a4782e2de5d4752c7b277f5fd4
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%
---

# 將 Adobe Learning Manager 新增至您的企業 AI 客戶端

你需要在 AI 客戶端擁有管理員權限。 請先從您的 Adobe Learning Manager 管理員取得 MCP 端點 URL、用戶端 ID 及祕密金鑰。 請參閱 **「設定模型情境協定伺服器** 」以取得更多詳細資訊。

## 新增連接器

1. 以管理員身分登入您的企業 AI 用戶端。
2. 開啟連接器的管理員設定。
3. 新增一個使用模型上下文協定的自訂連接器。
4. 輸入 Adobe Learning Manager MCP 端點網址。
5. 輸入客戶 ID 以及您 Adobe Learning Manager 管理員提供的密鑰。
6. 儲存連接器。
7. 讓您的學習者能使用連接器。

>[!NOTE]
>
>AI 客戶端介面經常變動。 如果這些步驟與您的客戶端不符，請參閱您 AI 客戶端供應商關於新增遠端連接器的文件。

## 疑難排解

**學習者看不到這個連結點。** 確認該連接器已為學習者的工作區或群組啟用。

**當學習者選擇「連線」時，授權會失敗。** 檢查用戶端 ID 與秘密金鑰是否與 Adobe Learning Manager 伺服器中用戶端憑證&#x200B;**頁面上的**&#x200B;數值相符。
