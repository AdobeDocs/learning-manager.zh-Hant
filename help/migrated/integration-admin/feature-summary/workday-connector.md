---
description: 學習如何將 Workday 連接器與 Adobe Learning Manager 整合
jcr-language: en_us
title: Workday 連接器
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 0%

---


# Adobe Learning Manager 中的 Workday 連接器

## 簡介

**Workday** 是一個雲端系統，協助組織管理員工與財務資料。 它主要用於人力資源工作，如招聘、薪資和績效追蹤。 連接 Adobe Learning Manager 後，能自動同步兩個平台間的使用者與技能資料。

Workday 連接器讓您能無縫整合 Adobe Learning Manager 與您組織的 Workday 租戶。 此整合使使用者資料與技能能在兩個系統間自動同步，提升資料準確性並減少人工工作量。

## 主要優點

- 將使用者從 Workday 匯入 Adobe Learning Manager。
- Workday 與 Adobe Learning Manager 之間的屬性映射。
- 將使用者技能從 Adobe Learning Manager 匯出到 Workday。
- 排程資料同步任務自動執行。

## 先決條件

在設定 Workday 連接器前，請向你的 Workday 管理員取得以下資訊：

- 主機網址
- 租戶識別
- 用戶名
- 密碼

## 設定 Workday 連接器

你可以在 Adobe Learning Manager 中設定 Workday 連接器，讓你能從 Workday 匯入使用者資料、匯出使用者技能回 Workday，並排程自動同步以保持兩套系統的即時更新。

要設定 Workday 連接器：

1. 以整合管理員身份登入 Adobe Learning Manager。
2. 將滑鼠移到Workday **圖**&#x200B;塊上，選擇&#x200B;**「連接**」。

   ![](assets/workday-connector1.png)
   _設定 Workday 連接器以匯入和匯出資料_

3. 輸入以下連接細節：
   - **連線名稱**：你為連線選擇的名稱。
   - **主機網址**：由您的 Workday 管理員提供。
   - **租戶**：來自你 Workday 管理員的內部識別碼。
   - **使用者名稱與密碼**：Workday 管理員建立一個具備必要安全權限的整合系統使用者（ISU），並與整合管理員共享。

   ![](assets/workday-connector2.png)
   _新增設定 Workday 連接器所需的細節_

4. 選擇 **連接** 以完成設定。

>[!NOTE]
>
>你可以在帳號裡設定多個 Workday 連線。

## 從 Workday 匯入使用者

### 地圖屬性

你可以使用 Workday 連接器，將 Workday 租戶的活躍使用者匯入 Adobe Learning Manager。 此整合透過保持員工紀錄同步，簡化了使用者管理。 除了 Workday 之外，Adobe Learning Manager 也支援從其他資料來源如 FTP 和 Salesforce 匯入使用者。

在匯入使用者之前，必須在 Workday 與學習管理員之間對應使用者屬性。

1. 請前往 **Workday Connector 的「概覽** 」頁面。
2. 在匯入&#x200B;**區塊中**&#x200B;選擇&#x200B;**「內部使用者**」。

   ![](assets/workday-connector3.png)
   _選擇內部使用者以映射使用者屬性_

3. 使用 **地圖屬性** 選項來連結兩個系統之間的欄位：
   - 在 **Adobe Learning Manager** 欄位中，選擇對應的 Adobe Learning Manager 屬性。
   - 在 **Workday** 欄位中，使用下拉選單選擇對應的 Workday 屬性。

   ![](assets/workday-connector4.png)
   _用 Adobe Learning Manager 欄位映射 Workday 屬性_

   >[!NOTE]
   >
   >Adobe Learning Manager 目前支援從 Workday 匯入最多 **69 個使用者屬性** 。 你可以使用 **Adobe Learning Manager 的「活動欄位** 」功能啟用額外欄位。 若要新增自訂 Workday 屬性，請聯絡您的客戶成功帳戶經理（CSAM）。

4. 選擇 **「排除臨時工作者** 」勾選框，以避免引進臨時工作者。
5. 如有需要，可以套用篩選器，例如將使用者匯入特定管理員。

>[!IMPORTANT]
>
>確保UUID、電子郵件地址和員工姓名都是唯一的。 錯誤或重複的值可能導致整合失敗。

## 支援的 Workday 屬性

支援的 Workday 屬性列表：

```
wd:User_ID wd:Worker_ID manager wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.@wd:Formatted_Name wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.@wd:Formatted_Name wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.wd:Prefix_Data.wd:Title_Descriptor wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.wd:Prefix_Data.wd:Title_Descriptor wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.wd:First_Name wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.wd:Last_Name wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.wd:First_Name wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.wd:Last_Name wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.@wd:Formatted_Address wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.wd:Postal_Code wd:Personal_Data.wd:Contact_Data.wd:Email_Address_Data.0.wd:Email_Address wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.wd:Country_Region_Descriptor wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.@wd:Formatted_Phone wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.wd:Country_ISO_Code wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.wd:International_Phone_Code wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.wd:Phone_Number wd:Personal_Data.wd:Primary_Nationality_Reference.wd:ID.1.$ wd:Personal_Data.wd:Gender_Reference.wd:ID.1.$ wd:Personal_Data.wd:Identification_Data.wd:National_ID.0.wd:National_ID_Data.wd:ID wd:Personal_Data.wd:Identification_Data.wd:Custom_ID.0.wd:Custom_ID_Data.wd:ID wd:User_Account_Data.wd:Default_Display_Language_Reference.wd:ID.1.$ wd:Role_Data.wd:Organization_Role_Data.wd:Organization_Role.0.wd:Organization_Role_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Position_Title wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Title wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Name wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.@wd:Formatted_Address
wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Classification_Summary_Data.0.wd:Job_Classification_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Classification_Summary_Data.0.wd:Job_Group_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Work_Space__Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Profile_Summary_Data.wd:Job_Family_Reference.0.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Profile_Summary_Data.wd:Job_Profile_Name wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Profile_Summary_Data.wd:Job_Profile_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.0.wd:Country_Reference.wd:ID.2.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Worker_Type_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.0.@wd:Formatted_Address wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Profile_Summary_Data.wd:Management_Level_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Status_Data.wd:Active wd:Employment_Data.wd:Worker_Status_Data.wd:Active_Status_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Hire_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Original_Hire_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Retired wd:Employment_Data.wd:Worker_Status_Data.wd:Retirement_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Terminated wd:Employment_Data.wd:Worker_Status_Data.wd:Termination_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Termination_Last_Day_of_Work wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Code wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Name wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Type_Reference.wd:ID.1.$ wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Subtype_Reference.wd:ID.1.$ wd:Qualification_Data.wd:Education.0.wd:School_Name wd:Qualification_Data.wd:External_Job_History.0.wd:Job_History_Data.wd:Job_Title wd:Qualification_Data.wd:External_Job_History.0.wd:Job_History_Data.wd:Company wd:Management_Chain_Data.wd:Worker_Supervisory_Management_Chain_Data.wd:Management_Chain_Data.0.wd:Manager.Employee_ID Primary Work Email wd:Organization_Type_Reference_Cost_Center_ID wd:Organization_Type_Reference_Cost_Center_Name wd:Organization_Type_Reference_Company wd:Organization_Subtype_Reference_Department
wd:Organization_Subtype_Reference_Division wd:Universal_ID wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.0.wd:Country_Region_Descriptor wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.0.wd:Country_Region_Reference.wd:ID.2.$ wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.wd:Municipality
```

## 將使用者技能匯出到 Workday

你可以將 Adobe Learning Manager 中所有活躍的使用者技能匯出到 Workday。 退役技能不會被輸出。

>[!IMPORTANT]
>
>- 不要嘗試同時從多個 Adobe Learning Manager 帳號匯出技能到同一個 Workday 帳號。
>- 若多個 Adobe Learning Manager 帳號共用同一個 Workday 帳號，請確保技能名稱在不同帳號間保持一致，以避免衝突。

### 設定排程匯出

要設定排程匯出：

1. 選擇使用者技能&#x200B;**，然後在** Workday 概覽&#x200B;**頁面選擇**&#x200B;設定排程&#x200B;**。**

   ![](assets/workday-connector5.png)
   _選擇使用者技能以排程匯出_

2. 選擇 **啟用使用者技能匯出，使用此連線** 勾選框。
3. 選擇 **啟用排程**。
4. 設定開始日期、時間和重複的間隔。

   ![](assets/workday-connector6.png)
   _在 Workday 連接器中設定排程匯出_

5. 選擇 **儲存** 以套用排程。

### 按需出口

要創造按需出口：

1. 在 **Workday 概覽**&#x200B;頁面選擇&#x200B;**隨選**。
2. 請輸入報告應該開始的起始日期。
3. 選擇 **執行** 以執行報表。

### 查看執行狀態

1. 切換到 **執行狀態**。
2. 查看所有任務的狀態，並視需要下載錯誤報告。

## 排程同步任務

你可以設定連接器自動執行資料同步任務：

- 排程每日從 Workday 匯入使用者到 Learning Manager。
- 排程定期匯出使用者技能到 Workday。

>[!NOTE]
>
>排程確保使用者紀錄與技能資料在兩系統中始終保持最新。

## 需要記住的重點

- Workday 輸入的 UUID 欄位無法被面向客戶的 LMS 管理員刪除。
- **使用者清除**&#x200B;功能每次最多支援 50 位使用者。匯入帶有 UUID 的使用者時要小心。
- 技能在 Workday 中以技能項目層級對應，使用 Adobe Learning Manager 的技能名稱與等級。
