---
jcr-language: en_us
title: 大量新增使用者
description: 瞭解如何一次新增多個使用者。
contentowner: saghosh
source-git-commit: 0534bd52c80b77d985cfe715f74054f3aabac9a2
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---



# 大量新增使用者

在本次訓練中，您將瞭解如何透過CSV大量新增使用者。

[![按鈕](feature-summary/assets/launch-training-button.png)](https://learningmanager.adobe.com/app/learner?accountId=98632&amp;sdid=51TC8QS1&amp;mv=display&amp;mv2=display#/course/7555555)

如果您無法啟動培訓，請寫信至 <almacademy@adobe.com>.

## 如何新增多個使用者

您可以按照以下步驟同時新增多個使用者：

1. 按一下 **[!UICONTROL Users]** 管理員登入中的左窗格，然後按一下 **[!UICONTROL Add]** > **[!UICONTROL Upload a csv]**. 隨即顯示快顯對話方塊。

1. 您可以使用.CSV檔案新增多個使用者。 按一下 **[!UICONTROL Import]** 並從電腦中選取/開啟.csv檔案。

1. 匯入檔案後，第一次上傳.csv檔案時，請使用應用程式標籤對應.csv檔案的內容。

   對於所有後續的上傳，會考慮標籤的先前設定。 按一下 **[!UICONTROL Save]** 完成資料對應後，請按一下 **[!UICONTROL Add]** 上傳對應的.csv檔案。

1. 按一下 **[!UICONTROL Save]** 完成資料對應後，請按一下 **[!UICONTROL Add]** 上傳對應的.csv檔案。

## 包含必填欄位的CSV上傳 {#csvuploadwithmandatoryfields}

不強制在CSV中新增使用者的設定檔和管理員的電子郵件ID。 使用者名稱和使用者的電子郵件ID是唯一的必填欄位。

在此情況下，貴公司的管理員預設會被視為使用者的管理員。 依預設，會將員工視為使用者的設定檔。

**範例CSV**

Learning Manager範例CSV包含以下必填欄位。
[Sample-CSV-name-email.zip](assets/sample-csv-name-email.zip)

## 包含所有欄位的CSV上傳 {#csvuploadwithallthefields}

在加入Manager的電子郵件ID給任何員工之前，請確保先在CSV中將該Manager新增為員工。 例如，在下列快照中，參照員工名稱Howard Walters：

![](assets/csv-example.png)

*要上傳的CSV範本*

此外，組織的管理員可以將自己新增為員工，並將其Manager的電子郵件ID提及為根。

**範例CSV**

Learning Manager範例CSV包含所有欄位。
[learning-manager-sample-csv.zip](assets/learning-manager-sample-csv.zip).

請參閱  [使用CSV上傳](/help/migrated/administrators/feature-summary/add-users-user-groups.md) 功能說明內容以取得詳細資訊。
