---
description: 將 Adobe Learning Manager 伺服器加入您自己的 Claude 帳戶，作為自訂連接器，登入並詢問您的學習情況
jcr-language: en_us
title: 將 Adobe Learning Manager 加入 Claude 作為學習者
exl-id: 31c00b29-4919-48b7-9993-ed3ac358ba5e
source-git-commit: 05691364449234a4782e2de5d4752c7b277f5fd4
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%
---

# 將 Adobe Learning Manager 加入 Claude 作為學習者

僅當您的組織尚未為您新增連接器時，才使用這些步驟。 如果您在 Claude 中看到 Adobe Learning Manager 連接器，請選擇 **「連線** 」。

## 在 Claude 中新增連接器

1. 在 Claude 中，前往 **「自訂** \> **連接器**」。
2. 選取新增&#x200B;**&#x200B;**（**+**），然後選擇&#x200B;**新增自訂連接器**。
3. 輸入 **名稱**，例如 Adobe Learning Manager。
4. 在遠端 MCP 伺服器 URL **中**&#x200B;輸入 MCP 端點 URL。
5. 選擇 **「繼續**」。
6. 在「驗證」下&#x200B;**，立即保持**「登入&#x200B;**」。**
7. 在 OAuth 用戶端下&#x200B;**，選取**「使用您自己的 OAuth 用戶端&#x200B;**」。**
8. 在 Client ID **中**&#x200B;輸入用戶端 ID。
9. 在用戶端密碼&#x200B;**中輸入秘密金鑰**。
10. 選擇 **新增**。
11. 登入頁面開啟時，請登入 Adobe Learning Manager。

登入後，連接器會顯示為已連接。 問一個關於你學習的問題。 如需點子，請參閱 **學習者**&#x200B;範例提示。

>[!IMPORTANT]
>
>Claude 將用戶端密鑰欄位標示為選填，但 Adobe Learning Manager 要求如此。 若將該欄位留空或輸入錯誤值，登入將失敗並出現「授權失敗」訊息。

>[!NOTE]
>
>您的請求會依照您自己的權限執行。 Claude 只能看到您在 Adobe Learning Manager 中所能看到的內容。

## 使用不同的 Adobe Learning Manager 帳戶

如果您的瀏覽器已有啟用的 Adobe Learning Manager 工作階段，Claude 會在不要求輸入憑證的情況下連接到該帳戶。 若要以不同使用者身分連線，請先登出 Adobe Learning Manager，或使用私人瀏覽器視窗。

## 其他 AI 客戶端

對於 ChatGPT 或其他客戶端，步驟有所不同。 請參閱您 AI 用戶端的文件，了解如何新增自訂連接器，並使用管理員提供的相同三個數值。

## 疑難排解

**登入顯示未註冊的重新導向訊息。** 您的管理員必須將 Claude 網域新增至 **伺服器的重新導向網域** 。 請您的管理員新增 <https://claude.ai>，然後再試一次。

**Claude說授權失敗了。** 檢查祕密金鑰是否有多餘空格或錯誤的值。 請再次從管理員複製，移除連接器，然後重新新增。

**你連線時用錯了使用者。** 斷開連接器，登出 Adobe Learning Manager，然後在私人瀏覽器視窗中重新連線。

**Claude 請你再簽一次。** 您的工作階段已過期，或您的存取權限已被撤銷。 選擇「 **連線** 」以再次登入。
