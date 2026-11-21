---
description: 了解講師與班級經理如何取得討論區活動的電子郵件摘要，以及如何使用 API 管理設定與訂閱者
jcr-language: en_us
title: 討論區講師通知
exl-id: 370c9add-5572-4555-8a95-ddb470c230f4
source-git-commit: 650ec8159a4291189dfc38b03701b7b96932233d
workflow-type: tm+mt
source-wordcount: '1231'
ht-degree: 0%
---

# 討論區講師通知

## 概觀

討論區講師通知會讓講師、班長和管理員收到他們所監控討論區近期活動的電子郵件摘要。 這對於同時管理多個班級並參加多個評審的講師來說很有幫助。

班長是負責管理一群學習者（即班級），這些學員會在同一個時間表上一起完成課程或計畫。

講師不必逐個開啟每個看板，而是會依照你設定的頻率，即時收到應用程式內提醒和電子郵件摘要，涵蓋他們所訂閱的看板。 您可以透過 [`boardSubscriptionSettings` API](api-changes-dec-2026.md#api-sequence) 及 [訂閱者 API](api-changes-dec-2026.md#api-get-subscribers) 管理看板訂閱與通知設定。

## 主要功能

* 您可以透過訂閱者 API（[`POST /boards/{id}/subscribers`](api-changes-dec-2026.md#api-subscribe-users)範圍 `admin:write`）訂閱活躍的 Adobe Learning Manager 使用者到指定的討論區。 當收到通知時，使用者必須能存取看板。
* 使用者會即時收到啟用事件類型的應用程式內通知，並依板塊分組的電子郵件摘要。 事件類型由 API](api-changes-dec-2026.md#api-sequence) 中的帳戶層級設定`notifyNewPost`（、、 `notifyComment`及 `notifyReply`）[`boardSubscriptionSettings`控制。
* 摘要視窗是將活動收集到單一摘要郵件中的期間。 你可以在帳戶層級設定，並搭配 `digestFrequencyHours` 屬性，從 1 到 168 小時（例如每日摘要為 24 小時）。 此規則適用於帳戶內所有使用者。
* 您可以依使用者 ID 或電子郵件地址訂閱使用者，也可以在同一次請求中新增多個使用者（[批量](api-changes-dec-2026.md#bulk-subscriptions)訂閱）。 使用者會先以一般方式在 Learning Manager 中建立。
* 摘要電子郵件會列出啟用事件類型的每篇新貼文、留言和回覆，並附上討論區名稱、作者姓名與電子郵件地址，以及直接連結。 它也會顯示自摘要期開始以來的更新統計。
* `boardSubscriptionSettings` API 與訂閱者 API 都是公開 API，因此您可以在沒有使用者介面的情況下管理設定與訂閱（API 驅動的整合）。

## 使用案例

以下使用案例說明講師通知如何提供協助：

| 使用情境 | 通知如何提供幫助 |
|---|---|
| 監控多個世代 | 負責多個學期的講師可從該學期相關委員會獲得活動摘要。 |
| 檢視學習者參與度 | Cohort Manager 可以監控新貢獻並識別活躍討論，而不必逐個檢視每個看板。 |
| 追蹤後續對話 | 摘要中的留言與回覆有助於講師辨識可能需要指導或管理的討論。 |

## 重要考量

* 當通知被發送時，使用者必須能夠存取看板。 存取權會在交付時再次檢查，而非僅在使用者訂閱時。 如果訂閱者失去對某個看板的存取權，訂閱會保留，但該看板的通知會被跳過。
* 摘要會以一封電子郵件形式發送，因此如果董事會忙碌，內容會變得非常長。 例如，約40名學習者的小組可在六小時內發表數百則留言。
* 如果你的討論區非常活躍，建議使用較短的摘要頻率，例如每六小時一次，這樣每封郵件都能輕鬆管理。 在 API](api-changes-dec-2026.md#api-create-settings) 中[`boardSubscriptionSettings`設定頻率`digestFrequencyHours`。
* 電子郵件摘要中的文章數量限制為每個摘要版每個版塊 20 篇。 同樣的上限也適用於每個版塊的留言（20）和回覆（20）數量。 只有顯示的清單會被截斷;標題/副標題的計數總是反映該視窗真實且未截斷的活動。
* 訂閱人數上限為每塊板 200 人。
* 由於內容是直接在電子郵件中傳送，而非附件，因此電子郵件內容也有大小限制。

## 訂閱模式、權限與資格

* 訂閱者是指接收看板通知的使用者。 董事會訂閱獨立於與論壇使用者的既有追蹤關係。
* 任何使用 OAuth 驗證並擁有 `admin:read` 和 `admin:write` 範圍的人，都可以使用訂閱設定和訂閱者的 API。 `admin:read` 允許您列出訂閱者並閱讀設定。 `admin:write` 讓您新增或移除訂閱者並變更設定。
* 您可以訂閱任何 Learning Manager 使用者，但該使用者必須存在、活躍且有權限存取看板才能接收通知。 當通知與摘要被傳送時，存取權會被重新檢查。
* 如果使用者失去存取權，該看板的傳送會被跳過，訂閱會被保留。 如果存取恢復，配送將恢復。
* 你可以在一次請求中新增多個使用者到看板（批量訂閱）。 如果使用者已經訂閱，請求仍會成功且不會產生重複請求。 請參閱 [批量訂閱](api-changes-dec-2026.md#bulk-subscriptions) 以了解請求格式、207 多重狀態回應及失敗案例。

## 摘要內容

### 包含的活動

摘要包含在 API](api-changes-dec-2026.md#api-create-settings)`notifyReply``notifyNewPost``notifyComment` 中符合匹配`true`[`boardSubscriptionSettings`設定時的新貼文、留言與回覆：、、 。你用 或 `PATCH /boardSubscriptionSettings`來設定這些。`POST`所有設定都是 `false` 預設的。

### 排除的事件

摘要會排除在 API](api-changes-dec-2026.md#api-create-settings) 中[`boardSubscriptionSettings`匹配設定為 `false`（例如 `notifyComment`）的事件。如果沒有符合資格的活動，則不會發送摘要。

### 摘要電子郵件版面範例

每個有符合資格活動的訂閱版塊都會寄出摘要電子郵件。 其結構如下：

* **摘要行：** 電子郵件開頭會列出看板上的總更新數（例如七次更新），並依類型分類（例如新貼文與留言），以及活動計算的時間點。
* **董事會區塊：** 活動依據董事會名稱分類。 每篇文章都列在下面。
* **商品詳情：** 每篇貼文、留言或回覆都會顯示創建該文章的使用者姓名與電子郵件地址，以及商品連結。
* **連結：** 點選連結即可直接開啟貼文、留言或回覆。 收件人必須登入，連結才會開啟。
* **留言與回覆：** 這些內容會與貼文同出現在同一封電子郵件中，讓講師能看到後續對話以及新的主題。

## 設定通知

### 使用 API 設定

您透過兩個公開 API 管理通知：[`boardSubscriptionSettings`](api-changes-dec-2026.md#api-sequence)API 適用於帳戶層級，以及[訂閱者 API](api-changes-dec-2026.md#api-get-subscribers)，適用於每個看板。兩者皆使用 OAuth 範圍 `admin:read` 與 `admin:write`。 請依照順序呼喚它們：

1. 使用 [`POST /boardSubscriptionSettings`](api-changes-dec-2026.md#api-create-settings)。
1. 稍後需要時可更改設定，使用 [`PATCH /boardSubscriptionSettings`](api-changes-dec-2026.md#api-update-settings)。
1. 使用 [`GET /boardSubscriptionSettings`](api-changes-dec-2026.md#api-get-settings)。
1. 以 為 列出訂閱該看板 [`GET /boards/{id}/subscribers`](api-changes-dec-2026.md#api-get-subscribers)的使用者。
1. 訂閱使用者加入一個包含 [`POST /boards/{id}/subscribers`](api-changes-dec-2026.md#api-subscribe-users). 的看板
1. 使用 [`DELETE /boards/{id}/subscribers/{userId}`](api-changes-dec-2026.md#api-unsubscribe-user).取消訂閱看板上的使用者

使用 `boardSubscriptionSettings` API 設定摘要的頻率（小時），並開啟或關閉摘要的貼文、留言和回覆。 例如，一個摘要頻率為 1 小時的帳戶，每小時會收到一封摘要電子郵件。 所有活動設定皆為 `false` 預設。

### 管理訂閱者

使用訂閱者 API 來選擇哪些活躍的 Learning Manager 使用者訂閱哪些看板。 訂閱與現有的董事會追蹤關係是分開的。 使用者必須能看到看板才能接收通知，這表示該使用者必須已登入。 失去可見性會抑制投遞，但不會移除訂閱。

### 啟用此功能

若要啟用講師通知，請建立帳戶層級設定，然後依 2026](api-changes-dec-2026.md) 年 11 月 API 變更中所述[，訂閱使用者至看板。之後，系統會收集在設定間隔內新建立的貼文、留言和回覆。 在該區間結束時，訂閱者會收到一份摘要通知，內容涵蓋已訂閱版面上符合資格的活動。

了解更多關於 2026](api-changes-dec-2026.md) 年 12 月的 API 變更[資訊。
