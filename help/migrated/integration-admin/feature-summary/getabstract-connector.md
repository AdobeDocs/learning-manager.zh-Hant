---
description: Adobe Learning Manager 中的 getAbstract connector
jcr-language: en_us
title: getAbstract connector
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---


# getAbstract connector for Adobe Learning Manager

## 簡介

**getAbstract 連接器**&#x200B;是為企業客戶[設計的 getAbstract.com](https://www.getabstract.com/)。它讓學習者能直接透過 Adobe Learning Manager 發現並使用 getAbstract 內容。 該連接器也允許管理員匯入使用者參與資料並自動追蹤學習者完成紀錄。

Adobe Learning Manager 希望為學習者提供持續且自我導向的學習機會，專注於領導力與軟實力。 管理員不需自行開發所有內容，而是透過 getAbstract 連接器將組織的 getAbstract 帳號連結至 Adobe Learning Manager。

- 會自動將 getAbstract 內容匯入 Adobe Learning Manager。
- 追蹤學習者對課程與學習路徑的使用情況。

本文說明了在 Adobe Learning Manager 中設定和管理 getAbstract 連接器的步驟。

## 先決條件

- 在設定連接器前，請確保&#x200B;**&#x200B;**&#x200B;您的帳戶已啟用遷移功能。
- 請從你的 getAbstract 帳戶代表那裡取得&#x200B;**客戶 ID** 和&#x200B;**客戶秘密。**&#x200B;這些憑證是取得課程元資料和使用者使用資料所必需的。

## 設定 getAbstract 連接器

getAbstract 連接器讓 Adobe Learning Manager 管理員能透過整合 getAbstract 中高品質且精心策劃的內容，提升學習體驗。

要設定 getAbstract 連接器：

1. 以整合管理員身份登入。
2. 在首頁選擇 **getAbstract** 。
3. 請從連接器圖塊上的&#x200B;**&#x200B;**&#x200B;以下選項中選擇：

   - **入門**&#x200B;指南：連接器概述。
   - **連結**：建立新的連結。
   - **管理連線：檢視**&#x200B;或修改現有連線。

   ![](assets/getabstract-connector1.png)
   _getAbstract tile 顯示三個配置選項_

## 建立新的連結

建立新的連結：

1. 選擇 **「連接**」。

   ![](assets/getabstract-connector2.png)
   _在 getAbstract 圖塊上選擇「連接」以建立新連線_

2. 輸入 A **連接名稱**。
3. 輸入 **客戶端 ID** 和 **客戶端秘密**。

   ![](assets/getabstract-connector3.png)
   _請在 getAbstract connection 頁面輸入連線、用戶端 ID 和用戶端秘密_

4. 選擇 **儲存** 以建立連線。

## Manage getAbstract connector

在匯入資料前，您必須先設定連接器並設定同步排程。 設定完成後，連接器會自動拉取使用資料，讓你能監控學習者進度，並將 getAbstract 內容納入學習計畫與報告中。

### 啟用連線

啟用連線：

1. 在 getAbstract 圖塊上選擇&#x200B;**「管理連線**&#x200B;**」。**

   ![](assets/getabstract-connector4.png)
   _管理連線以設定和排程資料匯入_

2. 選擇連線。
3. 在左側導覽窗格選擇 **「配置** 」。
4. 選擇 **啟用連線** ，然後選擇 **儲存**。

   ![](assets/getabstract-connector5.png)
   _啟用連線，將 getAbstract 的資料匯入 Adobe Learning Manager_

### 編輯連結

補充連結：

1. 在 getAbstract 圖塊上選擇&#x200B;**「管理連線**&#x200B;**」。**
2. 選擇連線。
3. 在左側導覽窗格選擇 **「配置** 」。
4. 選擇&#x200B;**編輯以更新**&#x200B;客戶端 ID **和**&#x200B;客戶端秘密&#x200B;**&#x200B;**。

   ![](assets/getabstract-connector6.png)
   _編輯憑證，包括客戶端 ID 和客戶端秘密_

5. 選擇 **儲存**。

### 排程同步

要排程同步：

1. 在 getAbstract 圖塊上選擇&#x200B;**「管理連線**&#x200B;**」。**
2. 選擇連線。
3. 在左側導覽窗格選擇 **「配置** 」。
4. 在排程同步區塊中選擇&#x200B;**啟用排程**&#x200B;**。**

   ![](assets/getabstract-connector7.png)
   _排程從 getAbstract 匯入資料到 Adobe Learning Manager_

5. 請選擇UTC的開始日期和時間。
6. 輸入同步應該重複的天數。
7. 選擇 **儲存**。

同步設定已經被保存下來。 連接器會在排程中執行，並將 getAbstract 的資料匯入 Adobe Learning Manager。

## 按需同步執行

**按需同步**&#x200B;選項允許你手動將 getAbstract 的資料匯入 Adobe Learning Manager。當你想立即更新學習者的活動資料，而不必等待下一次排程同步時，這非常有用。

要執行隨選資料匯入：

1. 在 getAbstract 圖塊上選擇&#x200B;**「管理連線**&#x200B;**」。**
2. 選擇連線。
3. 從左側窗格選擇 **「隨選執行** 」。
4. 選擇 **開始日期**。

   ![](assets/getabstract-connector8.png)
   _執行按需請求，立即從 getAbstract 匯入資料到 Adobe Learning Manager_

5. 請選擇以下選項之一：

   - **執行**&#x200B;時關閉 Adobe Learning Manager 存取權：若同步可能導致停機，建議使用。
   - **在執行**&#x200B;時啟用 Adobe Learning Manager 存取：建議以避免服務中斷。
6. 選擇 **執行** 以匯入從開始日期到現在的所有資料。

### 查看執行歷史

**執行狀態**&#x200B;頁面會依序列出所有同步執行。若執行有錯誤，則會顯示警告圖示。 你可以查看錯誤日誌，修正 CSV 檔案，必要時再重新執行最新的同步。

查看執行歷史：

1. 在左側窗格選擇 **執行狀態** 。
2. 你可以看到以下欄位：
   - **跑**
   - **開始日期**
   - **持續時間**
   - **類型** （排程或隨選）
   - **狀態** （進行中或完成）

   ![](assets/getabstract-connector9.png)
   _查看按需及排程匯入的執行狀態_

>[!NOTE]
>
>如果你刪除並重新建立連線，之前執行的歷史仍會顯示。 你只能重新執行最新的同步。

### 成功同步的要求

為確保同步正確運作：

- 有效的使用者訂閱檔案必須位於 getAbstract FTP 資料夾中，以符合指定的同步日期。
- 檔案應遵循以下命名格式：
   - report_export_yyyy_MM_dd_HHmmss.xlsx或，
   - report_export_yyyy_MM_dd.xlsx

下載 [範例 getAbstract 用戶訂閱檔](https://experienceleague.adobe.com/docs/learning-manager/assets/report-export-20170401175342.xlsx?lang=zh-Hant) 以了解格式。
