---
jcr-language: en_us
title: 可信
description: 瞭解Credly與ALM的整合，以便跨各種社群媒體頻道管理和共用平台的外部徽章
contentowner: chandrum
exl-id: 168f7ff8-51f5-4962-bf76-af909fc5565b
source-git-commit: f3a0ec693e1a2e75cdad24f91f22a0290d62740d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# 可信

[Credly](https://info.credly.com/)是數位認證平台，可讓學習者和組織贏取、分享及驗證專業成就，例如徽章或認證。 學習者可以透過其在社群媒體和其他位置的Credly設定檔管理和分享徽章。

## 先決條件

為您的組織設定Credly帳戶。 在Adobe Learning Manager中使用學習者的電子郵件ID將學習者新增至Credly。 這可讓學習者檢視Credly和Adobe Learning Manager上的徽章。

## 將Credly聯結器新增至Adobe Learning Manager

請依照下列步驟，將Credly Connector新增至Adobe Learning Manager：

1. 以&#x200B;**[!UICONTROL Integration Admin]**&#x200B;登入。
2. 選取「**[!UICONTROL Credly]** > **連線**」，將&#x200B;**[!UICONTROL Credly]**&#x200B;聯結器新增至Adobe Learning Manager。

   ![](assets/connector-credly.png)
   _新增Credly聯結器_

3. 輸入&#x200B;**[!UICONTROL Connection Name]**。
4. 輸入&#x200B;**[!UICONTROL Organization ID]**&#x200B;和&#x200B;**[!UICONTROL Authorization token]**。

   >[!NOTE]
   >
   >Credly中的每個徽章都隨附組織ID和授權權杖。 從Credly複製這些值。

5. 輸入&#x200B;**[!UICONTROL Hostname]**&#x200B;並選取&#x200B;**[!UICONTROL Connect]**。

## 從Credly移轉預算

Adobe Learning Manager中的badge.csv可讓您從現有的LMS或外部系統移轉徽章。 badge.csv已更新為兩個新欄：

* externalBadgeId
* externalBadgeProvider

外部徽章ID代表Credly平台中的徽章範本ID，而外部徽章提供者為Credly。 在badge.csv中新增這些值，並依照[移轉手冊](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/migration-manual#migrationprocedure)中所述的步驟來移轉csv。

## 建立技能 — 管理員

將徽章匯入Adobe Learning Manager後，管理員就可以建立此徽章為技能。 若要瞭解如何建立技能，請參閱[建立和修改技能](https://experienceleague.adobe.com/en/docs/learning-manager/using/admin/skills-levels)。

### 將技能/徽章指派給學習物件 — 作者

作者/管理員可以將這些Credly匯入的ALM徽章指派給課程、學習路徑或認證（不僅僅是技能），而且在這些學習物件的消耗上，此徽章將會完成並可在Credly和ALM應用程式上檢視。

學習者可以登入Credly並在Credly平台上檢視徽章。 來自Credly，他們可以在LinkedIn和其他社群媒體等外部平台上分享徽章。
