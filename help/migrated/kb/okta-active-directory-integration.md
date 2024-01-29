---
jcr-language: en_us
title: Okta Active Directory與Adobe Learning Manager整合
description: Okta Active Directory與Adobe Learning Manager整合
contentowner: nluke
source-git-commit: 6abc118c6ad7e66e3ded5bd26b9167c3a0b99e4b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---



# Okta Active Directory與Adobe Learning Manager整合 {#okta-active-directory-integration-with-adobe-learning-manager}

在本檔案中，您將瞭解如何將Adobe Learning Manager與Okta Active Directory (AD)整合。 將Adobe Learning Manager與Okta AD整合時，您可以：

* 檢查並控制Learning Manager使用者在Okta AD中的存取權。
* 讓使用者能夠使用其Okta AD帳戶自動登入AdobeLearning Manager。
* 在一個中央位置（Okta入口網站）管理您的帳戶。

AdobeLearning Manager支援身分提供者(IdP)和服務提供者(SP)起始的SSO。

## 在OKTA中建立應用程式

1. 以管理員身分登入Okta AD。
1. 按一下 **[!UICONTROL Applications]**. 如此即會在Okta中開啟應用程式商店。

   ![](assets/cp-application-store.png)

   *在Okta中檢視應用程式商店*

1. 按一下 **[!UICONTROL Create App Integration]**.

   ![](assets/cp-app-integrations.png)

   *選取建立應用程式整合*

1. 選取 **[!UICONTROL SAML 2.0]** 從「新應用程式整合」視窗。

   ![](assets/cp-saml2.0.png)

   *選取SAML2.0選項*

1. 選取 **[!UICONTROL Create SAML integration]** > **[!UICONTROL General settings page]**. 輸入應用程式名稱。

   請注意，這可以是任何可唯一識別您應用程式的名稱。 完成後，按一下 **[!UICONTROL Next]**.

   ![](assets/cp-saml-integration.png)

   *輸入應用程式的名稱*

1. 在「配置SAML設定」頁面上執行下列步驟：

   **若為IDP設定：**

   1. 在「單一登入URL」欄位中，輸入URL： [https://learningmanager.adobe.com/saml/SSO](https://learningmanager.adobe.com/saml/SSO)
   1. 在「對象URL」欄位中，輸入URL： [https://learningmanager.adobe.com](https://learningmanager.adobe.com/)
   1. 在 **名稱ID格式** 下拉式方塊，選取 **電子郵件地址**.
   1. 在 **應用程式使用者名稱** 從下拉式清單中選取Okta使用者名稱。
   1. 如果您想要傳遞任何其他屬性，可以在 **屬性陳述式** （可選）

   ![](assets/cp-saml-integration-step1.png)

   *新增SAML屬性*

   **若為SP設定：**

   1. 在「單一登入URL」欄位中，輸入URL： [https://learningmanager.adobe.com/saml/SSO](https://learningmanager.adobe.com/saml/SSO)
   1. 在「對象URL」欄位中，輸入URL： [https://learningmanager.adobe.com](https://learningmanager.adobe.com/)
   1. 在「名稱ID格式」下拉式方塊中，選取 **電子郵件地址**.
   1. 在應用程式中，使用者名稱下拉式清單選取Okta使用者名稱。
   1. 按一下 **顯示進階設定**.
   1. 在 **簽章演演算法**，選取RSA-SHA256
   1. 在 **判斷提示演演算法**，選取SHA256
   1. 在 **判斷提示加密** dropbox，選取 **已加密**.

   1. 在 **加密憑證** 選項，上傳由Adobe共用的憑證檔案。
   1. 如果您想要傳遞任何其他屬性，可以在 **屬性陳述式** （選擇性）。

   ![](assets/cp-saml-integration-step2.png)

   *新增其他屬性*

   完成後，按一下 **[!UICONTROL Next]**.

1. 此 **意見反應**  標籤為選用。 選取選項並提供您的意見回饋後，請按一下 **[!UICONTROL Finish]**.

   ![](assets/cp-saml-integration-step3.png)

   *完成SAML設定*

## 擷取IDP起始的URL和中繼資料檔案

若要檢視IdP/SP起始的URL和中繼資料檔案，請執行下列步驟：

1. 開啟您已建立的應用程式。
1. 在 **單一登入** 標籤，按一下 **[!UICONTROL View Instructions]**.

   ![](assets/cp-prime-sso.png)

   *選取SSO標籤*

   **若為IDP：**

   1. 身分提供者單一登入URL是IdP起始的URL。
   1. 複製「 」底下出現的所有文字 **可選** 欄位。
   1. 開啟新的記事本檔案並貼上複製的文字。
   1. 按一下 **[!UICONTROL File]** > **[!UICONTROL Save as]** > &quot;filename.xml&quot;。 這將是中繼資料檔案。

   **若為SP：**

   1. 身分提供者單一登入URL是IdP起始的URL。
   1. 身分提供者簽發者是實體ID。
   1. 複製「 」底下出現的所有文字 **可選** 欄位。
   1. 開啟新的記事本檔案並貼上複製的文字。
   1. 按一下 **[!UICONTROL File]** > **[!UICONTROL Save as]** > **[!UICONTROL filename.xml]**. 這將是中繼資料檔案。

   ![](assets/cp-saml-integration-step4.png)

   *儲存SP XML檔案*

   您必須以XML格式儲存此檔案。

## 設定Adobe Learning Manager SSO

若要設定Adobe Learning Manager SSO，請執行下文中所述的步驟。

<!--

article not in TOC

[SSO Authentication](/help/migrated/kb/sso-authentication-for-learning-manager.md)
-->