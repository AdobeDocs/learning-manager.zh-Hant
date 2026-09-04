---
jcr-language: en_us
title: 為 Adobe Learning Manager 內容撰寫器配置 Creative Cloud 儲存
description: 學習如何為 Adobe Learning Manager 內容撰寫器設定 Creative Cloud 儲存。 本指南說明為何需要 Creative Cloud 儲存，管理員如何在 Adobe 管理控制台中指定免費會員，以及如何排解儲存相關存取問題。
contentowner: saghosh
source-git-commit: 42512cc4cab0d0cdb1e9796610d6fc2f7b5c51d6
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---


>[!IMPORTANT]
>
>此文件適合誰：需要啟用 Adobe Learning Manager 使用者 Creative Cloud 儲存，以便存取並使用 Content Composer。 對於管理員處理儲存相關登入或存取錯誤，以及透過 Adobe 管理控制台分配免費會員優惠，特別有用。


Adobe Learning Manager （ALM） 內容撰寫器要求使用者與其 Adobe 帳號綁定 Creative Cloud 儲存空間。 沒有 Creative Cloud 儲存空間的使用者可能無法存取 Content Composer，並可能遇到登入或存取相關的錯誤。

為協助組織為受影響使用者配置儲存空間，Adobe 提供免費會員優惠，管理員可透過 Adobe 管理控制台指派。 此方案包含 Creative Cloud 儲存，適用於尚未提供儲存權限的方案使用者。

## 在你開始之前

確保：

* 你擁有 Adobe 管理控制台的管理員權限。
* 需要內容撰寫者存取權限的使用者會被識別。
* 你已經確認使用者是否已經有包含 Creative Cloud 儲存的方案。

## 為什麼使用者需要 Creative Cloud 儲存

Content Composer 使用 Creative Cloud 儲存空間來儲存課程。 未為 Adobe 設定檔分配儲存空間的使用者，嘗試使用 Content Composer 時可能會收到錯誤訊息。

![內容作曲家儲存錯誤](../assets/coco-storage1.png)

許多 Adobe 客戶已透過現有產品擁有 Creative Cloud 儲存空間，且未受影響。 然而，部分 Adobe Learning Manager 客戶可能預設未配置儲存空間，可能需要管理員啟用。

## 啟用免費的 Creative Cloud 儲存空間給使用者

如果使用者沒有 Creative Cloud 儲存空間，請從 Adobe 管理控制台設定免費會員優惠。

1. 使用擁有管理員權限的帳號登入 [Adobe 管理控制台](https://adminconsole.adobe.com/) 。 只有管理員能指派產品和優惠給使用者。
2. 從管理控制台中選擇產品>試用與特別優惠。

   ![管理控制台的試用與特別優惠](../assets/coco-storage2.png)

3. 在試用與特別優惠中尋找免費會員優惠。 這是建議尚未擁有儲存權限的使用者啟用 Creative Cloud 儲存的方法。

   ![免費會員優惠](../assets/coco-storage3.png)

4. 將免費會員優惠分配給所需用戶。 指派只能由擁有適當管理主控台權限的管理員完成。
5. 完成任務後，請確認使用者有 Creative Cloud 儲存空間，並請使用者重新登入 Content Composer。

## 透過免費會員提供的儲存空間

擁有免費會員的用戶可獲得約 2 GB 的 Creative Cloud 儲存空間，讓他們可以使用 Content Composer。

## 疑難排解

**使用者在存取內容撰寫器時會收到錯誤**

請確認使用者的 Adobe 個人檔案中是否有 Creative Cloud 儲存空間。

**使用者無法看到免費會員優惠**

確認這一點：

* 你已以管理員身份登入。
* 您正在瀏覽 Adobe 管理控制台的產品區。
* 該組織有資格使用此優惠。

## 常見問題

**每個 Adobe Learning Manager 使用者都會自動收到 Creative Cloud 儲存空間嗎？**

不。 部分 ALM 使用者可能預設未設定儲存空間，可能需要透過免費會員服務獲得額外權限。

**使用者可以自行啟用儲存嗎？**

不。 儲存權限必須由 Adobe 管理員透過管理控制台指派。

**內容撰寫者需要 Creative Cloud 儲存嗎？**

是的。 Content Composer 依賴使用者將 Creative Cloud 儲存與 Adobe 帳號綁定。

**如果使用者遇到與儲存相關的錯誤，管理員應該怎麼做？**

確認使用者是否擁有 Creative Cloud 儲存權限。 如果沒有，請透過 Adobe 管理控制台指定免費會員優惠，讓使用者重新嘗試。

**如果管理員仍有存取權或權利問題，應該怎麼做？**

若 Adobe 管理控制台管理員在指派 Creative Cloud 儲存或除錯存取相關問題時遇到問題，該問題可能需要企業帳號層級支援。 在這種情況下，請透過管理控制台中的支援選項聯絡 Adobe 企業支援。

欲了解更多資訊，請參閱 [Adobe 企業支援選項](https://helpx.adobe.com/business/enterprise/get-help/support-options/support-for-enterprise.html)
