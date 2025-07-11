---
jcr-language: en_us
title: Adobe Learning Manager Mobile應用程式中的白色標籤
description: 使用白色標籤是將應用程式或服務重新品牌化為您自己的品牌，並自訂它，就好像您是原始建立者一樣。 在Adobe Learning Manager中，您可以將白色標籤套用至行動應用程式，藉此重新命名應用程式，並讓您的使用者在自己的品牌下使用應用程式。
contentowner: saghosh
exl-id: f37c86e6-d4e3-4095-9e9d-7a5cd0d45e43
source-git-commit: 0c97b147a1e4c6e1a4a0cc69f56f8e9420c4602b
workflow-type: tm+mt
source-wordcount: '2081'
ht-degree: 0%

---

# Adobe Learning Manager Mobile應用程式中的白色標籤

Adobe Learning Manager行動應用程式現在支援貼上白色標籤，這表示您現在可以使用自己的品牌發佈應用程式。

ALM會根據下列時間表，提供已更新並標示為白色的二進位檔案：

1. 若為行動應用程式的主要發行版本，檔案將提前兩週提供使用。
2. 對於任何計畫中的緊急修正更新，將提前一週提供檔案。
3. 針對計畫外、緊急和立即的修正，我們將盡最大努力提供檔案。

二進位檔將可在客戶指定的資料夾中使用。 請連絡您的CSM以存取檔案。 客戶負責及時發佈和相關流程。

## 開始準備啟動標示為白色的應用程式的方法

若要部署和管理您自己的白色標籤應用程式，請遵循下列步驟：

1. 準備資產（如啟動畫面影像）和文字，以便兩者都能在應用程式中使用和應用程式/播放商店上的說明。

1. 指派技術資源，該資源應具備以下能力：

   * 產生推播通知憑證檔案。
   * 簽署ALM團隊提供的應用程式二進位檔。
   * 上傳及管理發布程式。 發佈程式需要應用程式管理員和應用程式/遊戲商店團隊溝通，確保應用程式符合所有發佈准則。 從ALM，您將會收到完全相容的應用程式二進位檔。

## 概觀

使用白色標籤是將應用程式或服務重新品牌化為您自己的品牌，並自訂它，就好像您是原始建立者一樣。 在Adobe Learning Manager中，您可以將白色標籤套用至行動應用程式，藉此重新命名應用程式，並讓您的使用者在自己的品牌下使用應用程式。

## 可自訂的專案

下列是可自訂的：

### 欄位

<table>

 <tbody>

  <tr>

   <td>

    <p>帳戶ID</p>

   </td>

   <td>

    <p>您帳戶的ID。 請注意，屬於任何其他帳戶的學習者將無法存取白色標籤應用程式。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>其他帳戶ID</p>

   </td>

   <td>

    <p>您可視需要新增多個帳戶（子網域）。 將子網域新增為逗號分隔（不含空格）。 例如，acc01、acc02、acc03等。<br> <b>注意：</b>指定子網域時，您必須新增帳戶識別碼。</br> </p>

   </td>

  </tr>

  <tr>

   <td>

    <p>應用程式名稱</p></td>

   <td>

    <p>您要用於應用程式的名稱。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>應用程式簡短名稱</p>

   </td>

   <td>

    <p>如果應用程式名稱過長，請為應用程式指定出現在裝置上的簡短名稱。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>內部應用程式名稱</p></td>

   <td>

    <p>作業系統用來識別應用程式的名稱。 通常使用的格式是： com.company-name.product-name。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>內部應用程式名稱 — iOS</p>

   </td>

   <td>

    <p>如果您的使用者使用iOS，請以不同方式命名應用程式。 我們建議對iOS和Android使用相同的名稱。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>應用程式圖示</p>

   </td>

   <td>

    <p>應用程式圖示為png。 此圖示會顯示在您的應用程式上。 名稱的格式為account-id_appIcon.png。 應用程式圖示的尺寸為512 × 512畫素。<div>請注意，Apple不允許應用程式圖示中使用Alpha頻道。 因此，在提交之前，請務必從資產中移除Alpha管道。</div></p>

   </td>

  </tr>

  <tr>

   <td>

    <p>應用程式啟動畫面</p></td>

   <td>

    <p>針對應用程式的啟動畫面，提供使用者啟動應用程式時顯示的影像(png)。 名稱的格式為account-id_splashIcon.png。 方形啟動顯示熒幕的尺寸為1052 × 1052畫素，圓形啟動顯示熒幕的尺寸為768 x 768畫素。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>使用者端ID和使用者端密碼</p>

   </td>

   <td>

    <p>註冊應用程式時，您帳戶的整合管理員會提供詳細資訊。 整合管理員必須使用下列專案：<ul><li>學習者：read，學習者：write as role</li><li>內部應用程式name://redirect作為重新導向URL</li></ul></p>

   </td>

  </tr>

  <tr>

   <td>

    <p>帳戶標誌</p>

   </td>

   <td>

    <p>代管您組織標誌的URL。 提供內容連結作為帳戶標誌。 URL必須經過網頁編碼。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>應用程式(iOS)的應用程式商店ID</p>

   </td>

   <td>

    <p>實作強制更新所需的ID。 應用程式必須知道學習者應被重新導向至應用程式商店，才能更新應用程式。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>應用程式的Google play商店id (Android)</p>

   </td>

   <td>

    <p>實作強制更新所需的ID。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>深層連結的主機名稱</p>

   </td>

   <td>

    <p>若要託管深層連結，請使用learningmanager。 如果您想使用其他主機名稱URL做為深層連結，請提供主機的URL。 例如， learningmanager.adobe.com。</p>

   </td>

  </tr>

 </tbody>

</table>

>[!NOTE]
>
>將資料提供給您的CSAM，讓CSAM可以將其新增至您的自訂應用程式二進位檔。


#### 更新網站關聯以處理自訂深層連結

如果您使用自訂網域或learningmanager\*.adobe.com作為主機，則不需要採取任何動作。 不過，如果您使用自訂解決方案或URL的特定主機名稱，請新增網站關聯檔案。

>[!CAUTION]
>
>如果檔案不存在，深層連結將無法運作。 確認檔案存在。


如需詳細資訊，請參閱下列連結：

* [Android](https://learningmanager.adobe.com/.well-known/assetlinks.json)
* [iOS](https://learningmanager.adobe.com/.well-known/apple-app-site-association)

## 取得App Store的團隊ID

若要取得您的團隊ID：

1. 登入您的&#x200B;**[!UICONTROL Apple Developer]**&#x200B;帳戶。
2. 選取頁面頂端的&#x200B;**[!UICONTROL Membership Details]**，並複製您的團隊ID。

若要在中繼資料檔案中新增白色標籤的應用程式專案，以啟用深層連結，此ID為必要專案。

## 取得Android的SHA-256指紋

新增白色標籤的應用程式專案時，需要Android簽署憑證的SHA-256指紋。

若要產生SHA-256指紋：

1. 執行以下命令：

```
keytool -list -v -keystore <keystore/jks file> -alias <aliaskey> -storepass <storepassword> -keypass <keypassword>
```

在輸出中尋找憑證指紋，然後複製SHA-256值。 視需要共用此指紋以用於深層連結設定。

## 產生推播通知

將推播通知傳送至Android和iOS應用程式需要兩種不同的機制。

* 針對iOS，產生推播通知憑證。
* 對於Android，請提供從Firebase專案產生的伺服器金鑰。

請依照下列指示，在Firebase中設定專案：

### iOS上的推播通知

在iOS應用程式開發中，推播通知憑證是Apple所核發的密碼編譯認證，可讓伺服器透過Apple的推播通知服務(APN)安全地傳送推播通知至iOS裝置。

向iOS裝置傳送推播通知時，憑證可確保您的伺服器（或提供者）與Apple的APNs之間安全通訊。

Android和iOS都使用Firebase Cloud Messaging (FCM)作為傳送推播通知至裝置的服務。

### 如何在iOS上產生憑證

請遵循下列程式：

1. 產生或下載&#x200B;**推播通知憑證**&#x200B;和私密金鑰(.p12)。 如需詳細資訊，請參閱[Apple開發人員檔案](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns)。

1. 在下載檔案之後安裝p12檔案。 使用密碼以安裝在您的&#x200B;**鑰匙圈存取**&#x200B;中。

1. 瀏覽至&#x200B;**我的憑證**&#x200B;並匯出憑證。 請務必選取mime型別.cer。

1. 在擁有p12檔案和cer檔案之後，請執行以下命令：

```
- openssl pkcs12 -in privatekey.p12 -out myapnappkey.pem -nodes –clcerts

- openssl x509 -in privatekey.cer -inform DER -out myapnsappcert.pem 

- openssl s_client -connect gateway.sandbox.push.apple.com:2195 -cert myapnsappcert.pem -key myapnappkey.pem 
```

如果您可以連線到伺服器，則您已建立的憑證有效。 從myapnappkey.pem檔案中，複製憑證和私密金鑰值。

### Android上的推播通知

對於Android，使用者需要從Firebase專案提供services.json檔案，以便在SNS服務中新增專案。

在Firebase中建立專案，並將services.json檔案共用給CSM團隊。 SNS中權杖型專案需要此檔案。 請注意，伺服器金鑰已不再使用。 請參閱[在Firebase](#create-project-in-firebase)中建立專案。

若要下載services.json檔案，請遵循下列步驟：

1. 登入&#x200B;**Firebase**&#x200B;主控台。
1. 移至&#x200B;**專案設定**&#x200B;並選取&#x200B;**雲端訊息**。
1. 尋找&#x200B;**Firebase Cloud Messaging API**&#x200B;並選取&#x200B;**管理服務帳戶**。
1. 在&#x200B;**服務帳戶**&#x200B;頁面中，選取左側面板中的&#x200B;**服務帳戶**。
1. 尋找您的專案專案，然後選取[動作]下的[管理詳細資料] **&#x200B;**。

   >[!NOTE]
   >
   >   專案專案格式將為&lt;-accountname->@appspot.gserviceaccount.com。

1. 移至&#x200B;**金鑰**&#x200B;索引標籤並選取&#x200B;**新增金鑰**。
1. 如果沒有金鑰，請選取&#x200B;**建立新金鑰**&#x200B;並選取&#x200B;**JSON**&#x200B;作為金鑰型別。 如此將可產生並下載JSON檔案。
1. 如果已經有金鑰，請選取&#x200B;**上傳現有的金鑰**，貼上金鑰並上傳。 如此將可產生並下載JSON檔案。

<!-- Set up a project in Firebase and share the server key with the CSAM.-->

請聯絡CSM團隊並分享JSON檔案，以將專案新增至AWS上的SNS服務。 使用者必須在SNS服務中針對推播通知註冊專案，這將要求他們共用上述產生以供驗證的憑證。

## 在Firebase中建立專案 {#create-project-in-firebase}

### Android

針對推播通知，重複使用您在上述步驟中建立的相同專案。

[在Firebase中新增專案](https://learn.microsoft.com/en-us/xamarin/android/data-cloud/google-messaging/firebase-cloud-messaging)，並擷取&#x200B;***google-services.json***&#x200B;檔案。

### iOS

[將專案](https://firebase.google.com/docs/ios/setup)新增至Firebase並擷取&#x200B;***GoogleService-Info.plist***&#x200B;檔案。

>[!IMPORTANT]
>
>將檔案傳送至Adobe Learning Manager CSAM團隊，以納入應用程式二進位檔案的建置。


## 產生已簽署的二進位檔案

### iOS

<!--```
sh""" xcodebuild -exportArchive -archivePath Runner.xcarchive -exportPath "ipa_path/" -exportOptionsPlist {ExportFile} 

mv ipa_path/*.ipa "${env.AppName}_signed.ipa" """ 
```-->

`<root>`資料夾包含&#x200B;**Runner.xcarchive.zip**&#x200B;檔案。 執行以下命令來產生已簽署的二進位檔案：

1. 執行以下命令以解壓縮封存：

   ```
   unzip Runner.xcarchive.zip
   ```

2. 導覽至應用程式目錄：

   ```
   cd Runner.xcarchive/Products/Applications/Runner.app
   ```

3. 複製行動布建檔案：

   ```
   cp <path>/<mobile-provisioningfile>.mobileprovision embedded.mobileprovision
   ```

4. 執行以下命令，將您的簽署資訊更新至框架程式庫：

   ```
   codesign -f -s "Distribution Certificate Name" Frameworks/*
   ```

5. 返回`<root>`資料夾（Runner.xcarchive.zip所在位置）：

   ```
   cd <root>
   ```

6. 使用xcodebuild匯出封存：

   ```
   xcodebuild -exportArchive -archivePath Runner.xcarchive -exportPath ipa_path/ -exportOptionsPlist <path>/<ExportOptions-file>.plist
   ```

7. 在ipa_path資料夾中找到.ipa檔案。
8. 將.ipa檔案上傳至`Diawi`網站。
9. 完全上傳後，選取&#x200B;**[!UICONTROL Send]**&#x200B;按鈕。
10. 完成後，您將會收到QR碼和連結。
11. 直接在Safari中開啟QR碼或連結。

如果裝置包含在布建設定檔中，則應在裝置上繼續進行安裝。

>[!NOTE]
>
>您需要有XCode 15.2或更新版本才能建置已簽署的二進位檔。


### Android

**適用於apk檔案**

>[!IMPORTANT]
>
>在執行`apksigner`命令之前，請執行以下命令，將您的金鑰存放區密碼和金鑰別名密碼匯出為環境變數：
>
>```
>export KS_PASS=your_keystore_password
>export KEY_PASS=your_key_password
>```

```
sh""" <path>/apksigner sign --ks $storeFile. --ks-pass env:KS_PASS --ks-key-alias $key_alias --key-pass env:KEY_PASS --out app-release-signed.apk -v app-release.apk """
```

>[!NOTE]
>
>`apksigner`工具的路徑通常如下所示： ~/Library/Android/sdk/build-tools/30.0.3/apksigner。

適用於aab檔案&#x200B;**的**

>[!NOTE]
>
>您需要Android sdk建置工具，才能建置已簽署的二進位檔。

Play Store需要aab格式的Android二進位檔才能發佈。 因此，我們將提供未簽署的.aab檔案。

>[!NOTE]
>
>建立金鑰存放區檔案時，您需要產生金鑰存放區密碼、簽署金鑰別名以及簽署金鑰別名密碼。

請依照下列步驟簽署.aab檔案：

執行以下命令：

```
<path>/jarsigner -verbose -sigalg SHA256withRSA -digestalg SHA-256 -keystore <keystore-file> app-release.aab <signingKeyAlias>
```

>[!NOTE]
>
>**[!UICONTROL jarsigner]**&#x200B;包含在Java中。 確定您使用的是Java 21。

出現提示時，請輸入下列密碼：

* 金鑰存放區密碼
* 簽署金鑰別名的密碼

您可以使用提供的應用程式。 不過，如果您需要從aab檔案產生apk，請遵循下列步驟：

>[!NOTE]
>
>您必須安裝&#x200B;**[!UICONTROL bundletool]**&#x200B;才能產生APK。


執行以下命令來建立apk檔案：

```
java -jar <path>/bundletool-all.jar  build-apks --bundle=app-release.aab --output=my_app.apks --mode=universal
```

若要解壓縮檔案，請執行以下命令：

```
unzip my_app.apks -d output_dir
```

您將從&#x200B;**[!UICONTROL output_dir]**&#x200B;資料夾中取得apk檔案。

**下一步**

產生二進位檔後，請將二進位檔推送到Play Store或App Store。

### 正在推送應用程式至商店以供檢閱

取得最終二進位檔後，您可以將其上傳至個別應用程式商店(iOS或Android)進行檢閱。 請依照下列步驟，將二進位檔上傳至應用程式商店。

**iOS**

1. 使用您的App Store憑證登入「傳輸程式」應用程式。
2. 選取左上方的&#x200B;**+**&#x200B;按鈕並上傳生產憑證（.ipa檔案）。
3. 如果.ipa檔案正確，系統會提示您上傳應用程式至App Store。
4. 應用程式傳送後，請登入App Store。 幾小時後，二進位檔就會顯示在TestFlight區段中。 您可以在應用程式稽核前，先在TestFlight中啟用它以進行最終的健全度測試，並在提交新版本的應用程式時，使用此IPA作為二進位。

**Android**

1. 開啟Google Play Store Console。
2. 前往&#x200B;**[!UICONTROL Dashboard]** > **[!UICONTROL View App Releases]** > **[!UICONTROL Release Dashboard]**，然後選取&#x200B;**[!UICONTROL Create New Release]**。
3. 上傳產生的.aab檔案作為應用程式套件組合，並輸入版本詳細資料，例如版本號碼和新增功能資訊。
4. 儲存您的變更並提交應用程式以供檢閱。
5. 請務必將應用程式發佈設為100% (Google預設會將其設為20%)。

#### 應用程式發佈的實用連結

**Android**

[建立並設定您的應用程式](https://support.google.com/googleplay/android-developer/answer/9859152?hl=en)
[準備您的應用程式以供檢閱](https://support.google.com/googleplay/android-developer/answer/9859455?sjid=2454409340679630327-AP)

**iOS**

[送出檢閱](https://developer.apple.com/help/app-store-connect/manage-submissions-to-app-review/submit-for-review)

## 如何套用變更

將所需的資產和檔案傳送到CSM團隊。 然後CSM團隊會以必要的變更填入[表單](https://forms.office.com/r/bJRRaRBvSh)並附加必要的資產。 然後團隊將稽核並通知工程團隊相關變更。 工程團隊將隨即產生組建並與CSM團隊共用。

CSM團隊將與客戶共用組建。

## 無法自訂的專案

* 更新密碼畫面
* 建立帳戶畫面
