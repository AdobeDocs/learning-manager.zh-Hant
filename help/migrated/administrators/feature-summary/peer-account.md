---
description: 閱讀本文章，瞭解如何在Learning Manager中建立和管理對等帳戶。
jcr-language: en_us
title: 對等帳戶
contentowner: shhivkum
exl-id: 251d0eeb-f5e8-4f70-a36c-dcecb4834042
source-git-commit: 05a8b4da646f0b2e4a14aa26159c3e8cfdde35fe
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 0%

---

# 對等帳戶

閱讀本文章，瞭解如何在Learning Manager中建立和管理對等帳戶。

Learning Manager提供使用Peer帳戶功能共用已購名額的功能。 透過Learning Manager中的對等帳戶，管理員可以和管理員相關聯的對等帳戶共用已購買的席位。 此外，已開始共用名額的管理員可以檢視對等帳戶的報告。

## 新增對等帳戶 {#addapeeraccount}

1. 在管理員儀表板中，按一下&#x200B;**[!UICONTROL Settings]** > **[!UICONTROL Peer Accounts]**。
1. 從右上角按一下&#x200B;**[!UICONTROL Add]**。

   ![](assets/peeraccount.png)

   *新增對等帳戶*

1. 在&#x200B;**[!UICONTROL Account Subdomain]**&#x200B;欄位中，指定您要建立配對帳戶的子網域。

   ![](assets/addpeer.png)

   *新增子網域*

>[!NOTE]
>
>若要尋找其他帳戶的子網域，請檢查帳戶的URL。 子網域會顯示在主網域之前，並協助識別特定帳戶。
>
>例如：
>
>在URL [https://www.learningmanager.com/accountname](https://www.learningmanager.com/accountname)中，子網域為&#x200B;**accountname**。
>
>在URL [https://www.accountname.learningmanager.com](https://www.accountname.learningmanager.com)中，子網域也為&#x200B;**accountname**。
>
>子網域對每個帳戶都是獨一無二的，且用來存取個別Learning Manager例項。

1. 輸入接受或拒絕對等帳戶請求的管理員的電子郵件ID。
1. 指定您想要與同事共用的座位數。 當您與對等帳戶共用名額時，對等帳戶會與收到的名額或對等本身購買的名額一起進入「使用中」狀態。

   如果您輸入的數字大於可用座位，系統會顯示警告。

1. 如果您想要檢視同行的註冊報告和共用目錄報告，請選取核取方塊。
1. 按一下「新增」以新增對等帳戶。

   如果管理員與對等共用名額，則該對等無法與其他任何人共用這些名額。 但是，同儕節點可以單獨購買一些座位並分享。

## 檢視對等帳戶共用的名額

管理員可以在管理員介面上檢視對等帳戶共用的名額數。

若要檢視對等帳戶共用的名額：

1. 以管理員身分登入Adobe Learning Manager。
2. 選取&#x200B;**[!UICONTROL Users]**，然後選取&#x200B;**[!UICONTROL Internal]**。

![](assets/peer-account-seats.png)
_使用者區段，顯示對等帳戶共用的名額數_

## 檢視與對等帳戶相關聯的報告 {#viewreportsassociatedwithpeeraccounts}

建立對等帳戶之後，您也可以為對等帳戶繪製報告。 作為管理員，如果您啟動對等帳戶請求，則可以檢視對等帳戶的報告。

如果對等體也想要檢視管理員報告，則對等體必須傳送個別的對等體帳戶要求給管理員。

若要瞭解如何產生和檢視對等帳戶的共用目錄，請參閱[檢視對等報告](reports.md#main-pars_header_894271250)。

## 刪除對等帳戶 {#deletingpeeraccounts}

如果您不想再與帳戶共用名額或購買專案，可以刪除對等帳戶。

1. 在Learning Manager管理員應用程式中，按一下「設定>對等帳戶」 。
1. 選取您要刪除的一或多個對等帳戶。
1. 執行下列任一項作業：

   * 按一下頁面右上角的「刪除」 。
   * 按一下您要刪除的對等帳戶旁的「刪除」圖示。

   刪除對等帳戶後，收到的名額就無法再使用。 如果對等帳戶僅收到名額而沒有購買名額，則該帳戶會進入「非使用中」狀態。

## 對等帳戶的使用者報告 {#download-peer-account}

管理員可以檢視對等帳戶的使用者報告。 父級帳戶管理員可以請求存取報告，當對等帳戶管理員接受此請求後，父級管理員將能夠檢視對等帳戶中註冊的使用者數量，並能夠下載對等帳戶的使用者報告。

1. 在[對等帳戶]頁面上，按一下&#x200B;**[!UICONTROL Add]**。
1. 啟用選項&#x200B;**[!UICONTROL Request permission to download user reports for entire account]**。

![](assets/image034.png)

*檢視對等帳戶的使用者報告*

若要下載對等帳戶的報告，請按一下&#x200B;**[!UICONTROL Download]**。

## 常見問題 {#frequentlyaskedquestions}

+++如何在不同帳戶之間共用座位？

新增對等帳戶時，請指定您可與另一個對等帳戶共用的名額數。

![](assets/share-seats.png)

*從一個帳戶共用名額到另一個帳戶*
+++
