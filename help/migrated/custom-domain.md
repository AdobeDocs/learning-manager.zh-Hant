---
jcr-language: en_us
title: 支援自訂網域
description: Learning Manager的Azure執行個體不支援自訂網域。
contentowner: saghosh
source-git-commit: 8635072782253cbac3f913953797cae7c0bc5ef4
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---



# 支援自訂網域

Learning Manager的Azure執行個體不支援自訂網域。

## 概觀 {#overview}

自訂網域支援可讓客戶完全控制可在Learning Manager中用於帳戶網域名稱。 客戶需要單獨購買自訂網域，並與Adobe團隊合作，將其設定為學習平台的登入URL。

這可讓客戶為登入和存取體驗加上白色標籤，讓使用者看不到任何Adobe或AdobeLearning Manager的存在。

例如，您想要自訂網域，讓使用者獲得與Adobe網域相同的體驗。 如果ABC Inc想要訓練他們的客戶，他們想要登陸到一個名為的網域 `abc.com/mylearning`，而非 `learningmanager.adobe.com/abc-inc/mylearning`.

>[!NOTE]
>
>您必須先註冊網域，然後Adobe會引導您自訂URL。


自訂網域功能需額外付費。 請聯絡您的客戶成功案例經理以瞭解更多詳細資訊。

* 若為學習者角色，網域開頭將為 `https://cdn.<customer_custom_domain>/` 例如， `https://cdn.elearningstage1.cpdomaintest.in/`
* 對於所有其他角色，網域的開頭將為 `https://<customer_custom_domain>/`. 例如， `https://elearningstage1.cpdomaintest.in/`

`<customer_custom_domain>` 是可自訂的零件。

## 如何在帳戶上設定自訂網域 {#howtosetupacustomdomainonanaccount}

作為先決條件，客戶必須擁有網域名稱並從提供者購買網域。

例如，我們假設客戶擁有虛構的網域， **acme.com**. 客戶希望從提供Learning Manager內容 **learning.acme.com**.

請依照下列步驟設定自訂網域。

1. 客戶必須 **新增三個CNAME** 網域中的記錄：

   * **learning.acme.com：** Adobe共用的Learning Manager的ALB公用端點
   * **lrs.learning.acme.com：** learning.acme.com所指向的ALB公用端點
   * **cdn.learning.acme.com：** Adobe共用的CDN端點

1. 客戶必須提供這些網域的SSL憑證：

   * learning.acme.com
   * lrs.learning.acme.com
   * cdn.learning.acme.com

1. Adobe會將這些SSL憑證上傳至AWS ALB，以處理對網域的請求。
1. Adobe將在其SAN憑證中新增learning.acme.com 。
1. Adobe將為客戶產生SP中繼資料，因為中繼資料將包含自訂網域URL。

   * 如果客戶希望進行社交登入，則Adobe必須在允許的url清單中包含社交網站的重新導向url模式。
   * 如果客戶已啟用SSO，則客戶必須與其IDP合作，將他們的網域納入重新導向URL中。 客戶必須與Adobe共用IDP中繼資料XML。 Adobe則必須更新客戶帳戶的SSO設定。

1. Adobe接著會修改S3 CORS規則，加入客戶的網域。
