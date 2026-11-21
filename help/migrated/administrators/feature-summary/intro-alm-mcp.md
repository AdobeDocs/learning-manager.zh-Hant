---
description: 讓學習者在 Claude、ChatGPT Enterprise 及自訂代理程式中，探索課程、追蹤進度，並從 Adobe Learning Manager 內容中獲得答案。
jcr-language: en_us
title: Adobe Learning Manager 模型情境協定伺服器
exl-id: 8d0a25a6-1301-4f68-8db7-e3b1d3ff6537
source-git-commit: 05691364449234a4782e2de5d4752c7b277f5fd4
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 0%
---

# Adobe Learning Manager 模型情境協定伺服器

## 概觀

模型情境協定（MCP）是 AI 用戶端連接工具的標準方式。 Adobe Learning Manager MCP 伺服器將學習帶到學習者已工作的地方。 它將 Adobe Learning Manager 學習工具開放給任何支援 MCP 的 AI 客戶端，例如客製化企業代理、Claude 或 ChatGPT。 學習者可在同一客戶端存取訓練內容與進度，內容則保留在 Adobe Learning Manager 中。

## 學習者能力

學習者在他們已經使用的 AI 客戶端中，以自然語言進行工作。 客戶會解讀每個請求，呼叫適當的 Adobe Learning Manager 學習者工具，並根據該學習者能存取的內容回傳回應。 學習者可以：

* 了解他們可參加的課程、認證與學習路徑。
* 追蹤他們的報名進度、進度與截止日期，包括即將到期的資訊。
* 在學習內容中獲得有根基的答案。
* 根據他們的目標生成個人化的學習路徑，並儲存下來。
完整清單請參閱 **學習工具參考**。

AI 用戶端呼叫 MCP 伺服器，MCP 會將每個請求導向匹配的學習者工具。

完整清單請參閱 **學習工具參考**。

## 客戶與合作夥伴教育

客戶與合作夥伴教育是 MCP 伺服器的主要用途之一。 自行打造企業 AI 代理的組織，可以將這些代理程式與 Adobe Learning Manager 學習者工具連結。 他們的客戶與合作夥伴則可在他們已使用的助理中學習，無需切換到獨立的學習助理。

例如，Acme Inc. 自行打造企業級 AI 助理。 Acme Inc. 的一位合作夥伴造訪 Lenovo 的環境，以了解 Lenovo 的產品。 Acme 的助理透過 MCP 伺服器連接其 Adobe Learning Manager 帳戶並回傳與學習相關的回應，確保合作夥伴永遠不會離開 Acme 體驗。

這種方法讓組織能夠：

* 在合作夥伴現有的 AI 經驗中提供學習。
* 讓客製化企業代理使用 Adobe Learning Manager 學習者工具。
* 把學習融入他們自己的工作流程中。
* 將學習與企業級 AI 生態系統整合。

## 員工教育

已經使用 AI 客戶端（例如 Claude）的員工，也能在那裡取得學習資訊。 例如，員工可以檢查分配的學習、檢視報名、尋找主題課程或要求學習路徑，而無需切換到 Adobe Learning Manager。 如需範例請求，請參閱 [學習者](https://word-edit.officeapps.live.com/docs/sample-prompts-adobe-learning-manager-learners)範例提示。

這種做法讓員工能夠：

* 繼續使用他們已經使用的工具。
* 無論他們在哪裡工作，都能觸及他們的學習。
* 使用任何支援 MCP 的 AI 客戶端作為進入 Adobe Learning Manager 的切入點。
* 在不改變情境的情況下獲取學習資訊。

## 同時支援兩種受眾的同一伺服器

客戶與合作夥伴教育與員工教育使用相同的學習工具與伺服器。 只有觀眾會改變。 選擇最適合你學習者的方式。

| **客群** | **範例** | **學習者工作地點** |
|----|----|----|
| 外部 | 客戶與合作夥伴 | 您組織自有的企業 AI 代理 |
| 內部 | 員工 | 企業級 AI 客戶端，例如 Claude 或 ChatGPT Enterprise |

## 設定角色

遊戲分為三個角色。

* **管理員：** 在 Adobe Learning Manager 中建立 MCP 用戶端應用程式並加以管理。 請參閱設定 [MCP 伺服器](https://word-edit.officeapps.live.com/docs/configure-model-context-protocol-server-adobe-learning-manager)。
* **AI 用戶端管理員：** 將伺服器新增至組織的企業 AI 用戶端，例如 Claude 或 ChatGPT Enterprise。
* **學習者：** 在 AI 用戶端選擇 **Connect** ，驗證連線並提供其 Adobe Learning Manager 帳戶資料。

## 學習者請求的安全性

每位學習者都會驗證連線並提供其 Adobe Learning Manager 帳戶資料。 請求以該學習者身份執行，因此 AI 用戶端只會回傳學習者在 Adobe Learning Manager 中能存取的資訊。 伺服器不給學習者額外存取權限。

## 本次更新中 MCP 的限制

* 工具的可用性取決於你的 AI 客戶端支援什麼。
* 每個請求都視為全新請求。 多回合對話只有在你的 AI 客戶端能保持對話上下文時才有效。
