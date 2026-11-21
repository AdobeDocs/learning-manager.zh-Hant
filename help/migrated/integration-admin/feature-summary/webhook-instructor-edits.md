---
description: 當講師編輯課程細節時，可於 Adobe Learning Manager 中取得 webhook 事件，並保持學習者通知及連接系統的最新狀態。
jcr-language: en_us
title: 接收用於講師課程編輯的 webhook 事件
exl-id: 6fa4b71b-a8f4-40a2-ab57-bb7f3016542c
source-git-commit: 90b45cb128b74ecb33a89bf42ef4d6e960101ff0
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%
---

# 講師編輯 LO 實例的 Webhook 事件

Adobe Learning Manager 提供 webhook 事件，當學習對象（LO）實例（例如講師主導課程的某個課程）被修改時，會通知外部系統。 過去，這些事件僅在管理員或作者修改 LO 實例時才會觸發。 現在，當講師編輯課程細節時，也會觸發 Webhook 事件。

您可以利用這些事件，讓外部系統（如電子郵件服務、行事曆、報告工具或分析平台）隨時掌握講師變動的最新狀態。 例如，您可以在課程時間變更時通知學習者。

講師編輯會使用現有的學習物件實例修改事件，因此不會引入新的事件類型。

>[!NOTE]
>
>講師編輯僅在啟用的 Webhook 訂閱學習物件實例修改事件時才會觸發 webhook。 了解如何 [作為整合管理員](/help/migrated/integration-admin/feature-summary/webhooks.md#create-manage-webhooks)建立和管理 webhook。

## 支援的講師編輯

當講師編輯以下任一課程細節時，會觸發 webhook 事件：

* 課程時間安排

* 製作人員

* 時區

* 場地

* 招生人數上限

* 候補名單上限

* 允許提交

## Webhook 有效載荷結構

每個 webhook 請求包含以下頂層結構：

```json
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "121da98-ab8d-43e9-b671-e79131cd69dc",
      "eventName": "LEARNING_OBJECT_INSTANCE_MODIFICATION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235603297000-040649-741781-0",
      "data": {
        "loInstanceId": "course:12324298_14453691",
        "loId": "course:12324298",
        "loType": "course"
      }
    }
  ]
}
```

無論誰修改 LO 實例，結構都會相同。 有效載荷並未顯示是講師、管理員或作者所做的變更。

當講師變更課程細節，例如時區、報名人數限制或等候名單限制時，webhook 會將此事件傳送至您的監聽者網址。 使用該事件取得最新的課程詳細資訊，並通知學習者或更新您的外部系統。

## 擷取更新後的工作階段詳細資訊

webhook 事件用來識別被修改的 LO 實例。 若要取得更新的會話詳細資訊，請使用 `loId` 活動中的 API 呼叫 Learning Manager 公開 API（Prime API）：

```http
GET /primeapi/v2/learningObjects/{loId}
```

找出回應中符合 `loInstanceId` 的實例，然後將其與系統中儲存的資料進行比對。

## 建立與 webhook 事件的整合

您可以利用這些 webhook 事件來：

* 當課程細節（如日期、時間、時區或場地變更）時，透過外部電子郵件或訊息服務發送學習者通知。

* 將會話資料與外部行事曆、報告或分析系統同步。

* 當課程的報名人數限制或等待名單限制變更時，追蹤容量變動。

* 透過記錄 `eventId`、 `timestamp`、 以及 `eventInfo` LO 與實例識別碼來維持稽核追蹤。

至少，你的 webhook 處理器應該：

* 驗證有效載荷並解析 `events[]`。

* 用於 `eventName` 識別學習物件實例修改事件。

* 使用 `loId` 和 `loInstanceId` 在系統中尋找對應的記錄，並呼叫公開 API 以取得目前的工作階段詳細資訊。

* 用於 `eventId` 防止同一事件多次傳送時產生重複處理。

同樣的事件也會被傳送給講師、管理員和作者所做的編輯，因此您的整合可能會比以往更頻繁地收到。 在發送通知之前，請將擷取的會話詳細資料與系統中的資料進行比較。 學習者僅在相關細節變更時才會收到通知。
