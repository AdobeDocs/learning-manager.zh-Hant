---
description: 在 Adobe Learning Manager 中建立 MCP 伺服器，連接至 Claude 或 ChatGPT，並管理憑證、工具、限制與故障排除
jcr-language: en_us
title: 設定 Adobe Learning Manager MCP 伺服器
exl-id: b5d2c08e-a11e-4f55-9ba5-a652a9575678
source-git-commit: 9d93dbeca8a0c6da5e75e935bbec1ff3476c0a6e
workflow-type: tm+mt
source-wordcount: '1908'
ht-degree: 0%
---

# 設定 Adobe Learning Manager MCP 伺服器

為您的組織設定一次模型情境協定（MCP）伺服器。 設定包含兩個部分：在 Learning Manager 中建立 MCP 伺服器，然後將其連接到您的 AI 助理。 之後，學習者透過 AI 助理登入 Learning Manager，即可使用 MCP 工具。

在開始之前，請確保：

* MCP 伺服器已為您的 Learning Manager 帳戶啟用。 請聯絡您的 Adobe 客戶成功經理或 Adobe 支援以啟用此功能。 在此之前，每個請求都會回傳 403 禁止。
* AI 助理管理員有權在該平台新增及設定連接器。

**先決條件：** 模型情境協定伺服器是一項基於後端旗標的功能，僅適用於終極等級帳號。

## 在 Learning Manager 中建立 MCP 伺服器

建立 MCP 伺服器會設定 OAuth 應用程式，並提供 MCP 伺服器 URL、用戶端 ID 及用戶端密碼。

1. 以整合管理員身份登入 Learning Manager。
2. 在導覽選單中，選擇 **MCP 伺服器**。
3. 在右上角，選取 **「建立**」。

   ![](assets/integration-admin-mcp1.png)

4. 在應用程式 **詳細資料** 頁面輸入下列內容，然後選擇 **「下一步**」：

   * **應用程式名稱：** 最多輸入 50 個字元，例如 ALM for Claude。 學習者在授權連線時會看到這個名稱，因此請選擇一個他們熟悉的名稱。
   * **重新導向網域：** 輸入每位 AI 助理的回撥網域，每行一個網域。 每條開頭都不要附上路徑。 此欄位為必填欄位。
   * **說明：** 最多輸入 150 個字元，例如，讓學習者使用 Claude 的 ALM。

5. 在 **工具設定** 頁面，檢視 AI 助理用來決定何時呼叫每個工具的工具與說明。 若要變更描述，請選擇 **「動作** （**...**）」\> **「編輯**」。 若要還原預設值，請選擇 **「重設**」。 然後選擇「 **下一步**」。
6. 在 **用戶端憑證** 頁面，複製 **MCP 伺服器 URL**、 **用戶端 ID** 及 **用戶端密碼**。 妥善保存。 你需要它們來連接你的 AI 助理。

MCP 伺服器始終具有學習者範圍，因此沒有可選擇的範圍。

為你打算連接的每個 AI 助理註冊網域。

| **AI 助理** | **將網域重新導向至註冊** | **完整回調 URL（參考）** |
|----|----|----|
| Claude | [https://claude.ai](https://claude.ai/) 和 [https://claude.com](https://claude.com/) | <https://claude.ai/api/mcp/auth_callback> |
| ChatGPT | [https://chatgpt.com](https://chatgpt.com/) | <https://chatgpt.com/connector/oauth/&lt;id>\>（ChatGPT 在設定時顯示 ID） |

註冊精確網域，例如 [https://chatgpt.com](https://chatgpt.com/)。 不要使用部分通配符，例如 [https://*chatgpt.com*](https://chatgpt.com)*，因為它們可能會匹配到無關的網域。 若要允許子網域，請使用全標籤通配符，例如* [*https://*.example.com](https：//.example.com)。

如果你列出所有 MCP 的轉址網域，一個 MCP 伺服器可以服務多個 AI 助理。 若要撤銷某位助理的存取權而不影響其他助理，請為每位助理建立獨立的 MCP 伺服器。 所有伺服器使用相同的 MCP 伺服器 URL。

您只需 MCP 伺服器 URL。 Claude 與 ChatGPT 會自動發現 Learning Manager OAuth 端點。 如需手動設定，請參閱 **Learning Manager MCP 伺服器**&#x200B;的 OAuth 端點。

## 連接 Claude Pro 或 Max

若這些步驟已與介面不符，請參閱 Claude 文件。

>[!NOTE]
>
>當客戶重新構圖並格式化answer_learning_content_question工具的回答時，對所提出問題的冗長程度也會有所改變。

1. 在 Claude 中，前往 **「自訂** \> **連接器**」。
2. 選取新增&#x200B;****（+），然後選擇&#x200B;**新增自訂連接器**。
3. 輸入連接器詳細資訊，然後選擇 **「繼續**」：

   * **名稱：** 輸入學習者熟悉的名稱，例如 Adobe Learning Manager。
   * **遠端 MCP 伺服器 URL：** 從用戶端認證頁面輸入 MCP 伺服器 URL，格式 [為 https://\[alm-host\]/v1/mcp](https://[alm-host]/v1/mcp)。

4. 在「驗證」下&#x200B;**，立即保持**「登入&#x200B;**」。** Claude 會讀取 Learning Manager OAuth 設定，並將符合的選項標記為 *偵測*&#x200B;到。
5. 在 OAuth 用戶端下&#x200B;**，選取**「使用您自己的 OAuth 用戶端&#x200B;**」。**&#x200B;貼上 **用戶端 ID** 與 **用戶端密鑰**。
6. 選擇 **新增**。 Claude 開啟 Learning Manager 登入頁面。 登入後，連接器會顯示為已連接。

>[!NOTE]
>
>Claude 將用戶端密鑰欄位標示為可選，但 Learning Manager 要求如此。 若將該欄位留空或輸入錯誤值，登入將失敗並出現「授權失敗」訊息。

## 連接 Claude 團隊或企業版

只有組織擁有者，或具有管理連接器角色的成員，才能新增該連接器。 成員永遠看不到用戶端 ID 或用戶端密鑰。

>[!NOTE]
>
>當客戶重新構圖並格式化answer_learning_content_question工具的回答時，對所提出問題的冗長程度也會有所改變。

1. 在 Claude 中，以組織擁有者或擁有管理連接器權限的成員身分登入。
2. 前往 **「組織設定** 」\ > **連接器**。
3. 選擇 **新增**，將滑鼠移至 **自訂**，然後選擇 **「網頁**」。
4. 輸入名稱與 MCP 伺服器 URL，然後依&#x200B;****&#x200B;照前述步驟第 4 和第 5 步驟設定驗證與 **OAuth 用戶端**。
5. 選擇 **新增**。

連接器現已可供您的組織使用。 每位成員選擇「 **連線** 」，並以自己的帳號登入 Learning Manager。

## 連接 ChatGPT 團隊或企業

>[!NOTE]
>
>當客戶重新構圖並格式化answer_learning_content_question工具的回答時，對所提出問題的冗長程度也會有所改變。

1. 以工作區擁有者或管理員身份登入 ChatGPT。
2. 在左側側邊欄，點選&#x200B;**「外掛程式」。**
3. 點選 **右上角的「新增** 」，然後選擇 **「建立 MCP 應用程式**」。
4. 在 **「新增外掛** 」視窗中，設定連線：

   * **名稱：** Adobe Learning Manager，或您的學習者認識您的學習平台名稱。
   * **連線：**&#x200B;保持伺服器 URL **選取，並輸入 [https://\[alm-host\]/v1**/mcp](https://[alm-host]/v1/mcp)
   * **驗證方式：** OAuth


     ![](assets/integration-administrator-mcp1.png)

5. 點選進 **階 OAuth 設定**。 ChatGPT 會自動發現 ALM OAuth 端點。
6. 在用戶端註冊中&#x200B;**，將註冊方法**&#x200B;設定&#x200B;**為**&#x200B;使用者定義 OAuth 用戶端&#x200B;**，然後輸入**&#x200B;步驟 1 中的 OAuth 用戶端 ID **與** OAuth 用戶端密鑰&#x200B;**。**
7. 請檢查 **此面板中顯示的回調 URL** 。 其網域<https://chatgpt.com>（）必須位於步驟 1 的 MCP 伺服器 **重新導向網域** 中。

   ![](/help/migrated/integration-admin/feature-summary/assets/integration-admin-mcp2.png)

**端點會自動被發現**

通常你不需要更改 OAuth 端點。 如果 ChatGPT 要求，請使用：Auth URL [https://\[alm-host\]/oauth/o/authorize](https://[alm-host]/oauth/o/authorize)、Token URL [https://\[alm-host\]/oauth/token](https://[alm-host]/oauth/token)、Registration URL empty、Resource [https://\[alm-host\]/v1/mcp](https://[alm-host]/v1/mcp)、scope learner:write。

1. 選擇&#x200B;**「我了解並想繼續」，然後點選**「建立&#x200B;****」。
1. 在「連線&#x200B;**」**&#x200B;視窗中，點選&#x200B;**「繼續**」並登入 ALM。視窗應顯示 *「已由您的管理員*&#x200B;核准」。
1. 將外掛提供給工作區中的目標使用者使用。

![](/help/migrated/integration-admin/feature-summary/assets/integration-admin-mcp3.png)

## 終端使用者驗證

當管理員完成 MCP 伺服器的設定後，學習者從其 AI 助理的連接器清單中新增 ALM 連接器，然後點擊 **「連線**」。 這會開啟 ALM 登入頁面。 登入（若帳號使用 SSO，則使用 SSO）並核准存取後，AI 助理會連結到學習者的 ALM 帳號。

## 輪換用戶端密鑰或撤銷存取權

你無法重新生成客戶端密鑰。 旋轉它的方法如下：

1. 依照本文前述所述建立新的 MCP 伺服器。
2. 用新的客戶端 ID 和客戶端秘密更新你的 AI 助理。
3. 在 **整合管理** \> **MCP 伺服器**&#x200B;中，為舊伺服器選擇 **「動作** 」（**...**）\> **刪除** 。

學習者在切換後必須重新登入。

若要為所有學習者斷開 AI 助理的連線，請從同一頁面刪除其 MCP 伺服器。

## 可用工具

MCP 伺服器會提供下列工具。 所有這些程式都以已登入學習者的權限執行。

<table style="width:100%;">
<colgroup>
<col style="width: 46%" />
<col style="width: 31%" />
<col style="width: 21%" />
</colgroup>
<thead>
<tr>
<th><strong>工具</strong></th>
<th><strong>它的功能</strong></th>
<th><strong>範例提示</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td>僅限search_learning_itemsread</td>
<td>在目錄中搜尋課程、學習路徑、認證、工作輔助工具、徽章、技能、目錄及標籤。 篩選條件：類型、學習者狀態、技能、標籤、目錄、交付格式、價格及語言。 每頁最多回傳 10 個結果。</td>
<td>「初學者 Python 課程」<br />「免費法語課堂訓練」</td>
</tr>
<tr>
<td>僅限list_my_learning_enrollmentsread</td>
<td>列出學員已註冊、進行中及已完成的學習，並附有狀態、進度及截止日期。 最近一次則預設優先註冊。</td>
<td>「我報名的是什麼？」<br />
「什麼快到期了？」<br />
「我完成的訓練」</td>
</tr>
<tr>
<td>僅限get_learning_objectread</td>
<td>依 ID 取得課程、學習路徑、認證或工作輔助的完整細節，並可選擇性包含實例、技能及子項目。</td>
<td>「告訴我更多關於第二道菜的事。」</td>
</tr>
<tr>
<td>僅限get_my_learning_profileread</td>
<td>取得學習者的 ALM 設定檔，包括帳戶與經理。</td>
<td>「我在 ALM 的經理是誰？」</td>
</tr>
<tr>
<td>answer_learning_content_questionuses AI 製作團隊</td>
<td>使用 ALM 學習助理回答有關課程主題的問題，並以課程內容為基礎並附有引用。 回傳助理用於後續問題的對話 ID。</td>
<td>「解釋我的網路課程中涵蓋的 TCP 與 UDP 的差異」</td>
</tr>
<tr>
<td>personalized_learning_path</td>
<td>在 Adobe Learning Manager 中提供依學習者目標、主題及學習需求量身打造的個人化學習路徑。 支援產生課程推薦、將所選學習路徑儲存至學習者帳戶、列出學習者已儲存的學習路徑（動作清單），以及透過該儲存路徑的 id（動作詳細資訊）取得該路徑的詳細資訊與課程。 協助學習者識別與技能發展及達成學習目標相關的學習內容。</td>
<td>「將所選學習路徑儲存到我的帳戶。」</td>
</tr>
</tbody>
</table>

透過 answer_learning_content_question 開始的對話會顯示在 Learner AI 對話報告中，與 ALM 學習助理中的對話相同。

## 限制

| **限制** | **價值** |
|----|----|
| 每頁結果（搜尋與報名） | 最多10個。 使用回傳的游標以顯示更多頁面。 |
| answer_learning_content_question 利率 | 每位學習者每分鐘 10 個請求（最多 5 次），同時最多可進行 2 件 |
| 支援的 MCP 協定版本 | 2025-11-25, 2025-06-18, 2025-03-26 |
| 交通 | 可串流 HTTP，無狀態（僅 POST;無伺服器傳送事件串流） |

## **OAuth 端點參考**

Claude 和 ChatGPT 會自動發現這些。 這些資料是為需要手動輸入的客戶或代理人列出的。 將 \[alm-host\] 替換為您的 MCP 伺服器 URL 中的主機（您的區域主機或 ALM 自訂網域）。

| **價值** | **網址** |
|----|----|
| MCP 伺服器 URL | [https://\[alm-host\]/v1/mcp](https://[alm-host]/v1/mcp) |
| 授權網址 | [https://\[alm-host\]/oauth/o/authorize](https://[alm-host]/oauth/o/authorize) |
| 權杖 URL | [https://\[alm-host\]/oauth/token](https://[alm-host]/oauth/token) |
| 重新整理網址 | [https://\[alm-host\]/oauth/token/refresh](https://[alm-host]/oauth/token/refresh) |
| 授權伺服器基底 | [https://\[alm-host](https://[alm-host])\] |
| 資源 | [https://\[alm-host\]/v1/mcp](https://[alm-host]/v1/mcp) |
| 範圍 | 學習者:write |

## 疑難排解

| **症狀** | **原因與修復** |
|----|----|
| 登入期間未註冊的重新導向 | AI 助理的回調網域不在應用程式的 **重新導向網域中**。 新增它（例如）， <https://claude.ai>然後再試一次。 |
| 登入成功後，助理說授權失敗（客戶端無效） | 助理中輸入的用戶端密鑰與應用程式不符。 再從 ALM 複製一次，檢查有沒有空格，然後重新連線。 |
| 所有請求都會返回 403 禁止 | 您的帳戶尚未啟用 MCP 伺服器。 聯絡 Adobe 支援。 |
| 以錯誤的 ALM 使用者連線 | 瀏覽器已經有 ALM 會話。 斷開連線，登出 ALM（或使用私人視窗），然後重新連線。 |
| Q&amp;A 工具中的「速率上限已超過」 | 學習者超過了問答速率上限。 等一下再試一次。 |
| 助理要求再次登入 | 學習者的代幣已過期或被撤銷。 再次點擊 **「連線** 」。 |

## 常見問題

### **學習者可以在沒有管理員設定的情況下使用 MCP 伺服器嗎？**

沒有。 整合管理員必須在 ALM 中建立 MCP 伺服器（步驟 1），因為 MCP 伺服器不支援動態用戶端註冊。

### **我們可以使用自己的網域嗎？**

是的。 如果您的 ALM 帳戶有自訂網域，請在所有網址中將其取代 \[alm-host\]。

### **哪些 ALM 角色可以使用 MCP 伺服器？**

任何 ALM 使用者都可以連線。 這些工具會在學習者情境中運作，而 ALM 自身的權限檢查會套用到每一個請求。
