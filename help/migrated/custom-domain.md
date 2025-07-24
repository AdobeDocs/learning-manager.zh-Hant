---
jcr-language: en_us
title: 支援自訂網域
description: Learning Manager的Azure執行個體不支援自訂網域。
contentowner: saghosh
exl-id: 162ce268-48e3-4c7e-acb1-5181cebbb18d
source-git-commit: a09c81a6dacbfc4bb55db39e64820ba87ce53d09
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# 支援自訂網域

Learning Manager的Azure執行個體不支援自訂網域。

## 概觀 {#overview}

自訂網域支援可讓客戶完全控制可以在Learning Manager中用於其帳戶的網域名稱。 客戶需要單獨購買自訂網域，並與Adobe團隊合作，將其設定為其學習平台的登入URL。

這可讓客戶為登入和存取體驗加上白色標籤，讓使用者看不見任何Adobe或Adobe Learning Manager的存在。

例如，您想要自訂網域，讓使用者獲得與Adobe網域相同的體驗。 如果ABC Inc想要訓練其客戶，它希望他們登陸在名為`abc.com/mylearning`的網域上，而不是`learningmanager.adobe.com/abc-inc/mylearning`。

>[!NOTE]
>
>您必須先註冊網域，Adobe才會引導您自訂URL。


自訂網域功能需額外付費。 請聯絡您的客戶成功案例經理以瞭解更多詳細資訊。

* 對於學習者角色，網域將以`https://cdn.<customer_custom_domain>/`開頭，例如`https://cdn.elearningstage1.cpdomaintest.in/`
* 對於所有其他角色，網域將以`https://<customer_custom_domain>/`開頭。 例如， `https://elearningstage1.cpdomaintest.in/`
* 實際的登入URL將是`https://<customer_custom_domain>/acapindex`或`https://<customer_custom_domain>/login`。

>[!NOTE]
>
>將`<customer_custom_domain>`取代為您組織的實際網域。

## 如何在帳戶上設定自訂網域 {#howtosetupacustomdomainonanaccount}

作為先決條件，客戶必須擁有網域名稱並從提供者購買網域。

例如，假設客戶擁有虛擬網域&#x200B;**acme.com**。 客戶希望從&#x200B;**learning.acme.com**&#x200B;提供Learning Manager內容。

請依照下列步驟設定自訂網域。

1. 客戶必須在網域中&#x200B;**新增三個CNAME**&#x200B;記錄：

   * **learning.acme.com：** Adobe共用的Learning Manager ALB公用端點
   * **lrs.learning.acme.com：** learning.acme.com所指向的ALB公用端點
   * **cdn.learning.acme.com：**&#x200B;由Adobe共用的CDN端點

1. 客戶必須提供這些網域的SSL憑證：

   * learning.acme.com
   * lrs.learning.acme.com
   * cdn.learning.acme.com

1. Adobe會將這些SSL憑證上傳至AWS ALB，以處理對網域的請求。
1. Adobe將在其SAN憑證中新增learning.acme.com 。
1. Adobe將為客戶產生SP中繼資料，因為中繼資料將包含自訂網域URL。

   * 如果客戶希望使用社交登入，則Adobe必須在允許的url清單中包含社交網站的重新導向url模式。
   * 如果客戶已啟用SSO，則客戶必須與其IDP合作，將他們的網域納入重新導向URL中。 客戶必須與Adobe共用IDP中繼資料XML。 然後Adobe必須更新客戶帳戶的SSO設定。

1. 接著Adobe會修改S3 CORS規則，加入客戶的網域。
