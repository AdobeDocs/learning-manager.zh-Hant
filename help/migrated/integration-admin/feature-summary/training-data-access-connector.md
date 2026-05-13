---
description: 了解如何將 Training Data Access 連接器整合到 Adobe Learning Manager
jcr-language: en_us
title: 訓練資料存取連接器
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 0%

---


# Adobe Learning Manager 中的訓練資料存取連接器

## 簡介

**訓練資料存取連接器**&#x200B;允許你建立無頭學習體驗，可獨立使用或整合於使用 **Adobe Experience Manager （AEM） 網站**&#x200B;的自訂介面中。此連接器協助你檢索並顯示最新的培訓內容給學習者，具備搜尋與篩選功能。

>[!IMPORTANT]
>
>- 此功能僅在 Adobe Learning Manager 作為 **Adobe Experience Manager 的附加元件** 銷售時使用。
>- 透過此連接器檢索的課程資料每 24 小時更新一次
>- 此連接器並非用於建立無頭或基於 AEM 的非登入體驗的自助式。 請聯絡 Adobe，為您的使用情境規劃合適的方案。

## 運作原理

啟用連結後，Adobe Learning Manager 會公開一組公開 API，提供訓練中繼資料，如課程、學習路徑與證書。 你可以利用這些 API 建立一個客製化、品牌化的前端，顯示訓練內容並支援搜尋與篩選功能。

## 設定訓練資料存取連接器

你可以將 Adobe Learning Manager 整合到資料儲存與搜尋系統，將訓練中繼資料推送到 AEM 網站或其他無頭體驗。

要設定連接器：

1. 以整合管理員身份登入 Adobe Learning Manager。
2. 將滑鼠移到 **訓練資料存取** 圖塊上，選擇 **連接**。

   ![](assets/training-data-access-connector1.png)
   _選擇 Connect 以設定訓練資料存取連接器_

3. 輸入 A **連接名稱**。
4. 選擇 **介面**&#x200B;類型：

   - **原生學習管理器**：標準登入體驗，預設可用。
   - **Headless 介面**：Premium 選項，提供公開 API，提供未登入且無頭的前端。

   ![](assets/training-data-access-connector2.png)
   _輸入訓練資料存取連接器配置所需的細節_

5. 選擇 **「連接**」。 Adobe Learning Manager 會 **自動產生基礎網址** 和 **CDN 網址** 。 你會在自訂網站或應用程式中使用這些網址來取得訓練資料。

>[!NOTE]
>
>使用高級方案的客戶會獲得與標準客戶不同的 API URL。

## 匯出訓練元資料

要匯出訓練元資料：

1. 在連接器頁面選擇 **匯出訓練元資料** 。
2. 選擇 **啟用訓練中繼資料匯出，使用此連線** 開始將您的訓練資料推送至搜尋與檢索系統。
3. 選擇 **啟用排程** ，並設定開始日期、時間和間隔。

   ![](assets/training-data-access-connector3.png)
   _訓練元資料排程匯出_

4. 選擇 **儲存**。

   - 這會自動將所有課程、學習路徑及憑證映像檔上傳至 CDN **。**
   - 它也會將相關的元資料匯出到你的搜尋系統。

### 按需出口

- **隨需執行匯出：**&#x200B;到隨選&#x200B;**模式，設定**&#x200B;開始日期&#x200B;**，選擇**&#x200B;執行&#x200B;**以在需要時**&#x200B;執行匯出。
- **檢查執行狀態：** 在 **執行狀態** 頁面查看匯出進度與歷史。

## 在 AEM 中建立並發布網站

要在無頭或基於 AEM Sites 的網站上顯示訓練資料：

1. **從 Adobe 的 GitHub 倉庫[&#128279;](https://github.com/adobe/adobe-learning-manager-reference-site/releases/tag/1.0.0)安裝 AEM 套件**（前置條件）。
2. 在 AEM 中，請使用 **基礎 URL**、 **CDN URL**、 **用戶端 ID**、 **用戶端秘密**&#x200B;和 **管理員刷新令牌** 來建立設定。
3. 使用 AEM 元件來建置網站。
4. 為學習者發布網站。
5. 完整設定細節請參閱 [本文](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/aem-sites/adobe-learning-manager-integration-aem) 及 [本文](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/aem-sites/integrate-aem-learning-manager)。

### 學習者體驗

網站上線後：

- 網站會顯示所有 **透過搜尋系統從 Adobe Learning Manager 取得的課程**、 **學習路徑**&#x200B;與 **證書** 。
- 未登入&#x200B;**的學習者**&#x200B;可瀏覽並查看課程詳情。
- 當學習者點擊註冊課程、學習路徑或證書時，系統會提示他們登入&#x200B;**&#x200B;**&#x200B;以完成註冊並開始訓練。

## 未登入體驗

未登入體驗讓你能為未登入用戶創造即時體驗。 例如，未登入體驗作為行銷活動的登陸頁，鼓勵用戶註冊。

Adobe Learning Manager 中的未登入體驗可透過 **訓練資料存取** 連接器進行設定。 該連接器提供以下服務：

- 標準發行
- 高級服務

### 標準發行

標準方案是建置原生版本的 Adobe Learning Manager。 使用者可以建立僅示範、非登入的 headless 體驗。 示範 Headless 經驗無法擴展，且不應用於生產環境。

### 高級服務

此高級方案協助使用者建立無頭介面，該介面由 **訓練資料存取** 連接器設定。 這讓使用者能即時取得課程與學習路徑的詳細資訊，如名稱、描述、作者、技能、時長等。在混合式學習情境中，你還會看到即時的名額限制、已佔名額、候補名單限制和候補名單數量。 客戶可利用這些 API 建立搜尋與篩選功能，並為未登入學習者提供完整的課程摘要。

客戶可以購買高級方案，打造這種高度可擴展的非登入體驗。

>[!NOTE]
>
>請聯絡客服團隊或客服經理購買高級方案。

用戶購買方案後，CSM 團隊會為他們啟用高級方案。 透過訓練資料存取連接器，使用者可以設定未登入的體驗，並使用上述功能。
