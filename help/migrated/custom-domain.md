---
jcr-language: en_us
title: 支援自訂網域
description: Azure 的 Learning Manager 實例不支援自訂網域。
contentowner: saghosh
exl-id: 162ce268-48e3-4c7e-acb1-5181cebbb18d
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%
---
# 支援自訂網域

Azure 的 Learning Manager 實例不支援自訂網域。

## 概觀 {#overview}

自訂網域支援讓客戶能完全掌控他們在學習管理員中可用於帳戶的網域名稱。 客戶需要另外購買自訂網域，並與 Adobe 團隊合作，將其設為學習平台的登入網址。

這讓客戶能將登入與存取體驗標示為白標，讓使用者不會看到 Adobe 或 Adobe Learning Manager 的存在。

例如，你想自訂網域，讓使用者擁有與 Adobe 網域相同的體驗。 如果 ABC Inc 想要訓練他們的客戶，他們希望他們能選擇一個名為 `abc.com/mylearning`的網域，而不是 `learningmanager.adobe.com/abc-inc/mylearning`。

>[!NOTE]
>
>作為前提，你必須註冊網域，Adobe 會引導你自訂網址。


自訂網域功能需額外付費使用。 請聯絡您的客戶成功經理以了解更多細節。

* 對於學習者角色，領域會以以下 `https://cdn.<customer_custom_domain>/` 方式開頭。例如， `https://cdn.elearningstage1.cpdomaintest.in/`
* 其他角色的領域將以 `https://<customer_custom_domain>/`開頭。 例如， `https://elearningstage1.cpdomaintest.in/`
* 實際的登入網址會是 `https://<customer_custom_domain>/acapindex` 或 `https://<customer_custom_domain>/login`。

>[!NOTE]
>
>用你組織的實際網域來取代 `<customer_custom_domain>` 。

## 如何在帳號上設定自訂網域 {#howtosetupacustomdomainonanaccount}

作為前提，客戶必須擁有網域名稱，並向供應商購買該網域。

舉例來說，假設一位客戶擁有一個虛構網域，acme.com **&#x200B;**。客戶希望學習經理的內容能從 **learning.acme.com** 提供。

請依照以下步驟設定自訂網域。

1. 客戶必須 **在網域中新增三個 CNAME** 記錄：

   * **learning.acme.com：** Adobe 共享的 Learning Manager ALB 公開端點
   * **lrs.learning.acme.com：** 由 learning.acme.com 指向的 ALB 公共端點
   * **cdn.learning.acme.com：** Adobe 共享的 CDN 端點

1. 客戶必須為以下網域提供 SSL 憑證：

   * learning.acme.com
   * lrs.learning.acme.com
   * cdn.learning.acme.com

1. Adobe 會將這些 SSL 憑證上傳到 AWS ALB，用於向網域發送請求。
1. Adobe 會在他們的 SAN 認證中加入 learning.acme.com。
1. Adobe 會為客戶產生 SharePoint 的元資料，因為該元資料會包含自訂的 domian URL。

   * 若客戶希望使用社群登入，Adobe 必須將社群網站的重定向網址模式納入允許的網址清單中。
   * 如果客戶已啟用 SSO，則必須與其 IDP 合作，將網域納入重定向網址中。 客戶必須與 Adobe 分享 IDP 元資料 XML。 Adobe 必須更新客戶帳號的 SSO 設定。

1. Adobe 接著會修改 S3 CORS 規則，納入客戶的網域。
