---
description: 了解更多關於如何在 Adobe Learning Manager 中設定進階設定
jcr-language: en_us
title: Adobe Learning Manager 的進階設定
exl-id: 7047c89f-5f1c-4e0a-a908-20ef0eb9667d
source-git-commit: 0862e0d042fac74377b44c3387a72336ec625161
workflow-type: tm+mt
source-wordcount: '2357'
ht-degree: 0%

---

# Adobe Learning Manager 的進階設定

## 目錄標籤

Adobe Learning Manager 中的目錄標籤用於標註學習對象（課程、認證、學習路徑等） 具有特定的欄位和數值。 這些標籤幫助你和作者有效分類與組織內容，促進更好的篩選、追蹤與報告。

更多資訊請參閱 [Adobe Learning Manager](/help/migrated/administrators/feature-summary/catalog-labels.md) 中的目錄標籤。


>[!NOTE]
>
>* 強制標籤：你可以選擇在課程創建時強制作者使用目錄標籤。
>* 作者工作流程：作者在建立或編輯課程時必須加上合規標籤，以確保分類正確。

## 內容資料夾

Adobe Learning Manager 中的內容資料夾控制哪些作者能在內容庫中看到和存取內容。 透過階層式內容資料夾，管理員可以將大型內容庫組織成多達三層巢狀的私密資料夾，讓內容更容易在組織內尋找、管理和重複使用。

### 什麼是內容資料夾

內容資料夾是一個容器，用來將相關內容分組並決定誰可以存取。 Adobe Learning Manager 中的每個內容檔案至少屬於一個資料夾。

內容資料夾有兩種類型：

**公共資料夾**——預設存在於每個帳號。 public 資料夾具有以下屬性：

* 帳號內的所有作者都能存取公開資料夾中的內容。
* 公開資料夾中的內容不能放在任何私人資料夾裡。 反過來也成立。 私人資料夾中的內容不能放在公開資料夾中。
* 公用資料夾不包含在角色基礎存取設定中。 限制自訂角色僅限於特定私人資料夾，並不限制對公開資料夾的存取。

**私人資料夾**——由管理員建立。 私有資料夾支援三層階級結構，存取權透過角色設定來控制。

**了解資料夾階層層級**

私人內容資料夾支援最多三層巢狀結構：

* **第一層資料夾**——位於你內容庫根部的頂層資料夾

* **Level 2 資料夾**——位於 Level 1 資料夾中的子資料夾

* **Level 3 資料夾** — 嵌入 Level 2 資料夾中的子資料夾

這種結構讓組織能夠靈活地依照現實世界的內容組織，依主題領域、交付類型、受眾或團隊來規劃，而不必管理數千個平坦清單中的檔案。

只有管理員能在任何層級建立、編輯或刪除資料夾。 作者與自訂使用者可與階層互動，但無法修改。

### 資料夾命名規則

資料夾名稱必須在同一層級內，在同一父資料夾內唯一。 具體來說：

| **劇本** | **允許？** |
|----------------------------------------------------------------------------------------------|--------------------------|
| 兩個同名的 Level 1 資料夾 | 不 |
| 同一個等級一資料夾下有兩個等級二的資料夾，名稱相同 | 不 |
| 兩個同名的 Level 1 資料夾，分別位於不同的 Level 1 資料夾下 | 是的 |
| 一個是 Level 2 資料夾，另一個是同名的 Level 3 資料夾 | 是的。 等級是有區別的 |
| 一個 Level 3 資料夾，另一個同名的 Level 2 資料夾 | 不 |


### 資料夾路徑的出現方式

內容庫會顯示每個內容檔案的完整資料夾路徑。 例如，**培訓計畫**> **SCORM 資產**>**入職**&#x200B;培訓。此路徑顯示內容的完整位置。

如果檔案存在於多個資料夾中，所有路徑都會以逗號分隔。 若路徑較長，則從一開始以省略號截斷（...），且最深的資料夾名稱始終顯示。

### 基於角色的資料夾存取

私人資料夾的存取權限僅&#x200B;**在**&#x200B;第一級分配。當自訂角色被授權存取 Level 1 資料夾時，該存取權會自動串接到該資料夾內所有 Level 2 和 Level 3 子資料夾。 沒有選項可以獨立授權子資料夾層級的存取權限。

下表說明每個角色在資料夾階層中能做什麼。

| **角色** | **他們能做的事** |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| 行政長官 | 建立、重新命名及刪除第 1、第 2 及第 3 層的私人資料夾;設定自訂角色的第 1 層資料夾存取權限 |
| 自訂管理員 | 管理可存取的 Level 1 分支資料夾，並依其分配的權限管理 |
| 作者 | 瀏覽資料夾、依資料夾篩選內容、將內容加入資料夾、複製並移動內容到資料夾間，新增模組時選擇內容 |
| 自訂作者 | 和作者一樣，但只能透過他們指定的 Level 1 權限存取資料夾 |

### 資料夾結構限制

| **極限** | **價值** |
|---------------------------------------|-----------|
| 每個帳號的 Level 1 資料夾 | 沒有限制 |
| 第二層子資料夾對應第一層資料夾 | 25 |
| 第三層子資料夾對應第二層資料夾 | 25 |
| 最大資料夾深度 | 三個關卡 |


### 資料夾選擇行為

例如，當你選擇資料夾時，過濾或刪除時，選取會依下列方式依序排列：

* 選擇 **Level 1 資料夾** 會自動選取該資料夾下所有 Level 2 和 Level 3 資料夾。

* 選擇 **第二級資料夾** 會自動選取該資料夾下所有第三級資料夾。 同一層級 1 資料夾下的其他 Level 2 資料夾則未被選取。

* 選擇 **Level 3 資料夾** 只會選擇該資料夾。 沒有選取其他資料夾。

>[!NOTE]
>
>當你選擇子資料夾但未選擇父資料夾時，該子資料夾不會顯示部分或混合選取指示器。 這是刻意安排的。 因為父資料夾本身可以包含內容，而不只是子資料夾。 選擇父資料夾的意思是「包含這個資料夾裡的所有內容，以及它下面的所有內容」。 部分指示會暗示父資料夾本身的內容部分包含，這會誤導人。 如果你只想依特定子資料夾篩選，請直接選擇該子資料夾。 如果你想把所有內容放在父資料夾及其子資料夾，請選擇父資料夾。

### 何時使用階層式資料夾結構

當組織管理大量內容檔案，需要有結構的方式來瀏覽、重用及控制存取時，階層式內容資料夾特別有價值。

常見情境包括：

* **大型內容庫**：當你有數千個內容檔案時，三層級的階層結構讓作者能直接找到所需資料，而不必在平面清單中滑動。

* **多個團隊或專案**：第一層資料夾可分隔團隊或專案區域;第二層資料夾可依交付類型組織;第三層資料夾可存放個別資產。

* **基於角色的內容分離**：當不同作者團隊應僅存取與其工作相關的內容時，第一層資料夾存取權指派可保持各團隊內容的私密。

### 階層式內容資料夾的實際應用案例

**使用情境一 - 針對特定司法管轄區內容的合規訓練**

全球性組織在多個地區強制執行合規訓練。 每個地區都有適用於所有人的核心模組，以及司法管轄區特定的法律附錄，例如資料隱私規定、當地勞動法、財務揭露要求，這些規定因國家或地區而異。

若沒有階層式資料夾，所有合規資產都放在一個平面清單中，使區域內容團隊難以分辨哪些檔案屬於哪個計畫或管轄區。

採用三層結構：

* 第一級：合規訓練

* 第二層級：EMEA / APAC / 美洲（每個區域一個子資料夾）

* 第三層級：特定區域的模組或資產（隱私規範 PDF、地方政策資料、評估檔案）

區域作者團隊僅可進入其第一級或第二級分支。 他們只能找到、更新並重複使用與其管轄區相關的資產，而不會看到或意外修改其他地區的內容。

**使用情境二 - 擁有多種角色的大規模入職計畫**

組織每年會以不同角色招募數千名員工：個人貢獻者、經理、承包商及技術專家。 每個職位都有自己的入職訓練軌，包含共享的基礎內容和職務專屬模組。

採用三層結構：

* 第一階段：入職

* 等級2：角色（個人貢獻者/經理/承包商/技術專員）

* 第三級：模組類型（SCORM 套件/ILT 卡組/活動指南/評量）

為每個職位建立課程的作者會直接進入第二級，找到該方向的精確檔案。 當模組跨角色重複使用時，例如公司價值影片，可以複製或連結到多個資料夾中而不產生重複。 內容保持單一來源，但會出現在所有相關分支中。

**使用情境三 - 擁有多個內容團隊的高量技術技能庫**

一家科技公司維護一個內部技能培訓庫，包含數千個涵蓋產品線、雲端基礎設施、開發工具、安全與資料工程的內容檔案。 多個作者團隊共同貢獻，各自負責一個產品領域。 課程模組每門課可執行40至60個檔案。

沒有階層制度，成千上萬的檔案都集中在少數頂層資料夾中，不同團隊的作者經常選擇錯誤的檔案版本或不小心覆蓋共享資產。

採用三層結構：

* 第一層級：產品領域（雲端/開發工具/安全/資料工程）

* 第二級：課程名稱

* 第三級：資產類型（影片/PDF/SCORM/測驗）

每個產品團隊僅能存取其第一層資料夾。 要找到特定課程的測驗，就是要精確找到正確的第三級資料夾，而不是在成千上萬的檔案中搜尋。 當安全團隊更新 SCORM 套件時，他們知道該套件存在於 SCORM > > [課程名稱] 中，不會誤落到其他團隊的分支。

### 以管理員身份管理內容資料夾

作為 Adobe Learning Manager 的管理員，你可以建立並維護內容資料夾的階層結構，控制哪些自訂角色可以存取特定資料夾，並管理資料夾名稱與刪除。 作者可以將內容加入資料夾並在階層中組織內容，但只有管理員能建立、重新命名或刪除資料夾。

#### 建立內容資料夾

>[!NOTE]
>
>同父目錄下同層級的兩個資料夾不能共用名稱。 不同分支或不同層級允許使用相同名稱。

1. 以管理員身份登入 Adobe Learning Manager。
2. 在左側導覽中，選擇 **設定** > **設定**。
3. 在 **進階** 區塊中，選擇 **內容資料夾**。
4. 在頁面右上角選擇 **新增** 。 **新增資料夾**&#x200B;對話框會打開。
5. 輸入資料夾名稱和可選的描述。
6. 選擇 **儲存**。 該資料夾會被建立並顯示在資料夾清單中。


#### 建立子資料夾

1. 在 **內容資料夾** 頁面，找到父資料夾。
2. 選擇 **資料夾名稱旁的「建立子資料夾** 」選項。
3. 輸入子資料夾的名稱和可選的描述。
4. 選擇 **儲存**。 子資料夾會在資料夾列表中以縮排方式顯示在其父資料夾下方。

>[!NOTE]
>
>每個資料夾最多可包含 25 個直接子資料夾。 3級是最大深度。 你無法在第三層資料夾中建立子資料夾。

#### 重新命名資料夾

1. 在 **內容資料夾** 頁面，選擇你想重新命名的資料夾。 資料夾會以編輯模式開啟。
2. 更新資料夾名稱，必要時更新描述。
3. 選擇 **儲存**。 資料夾會以新名稱儲存。

#### 刪除資料夾

刪除前，請注意以下規則：

* 你可以在任何層級刪除空資料夾。
* 如果資料夾包含與其他資料夾沒有連結的內容，你就無法刪除。 先把那些內容移到另一個資料夾。
* 刪除父資料夾會刪除它所有的子資料夾。 選擇父資料夾會自動選取其所有子資料夾。

#### 刪除父資料夾

1. 在 **內容資料夾** 頁面，選擇你想刪除的每個資料夾旁的勾選框。
2. 在頁面右上角選擇 **「動作** 」> **「刪除資料夾** 」。
3. 當被要求刪除時確認刪除。 父資料夾內的所有子資料夾也會被刪除。

#### 刪除子資料夾

1. 在 **內容資料夾** 頁面，選擇你想刪除子資料夾旁的勾選框。
2. 在頁面右上角選擇 **「動作** 」> **「刪除資料夾** 」。
3. 當被要求刪除時確認刪除。 子資料夾已被刪除。

>[!CAUTION]
>
>刪除資料夾是永久的。 確認資料夾內所有內容都已移至其他位置再確認。


#### 設定自訂角色的資料夾存取權限

你可以將自訂角色限制在特定的 Level 1 資料夾，讓擁有這些角色的自訂管理員和作者只看到與他們相關的內容。

存取權限僅&#x200B;**設定在** Level 1 資料夾層級。當你授權自訂角色存取一個 Level 1 資料夾時，該角色會自動取得裡面所有 Level 2 和 Level 3 子資料夾的存取權。 你無法獨立在子資料夾層級分配存取權限。

1. 在左側導覽中，選擇 **「使用者** > **自訂角色**」。
2. 打開你想設定的自訂角色，或是建立一個新的。
3. 在帳號權限&#x200B;**下**，找到&#x200B;**內容資料夾**&#x200B;區塊。
4. 選擇 **「選取資料夾**」。
5. 選擇這個角色應該能存取的 Level 1 資料夾。
6. 選擇 **確定**。

擁有此角色的使用者只會看到所選第一層資料夾及其子資料夾的內容。 其他私人資料夾及公開資料夾中的內容對他們仍無法存取。

#### 最佳實務

以下做法能幫助你建立一個能良好擴展且易於操作的資料夾結構。

1. **在建立資料夾前先規劃好你的結構。** 一旦內容被組織成階層，重組就需要移動大量內容。 在開始之前，先決定你的第一級類別，例如產品線、部門或培訓計畫。

2. **使用三個層級來進行有意義的分組。** 常見的模式是：廣泛領域或計畫為第一級，交付類型或團隊為第二級，個別資產為第三級。 例如：

   * 第一級：銷售訓練

   * 第二級：自我進度模組

   * 第三層級：PDF 資產

3. **名字保持簡短、具描述性，且在父母中獨一無二。** 避免使用像「模組1」或「內容」這類通用名稱。 使用使用者瀏覽圖書館時能理解的識別碼。

4. **只在 Level 1 時才分配自訂角色權限。** 由於存取會自動連鎖處理，第一級指派即可，並使存取管理更簡單。 新增 Level 2 或 Level 3 子資料夾時，不需要更新存取權限。

5. **刪除資料夾前先移動內容。** 如果資料夾中的內容沒有連結到其他地方，刪除就會被阻擋。 養成刪除前檢查資料夾內容的習慣。


<!--

**Key points:**

A folder is a repository of content, which is a subset of the entire content library available in an account with the following properties:

* Only you (administrator) can create, edit, or delete a folder.
* You can control access to folders as part of defining roles only for custom administrators.
* Content must at all times be associated with at least one folder. To start with, all content will be associated with the public folder, which can later be changed.
* Content can be associated with multiple folders at the time of creation, which will also be possible by a copy operation
* All folder names must be unique within the account, otherwise there will be an error in naming a folder.

Folders only control visibility of content and don't create copies of content. Therefore, editing content will reflect in all the associated folders.

**Public folder**

A public folder is always present in an account and initially, all content will be part of this folder. Later, authors can move content out of this folder into other folders. A public folder has the following properties:

* All content associated with this folder will be accessible to all types of authors, by default.
* Any content that is a part of a public folder, cannot be part of any other folder. The converse also holds true.

This folder cannot be part of configurable role definition. Consequently, not having a public folder in configurable role definition doesn't restrict access to a public folder.

**Private folder**

Any folder created by you is a private folder.

**Add a content folder**

To add a content folder, follow the steps:

1. Select **[!UICONTROL Settings]** > **[!UICONTROL Content Folder]**.
2. Select **[!UICONTROL Add]** to create a new folder.
3. Type the name and description of the folder to be created.
 
    ![alt text](assets/advanced-settings-picture1.png)

4. Select **[!UICONTROL Save]** to create the folder.

**Folder operations**

* **[!UICONTROL Add a folder]**: To add a folder, select the folder, and then select **[!UICONTROL Add]** on the upper-right corner of the screen.
* **[!UICONTROL Delete a folder]**: To delete a folder, select the folder to delete, select the **[!UICONTROL Actions]** menu, and then select **[!UICONTROL Delete Folder]**.
-->

## 教室地點

建立並管理實體或虛擬教室的圖書館。 這些地點可供作者與管理者使用，舉辦由講師主導的訓練（ILT）活動。 此功能確保教室細節如座位限制與地點資訊皆預先設定且易於存取。

更多資訊請參閱 [Adobe Learning Manager](/help/migrated/administrators/feature-summary/classroom.md) 中的「新增教室地點」。

## 報表

此區塊允許您設定合規與群組成功儀表板。

![替代文字](assets/advanced-settings-picture2.png)

更多資訊請參見以下內容：

* [合規儀表板](/help/migrated/administrators/feature-summary/reports.md#compliance-dashboard)
* [團體成功儀表板](/help/migrated/administrators/feature-summary/group-success-dashboard.md)
