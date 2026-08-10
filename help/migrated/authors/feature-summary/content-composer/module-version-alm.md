---
description: 了解內容撰寫者如何在 Adobe Learning Manager 中處理課程更新——重新發布如何產生新模組版本，以及 ALM 作者如何更新現有課程以使用最新版本。
jcr-language: en_us
title: Adobe Learning Manager 中的模組版本管理
source-git-commit: ea6d296fa99686136ab08d756a20570a4681d704
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Adobe Learning Manager 中的模組版本管理

原始素材會隨時間改變——政策會修訂，標準作業程序會有新版本，簡報資料會更新。 Content Composer 和 ALM 會把刷新當作版本變更，而不是原地編輯，所以在你更新底層模組時，之前已發佈的課程會繼續運作。

當你重新發布時，Adobe Learning Manager 會將現有模組上傳為新版本，並將模組的版本號增加一。

1. 在內容撰寫器中，更新原始檔案並重新生成受影響的課程（參見「當原始資料變更時更新課程」），然後重新發布。

2. 發佈更新不會覆蓋現有模組——而是在 ALM 內容庫中新增一個新版本。

3. ALM 作者需要明確更新每門使用該模組的 ALM 課程，以指向新版本;現有課程會持續參考它們所建構的版本，直到 ALM 作者做出更改。

4. 已完成前一版本課程的學員則保留現有的完成紀錄。 新版本適用於在ALM課程更新後註冊的學習者。

在重新發布前，請先在內容撰寫器中檢視重製的課程內容。 Regenerator 可以調整受影響課程中先前編輯的文字、圖片或測驗題目。
