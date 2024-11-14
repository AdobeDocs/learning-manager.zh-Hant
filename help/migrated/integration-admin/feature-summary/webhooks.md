---
jcr-language: en_us
title: Webhooks
description: 瞭解Webhook以將即時資訊（例如課程註冊、課程建立和其他資訊）傳送至特定URL
contentowner: chandrum
exl-id: 472aaf2b-9c2f-4f43-a791-2b2d81e69471
source-git-commit: e4c3489db8207ead0416656161b918eba42f4582
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Webhooks

webhook可讓一個實體在特定事件發生時自動向另一個實體傳送即時資料或通知。 如此一來，應用程式便能在不持續要求資訊的情況下，為其他應用程式提供資訊。 例如，如果使用者完成學習管理系統(LMS)課程，webhook可以自動將該資訊傳送到另一個平台，例如CRM或報告工具。 Webhook通常用於整合中，以自動化流程並減少系統之間手動更新的需求。 提供您要傳送資料的回呼URL，以設定Webhook。

## Webhook與API

Webhook和API都有助於系統相互通訊，但它們的工作方式不同。 透過API，資訊僅在使用者請求時分享。 例如，如果學習者需要課程進度資料，他們會傳送請求至API，然後提供資訊。 另一方面，Webhook會在事件發生時自動立即傳送資料。 例如，若學習者完成課程，資料會立即傳送至接聽程式URL，無需手動要求。

## 什麼是即時API？

即時API可讓應用程式在事件發生時立即交換資料。 傳統API會等待使用者要求資訊，而即時API則會在事件發生時共用資料。 Webhook可作為即時API，每當指定事件發生時，都有助於立即共用資料。 即時API可確保此資料傳輸立即進行，而無需任何手動請求，這使得系統可即時保持更新。

## Webhook活動

Webhook事件是發生在系統中的特定動作，可自動將資料傳送至監聽器URL。 例如，當學習者註冊課程時，系統會觸發webhook事件，並將註冊詳細資料傳送至接聽程式URL。
Webhook活動分為兩個類別：

* **即時事件**：事件已處理並即時傳送至目標URL
* **非即時事件**：事件會以批次處理，並在指定時間傳送，而非即時傳送

## 監聽器URL

監聽器URL是在事件發生時接收資料資訊的端點或目的地。 每當發生特定事件（例如使用者註冊課程），系統就會自動將詳細資料傳送至此URL，無需任何手動要求。 監聽器URL是傳送所有這些更新的位址。
Webhook會以JSON格式傳送相關資訊。 以下是Adobe Learning Manager中觸發之事件的裝載範例：

```
{
  "accountId": 1010,
  "events": [
    {
      "eventId": "d5fb7071-10a9-46b2-9f9e-79dde346c052",
      "eventName": "COURSE_ENROLLMENT_BATCH",
      "timestamp": 1727414643000,
      "eventInfo": "1727414643000-047210-84242-0",
      "data": {
        "userId": 4279332,
        "loId": "course:7374992",
        "loInstanceId": "course:7376092_10250977",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": 1727414643
      }
    }
  ]
}
```

## 建立和管理Webhook — 整合管理員

請依照下列步驟，在Adobe Learning Manager中建立Webhooks整合：

1. 以&#x200B;**[!UICONTROL Integration Admin]**&#x200B;登入。
2. 在首頁上，選取&#x200B;**[!UICONTROL Webhooks]** > **[!UICONTROL Add Webhook]**。

   ![](assets/create-webhook.png)
   _新增webhook_

3. 輸入Webhook的&#x200B;**[!UICONTROL Name]**&#x200B;和&#x200B;**[!UICONTROL Description]**。
4. 輸入接聽程式URL作為您要傳遞事件資料的&#x200B;**[!UICONTROL Target URL]**。
5. 選取任一驗證方法：
Webhooks中的驗證是一種安全性方法，可確保傳送至接聽程式URL的資料來自信任的來源。
   * **[!UICONTROL None]**：不需要驗證。
   * **[!UICONTROL Basic]**：這是認證式驗證。 輸入使用者名稱和密碼。
   * **[!UICONTROL Signature]**：系統建立特殊簽章，並將其新增至webhook資料。 接收伺服器會檢查此程式碼，確認資料為真實資料，且未曾變更。 產生簽章並用於驗證。 將簽名下載為JSON。
6. 從&#x200B;**[!UICONTROL Trigger events]**&#x200B;下拉式清單中選取Webhook事件。

   >[!NOTE]
   >
   >您也可以從「新增Webhook」頁面選取「測試Webhook」選項來測試Webhook。

7. 選取&#x200B;**[!UICONTROL Activation Status]**&#x200B;切換以啟用webhook。 啟用後，每當選取的事件發生，就會傳遞資料。

>[!NOTE]
>
>您最多可以建立和管理5個Webhook。

### 編輯Webhook — 整合管理員

請依照下列步驟，從Adobe Learning Manager編輯Webhook：

1. 以&#x200B;**[!UICONTROL Integration Admin.]**&#x200B;身分登入
2. 在首頁上選取&#x200B;**[!UICONTROL Webhooks]**。
3. 選取您要編輯的webhook。

   ![](assets/edit-webhook.png)
   _編輯webhook_
4. 選取&#x200B;**[!UICONTROL Edit]**&#x200B;以修改webhook的詳細資料，並選取&#x200B;**[!UICONTROL Save]**。

### 移除Webhook — 整合管理員

請依照下列步驟，從Adobe Learning Manager編輯Webhook：

1. 以&#x200B;**[!UICONTROL Integration Admin]**&#x200B;登入。
2. 在首頁上選取&#x200B;**[!UICONTROL Webhooks]**。
3. 選取您要刪除的webhook。
4. 選取&#x200B;**[!UICONTROL Delete]**&#x200B;以移除webhook。

![](assets/delete-webhooks.png)
_移除webhook_

### 淘汰Webhook — 整合管理員

請依照下列步驟淘汰webhook：

1. 以&#x200B;**[!UICONTROL Integration Admin]**&#x200B;登入。
2. 在首頁上選取&#x200B;**[!UICONTROL Webhooks]**。
3. 選取您要編輯的webhook。
4. 選取&#x200B;**[!UICONTROL Edit]**&#x200B;並停用&#x200B;**[!UICONTROL Activation Status]**&#x200B;以停用webhook。

![](assets/retire-webhook.png)
_淘汰webhook_
