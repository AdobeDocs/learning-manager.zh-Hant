---
jcr-language: en_us
title: Adobe Learning Manager 行動應用程式中的白標
description: 白標是指將應用程式或服務重新包裝成自己的品牌，並像你是原始創作者一樣進行客製化。 在 Adobe Learning Manager 中，你可以對行動應用程式套用白標，這樣你就能重新品牌化應用程式，並以你自己的品牌讓使用者使用該應用程式。
contentowner: saghosh
exl-id: f37c86e6-d4e3-4095-9e9d-7a5cd0d45e43
source-git-commit: 864c3a4e60cf1bf1c049838fb2ba46ebbcb28ddf
workflow-type: tm+mt
source-wordcount: '2167'
ht-degree: 0%

---

# Adobe Learning Manager 行動應用程式中的白標

Adobe Learning Manager 行動應用程式現在支援白標，這表示你可以以自己的品牌發佈應用程式。

ALM 將依照以下時間表提供更新的白標二進位檔案：

1. 對於行動應用程式的重大釋出，檔案會提前兩週提供。
2. 對於任何緊急修正的計畫更新，檔案會提前一週提供。
3. 對於未計畫、緊急及立即的修復，檔案將以盡力提供。

雙進制檔案會放在客戶指定的資料夾中。 聯絡你的CSM以取得這些檔案。 客戶負責及時發布及相關流程。

## 你應該如何開始準備啟動你的白標應用程式

要部署和管理你自己的白標應用程式，請遵循以下步驟：

1. 準備素材（像是開場畫面圖片）和文字，讓兩者都能在應用程式中使用，並在應用程式/Play 商店中填寫說明。

1. 指派一位具備以下能力的技術資源：

   * 產生推送通知憑證檔案。
   * 簽署由 ALM 團隊提供的應用程式二進位檔。
   * 上傳與管理發佈流程。 發佈流程需要你的應用程式經理與應用程式/Play 商店團隊之間溝通，確保你的應用程式符合所有發佈指引。 從 ALM 那裡，你會收到一個完全合規的應用程式二進位檔。

## 概觀

白標是指將應用程式或服務重新包裝成自己的品牌，並像你是原始創作者一樣進行客製化。 在 Adobe Learning Manager 中，你可以對行動應用程式套用白標，這樣你就能重新品牌化應用程式，並以你自己的品牌讓使用者使用該應用程式。

## 可以客製化的部分

以下內容可進行客製化：

### 欄位

<table>

 <tbody>

  <tr>

   <td>

    <p>帳號ID</p>

   </td>

   <td>

    <p>你的帳號ID。 請注意，白標應用程式將無法對擁有其他帳號的學習者開放。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>附加帳號 ID</p>

   </td>

   <td>

    <p>如果想的話，可以新增多個帳號（子網域）。 將子域以逗號分隔且無空格的方式加入。 例如 acc01、acc02、acc03 等等。<br> <b>注意：</b> 在指定子網域時，你需要填寫帳號 ID。</br> </p>

   </td>

  </tr>

  <tr>

   <td>

    <p>應用程式名稱</p></td>

   <td>

    <p>你想用來命名應用程式名稱。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>應用程式簡稱</p>

   </td>

   <td>

    <p>若應用程式名稱較長，請為裝置上顯示的簡短名稱。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>內部應用程式名稱</p></td>

   <td>

    <p>作業系統用來識別該應用程式的名稱。 通常使用的格式為：com.company-name.product-name。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>內部應用程式名稱-iOS</p>

   </td>

   <td>

    <p>如果你的用戶是 iOS，應用程式名稱會有所不同。 我們建議 iOS 和 Android 都使用相同名稱。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>應用程式圖示</p>

   </td>

   <td>

    <p>應用程式圖示是 png。 這個圖示會顯示在你的應用程式上。 名稱格式為account-id_appIcon.png。 應用程式圖示的尺寸是 512 × 512 像素。<div>請注意，蘋果不允許在應用程式圖示中使用 Alpha 頻道。 所以，提交前務必先移除 Alpha 頻道。</div></p>

   </td>

  </tr>

  <tr>

   <td>

    <p>應用程式啟動畫面</p></td>

   <td>

    <p>在應用程式的啟動畫面中，提供一張圖片（png），當使用者啟動應用程式時會顯示。 命名格式為account-id_splashIcon.png。 方形開機畫面的尺寸為 1052 × 1052 像素，圓形開機畫面則為 768 x 768 像素。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>用戶端 ID 與用戶端秘密</p>

   </td>

   <td>

    <p>你帳號的整合管理員會在註冊應用程式時提供詳細資訊。 整合管理員必須使用以下工具：<ul><li>學習者：閱讀，學習者：以角色形式寫作</li><li>內部應用程式 name://redirect 作為重定向網址</li></ul></p>

   </td>

  </tr>

  <tr>

   <td>

    <p>帳戶標誌</p>

   </td>

   <td>

    <p>你組織標誌所在的網址。 請提供 cpcontents 連結作為帳號標誌。 網址必須是網頁編碼的。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>應用程式的 App Store ID（iOS）</p>

   </td>

   <td>

    <p>這是實施部隊更新所需的ID。 應用程式需要知道學習者應該被導向到 App Store，才能更新應用程式。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>Google Play 應用程式的商店 ID（Android）</p>

   </td>

   <td>

    <p>這是實施部隊更新所需的ID。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>深連結主機名稱</p>

   </td>

   <td>

    <p>要架設深度連結，請使用 learningmanager。 如果你想使用另一個主機名稱 URL 作為深度連結，請提供主機的網址。 例如，learningmanager.adobe.com。</p>

   </td>

  </tr>

 </tbody>

</table>

>[!NOTE]
>
>把資料提供給你的 CSAMs，讓他們能加入你自訂的應用程式二進位檔。


#### 更新網站關聯以處理自訂深度連結

如果你使用自訂網域或 learningmanager\*.adobe.com 作為主機，就不需要採取任何行動。 不過，如果你使用自訂解決方案或特定主機名稱來設定網址，請加入網站關聯檔案。

>[!CAUTION]
>
>如果檔案不存在，深層連結將無法使用。 確保檔案齊全。


請參考以下連結以獲得更多資訊：

* [Android](https://learningmanager.adobe.com/.well-known/assetlinks.json)
* [iOS](https://learningmanager.adobe.com/.well-known/apple-app-site-association)

## 取得你的 App Store 團隊編號

要取得你的隊伍識別碼：

1. 登入你的 **[!UICONTROL Apple Developer]** 帳號。
2. 在頁面頂端選擇 **[!UICONTROL Membership Details]** 並複製你的團隊編號。

此 ID 是加入元資料檔案中白標應用程式條目以啟用深度連結所必需的。

## 取得 Android 版 SHA-256 指紋認證

新增白標應用程式條目時，必須提供 ANDROID 簽署憑證的 SHA-256 指紋。

要產生 SHA-256 指紋：

1. 執行以下指令：

```
keytool -list -v -keystore <keystore/jks file> -alias <aliaskey> -storepass <storepassword> -keypass <keypassword>
```

在輸出中，找到憑證指紋，然後複製 SHA-256 的值。 根據需要，分享此指紋以便深度連結設定。

## 產生推播通知

向 Android 和 iOS 應用程式發送推播通知需要兩種不同的機制。

* iOS 則產生推播通知憑證。
* 對於 Android 來說，提供由 Firebase 專案產生的伺服器金鑰。

請依照以下指示在 Firebase 中設定專案：

### iOS 上的推播通知

在 iOS 應用程式開發中，推播通知憑證是由蘋果頒發的一種密碼學憑證，允許伺服器透過蘋果的推播通知服務（APN）安全地向 iOS 裝置發送推播通知。

該憑證確保您的伺服器（或服務提供者）與蘋果 APN 在向 iOS 裝置發送推播通知時的安全通訊。

Android 和 iOS 都使用 Firebase Cloud Messaging （FCM） 作為向裝置發送推播通知的服務。

### 如何在 iOS 上產生證書

請遵循以下程序：

1. 產生或下載 **推播通知憑證** 與私鑰（.p12）。 更多資訊請參閱 [蘋果開發者文件](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns)。

1. 下載完 p12 檔案後再安裝。 使用密碼安裝您的 **鑰匙圈存取**&#x200B;權限。

1. 進入 **「我的憑證」** 並匯出憑證。 務必選擇默劇.cer類型。

1. 一旦你取得 p12 檔案和 cer 檔案，請執行以下指令：

```
- openssl pkcs12 -in privatekey.p12 -out myapnappkey.pem -nodes –clcerts

- openssl x509 -in privatekey.cer -inform DER -out myapnsappcert.pem 

- openssl s_client -connect gateway.sandbox.push.apple.com:2195 -cert myapnsappcert.pem -key myapnappkey.pem 
```

如果你能連接到伺服器，你建立的憑證就是有效的。 從 myapnappkey.pem 檔案複製憑證和私鑰值。

### Android 上的推播通知

對於 Android，使用者需要提供 Firebase 專案中的 services.json 檔案，以便在 SNS 服務中新增條目。

在 Firebase 建立專案，並將 services.json 檔案分享給 CSM 團隊。 此檔案用於 SNS 中基於標記的輸入。 請注意，伺服器金鑰已不再使用。 請參見 [Firebase](#create-project-in-firebase) 中的 Create 專案。

要下載services.json檔案，請依照以下步驟操作：

1. 登入 **Firebase** 控制台。
1. 到專案設定&#x200B;**中**&#x200B;選擇&#x200B;**雲端訊息**。
1. 找到 **Firebase 雲端訊息 API** ，並選擇 **管理服務帳戶**。
1. 在 **服務 cccounts** 頁面，選擇左側面板的 **服務帳戶** 。
1. 找到你的專案條目，並在動作中選擇 **「管理細節** 」。

   >[!NOTE]
   >
   >   專案的參賽格式將為 &lt;-accountname->@appspot.gserviceaccount.com。&lt;/-accountname->

1. 到「 **鑰匙** 」標籤，選擇 **「新增鑰匙**」。
1. 如果沒有金鑰，請選擇 **建立新金鑰** ，並選擇 **JSON** 作為金鑰類型。 這樣就能產生並下載 JSON 檔案。
1. 如果已經有金鑰，選擇 **「上傳現有金鑰**」，貼上金鑰並上傳。 這樣就能產生並下載 JSON 檔案。

<!-- Set up a project in Firebase and share the server key with the CSAM.-->

聯絡 CSM 團隊，分享 JSON 檔案，以便將條目加入 AWS 的 SNS 服務。 用戶必須在 SNS 服務中註冊該條目以接收推播通知，並需分享上述產生的憑證以供驗證。

## 在 Firebase 建立專案 {#create-project-in-firebase}

### Android

重複使用你在上述步驟中建立的推播通知專案。

[在 Firebase 加入專案](https://learn.microsoft.com/en-us/xamarin/android/data-cloud/google-messaging/firebase-cloud-messaging) 並取得 ***google-services.json*** 檔案。

### iOS

[將專案](https://firebase.google.com/docs/ios/setup) 加入 Firebase，並取得 ***GoogleService-Info.plist*** 檔案。

>[!IMPORTANT]
>
>將檔案送給 Adobe Learning Manager 的 CSAM 團隊，讓他們加入你的應用程式二進位檔案建置中。


## 產生有符號的二進位

### iOS

<!--
```
sh""" xcodebuild -exportArchive -archivePath Runner.xcarchive -exportPath "ipa_path/" -exportOptionsPlist {ExportFile} 

mv ipa_path/*.ipa "${env.AppName}_signed.ipa" """ 
```
-->

資料夾裡 `<root>` 有 **Runner.xcarchive.zip** 檔案。 執行以下指令以產生有符號的二進位檔：

1. 執行以下指令來解壓縮壓縮檔案：

   ```
   unzip Runner.xcarchive.zip
   ```

2. 前往應用程式目錄：

   ```
   cd Runner.xcarchive/Products/Applications/Runner.app
   ```

3. 複製行動裝置配置檔案：

   ```
   cp <path>/<mobile-provisioningfile>.mobileprovision embedded.mobileprovision
   ```

4. 執行以下指令，將你的簽署資訊更新到框架函式庫：

   ```
   codesign -f -s "Distribution Certificate Name" Frameworks/*
   ```

5. 返回 `<root>` 資料夾（Runner.xcarchive.zip所在位置）：

   ```
   cd <root>
   ```

6. 使用 xcodebuild 匯出壓縮檔：

   ```
   xcodebuild -exportArchive -archivePath Runner.xcarchive -exportPath ipa_path/ -exportOptionsPlist <path>/<ExportOptions-file>.plist
   ```

7. 在ipa_path資料夾中找到 .ipa 檔案。
8. 把 .ipa 檔案上傳到 `Diawi` 網站。
9. 上傳完成後，選擇按鈕 **[!UICONTROL Send]** 。
10. 完成後，您將收到一個 QR 碼和一個連結。
11. 直接在 Safari 裡開啟 QR 碼或連結。

如果裝置包含在配置設定檔中，安裝應該會持續進行。

>[!NOTE]
>
>你需要 XCode 15.2 或以上的版本來建立有符號的二進位檔。


### Android

**用於apk檔案**

>[!IMPORTANT]
>
>執行 `apksigner` 指令前，請執行以下指令，將你的鑰匙儲存密碼和鑰匙別名密碼匯出為環境變數：
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
>工具的 `apksigner` 路徑通常如下：~/Library/Android/sdk/build-tools/30.0.3/apksigner。

**對於 AAB 檔案**

>[!NOTE]
>
>你需要使用 Android SDK 建置工具來建立已簽署的二進位檔。

Play 商店發佈時必須有 Android 二進位檔，格式為 aab 格式。 因此，我們將提供未簽名的 .aab 檔案。

>[!NOTE]
>
>建立金鑰儲存檔案時，你需要產生金鑰儲存密碼、簽署金鑰別名和簽名金鑰別名密碼。

請依照以下步驟簽署 .aab 檔案：

執行以下指令：

```
<path>/jarsigner -verbose -sigalg SHA256withRSA -digestalg SHA-256 -keystore <keystore-file> app-release.aab <signingKeyAlias>
```

>[!NOTE]
>
>這是 **[!UICONTROL jarsigner]** Java 內建的。 請確保你使用的是 Java 21。

當被要求時，請輸入以下密碼：

* 金鑰儲存密碼
* 用於簽署金鑰別名的密碼

你可以使用提供的 apk。 不過，如果你需要從 aab 檔案產生 apk，請遵循以下步驟：

>[!NOTE]
>
>你需要安裝 **[!UICONTROL bundletool]** 才能產生 APK 檔案。


執行以下指令來建立 apk 檔案：

```
java -jar <path>/bundletool-all.jar  build-apks --bundle=app-release.aab --output=my_app.apks --mode=universal
```

要解壓縮檔案，請執行以下指令：

```
unzip my_app.apks -d output_dir
```

你會從 **[!UICONTROL output_dir]** 資料夾取得 apk 檔案。

**接下來的計畫**

產生二進位檔後，將二進位檔推送到 Play 商店或 App Store。

### 將應用程式推送到商店進行審查

取得最終的二進位檔後，你可以將它們上傳到各自的應用商店（iOS 或 Android）進行審查。 請依照以下步驟將二進位檔上傳到應用程式商店。

**iOS**

1. 用你的 App Store 帳號登入 Transporter 應用程式。
2. 請點選 **左上方的 +** 鍵，並上傳生產證書（.ipa 檔案）。
3. 如果 .ipa 檔案正確，系統會提示你將應用程式上傳到 App Store。
4. 應用程式交付後，登入 App Store。 幾小時內，二進位檔會出現在 TestFlight 區塊。 你可以在 TestFlight 中啟用它作為最終的合理性測試，並在提交新版本時使用這個 IPA 作為二進位。

**Android**

1. 打開 Google Play 商店主控台。
2. 前往 **[!UICONTROL Dashboard]** > **[!UICONTROL View App Releases]** > **[!UICONTROL Release Dashboard]** ，然後選擇 **[!UICONTROL Create New Release]**。
3. 將產生的 .aab 檔案上傳為應用程式組合包，並輸入版本號和最新資訊等發佈資訊。
4. 儲存你的更改並提交應用程式審核。
5. 記得把應用程式的分布設為 100%（Google 預設是 20%）。

#### 應用程式發佈的實用連結

**Android**

[建立並設定你的應用程式](https://support.google.com/googleplay/android-developer/answer/9859152?hl=en)
[準備你的申請進行審查](https://support.google.com/googleplay/android-developer/answer/9859455?sjid=2454409340679630327-AP)

**iOS**

[提交審核](https://developer.apple.com/help/app-store-connect/manage-submissions-to-app-review/submit-for-review)

## 我該如何套用這些變更

將所需的資產和檔案傳送給CSM團隊。 CSM 團隊接著填寫[](https://forms.office.com/r/bJRRaRBvSh)表格，填寫所需變更並附加所需資產。團隊將審查並通知工程團隊這些變更。 工程團隊會生成一個建置版本並與 CSM 團隊分享。

CSM 團隊會與客戶分享組裝版本。

## 無法客製化的部分

* 更新密碼畫面
* 建立帳號畫面
