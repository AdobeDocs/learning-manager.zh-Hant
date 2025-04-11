---
jcr-language: en_us
title: 大量新增使用者
description: 瞭解如何一次添加多個使用者。
contentowner: saghosh
exl-id: c3309ce5-8764-452e-82d5-5637c23c661b
source-git-commit: a28ac8f57710c118ca4ad02872fd100c6f24beac
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# 大量新增使用者

在本培訓中，您將學習如何透過 CSV 大量新增使用者。

[![按鈕](feature-summary/assets/launch-training-button.png)](https://content.adobelearningmanageracademy.com/app/learner?accountId=98632#/course/7555555)

如果您無法啟動培訓，請寫信給 <almacademy@adobe.com>。

## 如何添加多個使用者

您可以按照以下步驟一次添加多個使用者：

1. 按兩下&#x200B;**[!UICONTROL Users]**&#x200B;管理員登入中的左窗格，然後按兩下>**[!UICONTROL Add]****[!UICONTROL Upload a csv]**“。此時將顯示一個快顯視窗對話框。

1. 您可以使用 .CSV檔案。 按兩下 **[!UICONTROL Import]** 並選擇/打開電腦中的.csv檔。

1. 導入文件後，首次上傳文件時.csv應用程式標籤映射.csv文件的內容。

   對於所有後續上傳，系統會考慮先前的標籤設定。 完成數據映射后按兩下 **[!UICONTROL Save]** ，然後按下以 **[!UICONTROL Add]** 上傳映射的.csv檔。

1. 完成數據映射后按兩下 **[!UICONTROL Save]** ，然後按下以 **[!UICONTROL Add]** 上傳映射的.csv檔。

## CSV上傳與必填字段 {#csvuploadwithmandatoryfields}

在CSV中添加用戶的設定檔和經理的電子郵件 ID 不是強制性的。 使用者名和用戶的電子郵件 ID 是唯一的必填欄位。

在這種情況下，預設情況下，公司的管理員被視為使用者的管理員。 默認情況下，員工被視為用戶的設定檔。

>[!NOTE]
>
>要添加新使用者，請創建一個包含其詳細資訊的新CSV檔並對其進行上傳。 不支援更新和重新上傳現有的 CSV 檔案。

**範例CSV**

下面提供了包含必填欄位的學習管理器示例CSV。[Sample-CSV-name-email.zip](assets/sample-csv-name-email.zip)

## CSV上傳所有欄位 {#csvuploadwithallthefields}

在包含任何員工的經理電子郵件 ID 之前，請確保首先將經理添加為 CSV 中的員工。 例如，在下面的快照中引用員工姓名 Howard Walters：

![](assets/csv-example.png)

*CSV 上傳 的範本*

此外，組織的管理員可以將自己添加為員工，並將其經理的電子郵件ID稱為root。

**範例CSV**

下面提供了包含所有欄位的學習管理器示例CSV。[learning-manager-sample-csv.zip](assets/learning-manager-sample-csv.zip)。

如需詳細信息，請参閱  [使用CSV上傳](/help/migrated/administrators/feature-summary/add-users-user-groups.md) 功能說明內容。
