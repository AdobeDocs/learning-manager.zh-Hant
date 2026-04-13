---
description: 閱讀本文了解如何在學習管理員中建立和管理同儕帳號。
jcr-language: en_us
title: 同儕帳號
contentowner: shhivkum
exl-id: 251d0eeb-f5e8-4f70-a36c-dcecb4834042
source-git-commit: 2604dc206de5f6e883c1073880348b2ab97b01c6
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 0%

---

# 同儕帳號

閱讀本文了解如何在學習管理員中建立和管理同儕帳號。

學習管理器提供透過同儕帳號功能分享已購買座位的功能。 透過 Learning Manager 中的同儕帳號，管理員可以將購買的座位分享給其所關聯的同儕帳號。 此外，發起席位共享的管理員也能查看同儕帳號的報告。

## 新增同儕帳號 {#addapeeraccount}

1. 從管理員儀表板，點擊 **[!UICONTROL Settings]** > **[!UICONTROL Peer Accounts]**。
1. 從右上角點擊 **[!UICONTROL Add]**。

   ![](assets/peeraccount.png)

   *新增同儕帳號*

1. 在欄位 **[!UICONTROL Account Subdomain]** 中，指定你想建立同儕帳號的子網域。

   ![](assets/addpeer.png)

   *新增子網域*

>[!NOTE]
>
>要找到另一個帳號的子網域，請檢查該帳號的網址。 子網域會顯示在主網域之前，並協助識別特定帳號。
>
>例如：
>
>在網址 [https://www.learningmanager.com/accountname](https://www.learningmanager.com/accountname) 中，子網域是 **accountname**。
>
>在網址 [https://www.accountname.learningmanager.com](https://www.accountname.learningmanager.com) 中，子網域也是 **accountname**。
>
>子網域對每個帳號獨一無二，並用於存取相應的 Learning Manager 實例。

1. 輸入接受或拒絕同儕帳號請求的管理員的電子郵件 ID。
1. 請指定你想與同儕共享的席次數量。 當你與同儕帳號共享席位時，該帳號會進入「活躍狀態」，與已獲得的席位或同儕自己購買的席位一起。

   如果你輸入的號碼超過可用座位，系統會顯示警告。

1. 如果您想查看同儕的註冊報告及共享目錄報告，請勾選方塊。
1. 點擊新增以新增同儕帳號。

   如果管理員與同儕共用席位，該同儕不能與其他人共享席位。 不過，同儕可以另外購買部分座位並共享。

## 查看同儕帳號共享的座位

管理員可以在管理員介面查看同儕帳號共享的席位數。

要查看同儕帳號共享的席次：

1. 以管理員身份登入 Adobe Learning Manager。
2. 選擇 **[!UICONTROL Users]** ，然後選擇 **[!UICONTROL Internal]**。

![](assets/peer-account-seats.png)
_使用者區塊顯示對等帳號共享的席位數_

## 查看與同儕帳號相關的報告 {#viewreportsassociatedwithpeeraccounts}

建立同儕帳號後，你也可以為同儕帳號繪製報告。 作為管理員，如果你發起同儕帳號申請，你可以查看該同儕帳號的報告。

如果對等端也想查看管理員報告，則必須向管理員發送獨立的對等帳號請求。

欲了解如何產生及查看同儕帳號的共享目錄，請參閱 [「檢視同儕報告](reports.md#main-pars_header_894271250)」。

## 刪除同儕帳號 {#deletingpeeraccounts}

如果你不想再與某個帳號共享座位或購買，可以刪除同儕帳號。

1. 從 Learning Manager 管理員應用程式中，點選 > 同儕帳號的設定。
1. 選擇你想刪除的同儕帳號。
1. 請做以下其中一項：

   * 從頁面右上角點擊刪除。
   * 點擊你想刪除的同儕帳號旁的刪除圖示。

   當同儕帳號被刪除後，所獲得的座位將不再可用。 如果同儕帳號只收到席位，沒有購買席位，帳號就會進入非活躍狀態。

## 同儕帳號的使用者回報 {#download-peer-account}

管理員可以查看該同儕帳號的使用者報告。 父帳號管理員可以申請存取報告，一旦同儕帳號管理員同意，父管理員就能查看該帳號中註冊的使用者數量，並能下載同儕帳號的使用者報告。

1. 在同儕帳戶頁面，點擊 **[!UICONTROL Add]**。
1. 啟用選項。 **[!UICONTROL Request permission to download user reports for entire account]**

![](assets/image034.png)

*查看同儕帳號的使用者報告*

要下載同儕帳號的報告，請點擊 **[!UICONTROL Download]**。

## 共用課程（包括先前取得課程）的作者名稱顯示

Adobe Learning Manager 顯示 **透過同儕帳號分享或取得的課程原作者姓名** 。

早期，從同儕帳號取得的課程常以作者名 **顯示為外部作者**。 此系統已加強以提升內容歸屬與清晰度。

### 運作方式

* 當課程從同儕帳號分享時，Learning Manager 現在會解析並顯示 **來源帳號的實際作者名稱** 。
* 這種行為適用於：
   * 新共享課程
   * 在這項強化導入前已修習的課程

### 事後行為

此項增強是追溯&#x200B;**適用**&#x200B;的。\
在此變更前已從同儕帳號取得的課程，會自動顯示正確的作者名稱。

管理員或作者無需採取任何行動：

* 你不需要重複分享課程
* 你不需要重新發布或編輯課程內容
* 現有的學員註冊人數與進度保持不變

### 不變的事

* 球場所有權與許可保持不變
* 只有 **顯示的作者名稱** 會被更新
* 報告、註冊人數及課程結構均不受影響

這確保所有共享內容（包括透過同儕帳號取得的歷史課程）都能一致且準確地標示作者。

## 常見問題 {#frequentlyaskedquestions}

+++如何從一個帳號共享座位到另一個帳號？

新增同儕帳號時，請指定你可以與另一個同儕帳號共享的席位數。

![](assets/share-seats.png)

*從一個帳號共享席位到*
+++
