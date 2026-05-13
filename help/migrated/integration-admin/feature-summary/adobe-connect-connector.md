---
description: 學習如何將 Adobe Connect 連接器與 Adobe Learning Manager 整合
jcr-language: en_us
title: Adobe Connect 連接器
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%

---


# Adobe Learning Manager 中的 Adobe Connect 連接器

## 簡介

Adobe Learning Manager 與 Adobe Connect 整合，協助你提供並管理虛擬教室訓練。 透過此整合，您可以安排課程、使用持續或動態會議室、記錄出席、匯入測驗結果，並為學習者提供課程錄影。

## 設定 Adobe Connect

要設定 Adobe Connect：

1. 以整合管理員身份登入 Adobe Learning Manager。
2. 將滑鼠移到 **Adobe Connect** 圖塊上，選擇 **「連接**」。

   ![](assets/adobe-connect-connector1.png)
   _選擇 Connect 以設定 Adobe Connect 連接器_

3. 請輸入以下細節：

   - **連接名稱**
   - **Adobe Connect 網址**
   - **Connect 管理員電子郵件**
4. 輸入 **Connect 管理員登入 ID（若未使用 Adobe Connect 的電子郵件登入，則需輸入** ）。

   ![](assets/adobe-connect-connector2.png)
   _輸入 Adobe Connect 設定所需的細節_

5. 選擇 **啟用連接認證**。

   >[!NOTE]
   >
   >僅支援 Adobe 主機的 Connect 帳號。 （網域必須以 .adobeconnect.com 結尾）

6. 選擇 **「連接**」。

在你驗證管理員電子郵件 ID 之後：

- Adobe Learning Manager 會顯示成功訊息，確認 Connect 已整合。
- 申請會送交 Adobe Connect 後端團隊審核。 這通常需要一到兩天。

>[!IMPORTANT]
>
>Adobe Connect 帳號管理員首次登入時必須同意條款與條件。 若未完成此操作，登入認證可能會失敗。

## 新增虛擬教室課程資訊

若作者尚未提供虛擬教室課程的課程細節，管理員可新增：

1. 以管理員身份登入。
2. 選擇VC課程。
3. 選擇 **實例** ，然後選擇 **會話細節**。
4. 選擇 **編輯** 圖示以新增或更新會話資訊。

>[!NOTE]
>
>你的 Connect 帳號必須有足夠的會議室和容量，讓同時使用者能執行虛擬教室。 每次 Adobe Learning Manager 虛擬教室會話都會自動建立一個新的 Connect 會議室，除非你使用持久性會議室。

## 持續存在的會議室

Adobe Connect 支援持久會議室，且會議室可持續使用。

- 你可以在 Connect 裡利用現有的持續教室建立虛擬教室。
- 你也可以選擇讓 Adobe Learning Manager 為每個會話建立一個動態房間。

當學習者使用 Adobe Connect 參加課程時，會透過 Learning Manager 使用安全認證進入教室。

完成一場課程後，學習者可以在他們的學習管理軟體中存取課程錄影與密碼。

## 從 Adobe Connect 匯入測驗分數

Adobe Learning Manager 可以從 Adobe Connect 會議中匯入測驗資料，並與其他報告工作流程結合。 這包括測驗分數、學習者回應和完成度數據，例如自學模組的運作方式。

### Quiz 匯入工作流程

#### Adobe Connect（主機）

- Connect 主持人會建立課程並上傳包含互動測驗的內容。
- 主持人會設置虛擬教室（VC）訓練，並將課程連結到虛擬教室，或使用 **分享課程** 選項在課程中分享。

#### Adobe Learning Manager（作者）

- 作者會在 Adobe Learning Manager 建立一門課程，模組類型設定為 **虛擬教室**。
- 從 **會議系統** 下拉選單中，選擇 **「連線** 」作為虛擬客戶提供者。
- 在 Connect 中選擇 **由主持人建立的持續會議室** 。
- 指派一位講師，儲存並發佈課程內容。

#### Adobe Learning Manager（學習者）

- 學習者報名課程並加入 Connect VC 課程。
- Connect 主機允許學習者存取該工作階段。

### Adobe Connect（主機與學習者）

- 主持人會在場次中分享測驗。
- 學習者完成測驗後離開該場次。

### Adobe Learning Manager（同步與管理）

- 當課程結束時，Adobe Learning Manager 會自動同步測驗資料。
- 測驗匯入工作流程會在排定時長結束後開始。
- 要追蹤進度，整合管理員可以在 Adobe Connect 連接器中檢查 **執行狀態** 。
- 匯入完成後，狀態會更新為 **「完成**」。

管理員接著可以審查匯入的結果：

- **出席人數與計分：** 查看最終測驗分數與出席人數。
- **L2 測驗分數：**
   - **使用者說明：** 以點數和百分比顯示個人分數。
   - **題目：** 以報告表顯示測驗結果。
