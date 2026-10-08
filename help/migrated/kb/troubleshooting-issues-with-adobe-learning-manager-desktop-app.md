---
description: 本文件包含基本的故障排除建議，以解決安裝及使用 Adobe Learning Manager 桌面應用程式時常見的問題。
jcr-language: en_us
title: Adobe Learning Manager 桌面應用程式故障排除
contentowner: kuppan
exl-id: 68d40a52-e048-43af-a7aa-917b569b583d
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 0%
---
# Adobe Learning Manager 桌面應用程式故障排除

本文件包含基本的故障排除建議，以解決安裝及使用 Adobe Learning Manager 桌面應用程式時常見的問題。

## 我無法做到以下幾點 {#iamunabletodothefollowing}

+++我無法下載 Adobe Learning Manager 桌面應用程式

1. 檢查你的網路連線和防火牆設定。
1. 在社交學習中，點擊 **[!UICONTROL New Post]** 建立一篇貼文。 如果你沒有看板，先建立一個看板。
1. 點擊以下任何一個貼文按鈕選項，這些選項看起來可以產生內容，如截圖、錄製音訊、錄製影片、學習管理員圖庫。 您將被導向 Adobe Learning Manager 桌面應用程式頁面，從那裡您可以下載 Adobe Learning Manager 桌面應用程式。
1. 你需要一個有效的 Adobe Learning Manager 帳號，且管理員已啟用 Social Learning。 你的管理員也可能已經停用了網頁瀏覽器的下載功能。 如需更多下載 Adobe Learning Manager 桌面應用程式的資訊，請聯絡您的 Adobe Learning Manager 管理員。

+++

+++我無法安裝 Adobe Learning Manager 桌面應用程式

1. 確保你的系統符合最低系統要求。 請參閱 [桌面版](../learners/adobe-learning-manager-app-for-desktop/adobe-learning-manager-desktop-app-system-requirements.md) Adobe Learning Manager 應用程式的系統要求。
1. 清理任何先前安裝的 Adobe Learning Manager 桌面應用程式。 欲了解更多資訊，請參閱[「如何清理先前安裝」。](#howtocleanuppreviousinstallationsofadobelearningmanagerdesktopapp)
1. 安裝過程中的錯誤請參見 [「如何查找應用程式日誌](#howtofindapplicationlogs)」。 如需更多協助，請聯絡您的 Adobe Learning Manager 桌面應用程式管理員。

+++

+++我無法啟動 Adobe Learning Manager 桌面應用程式

1. 請確保 Adobe Learning Manager 桌面應用程式已下載並安裝。
1. 在社會學習中，點擊 **[!UICONTROL New Post]** （如果你沒有板子，就建立板子）。 點擊以下出現的文章按鈕選項之一——截圖、錄音、錄影、Adobe Learning Manager 圖庫。 你會被導往一個頁面，從那裡可以啟動 Adobe Learning Manager 桌面應用程式。
1. 如果應用程式無法啟動，你也可以在 Windows 的開始功能表啟動，或在 Mac OS X 的 Launchpad 啟動。

+++

+++我無法在 Adobe Learning Manager 桌面應用程式中登入我的帳號

1. 請確保你已連上網際網路，且防火牆設定沒有阻擋 Adobe Learning Manager 桌面應用程式。
1. 請確認你有一個有效的 Adobe Learning Manager 學習者帳號，並且啟用了 Social Learning。
1. 如果你還是無法登入，請退出並重新啟動 Adobe Learning Manager 桌面應用程式，然後再試一次。
1. 如需更多協助，請聯絡您的 Adobe Learning Manager 管理員。

+++

+++我在 Adobe Learning Manager 桌面應用程式中無法看到我的攝影機/麥克風

1. 請確保您的網路攝影機/麥克風正確插上系統並正常運作。
1. 確保你安裝了最新的網路攝影機/麥克風驅動程式。 有些裝置沒有專用驅動程式就無法正常運作。
1. 重設應用程式偏好設定，然後重新啟動 Adobe Learning Manager 桌面應用程式並重試。 欲了解更多資訊，請參閱 [如何重設應用程式偏好設定](#howtoresetapplicationpreferences)。
1. 如果你使用的是 Mac OS X Mojave 10.14，請授權 Adobe Learning Manager 桌面應用程式存取你的攝影機/麥克風。 更多資訊請參閱 [《如何在 OSX Mojave](#howtosetwebcammicrophonepermissionsonMacOSXMojave) 設定網路攝影機/麥克風權限》。

+++

+++我無法從 Adobe Learning Manager 桌面應用程式發佈我的文章

1. 請確保您擁有由 Adobe Learning Manager 管理員啟用的有效 Adobe Learning Manager 學習者帳號。
1. 重設應用程式偏好設定，然後重新啟動 Adobe Learning Manager 桌面應用程式並重試。 更多資訊請參見 [「如何重設應用程式偏好設定](#howtoresetapplicationpreferences)」。
1. 若發布時有錯誤，請啟用進階日誌。 欲了解更多資訊，請參閱 [如何啟用進階日誌](#howtoenableadvancedlogging)、重新啟動Adobe Learning Manager桌面應用程式、重做上述導致錯誤的步驟。 請將最新的應用程式日誌寄給你的 Adobe Learning Manager 管理員尋求協助。 欲了解更多資訊，請參閱 [「如何查找申請日誌](#howtofindapplicationlogs)」。

+++

+++我無法看到或打開我以前的專案

1. 你只能看到用 Adobe Learning Manager 帳號在同一台電腦上建立的專案。
1. 重設應用程式偏好設定，然後重新啟動 Adobe Learning Manager 桌面應用程式並重試。 如需協助，請參閱 [「如何重設應用程式偏好設定](#howtoresetapplicationpreferences)」。
1. 對於開啟專案時出現錯誤，請啟用進階日誌。 欲了解更多資訊，請參閱 [如何啟用進階記錄](#howtoenableadvancedlogging)。 重新啟動 Adobe Learning Manager 桌面應用程式，並重做導致錯誤的步驟。 請將最新的應用程式日誌寄給你的 Adobe Learning Manager 管理員尋求協助。 欲了解更多資訊，請參閱 [「如何查找申請日誌](#howtofindapplicationlogs)」。

+++

## 如何重置應用程式偏好設定？ {#howtoresetapplicationpreferences}

### 窗戶 {#windows}

1. 要開啟執行對話框，請按 **Windows + R** 鍵。
1. 輸入 `**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**` 並按下 Enter 鍵。
1. 刪除名為 **preferences.json** 和 **preferences.xml** 的檔案。

### Mac OS X {#macosx}

1. 開啟尋覓器。
1. 要開啟 **「前往資料夾** 」對話框，按 **Cmd + Shift + G** 鍵。
1. 輸入 `**~/Library/Application Support/Adobe/Learning Manager 1.0**` 並按下 Enter 鍵。
1. 刪除名為 **preferences.json** 和 **preferences.xml** 的檔案。

## 如何找到申請日誌？ {#howtofindapplicationlogs}

### 窗戶 {#application-logs}

1. 要開啟執行對話框，請按 **Windows + R** 鍵。
1. 輸入 `**%TEMP%\\elthor**` 並按下 Enter 鍵。
1. 依照修改&#x200B;**日期排序資料夾**，然後打開最近的資料夾。此資料夾包含最新的應用程式日誌。

### Mac OS X {#MacOSX-1}

1. 開啟 **尋覓**&#x200B;器。
1. 要開啟 **「前往資料夾** 」對話框，按 **Cmd + Shift + G** 鍵。
1. 輸入「**/var/folders**」（不加引號）並按 Enter。
1. 在搜尋欄搜尋「**elthor**」並打開資料夾。
1. 依照修改日期排序資料夾，然後打開最近的資料夾。 此資料夾包含最新的應用程式日誌。

## 如何啟用進階日誌？ {#howtoenableadvancedlogging}

### 窗戶 {#Windows-1}

1. 要開啟執行對話框，請按 **Windows 鍵 + R**。**&#x200B;**
1. 輸入「**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**」（不加引號），然後按下 Enter。**&#x200B;**
1. 先備份檔案 **preferences.json**，然後用文字編輯器打開。**&#x200B;**
1. 搜尋 **debugMode** 鍵，並將此鍵的值屬性改為「**true**」（不加引號）。

### Mac OS X {#MacOSX-2}

1. 開啟尋覓器。
1. 要開啟 **「返回資料夾** 」對話框，按 **Cmd + Shift + G**。
1. 輸入「**~/Library/Application Support/Adobe/Learning Manager 1.0**」（不加引號），然後按下 Enter。
1. 先備份檔案 **preferences.json**，然後用文字編輯器打開。
1. 搜尋 **debugMode** 鍵，並將此鍵的值屬性改為「**true**」（無引號）

## 如何在 Mac OS X Mojave 上設定網路攝影機/麥克風權限？ {#howtosetwebcammicrophonepermissionsonmacosxmojave}

1. 點擊 **[!UICONTROL System Preferences]** Dock 中的圖示。
1. 點擊 **[!UICONTROL Security & Privacy]** > **[!UICONTROL Privacy]。**
1. 點擊 **[!UICONTROL Webcam and Microphone options]** 並確認已勾選 Adobe Learning Manager 的核取方塊。 如果你沒有看到 Adobe Learning Manager 的清單，請先安裝並啟動 Adobe Learning Manager 桌面應用程式。

## 如何清理 Adobe Learning Manager 以處理桌面更新快取？ {#howtocleanupadobecaptivateprimefordesktopupdatescache}

### 窗戶 {#clean-previous-installation}

1. 要開啟執行對話框，請按 **Windows 鍵 + R**。
1. 輸入 `**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**` 並按下 Enter 鍵。
1. 刪除名為 **updates 的**&#x200B;資料夾。

### Mac OS X {#MacOSX-3}

1. 開啟尋覓器。
1. 要開啟 **「返回資料夾** 」對話框，按 **Cmd + Shift + G**。
1. 輸入 `**~/Library/Application Support/Adobe/Learning Manager 1.0**` 並按下 Enter 鍵。
1. 刪除名為 **updates 的**&#x200B;資料夾。

## 如何清理桌面臨時資料夾的 Adobe Learning Manager？ {#howtocleanupadobecaptivateprimefordesktoptempfolder}

### 窗戶 {#clean-previous-installation-1}

1. 要開啟執行對話框，按 **Windows 鍵 + R**。
1. 輸入「**%TEMP%**」（不加引號）並按下 Enter。
1. 刪除名為「**elthor**」的資料夾。

### Mac OS X {#MacOSX-4}

1. 開啟尋覓器。
1. 要開啟 **「前往資料夾** 」對話框，按 **Cmd + Shift + G** 鍵。
1. 輸入「**/var/folders**」（不加引號）並按 Enter。
1. 在搜尋欄搜尋「**elthor**」。
1. 刪除名為「**elthor**」的資料夾。

## 如何找到用於桌面專案的 Adobe Learning Manager？ {#howtolocateadobecaptivateprimefordesktopprojects}

### 窗戶 {#Windows-2}

1. 要開啟執行對話框，請按 **Windows 鍵 + R**。
1. 輸入「**~/Documents/My Adobe Learning Manager Projects**」（不加引號），然後按下 Enter。
1. 你或你的 Adobe Learning Manager 管理員可能更改了預設專案資料夾的位置。 請聯絡您的管理員，以獲得更多協助，協助尋找並清理專案。

### Mac OS X {#MacOSX-5}

1. 開啟尋覓器。
1. 要開啟 **「前往資料夾** 」對話框，按 **Cmd + Shift + G** 鍵。
1. 輸入「**~/Documents/My Adobe Learning Manager Projects**」（不加引號），然後按下 Enter。

   你或你的 Adobe Learning Manager 管理員可能更改了預設專案資料夾的位置。 如需更多協助，請聯絡您的管理員，協助尋找並整理專案。

## 如何清理之前安裝的 Adobe Learning Manager 桌面應用程式？ {#howtocleanuppreviousinstallationsofadobelearningmanagerdesktopapp}

### 窗戶 {#Windows-3}

1. 要開啟 **執行對話框，請**&#x200B;按&#x200B;**Windows 鍵 + R**。
1. 輸入 regedit 並搜尋「**HKEY_LOCAL_MACHINE \\SOFTWARE\\Classes\\Installer\**\」（不加引號）或「**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Installer\\UserData\\\S-1-5-18\\\Products\\**」（不加引號）並按 Enter。
1. 找到名為 Adobe Learning Manager 的資料夾，找到之前的安裝。 刪除登錄檔條目。  你可以按 F3 鍵找到這個鍵。

### Mac OS X {#MacOSX-6}

將以下路徑&#x200B;**的檔案「/Applications/Adobe Learning Manager/Users/Shared/Adobe/Learning Manager Assets/1.0**」移到垃圾桶，然後清空垃圾桶。
