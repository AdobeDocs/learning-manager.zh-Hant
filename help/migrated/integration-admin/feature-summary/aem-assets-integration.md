---
description: 將 Adobe Experience Manager 資產中的學習內容與影像匯入 Adobe Learning Manager，並自動保持連結內容的最新。
jcr-language: en_us
title: AEM 資產整合
exl-id: cd33c0f2-59df-4f35-a7d9-d7bff6b9ffba
source-git-commit: 3c0f45721777421361401cf836a21b88cee3a259
workflow-type: tm+mt
source-wordcount: '3405'
ht-degree: 0%
---

# AEM 資產整合

## 概觀

Adobe Learning Manager 現已與 Adobe Experience Manager Assets as a Cloud Service 整合。 Teams 可以在 Adobe Experience Manager 資產中儲存學習內容與影像，匯入 Adobe Learning Manager，並從一處管理更新。 當資產變更時，內容庫中連結的內容可以自動更新，作者無需重新上傳檔案。

由於您的組織將資產集中管理，作者會使用目前且經品牌認可的檔案，而非下載並重新上傳副本。 Adobe Experience Manager Assets 也會保存每個檔案的版本歷史，讓您知道哪個版本曾上線以及何時上線。

設定是一次性的任務，也是最需要細心照顧的部分。 設定完成後，匯入素材就像一般上傳一樣。

>[!NOTE]
>
>此整合適用於所有擁有 Adobe Experience Manager 資產授權的 Adobe Learning Manager 帳戶，包括 Prime 與 Ultimate 帳戶。 兩者都適用相同的文件說明。

## 誰做什麼

| 角色 | 他們做什麼 |
|---|---|
| ALM 整合管理員 | 連接帳戶並選擇整合設定。 |
| Adobe 管理主控台管理員 | 將產生的技術帳戶指派至正確的 AEM Assets 產品設定檔。 |
| ALM 管理員 | 使用整合功能從不同位置匯入影像。 |
| ALM 作者 | 匯入內容與圖片，並建立課程。 |

每個角色在設定與使用整合時都有獨立的角色。

## 支援的部署

| 商品 | 支援 |
|---|---|
| Adobe Experience Manager Assets 雲端服務，作者實例 | 是的 |
| Adobe Experience Manager Assets 雲端服務、發佈或交付實例 | 不 |
| Adobe Experience Manager 本地部署 | 不 |

>[!NOTE]
>
>Adobe Learning Manager 之所以會連接到作者實例，是因為資產是在那裡建立和管理的。 發佈與交付實例並不包含在目前的整合中。

## 設定整合

將 Adobe Learning Manager 連接到 Adobe Experience Manager Assets，指派技術帳戶，並選擇您的更新設定。

此工作流程適用於整合管理員。 完成每一個步驟，讓自動更新能為您的作者有效運作。 設定包含五個部分：連接您的 IMS 組織、找到技術帳戶、在 Adobe 管理控制台中指派、選擇您的設定，以及授予作者存取權。

### 先決條件 {#setup-prerequisites}

您必須符合所有這些要求。 錯過其中任何一項是連線失敗最常見的原因。

* 您在 Adobe Learning Manager 中擁有整合管理員角色。 連線工作流程僅此角色可用。
* 您是所選擇的 Adobe 身份管理系統（IMS）組織的 IMS 組織管理員。
* 您至少可以存取一個組織，讓 AEM Assets 實例與 Learning Manager 關聯。

如果您不是 IMS 組織管理員，請請您的 IT 管理員授權您存取權限或與您連線。

### Adobe Learning Manager 如何映射到您的 IMS 組織

每個 Adobe Learning Manager 帳戶都會連接到一個 IMS 組織（也稱為 IMS 設定檔）。 規劃您的設定時請記得以下事項：

* 一個 IMS 組織可以包含多個程式與環境，每個程式都可以擁有 Adobe Experience Manager Assets 實例。 你可以在已連結的帳戶中使用上述任何一個實例。
* 不同 IMS 組織中的執行個體無法與該帳戶一起使用。
* 連結到一個 Adobe Learning Manager 帳戶的 IMS 組織，不能同時連結到另一個帳戶。

>[!NOTE]
>
>如果您的公司有多個 IMS 組織，請選擇持有您 Adobe Experience Manager Assets 授權及您希望作者使用的實例的組織。

### 連接您的 IMS 組織

1. 以整合管理員&#x200B;**身份登入 Adobe Learning Manager**。
1. 選擇 **Adobe Experience Manager 資產** 作為連接器類型。

   ![](assets/aem-assets-integrationstep1.png)

1. 選擇 **「連線**」。

   ![](assets/aem-assets-integrationstep2.png)

1. 當系統提示時，請以您的 Adobe ID 登入，並選擇包含您 Adobe Experience Manager Assets 實例的 IMS 組織。

   ![](assets/aem-assets-integrationstep3.png)

   ![](assets/aem-assets-integrationstep4.png)

Adobe Learning Manager 接著驗證您的 IMS 組織管理員角色及實例存取權。 若兩項檢查皆通過，系統會將您的帳戶連結至已建立且具有 AEM Assets Author API 範圍的 IMS 帳戶，並為您的組織建立技術帳戶。 接著開啟連線總覽頁面，並顯示技術帳戶詳細資訊。

### 尋找技術帳戶

技術帳戶是專為您的組織建立的。 Adobe Learning Manager 會利用它在背景中使用 AEM Assets [Open API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/) 來讀取或寫入。

1. 以 **整合管理員**&#x200B;身份登入，開啟 **Adobe Experience Manager 資產** 連線概覽頁面。
1. 在 **「憑證」** 區段，找到 **「技術帳戶」電子郵件**。
1. 複製技術帳戶的電子郵件。 你會使用它在 Adobe 管理主控台&#x200B;**中**&#x200B;尋找該帳戶。

### 在 Adobe 管理主控台中指派技術帳戶

將技術帳戶新增至您希望 Adobe Learning Manager 使用的每個 Adobe Experience Manager Assets 實例的產品設定檔。 例如，如果您有 10 個實例，但只希望其中 6 個能與 Adobe Learning Manager 搭配使用，請將帳號指派給這 6 個實例的個人檔案。

1. 以同一 IMS 組織的管理員身分登入 **Adobe Admin Console** 。
2. 選擇「 **產品與服務**」，然後選擇「 **Adobe Experience Manager 作為雲端服務**」。

   ![](assets/aem-assets-integration6.png)

3. 選擇您想與 Adobe Learning Manager 一起使用的實例。

   ![](assets/aem-assets-integration7.png)

4. 開啟擁有 Adobe Learning Manager 所需存取權限的產品設定檔。 例如，AEM 管理員設定檔。

   ![](assets/aem-assets-integration8.png)

5. 選擇 **「**&#x200B;新增 API 認證」。

   ![](assets/aem-assets-integration9.png)

6. 搜尋技術帳戶。 將其與您從整合管理員複製的技術帳戶電子郵件比對。 該帳戶通常排在清單的最底層。

   ![](assets/aem-assets-integration10.png)

7. 選擇技術帳戶，然後選擇 **「儲存**」。
8. 對每個你想使用的實例重複步驟 3 到 7。

如果設定檔的 API 認證清單為空，表示技術帳戶尚未指派。 欲了解更多產品設定檔與 API 憑證，請參閱 Adobe 管理主控台文件。

>[!IMPORTANT]
>
>不要跳過這一步。 如果您未指派技術帳戶，作者仍可從 Adobe Experience Manager 資產匯入資產，但自動更新無法運作。 接著您必須手動更新內容。

### 選擇您的整合設定

連線後，啟用連線並選擇 Adobe Learning Manager 如何處理更新與預覽。

| 背景設定 | 它的功能 |
|---|---|
| 自動更新 | 當資產在 Adobe Experience Manager Assets 中變更時，會更新連結的內容庫項目。 |
| 學習物件更新 | 同時也會將更新套用於使用 Content Library 項目的學習物件。 |
| 公開預覽連結 | 為支援內容建立預覽連結，並將其儲存在 AEM Assets 資產的元資料中。 |

「更新至學習物件」是自動更新的子設定。 只有在先啟用自動更新時才能啟用。 如果您關閉自動更新，作者會在內容庫中手動更新內容。

>[!IMPORTANT]
>
>這些設定的變更，包括關閉它們，可能需要長達一小時才會生效。 啟用連線後情況亦同。 延遲並不代表有什麼問題。 請等待最多一小時再進行測試。

### 授權作者存取 Adobe Experience Manager 資產 {#give-authors-access}

設定整合並不會讓作者存取您的資產。 每位匯入資產的 Adobe Learning Manager 作者或管理員，也必須擁有對應的 Adobe Experience Manager 資產作者實例的存取權。

* 將作者新增為同一 IMS 組織中 Adobe Experience Manager Assets 作者實例的使用者。
* 至少給他們瀏覽和選擇資產所需的存取權限。 您的 Adobe Experience Manager 管理員決定使用哪些角色與產品設定檔。

>[!NOTE]
>
>授予此存取權是您作為 Adobe Experience Manager 管理員的責任。 Adobe Learning Manager 並未規定特定角色。 如需使用者與設定檔協助，請參閱 Adobe Experience Manager 資產文件。

### 驗證設定

1. 請等待上述設定延遲結束。
1. 以擁有實例存取權的作者身分登入。
1. 在內容庫中&#x200B;**，選擇****瀏覽**，並確認 **AEM 資產**&#x200B;出現在裝置&#x200B;**旁**。
1. 匯入資產並確認其是否已匯入。
1. 如果資產被替換、是新版本或重新處理，大多數情況下會在幾分鐘內更新，少數情況下可能需要長達一小時。 如果需要超過一小時，您可以在 AEM Assets 中重新處理該資產。

## 從 Adobe Experience Manager Assets 匯入內容

從 Adobe Experience Manager Assets 匯入學習內容與影像，並建立持續更新內容的課程。

此工作流程適用於作者。 您的整合管理員必須先設定整合。

### 先決條件 {#import-prerequisites}

* 您的整合管理員已連接帳戶並啟用該連線。
* 您可以在已連接的 IMS 組織中存取存放您資產的 Adobe Experience Manager Assets 作者實例。 您的 Adobe Experience Manager 管理員授予此權限。 請參閱 [「授權作者存取 Adobe Experience Manager 資產](#give-authors-access)」。

啟用整合後，Adobe Learning Manager 中任何支援此整合的上傳選項都會顯示兩個來源：裝置與 AEM 資產。 這包括內容庫以及課程圖片的上傳選項。 裝置仍可用，因此您仍可從電腦上傳檔案。

### 您可以從哪裡匯入

支援 AEM 資產的上傳位置會出現 AEM 資產選項。 裝置上傳仍保留。 您可以匯入：

* 內容庫中的模組內容。
* 圖片，例如球場封面圖片和橫幅圖片。
* 工作輔助工具

只會顯示該上傳位置支援的檔案類型。 例如，封面圖片選項只顯示圖片。 支援的類型包括影像（JPEG、PNG、SVG）、影片（MP4）以及文件（PDF、SCORM 套件、PowerPoint 和 Word）。 檔案副檔名與大小限制與該位置其他上傳相同。

### 內容與圖片的處理方式不同

| 商品 | 處理方式 |
|---|---|
| 內容庫中的內容 | 複製並連結到來源資產，使其能自動更新。 |
| 圖片，例如封面與橫幅圖片 | 選取時會複製。 它們沒有連結，也不會自動更新。 |

### 將內容匯入內容庫

1. 開啟 **內容庫**，然後新增內容。
1. 選擇 **「**&#x200B;瀏覽」。
1. 選擇 **AEM Assets**。
1. 如果系統提示，請使用您的 Adobe ID 登入。
1. 在 **Adobe Experience Manager 資產** 視窗中，瀏覽至該資產。 如果您能存取多個儲存庫（AEM Assets 已啟用 AEM 實例），請視需要在它們之間切換。
1. 選取資產，然後完成上傳與儲存。
1. 使用內容群組建立您的課程。

請記住以下幾點：

* 您一次選擇一個資產。 無法支援批量匯入與資料夾匯入，且無法將現有的內容庫遷移至 Adobe Experience Manager 資產。
* 資產選擇器可讓您在 Adobe Experience Manager 資產中開啟資產。
* Adobe Learning Manager 不會直接從 Adobe Experience Manager Assets 傳送內容。 它會複製每個匯入的資產，並保留本地副本。
* 匯入的內容會像 Adobe Learning Manager 中其他內容一樣處理，包括學習者助理的轉錄。

### 新增工作輔助工具

從 AEM Assets 中選擇工作輔助檔案，例如 PDF 和參考文件，就像匯入內容庫內容一樣。

### 無法存取的作者

如果作者無法存取已連接 IMS 組織的 Adobe Experience Manager 資產，當他們選擇 AEM 資產時，會看到關於其有限存取權限的訊息。

## 保持內容最新

隨著 Adobe Experience Manager 資產的變更，保持連結內容庫項目的即時更新。

### 自動更新的運作方式

當從整合管理員區段啟用自動更新並指派技術帳戶時，Adobe Learning Manager 會讓內容庫與 Adobe Experience Manager 資產保持同步。

1. 在 Adobe Experience Manager Assets **中**，上傳資產的新版本，或還原先前版本。
1. Adobe Experience Manager Assets 會完成資產的處理。 如果資產被替換，大多數情況下會在幾分鐘內更新，少數情況下可能需要長達一小時。 如果需要超過一小時，您可以在 AEM Assets 中重新處理該資產。
1. Adobe Learning Manager 會更新連結 **的內容庫** 項目，並遞增版本號。
1. 如果 **啟用「更新至學習物件** 」，使用這些項目的學習物件也會同步更新。 目前註冊的學習者與未來學習者皆可獲得最新版本。
1. 學習者下次啟動內容時會獲得最新版本。 已開啟內容的學習者需要關閉並重新啟動內容。

更新不是即時的。 稍等片刻，並重新整理內容庫以查看變更。

### 手動更新內容

如果自動更新已關閉，或 Adobe 管理主控台中未指派技術帳戶，請手動更新內容：

1. 在內容庫&#x200B;**中**&#x200B;開啟該項目。
1. 從 AEM Assets **中選取已更新的檔案**。
1. 選擇「 **儲存**」。

### 更新如何跨地區適用

如果多語言內容庫項目的多個語系使用相同資產，更新該資產會更新所有這些語系。 使用不同資產的地區則不會受到影響。

### 資產可擁有多少個內容群組

單一資產最多可連結至 10 個內容群組。

>[!NOTE]
>
>規劃內容群組時，請將此納入考量。 如果您需要來自同一來源的超過 10 個內容群組，請使用資產的複本作為額外群組。

## 預覽 Adobe Experience Manager Assets 的內容

使用預覽連結來檢視 SCORM 與 HTML 內容，而無需以學習者身份啟動。

如果啟用公開預覽連結設定，Adobe Learning Manager 會為您匯入內容庫的支援內容建立預覽連結，並將其儲存在 Adobe Experience Manager 資產的資產元資料中。

預覽連結會為以下內容類型建立：

* SCORM 1.2
* SCORM 2004
* HTML

尋找並使用連結的方法：

1. 在 Adobe Experience Manager Assets 中，開啟該資產的屬性。
1. 在中繼資料中尋找預覽連結。

   <!-- TODO: The source document says "path to be mentioned here". Add the exact metadata location (confirm with Kranthi). -->

1. 複製連結並貼到瀏覽器中以預覽該資產。

任何打開資產元資料的人都能看到並使用這個連結。

>[!NOTE]
>
>使用預覽連結不會計入您的 ALM 授權使用量。 如果您關閉公開預覽連結，Adobe Learning Manager 在 Adobe Experience Manager 資產中建立的預覽檔案將會被移除。

## 當資產、存取權或連線變更時

了解刪除資產、失去存取權或斷線對內容的影響。

### 刪除資產時會發生什麼事 {#delete-asset}

已經使用該內容的課程即使刪除來源資產，仍然能正常運作。 刪除對內容庫的影響取決於內容群組的語系。

| 劇情 | 發生什麼事 |
|---|---|
| 該資產僅供多語言內容群組的一個地區使用。 | 該地點已被移除。 其他地點則保留。 |
| 資產是內容群組背後唯一的資產 | 內容群組已停用。 |

當內容群組被淘汰時：

* 現有的關卡會持續播放複製的內容。
* 您無法使用內容群組來建立新的課程關聯。
* 你無法編輯內容群組。

### 如果作者失去存取權限會發生什麼事

作者先前匯入的內容仍持續運作。 但作者無法從該實例匯入新資產、建立內容群組，或編輯使用該實例的現有內容群組。

### 如果你斷線會發生什麼事

匯入的內容和影像會保留在 Adobe Learning Manager 中，因為它們是複本。 連結到來源資產的連結已失效，因此連結內容不再更新。 學習物件與內容群組持續運作。

## 疑難排解

**我無法連接或看不到連接器**

請確認您在 Adobe Learning Manager 中擁有整合管理員的角色。

**即使我是 IMS 組織管理員，連線仍失敗**

請確保您在所選 IMS 組織中至少擁有一個 Adobe Experience Manager Assets 實例的存取權。 這種情況可能發生在您的 IT 支援團隊管理組織，但未指派至 Adobe Experience Manager Assets 產品時。 請您的 Adobe Experience Manager 管理員將您加入實例，然後再重新連線。

**我的 Adobe Experience Manager 資產實例未被列出**

請確認該實例屬於與您的 Adobe Learning Manager 帳戶連結的 IMS 組織，且是 Adobe Experience Manager Assets as a Cloud Service 的作者實例。

**我沒看到 AEM Assets 是上傳選項**

請您的整合管理員確認連線已啟用，並在啟用後最多一小時等待連線。

**作者無法看到資產或無法匯入**

請請您的 Adobe Experience Manager 管理員授權作者存取已連接 IMS 組織中的 Adobe Experience Manager 資產作者實例。

**內容沒有更新，或我的課程顯示的是舊內容**

1. 確認整合管理員設定中的自動更新已啟用，並等待變更生效。
2. 確認技術帳戶已指派至Adobe Admin Console中實例的產品設定檔。
3. 重新啟動內容。 如果還是顯示舊內容，就手動更新。

**內容群組已停用**

來源資產在 Adobe Experience Manager 資產中已被刪除。 請參閱 [刪除資產](#delete-asset)時會發生什麼事。

**預覽連結不會出現在資產的元資料中**

確認公開預覽連結已開啟，內容為 SCORM 1.2、SCORM 2004 或 HTML，且您在開啟設定後已等待最多一小時。

## AEM 資產整合 - 常見問題

**Q.ALM 是否直接從 AEM Assets 提供學習內容？**

**A.** 不。 我們會將內容從 AEM Assets 複製到 ALM，並在 ALM 中保留本地副本。

**Q.資產在 AEM Assets 中更新時會發生什麼事？**

**A.** 如果在 ALM 中啟用了自動更新選項，與 AEM Assets 相關的內容會同步更新，版本也會同步更新。

**Q.管理員能否控制 AEM 更新是否能自動傳送到課程？**

**答。** 是的。 在整合過程中，整合管理員應選擇「自動更新」，並決定更新是否也會自動套用於學習物件。 根據帳戶設定，學習物件的更新將會成功。

**Q.作者還能從電腦上傳檔案嗎？**

**答。** 是的

**Q.客戶能否將現有的 ALM 內容庫遷移至 AEM Assets？**

**A.** 不。 截至目前，並無此類規定。

**Q.整個 AEM Assets 資料夾可以匯入內容庫嗎？**

**A.** 不。 截至目前，並無此類規定。

**Q.整合是否支援大量匯入資產？**

**答：** 不，截至目前並無此規定。

**Q.可以從 AEM Assets 中選擇哪些 ALM 內容？**

**答：** 我們在每個上傳位置都支援與現今相同的副檔名。 當 AEM 內容顧問在該上傳接觸點開啟時，這些篩選器就會套用。

**Q.內容資產和影像資產的行為是否相同？**

**A.** 自動更新功能僅適用於內容資產，不適用於 ALM 中的任何其他資產。

**Q.原本來自 AEM Assets 的圖片，之後能否以本機檔案替換？**

**答。** 是的

**Q.ALM 作者可以查看哪些 AEM 資產？**

**A.ALM** 作者可以根據其在 AEM Assets 中的使用者權限，查看他們可存取的所有資料夾與檔案。

**Q.如果作者的 AEM 存取權限被移除會發生什麼事？**

**A.** 作者將無法從 AEM 資產中編輯或建立內容群組，因為他們已無法透過 AEM Content Advisor 存取該 IMS 設定檔的資產實例。

**Q.如果 AEM Assets 整合被停用或斷開連線會發生什麼事？**

**A.** 學習物件與內容群組仍然可用，但這些資產的自動更新功能將停止，且無法繼續。

**Q.整合是否支援本地部署的 AEM ？**

**A.** 不。 它只支援雲端實例。

**Q.一個 ALM 帳戶可以連接多個 AEM Assets 帳戶嗎？**

**答：** ALM 帳戶對應到 IMS 設定檔，且該 IMS 設定檔中的所有 AEM Assets 實例都可以連線並使用。 一旦 IMS 設定檔連結到某個 ALM 帳戶，該 IMS 設定檔就無法連結到另一個 ALM 帳戶。

**Q.從 AEM Assets 匯入的內容可以被學習者助理使用嗎？**

**A.** 如果使用 AEM Assets 匯入的內容來建立課程，則學習助理可在相關對話中引用該內容。

**Q.作者可以在選取 AEM 資產之前預覽它嗎？**

**A.** 不。 在選擇資產之前，預覽功能無法使用，但 AEM Assets 支援部分檔案格式的預覽功能。

**Q.ALM 會產生公開預覽連結嗎？**

**答：** 是的，僅限於 SCORM 1.2、SCORM 2004 及 HTML 檔案。 這僅在整合管理員啟用公開預覽功能時才可行。
