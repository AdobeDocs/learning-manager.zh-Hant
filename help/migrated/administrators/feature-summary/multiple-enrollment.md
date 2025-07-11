---
title: Adobe Learning Manager中的多重註冊
description: 身為帳戶管理員，您的一項主要職責就是建立跨不同時區的不同VILT工作階段例項，並可能為特定使用者群組建立工作階段。
exl-id: c430545d-b48e-432d-a278-658c9281818f
source-git-commit: 22cfa30d22a45afd3e0a65d8c088c2dda4d93072
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---

# Adobe Learning Manager中的多重註冊

在Adobe Learning Manager中，每個課程可以有不同的例項。 身為帳戶管理員，您的一項主要職責就是建立跨不同時區的不同VILT工作階段例項，並可能為特定使用者群組建立工作階段。

在2023年7月版本之前，當管理員註冊了學習者時，他們只能註冊一個例項。 如果學習者希望參加不同執行個體的課程，管理員會建立多個課程，每個執行個體各一個。

Adobe Learning Manager的多重註冊功能可協助管理員避免此類情況。

## 管理執行個體

>[!INFO]
>
>在本次訓練中，您將瞭解如何編輯執行個體詳細資訊和執行個體屬性。<br><br>[![按鈕](assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/8318912)</br></br>

如果您無法啟動訓練，請寫信到<almacademy@adobe.com>。

## 什麼是多重註冊

透過各種可用例項，將學習者多重註冊為課程中的多次。  學習者可註冊多個課程例項，無論其已註冊、已完成或尚未開始的狀態為何。 當作者啟用[!UICONTROL Multiple Enrollment]切換時，學習者可以註冊課程的多個執行個體。

![多重註冊影像](assets/multi-enrollment-author.png)
*從設定啟動多重註冊*

您可以個別追蹤每個執行個體的進度，也可以匯出報告來追蹤每個執行個體的進度。

## 重要點

* 多重註冊僅適用於課程有多個例項時。
* 多註冊選項啟用且使用者在多個例項中註冊後，學習者成績單報告中會為每個課程建立新列（每個例項和每個學習者各一列）
* 若設定報表自動化時每門課程僅預期一列，則您必須對報表自動化進行必要的調整，才能啟用「多重註冊」功能。
* 管理員API不支援多重註冊情況。 如果您有任何需求，請洽詢您的CSM。

## 如何啟用多重註冊

1. 以作者身分登入您的Adobe Learning Manager帳戶。
1. 選取您想要學習者多次註冊的課程。
1. 在左側面板中，選取&#x200B;**[!UICONTROL Settings]** > **[!UICONTROL Edit]** > **[!UICONTROL Instance configuration]** > **[!UICONTROL Enable Multiple Enrollment]**。

![多重註冊影像](assets/multi-enrollment-author.png)
*啟用多重註冊*

>[!NOTE]
>
>身為作者，您不能同時啟用[執行個體切換]和[多重註冊]。

## 學習者檢視

當學習者想要註冊教室或VC課程，或想要在繼續其他課程前完成課程時，多次註冊將有所幫助。

對於未註冊的學習者，當他們選取課程時，將會檢視課程底下具有多個例項的畫面。 接著，他們便可以選取每個例項並註冊。

![學習者檢視影像](assets/learner-view.png)
*檢視執行個體*

註冊一個執行個體後，他們可以在右側窗格中選取「檢視所有執行個體」選項，註冊其他執行個體。

![多重註冊課程影像](assets/enroll-instance.png)
*註冊執行個體*

每個執行個體的進度都可追蹤如下：

![追蹤進度](assets/check-progress.png)
*追蹤每個執行個體的進度*

## 管理員中的多重註冊變更

**註冊：**

註冊學習者時，您可以啟用下列核取方塊：

「*」選取的學習者可能已註冊此課程的其他執行個體。 允許這些學習者也在執行個體上註冊……&quot;*

![管理員變更](assets/admin-changes.png)
管理員的*註冊選項*

如果學習者已註冊一個例項，而您身為管理員，嘗試將學習者註冊到其他課程例項，請選取「是」。

## 報告

對於已註冊相同課程的兩個例項的學習者，系統會為每個課程例項建立兩列。 報表也會顯示執行個體的進度。
