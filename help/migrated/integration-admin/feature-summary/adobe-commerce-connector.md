---
description: 學習如何整合 Adobe Commerce 連接器
jcr-language: en_us
title: Adobe Commerce 連接器
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 0%

---


# Adobe Learning Manager 中的 Adobe Commerce 連接器

## Adobe Commerce 連接器

>[!NOTE]
>
>此功能僅在 Adobe Learning Manager 作為 **Adobe Experience Manager 的附加元件** 銷售時使用。 連接器也可啟用試用&#x200B;**&#x200B;**&#x200B;帳號。

Adobe Learning Manager 與 Adobe Commerce 整合，後者是一個可擴充且可擴展的電子商務解決方案，讓您能為 B2B 及 B2C 客戶提供多通路商務體驗。 使用 Adobe Commerce 連接器將 Adobe Learning Manager 與 Adobe Commerce 連接，讓您的學習平台啟用付費培訓與電子商務功能。

啟用連結後，Learning Manager 會將培訓資料傳送至 Adobe Commerce，讓學習者能購買課程、學習路徑或認證。 連接器同時收集購買資訊以驗證交易，並讓學習者取得培訓。

## 先決條件

在設定 Adobe Commerce 連接器前，請先確認以下事項：

- 啟用 [RabbitMQ](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/start/overview) 或其他任何訊息代理。
- 啟用 [CRON](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/start/overview#cron_consumers_runner) 職缺。

要啟用這些檔案，請編輯以下檔案：

- .magento.app.yaml
- .magento/services.yaml
- .magento.env.yaml

其他設置需求：

- 自訂模組的覆蓋選項限制。 此步驟為可選，但建議用於大型資料集。
- 啟用所有 **非同步 API**。 大型訓練資料集則以非同步方式匯出。 當 Learning Manager 呼叫 Adobe Commerce API 時，請求會被排隊並由在商務端建立產品的消費者處理。 非同步處理必須啟用，因為 Adobe Commerce 預設不支援非同步處理。
- 在 Adobe Commerce 的付款成功頁面新增 **Learning Manager 的退貨連結** 。
   - 請使用此 [回傳網址](https://learningmanager.adobe.com/app/learner#/postPayment)：
- 將索引&#x200B;**從**&#x200B;**「**&#x200B;儲存中」改為&#x200B;**「排程」。**&#x200B;更多資訊請參閱 [知識庫](https://experienceleague.adobe.com/zh-hant/support?support-tab=home#home) 。
- 套用必要的 **補丁**。 請參閱 [「套用補丁」文件](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/start/overview) 中的說明。
- 在雲端基礎架構（暫存與生產環境）上設定 **Fastly** for Adobe Commerce。 更多資訊請參見[「設定快速」。](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)

## 設定連接器

要設定 Adobe Commerce 連接器：

1. 以整合管理員身份登入 Adobe Learning Manager。
2. 將滑鼠移到 **Adobe Commerce** 連接器圖塊上，選擇 **連接**。

   ![](assets/adobe-commerce-connector1.png)
   _選擇「連接」以設定 Adobe Commerce 連接器_

3. 請輸入以下細節：

   - 連接名稱
   - 存取令牌
   - Adobe Commerce 網址
   - 商店代碼
4. 請從以下介面類型中選擇：

   - 原生學習管理器
   - 使用 AEM 網站客製化製作

   ![](assets/adobe-commerce-connector2.png)
   _輸入 Adobe Commerce 設定所需的細節_

5. 選擇 **「連接**」。

## 為培訓設定價格

連線啟用後：

- 作者可以設定課程、學習路徑或證照的價格。
- 發表後，學習者可透過 Adobe Learning Manager 或自訂 AEM 網站購買培訓。

## 購買流程

### 原生 Adobe Learning Manager

- 學習者登入 Adobe Learning Manager 購買課程、學習路徑或證書。
- 當學習者點擊「立即購買」時，他們會被導向 Adobe Commerce 完成付款。
- 付款後，學習者會被提示返回 Adobe Learning Manager 開始訓練。
- 學習者必須另行登入 Adobe Commerce 以完成購買。
- 學習者會收到來自 Learning Manager 和 Adobe Commerce 的購買確認電子郵件。 Adobe Commerce 電子郵件可視需要啟用或停用。

### 自訂 AEM 網站

使用自訂 AEM 網站時：

- 學習者可透過 AEM 網站瀏覽並購買課程。
- AEM 網站使用與 Adobe Learning Manager 同步的元資料進行搜尋與顯示。
- 登入用戶和訪客用戶都能瀏覽。 不過，只有登入用戶才能購買。
- 登入後，學習者可以將課程加入購物車、預覽細節並完成購買。

## 匯出課程至 Adobe Commerce

### 排程匯出

排程匯出：

1. 選擇 **匯出訓練中繼資料** ，然後選擇 **設定排程**。
2. 選擇 **使用此連線**&#x200B;啟用訓練中繼資料匯出。
3. 選擇 **啟用排程** ，並設定 **開始日期**、 **時間**&#x200B;和 **間隔**。

   ![](assets/adobe-commerce-connector3.png)
   _啟用排程匯出_

4. 選擇 **儲存**。

### 按需出口

作者設定訓練價格後，整合管理員必須匯出訓練資料：

1. 選擇 **匯出訓練中繼資料** ，然後選擇 **隨選**。
2. 選擇日期範圍。
3. 選擇 **執行** 以匯出。

   ![](assets/adobe-commerce-connector4.png)
   _建立按需出口_

4. 成功後，付費課程與學習路徑會轉移至 Adobe Commerce 供購買。
