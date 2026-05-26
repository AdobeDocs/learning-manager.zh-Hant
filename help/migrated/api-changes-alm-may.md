---
description: ALM 中的 API 變更
jcr-language: en_us
title: 2026 年 5 月補丁版本中的 API 變更
source-git-commit: 24f54599749bce60916a57634144b0ca7f6a6d10
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# 2026 年 5 月補丁版本中的 API 變更

## GET /learningObjects API 增強功能

當實例關聯被包含時，GET /learningObjects API 現在會在 learningObjectInstance 資源中新增一個 startDate 屬性。

**終點**&#x200B;取得 /learningObjects/{id}？include=instances

**變化**&#x200B;新增了一個欄位 startDate，位於：包含[].屬性.起始日期

**描述** startDate 代表學習物件實例的排程開始日期與時間。

**範例** https://learningmanagerstage1.adobe.com/primeapi/v2/learningObjects/course:13209797？include=instances取樣響應（截斷）

```
{
  "id": "course:13209797_16226533",
  "type": "learningObjectInstance",
  "attributes": {
    "dateCreated": "2026-05-20T04:35:46.000Z",
    "isAET": false,
    "isDefault": true,
    "isFlexible": false,
    "startDate": "2026-10-06T18:29:59.000Z",
    "state": "Active",
    "timeZoneCode": "IST"
  }
}
```

**註釋**

* 該欄位僅在適用的學習物件實例中回傳。
* 該值以 ISO 8601 UTC 日期-時間格式回傳。
* 現有的整合仍向下相容。
