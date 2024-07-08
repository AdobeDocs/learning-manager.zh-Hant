---
description: 面向希望將現有 LMS 遷移到學習管理器 LMS 的整合管理員Adobe Systems參考手冊。
jcr-language: en_us
title: 移轉手冊
exl-id: bfdd5cd8-dc5c-4de3-8970-6524fed042a8
source-git-commit: 7be69e68f3b8970e090c8eccd25771cd2e5e99f1
workflow-type: tm+mt
source-wordcount: '3604'
ht-degree: 0%

---

# 移轉手冊

希望將現有 LMS 遷移到學習管理器 LMS 的整合管理員參考手冊

<!-- ## Overview {#overview} -->

## 使用案例 {#usagescenario}

通常，大型企業擁有其內部LMS或任何供應商提供的傳統學習管理系統。 LMS 由您的企業培訓 內容和訓練資料組成。 作為企業，當您購買學習管理器時，您可能希望將現有的 LMS 內容和數據移動到學習管理器，以便您可以善用現代且直觀的 LMS 的優勢，而不會丟失組織的任何舊數據。

學習管理器提供必要的工具和規範，以便組織的集成管理員可以設置和執行遷移任務。

截至目前，組織的管理員可以通過聯繫Adobe Systems支持團隊來訪問學習管理器中的遷移功能。 要在帳戶中啟用遷移功能，您可以聯繫Adobe Systems學習管理器支持團隊。

## 移轉程式 {#apidescription}

本節介紹了遷移的先決條件、遷移過程中涉及的關鍵步驟、遷移衝刺、規範、數據和內容遷移步驟，如下所示：

### 必要條件 {#prerequisites}

學習管理器團隊期望在執行遷移過程之前由組織的集成管理員執行以下任務：

* 集成管理員從現有 LMS 中提取数据和內容，並將數據轉換為學習管理器定義的文件格式。
* 學習管理員不支援在遷移過程中導入使用者，並希望組織使用連接器導入使用者。 Adobe Systems希望在遷移過程之前配置這些連接器。 有關詳細資訊，請參閱 [學習管理器連接器說明](connectors.md) 。

學習管理器建議管理員可以先在試用帳戶中試用遷移過程，然後再將數據和內容遷移到學習管理器生產環境。

### 遷移過程的關鍵步驟 {#keystepsofmigrationprocess}

將內容和數據從現有 LMS 遷移到學習管理器所涉及的關鍵步驟如下：

1. 集成管理員或合作夥伴評估需要遷移的現有 LMS 数据和內容。
1. 集成管理員評估學習管理器提供的用于引入數據和內容的工具和規範。
1. 集成管理員編寫代碼或執行手動工作，以根據舊 LMS 提供的功能從舊 LMS 導出訓練資料和內容。
1. 訓練資料和內容可用后，集成管理員將分析並映射數據和內容，以匹配學習管理器遷移規範。
1. 整合管理員使用學習管理員提供的工具按以下順序進行遷移：

   1. 將學習者轉移到學習管理員
   1. 將培訓 內容轉移到學習管理器和
   1. 最後，將培訓數據傳輸到學習管理器中。

組織可以使用學習管理器 LMS 和旧版內容進行開始。

### 遷移物件的範圍 {#scopeofmigrationobjects}

您只能為以下學習對象遷移內容：

* 模組
* 徽章
* 課程
* 模組版本
* 課程執行個體
* 課程模組
* 技能
* 技能水準
* 技能課程
* 認證
* 認證課程
* 認證提交
* 學習方案
* 學習方案課程
* 學習方案 執行個體
* 學習方案課程執行個體
* 工作輔助
* 工作輔助版本
* 工作輔助課程
* 工作輔助技能
* 招生
* 認證註冊
* 學習方案註冊
* 工作輔助註冊
* 用戶課程成績



### 移徙的關鍵概念 {#keyconceptsofmigration}

簡要介紹了學習管理器遷移過程的一些關鍵概念，以便您快速參考，如下所示：

**移轉專案**

在學習管理器中，遷移專案由一個或多個衝刺 （sprint） 組成。 您也可以為帳戶設定多個移轉專案。 學習管理器中的遷移過程從創建遷移項目開始。

**短跑**

學習管理器遷移過程中的衝刺 （Sprint） 定義一組已選擇從現有 LMS 遷移的遷移項。 遷移專案可以是課程模組、學習者記錄或一組課程。 一個衝刺 （sprint） 中可以有多個學習數據項。 您可以在每個衝刺 （sprint） 中執行遷移作業。

**衝刺運行**

衝刺運行是啟動衝刺遷移作業的過程。 可以在運行的任何時間點停止衝刺運行。

**衝刺重新運行**

遷移衝刺 （sprint） 完成後，可以隨時重新執行遷移衝刺 （sprint）。 當您想要將數據追加到衝刺 （sprint） 項中並再次將其遷移到應用程式或更正 CSV 中的錯誤時，會發生重新執行或重新運行衝刺 （sprint） 的情況。

**CSV規格**

學習管理器為您提供了一組 [標準CSV規範](migration-manual.md#main-pars_header_140933605)。 最佳做法是在開始遷移過程之前瀏覽這些CSV規範。 組織的集成管理員可以分析現有數據格式，並將其映射為與CSV 範本項提供的學習管理器匹配。

**移轉項目標記**

Adobe Systems建議使用一組關鍵字作為標記，以便在學習管理器應用程式中輕鬆標識遷移專案。 這些標記使您能夠在任何給定時間點在學習管理器應用程式內部標識專案。

**無內容模組**

學習管理器允許您無需內容即可上傳模組。 Adobe Systems將其視為學習管理器中的無內容模組。 在不需要任何內容的情況下從現有 LMS 遷移某些舊數據的情況下，無需URL引用即可上傳 模組_version.csv 文件。

## CSV規格和範例 CSV {#csv}

在下面找到可用於與現有 LMS 遷移數據進行映射的標準CSV規範。 按兩下 csv-specification、sample-csvs 以下載 zip 檔案。 下載的csv-specifications.zip包含七個 Excel 工作表檔案。 這些Excel工作表檔是帶有說明的規範，可讓您瞭解如何填寫.csv檔。 相應的.csv檔應包含規定格式中每個欄位的數據，如這些.xlsx檔中所述。

<table border="1" cellspacing="0" cellpadding="0" width="100%">
 <tbody>
  <tr>
   <th>
    <p><b>Sl.no</b></p></th>
   <th>
    <p><b>檔名</b></p></th>
   <th>
    <p><b>内容說明</b></p></th>
   <th>
    <p>筆記</p></th>
  </tr>
  <tr>
   <td>
    <p>1</p></td>
   <td>
    <p>module.xlsx</p></td>
   <td>
    <p>模組.csv 的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>2</p></td>
   <td>
    <p>badge.xlsx</p></td>
   <td>
    <p>badge.xlsx的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>3</p></td>
   <td>
    <p>course.xlsx</p></td>
   <td>
    <p>course.csv的元數據</p></td>
   <td>
    <p>為給定課程提及一個作者姓名，因為有時遷移後應用程式中無法準確顯示多個作者姓名。 </p></td>
  </tr>
  <tr>
   <td>
    <p>4</p></td>
   <td>
    <p>模組_version.xlsx </p></td>
   <td>
    <p>模組_version.csv 的元數據</p></td>
   <td>
    <p>確保提供上傳內容的 Box 帳戶資料夾的URL路徑。 </p></td>
  </tr>
  <tr>
   <td>
    <p>5</p></td>
   <td>
    <p>course_執行個體.xlsx</p></td>
   <td>
    <p>course_執行個體.csv 的元数据 </p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>6</p></td>
   <td>
    <p>session.xlsx</p></td>
   <td>
    <p>session.csv的元數據</p></td>
   <td>
    <p>確保會話 csv 中的每個條目都與至少一個教室/虛擬教室模組相關聯</p></td>
  </tr>
  <tr>
   <td>
    <p>7</p></td>
   <td>
    <p>course_模組.xlsx</p></td>
   <td>
    <p>course_模組.csv 的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>8</p></td>
   <td>
    <p>skill.xlsx</p></td>
   <td>
    <p>skill.csv的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>9</p></td>
   <td>
    <p>skill_level.xlsx</p></td>
   <td>
    <p>skill_level.csv的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>10</p></td>
   <td>
    <p>skill_course.xlsx</p></td>
   <td>
    <p>skill_course.csv的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>11</p></td>
   <td>
    <p>certification.xlsx</p></td>
   <td>
    <p>Certification.csv的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>12</p></td>
   <td>
    <p>certification_course.xlsx</p></td>
   <td>
    <p>certification_course.csv的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>13</p></td>
   <td>
    <p>certification_commit.xlsx</p></td>
   <td>
    <p>certification_commit.csv的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>14</p></td>
   <td>
    <p>learning_方案.xlsx</p></td>
   <td>
    <p>learning_方案.csv 的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>15</p></td>
   <td>
    <p>learning_方案_course.xls </p></td>
   <td>
    <p>learning_方案_course.csv 的元數據 </p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>16</p></td>
   <td>
    <p>learning_方案_執行個體.xlsx </p></td>
   <td>
    <p>learning_方案_執行個體.csv 的元数据</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>17</p></td>
   <td>
    <p>learning_方案_執行個體_course_執行個體.xlsx </p></td>
   <td>
    <p>learning_方案_執行個體_course_執行個體.csv 的元数据</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>18</p></td>
   <td>
    <p>job_aid.xlsx</p></td>
   <td>
    <p>job_aid.csv的元數據</p></td>
   <td>
    <p>每個移轉的job_aid都需要具有一個或多個job_aid版本。</p></td>
  </tr>
  <tr>
   <td>
    <p>19</p></td>
   <td>
    <p>Job_aid_version.xlsx</p></td>
   <td>
    <p>job_aid_version.csv 的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>20</p></td>
   <td>
    <p>job_aid_course.xlsx</p></td>
   <td>
    <p>job_aid_course.csv的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>21</p></td>
   <td>
    <p>job_aid_skills.xlsx</p></td>
   <td>
    <p>job_aid_skills.csv的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>22</p></td>
   <td>
    <p>enrollments.xlsx</p></td>
   <td>
    <p>enrollments.csv的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>23</p></td>
   <td>
    <p>certification_enrollement.xlsx</p></td>
   <td>
    <p>certification_enrollement.csv的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>24</p></td>
   <td>
    <p>learning_方案_enrollment.xlsx</p></td>
   <td>
    <p>learning_方案_enrollment.csv 的元數據<br><br></p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>25</p></td>
   <td>
    <p>job_aid_enrollment.xlsx</p></td>
   <td>
    <p>job_aid_enrollment.csv的元數據</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>26</p></td>
   <td>
    <p>用戶_course_grade.xlsx</p></td>
   <td>
    <p><br>
      用戶_course_grade.csv 的元數據</p></td>
   <td>
    <p>在.csv檔中提供所需的學習者記錄數據平均儘管它們不是強制性的。 如果沒有此資訊，平均如果為遷移處理.csv，學習管理器應用程式可能不會反映任何數據。 sample-csvs.zip檔包含七個.csv檔與上述類似的命名約定。</p></td>
  </tr>
  <tr>
   <td>
    <p>27</p></td>
   <td>
    <p>用戶_skill.xlsx</p></td>
   <td>
    <p><br>
      用戶_skill.csv 的元數據</p></td>
   <td>
    <p> </p></td>
  </tr>
 </tbody>
</table>

學習管理員僅支援UTF 8和32位格式的日期和時間值。 如果您在超出範圍的日期為 2038-07-17T08:53:21.000Z 或 1980-04-17T08:13:25.322Z 的檔中CSV提及日期，則在遷移過程中可能會收到錯誤。

* [sample-csvs.zip](assets/sample-csvs.zip)
* [csv_specifications.zip](assets/csv-specifications.zip)

在匯入期間，您需要注意CSV檔案的下列相依性：

* 模組_version.csv與模組.csv 相依關係
* course_執行個體.csv 取決於course.csv
* course_模組.csv 須與 course.csv、模組.csv 和 模組_version.csv 搭配使用
* course_執行個體.csv 取決於course.csv
* session.csv取決於 course.csv和 模組.csv
* enrollment.csv取決於course.csv
* 用戶_course_grade.csv 須依賴 course.csv 和 模組.csv
* skill_course.csv取決於course.csv
* skill_level.csv取決於skill.csv
* learning_方案_執行個體.csv 依賴于 learning_方案 和 learning_方案_course.csv
* learning_方案_course.csv依賴於 learning_方案.csv
* learning_方案_enrollment.csv 依賴于 learning_方案 和 learning_方案_執行個體.csv
* learning_方案_執行個體_course_執行個體.csv 依賴于 learning_方案.csv、learning_方案_執行個體.csv 和 course_執行個體.csv
* certification_course.csv取決於certification.csv和course.csv
* certification_commit.csv取決於certification.csv和certification_course.csv
* certification_enrollment.csv取決於certification.csv、certification_course.csv和certification_enrollment.csv



## 移轉程式 {#migrationprocedure}

在開始遷移過程之前，請務必注意以下幾點：

* 在任何給定時間點，帳戶中只能有一個遷移專案處於活動狀態。 在一個專案中，在任何給定的時間點只能有一個衝刺 （sprint） 處於活動狀態。
* 無法撤銷已在遷移過程中的運行。 但是，可以使用學習管理器的每個功能中的現有刪除選項來撤消任何數據或內容遷移。
* 移轉項目一啟動，就會進入「移轉中」狀態。 在遷移期間，除集成管理員角色之外，任何其他角色都無法登錄到學習管理器。

### 建立 FTP 和 Box 帳戶 {#creatingftpandboxaccounts}

規劃遷移專案非常重要。 建議將專案分解為多個衝刺 （sprint），並清楚地確定在每個衝刺 （sprint） 中按讚遷移的內容。 在每個衝刺 （sprint） 之後做一些驗證，以便對在該衝刺 （sprint） 中遷移的數據充滿信心，而不是在項目結束時進行一個宏大的驗證階段，這可能平均是一個好主意。 在開始 Sprint 作為遷移專案的一部分之前，您需要分別在 FTP 和 Box 伺服器中上傳数据和內容 CSV文件。 如果您沒有 Custom FTP 和 Box 的帳戶，可以建立它們。

<!--**Create FTP account**-->

<!--Click **[!UICONTROL Request for CSV FTP folder]**. A pop-up dialog appears prompting you to enter your e-mail id. Go through online instructions and create an FTP account. As soon as you create your account, you can view your migration project and sprint project folders in FTP. 

A sample snapshot of project files and folder of FTP is shown below for your reference. -->

<!--![](assets/exavault-migration-upload-folders.png)-->

**建立框帳戶**

建立 內容 上傳資料夾的建立過程與以下步驟類似。 按下左側窗格中的遷移，然後按下顯示頁面底部的請求內容 上傳資料夾。

您將從 Box 收到一封電子郵件，其中包含對共享資料夾連結。 如果沒有帳戶框，請按兩下“註冊”並創建一個帳戶。 登入指示會傳送至整合管理員電子郵件ID。

**上載資料 （.csv 個檔案） 至 FTP 資料夾或 Box 檔案夾**

在建立移轉專案之前，必須先建立 FTP 或 Box 帳戶。 因此，在此階段您可以在學習管理器應用程式中創建遷移項目和衝刺。  請参閱 **本頁面中的數據和內容遷移過程** 部分以創建遷移專案。

在 FTP 或 Box 帳戶 中，按下您的項目資料夾名稱，然後按兩下 Sprint 名稱。 在 sprint 資料夾中，可以上傳要遷移的.csv數據文件。 要上傳，請按兩下 FTP 或 Box 伺服器頂部的上傳檔案 按鈕，然後拖放.csv檔。 下面顯示了一個上傳到 FTP 後的快照示例，供您參考。

<!--![](assets/exavault-upload.png)-->

可以返回到學習管理器遷移專案，按兩下 **[!UICONTROL Refresh]** 並視圖遷移衝刺中列出的所有.csv數據類型。

**上傳培訓 內容內容資料夾**

將現有 LMS 的培訓 內容上傳到您的 Box 帳戶。 如果已創建遷移專案並衝刺，則 Box 帳戶將填充遷移項目和衝刺 （Sprint） 名稱。 您可以上傳相同路徑中的內容。 請参閱 **本頁面中的數據和內容遷移過程** 部分以創建遷移專案。

您可以拖放內容文件，也可以按下 **[!UICONTROL Upload]** 並從桌面中選擇文件。 如果內容的文件大小很大，則在上傳文件時可能會體驗一些時間延遲。 根據文件的大小，將文件上傳到 Box 帳戶所需的時間會有所不同。

下面显示了將 Box 帳戶 上傳到 Box 內容 后的示例快照，供您參考：

![](assets/box-account.png)

*檔案 in Box 帳戶*

將文件上傳到 Box 帳戶后，請確保在 模組_version.csv 文件中提及此 Box 內容 文件的相對路徑。 這是您指明模組 內容路徑的必要步驟。

登錄到 FTP 和 Box 伺服器並上傳內容后，CSV位置將顯示，如下面的學習管理器中的快照所示。

![](assets/after-setup.jpg)

*CSV Box 帳戶 中的位置*

## 數據和內容遷移程序 {#dataandcontentmigrationprocedure}

將企業 LMS 數據和內容遷移到學習管理器的過程說明如下：

在開始遷移之前，請先完成遷移過程的先決條件。 請参閱 [本頁面中的CSV規範和示例 CSV](migration-manual.md#main-pars_header_140933605) 部分，併為数据和內容遷移準備 CSV。

1. 以整合管理員身份登錄學習管理器應用程式然後按下 **[!UICONTROL Migration]** 左側窗格。

   此時將顯示遷移專案首頁。 如果您的組織已創建遷移專案，則可以視圖此頁面中所有遷移專案的清單。

1. 按兩下 **[!UICONTROL New]** 頁面右上角，建立遷移專案。 或者，您可以按下 **[!UICONTROL Create a migration project]** 頁面上的連結以創建遷移專案。 建立出現移轉專案頁面。

   如果尚未建立 FTP 資料夾，系統會提示您在帳戶中建立 FTP 資料夾。 這是開始創建遷移專案之前的必步驟。

   ![](assets/create-project.png)
   *建立 FTP 資料夾*

   提供遷移專案的專案名稱、項目標記、課程目錄和描述。 按兩下 **[!UICONTROL Create]**。

   使用此遷移項目標記標識您的遷移數據項。 如果您沒有任何特定的課程目錄，請從下拉清單中選擇預設目錄。 您使用遷移項目遷移的所有課程都將包含在您在此階段選擇的目錄中。 如果未選擇任何目錄，則所有遷移的課程都將是預設目錄的一部分。

1. Sprint 配置頁面將显示，如以下快照所示。 您需要在遷移項目中創建衝刺 （sprint）。 選擇衝刺名稱並提供衝刺的簡要說明。 如果要在此衝刺 （sprint） 過程中遷移內容，可以選擇“是”。 按兩下 **[!UICONTROL Next]**。

   ![](assets/users-modified-sprint.png)
   *衝刺遷移*

   選中標題 **為“自上次運行**&#x200B;以來已添加或修改使用者”的複選框，以將使用者清單與學習管理器應用程式同步。 如果要將內容和数据遷移到學習管理器 應用程式，這可能不是必需的。 但是，如果從早期的衝刺遷移到最新的衝刺遷移之間存在時間間隔，那麼最佳實務您選擇同步使用者清單。 此步驟使學習管理器資料庫能夠與 LMS 使用者同步。

   移轉 enrollment.csv 和 用戶_course_grade.csv 時，建議執行此同步步驟。 此步驟使學習管理器資料庫能夠與遷移資料庫同步，並確保要在Sprint中遷移其記錄的所有使用者都可以在遷移資料庫中使用。

1. 您可以使用上傳的數據和內容開始 Sprint 遷移。 在開始衝刺運行之前按兩下連結， **[!UICONTROL Refresh]** 使用學習管理器應用程式同步 FTP 和內容資料夾。

   ![](assets/sprint1-filesupload.png)
   *開始衝刺遷移*

   按下 **[!UICONTROL Start]** 頁面右上角。 您可以在Sprint遷移過程中隨時按下 **[!UICONTROL Stop]** 以中止Sprint遷移。

   遷移狀態顯示在每個衝刺 （sprint） 數據項和內容上。 在遷移衝刺運行過程中檢查成功和失敗項目的數量。

   如果您要上載模組 內容，請確保在 模組_version.csv 中提供內容資料夾路徑。 如果您錯過了此步驟，可能會在遷移過程中遇到錯誤。 例如，如果您要上傳自定進度模組 內容（如視頻），則需要在 模組_version.csv 中指定相對的 Box URL 路徑。 針對活動 模組 內容，您可以指定URL名稱。

   下面提供了進度對話框的示例快照，供您參考。 如快照所示，您可以視圖為每個遷移數據項處理的記錄數以及成功和失敗項狀態。 按兩下針對要下載的失敗項目下載錯誤記錄並視圖錯誤日誌。 您可以在 CSV 中修正問題，然後在 FTP 中再次上傳。

   ![](assets/sample-sprint-progress-status.png)
   *檢視衝刺進度*

   如果要視圖遷移專案的所有衝刺清單，請按下左側窗格中的衝刺清單。 您可以視圖所有衝刺的清單、為每個衝刺執行的運行次數、開始日期、持續時間和完成狀態，如下面的示例快照所示。

   ![](assets/sprint-list.png)
   *衝刺檢視 清單*

1. 上傳最新更新的 CSV 后，可以按下頁面右上角的重新運行。 重新運行將再次處理所有資料項，忽略沒有任何更改的項。 對衝刺 （sprint） 中的數據項遷移感到滿意后，可以通過按兩下頁面頂部的按鈕將春季遷移標記為已完成。 您可以稍後開始包含更多數據項的新衝刺 （sprint）。 一旦衝刺被標記為完成，就不能再重新運行它。 同樣，在遷移專案中，您可以有任意數量的衝刺。 一旦你對所有衝刺的遷移狀態感到滿意，你可以通過按下 **頁面衝刺清單上的連結標記專案完整應用程式** ，將遷移項目標記為完整應用程式。

   在將遷移項目標記為已完成之前，必須確保專案的所有衝刺 （sprint） 都已完成。 將遷移項目標記為完成後，您將無法返回並在該專案中創建任何衝刺 （sprint） 或對該專案進行任何修改。 您必須創建另一個遷移專案並向其添加衝刺 （sprint）。

## 移轉驗證 {#registration}

從組織的舊版 LMS 遷移學習數據和內容后，您可以使用各種學習物件功能驗證導入的數據和內容。 例如，您可以以管理員身份應用程式登錄學習管理器，並驗證導入的模塊和課程數據和內容的可用性。

## 遷移中的改造 {#retrofittinginmigration}

此整合功能允許您將學習物件的歷史資料從舊式學習管理系統改裝到在學習管理器中創建的活動課程。

在下面找到可用於與現有 LMS 遷移數據進行映射的標準CSV規範。 按兩下 csv-specification、sample-csvs 以下載 zip 檔案。 下載的csv-specifications.zip包含四個 Excel 工作表檔案。 這些Excel工作表檔是帶有說明的規範，可讓您瞭解如何填寫.csv檔。 相應的.csv檔應包含規定格式中每個欄位的數據，如這些.xlsx檔中所述。

1-enrollment.xlsx-包含檔案所需中繼資料的說明retrofit_enrollment.csv。

2-certification_enrollment.xlsx-包含檔案所需中繼資料的說明retrofit_certification_enrollment.csv。

3-learning_方案_enrollment.xlsx-包含 RETROFIT_LEARNING_方案_enrollment.csv 檔案所需中繼資料的說明。

4-用戶_course_grades.xlsx-包含 RETROFIT_用戶_course_grades.csv 檔案所需中繼資料的說明。[csv-specifications.zip](assets/csv-specifications.zip)

>[!NOTE]
>
>UUID （通用唯一 ID） 也是移轉 csv 中的一欄。


## 移轉問題疑難解答 {#troubleshootingmigrationissues}

[按兩下此處](../../kb/troubleshooting-migration.md) 了解整合管理員在將資料和內容從現有 LMS 遷移到學習管理器應用程式時所面臨問題的解決方法/解決方案。

## 關於User Management的提示 {#usermanagement}

在本主題中，您可以找到一些提示，以瞭解如何在學習管理器中考慮和管理使用者。 這些概念將説明您在使用學習管理器CSV導入、連接器和遷移功能時更好地管理使用者。

## 學習管理器ID {#captivateprimeids}

學習管理員為使用者提供兩種類型的唯一 ID：

* 電子郵件ID
* UUID （通用唯一 ID）

學習管理器支援 UUID，為組織控制用戶帳戶提供靈活性。 身為管理員，如果您在帳戶中有使用者的 UUID，則可以修改該帳戶使用者的電子郵件 ID。

**UUID 在組織中的使用場景**

考慮員工 A 作為承包商加入名為「學習管理器」的公司的情況。 在合同期內，學習管理器公司可能不會提供公司電子郵件 ID，```A@example.com```相反，公司可能僅考慮員工的個人電子郵件帳戶，例如。 ```A@gmail.com```完成 6 個月的合同期後，如果同一員工 A 以全職員工身份加入學習管理員，則學習管理器可能需要將其電子郵件 ID 更改為公司電子郵件 ID： ```A@example.com```。

在上述場景中，擁有對用戶 帳戶的 UUID 訪問許可權將使 公司 學習管理器受益。 學習管理器公司可以輕鬆地將員工 A 的個人電子郵件 ID 替換為正式電子郵件 ID。 與此帳戶相關的員工記錄不受此更改的影響。

## 單一用戶識別 {#singleuseridentification}

學習管理器識別並記住如何添加單個用戶，例如，使用自註冊、使用CSV 上傳或使用用戶介面或通過 API 添加單個用戶。

* 如果使用使用者介面 （UI） 或透過 API 新增單個使用者，則可以使用UI或通過 API 刪除此類單個使用者。
* 您可以使用CSV上傳過程更新單個使用者，但您需要記住，這些單個用戶被視為CSV使用者，並且CSV工作流程適用於此類使用者。

## 指派管理員角色 {#assigningmanagerrole}

不能將管理員角色直接分配給學習管理器中的任何用戶。 僅當您將該帳戶中的任何用戶（例如 Y）的經理屬性設置為 X 時，用戶 X 才能成為學習管理員管理器。

在 X 是使用者的經理（例如 A、B 和 C）的情況下，如果 X 離開組織，則需要確保將 A、B 和 C 的 Manager 屬性設定為新的經理。 或者，您也可以將這些使用者的 Manager 屬性暫時設置為 ROOT，並在以後使用新的 Manager 名稱進行分配。

有關此主題的詳細信息，請参閱以下說明 內容：

* [上傳 CSV 的常見問題](/help/migrated/administrators/add-users-in-bulk.md)
* [新增使用者的功能說明](/help/migrated/administrators/feature-summary/add-users-user-groups.md)
