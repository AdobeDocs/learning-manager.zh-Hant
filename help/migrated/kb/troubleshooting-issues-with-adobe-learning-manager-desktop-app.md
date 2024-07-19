---
description: 本檔案包含基本疑難排解提示，可解決安裝和使用Adobe Learning Manager案頭應用程式時遇到的部分典型問題。
jcr-language: en_us
title: 疑難排解Adobe Learning Manager案頭應用程式的問題
contentowner: kuppan
exl-id: 68d40a52-e048-43af-a7aa-917b569b583d
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '1434'
ht-degree: 0%

---

# 疑難排解Adobe Learning Manager案頭應用程式的問題

本檔案包含基本疑難排解提示，可解決安裝和使用Adobe Learning Manager案頭應用程式時遇到的部分典型問題。

## 我無法執行下列動作 {#iamunabletodothefollowing}

+++我無法下載Adobe Learning Manager案頭應用程式

1. 檢查您的網際網路連線和防火牆設定。
1. 在社交學習中，按一下「**[!UICONTROL New Post]**」以建立貼文。 如果您沒有展示板，請先建立展示板。
1. 按一下以下任何一個顯示用來建立內容的貼文按鈕選項，例如熒幕擷圖、錄製音訊、錄製視訊、Learning Manager Gallery。 系統會將您重新導向至Adobe Learning Manager案頭應用程式頁面，您可在其中下載案頭適用的Adobe Learning Manager案頭應用程式。
1. 您需要具備管理員所啟用社交學習功能的有效Adobe Learning Manager帳戶。 您的管理員也可能已停用透過網頁瀏覽器的下載。 如需下載Adobe Learning Manager案頭應用程式的詳細資訊，請聯絡Adobe Learning Manager管理員。

+++

+++我無法安裝Adobe Learning Manager案頭應用程式

1. 確定您的系統符合最低系統需求。 檢視案頭版Adobe Learning Manager應用程式的[系統需求](../learners/adobe-learning-manager-app-for-desktop/adobe-learning-manager-desktop-app-system-requirements.md)。
1. 清除先前安裝的任何一個Adobe Learning Manager案頭應用程式。 如需詳細資訊，請參閱[如何清除先前的安裝](#howtocleanuppreviousinstallationsofadobelearningmanagerdesktopapp)以瞭解詳細資訊。
1. 如需安裝過程中的錯誤，請參閱[如何尋找應用程式記錄檔](#howtofindapplicationlogs)。 如需更多說明，請連絡您的Adobe Learning Manager案頭應用程式管理員。

+++

+++我無法啟動Adobe Learning Manager案頭應用程式

1. 請確定已下載並安裝Adobe Learning Manager案頭應用程式。
1. 在Social Learning中，按一下&#x200B;**[!UICONTROL New Post]** （如果沒有展示板，則建立展示板）。 按一下顯示的下列任一張貼按鈕選項 — 拍攝熒幕擷圖、錄音、錄影、Adobe Learning Manager收藏館。 系統會將您重新導向至可啟動Adobe Learning Manager案頭應用程式的頁面。
1. 如果應用程式無法啟動，您也可以從Windows上的「開始」功能表，或從Mac OS X的Launchpad啟動應用程式。

+++

+++我無法在Adobe Learning Manager案頭應用程式中登入我的帳戶

1. 請確定您已連線至網際網路，且防火牆設定不會封鎖Adobe Learning Manager案頭應用程式。
1. 請確定您擁有已啟用社交學習的有效Adobe Learning Manager學習者帳戶。
1. 如果您仍然無法登入，請結束並重新啟動Adobe Learning Manager案頭應用程式，然後重試。
1. 如需更多說明，請連絡您的Adobe Learning Manager管理員。

+++

+++我無法看到我的網路攝影機/麥克風列在Adobe Learning Manager案頭應用程式中

1. 請確認網路攝影機/麥克風已正確插入系統且運作正常。
1. 確定您已安裝網路攝影機/麥克風的最新驅動程式。 若沒有專用驅動程式，部分裝置無法正常運作。
1. 重設應用程式偏好設定，然後重新啟動Adobe Learning Manager案頭應用程式並重試。 如需詳細資訊，請參閱[如何重設應用程式偏好設定](#howtoresetapplicationpreferences)。
1. 如果您使用Mac OS X Mojave 10.14，請授予Adobe Learning Manager案頭應用程式存取網路攝影機/麥克風的許可權。 如需詳細資訊，請參閱[如何在OSX Mojave上設定網路攝影機/麥克風許可權](#howtosetwebcammicrophonepermissionsonMacOSXMojave)。

+++

+++我無法從Adobe Learning Manager案頭應用程式發佈貼文

1. 請確定您擁有有效的Adobe Learning Manager學習者帳戶，且您的Adobe Learning Manager管理員已啟用社交學習。
1. 重設應用程式偏好設定，然後重新啟動Adobe Learning Manager案頭應用程式並重試。 如需詳細資訊，請參閱[如何重設應用程式偏好設定](#howtoresetapplicationpreferences)。
1. 針對發佈時的錯誤，請啟用進階記錄。 如需詳細資訊，請參閱[如何啟用進階記錄](#howtoenableadvancedlogging)、重新啟動Adobe Learning Manager案頭應用程式、重做造成錯誤的上述步驟。 傳送最新應用程式記錄檔給您的Adobe Learning Manager管理員以尋求協助。 如需詳細資訊，請參閱[如何尋找應用程式記錄檔](#howtofindapplicationlogs)。

+++

+++我無法檢視或開啟我的舊專案

1. 您只能在使用Adobe Learning Manager帳戶建立的專案建立所在的電腦上，檢視這些專案。
1. 重設應用程式偏好設定，然後重新啟動Adobe Learning Manager案頭應用程式並重試。 如需說明，請參閱[如何重設應用程式偏好設定](#howtoresetapplicationpreferences)。
1. 若在開啟專案時發生錯誤，請啟用進階記錄。 如需詳細資訊，請參閱[如何啟用進階記錄](#howtoenableadvancedlogging)。 重新啟動Adobe Learning Manager案頭應用程式，並重做導致錯誤的步驟。 傳送最新應用程式記錄檔給您的Adobe Learning Manager管理員以尋求協助。 如需詳細資訊，請參閱[如何尋找應用程式記錄檔](#howtofindapplicationlogs)。

+++

## 如何重設應用程式偏好設定？ {#howtoresetapplicationpreferences}

### Windows {#windows}

1. 若要開啟[執行]對話方塊，請按&#x200B;**Windows + R**&#x200B;鍵。
1. 輸入`**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**`並按Enter。
1. 刪除名為&#x200B;**preferences.json**&#x200B;和&#x200B;**preferences.xml**&#x200B;的檔案。

### MAC OS X {#macosx}

1. 開啟「尋找器」。
1. 若要開啟&#x200B;**移至**&#x200B;資料夾對話方塊，請按&#x200B;**Cmd + Shift + G**&#x200B;鍵。
1. 輸入`**~/Library/Application Support/Adobe/Learning Manager 1.0**`並按Enter。
1. 刪除名為&#x200B;**preferences.json**&#x200B;和&#x200B;**preferences.xml**&#x200B;的檔案。

## 如何尋找應用程式記錄檔？ {#howtofindapplicationlogs}

### Windows {#application-logs}

1. 若要開啟[執行]對話方塊，請按&#x200B;**Windows + R**&#x200B;鍵。
1. 輸入`**%TEMP%\\elthor**`並按Enter。
1. 依&#x200B;**修改日期**&#x200B;排序資料夾，並開啟最近的資料夾。 此資料夾包含最新的應用程式記錄檔。

### MAC OS X {#MacOSX-1}

1. 開啟&#x200B;**搜尋器**。
1. 若要開啟&#x200B;**移至資料夾**&#x200B;對話方塊，請按&#x200B;**Cmd + Shift + G**&#x200B;鍵。
1. 輸入&quot;**/var/folders**&quot; （不含引號）並按Enter。
1. 在搜尋列中搜尋「**elthor**」並開啟資料夾。
1. 依**修改日期**將資料夾排序，然後開啟最近的資料夾。 此資料夾包含最新的應用程式記錄檔。

## 如何啟用進階記錄？ {#howtoenableadvancedlogging}

### Windows {#Windows-1}

1. 若要開啟[執行]對話方塊，請按&#x200B;**Windows鍵+ R**。****
1. 型別&#39;&#39;**%APPDATA%\\\..\\Local\\Adobe\\Learning Manager 1.0**」（不含引號）並按Enter。****
1. 備份檔案&#x200B;**preferences.json**，然後在文字編輯器中開啟它。****
1. 搜尋索引鍵&#x200B;**debugMode**，並將這個索引鍵的值屬性變更為&quot;**true**&quot; （不含引號）。

### MAC OS X {#MacOSX-2}

1. 開啟「尋找器」。
1. 若要開啟&#x200B;**移至資料夾**&#x200B;對話方塊，請按&#x200B;**Cmd + Shift + G**。
1. 輸入&quot;**~/Library/Application Support/Adobe/Learning Manager 1.0**&quot; （不含引號）並按Enter。
1. 備份檔案&#x200B;**preferences.json**，然後在文字編輯器中開啟它。
1. 搜尋索引鍵&#x200B;**debugMode**，並將這個索引鍵的值屬性變更為&quot;**true**&quot; （不含引號）

## 如何在Mac OS X Mojave上設定網路攝影機/麥克風許可權？ {#howtosetwebcammicrophonepermissionsonmacosxmojave}

1. 按一下Dock中的&#x200B;**[!UICONTROL System Preferences]**&#x200B;圖示。
1. 按一下&#x200B;**[!UICONTROL Security & Privacy]** > **[!UICONTROL Privacy].**
1. 按一下「**[!UICONTROL Webcam and Microphone options]**」並確保已選取Adobe Learning Manager核取方塊。 如果畫面未列出Adobe Learning Manager，請先安裝並啟動Adobe Learning Manager案頭應用程式。

## 如何清除Adobe Learning Manager的案頭更新快取？ {#howtocleanupadobecaptivateprimefordesktopupdatescache}

### Windows {#clean-previous-installation}

1. 若要開啟[執行]對話方塊，請按&#x200B;**Windows鍵+ R**。
1. 輸入`**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**`並按Enter。
1. 刪除名為&#x200B;**更新**&#x200B;的資料夾。

### MAC OS X {#MacOSX-3}

1. 開啟「尋找器」。
1. 若要開啟&#x200B;**移至資料夾**&#x200B;對話方塊，請按&#x200B;**Cmd + Shift + G**。
1. 輸入`**~/Library/Application Support/Adobe/Learning Manager 1.0**`並按Enter。
1. 刪除名為&#x200B;**更新**&#x200B;的資料夾。

## 如何清理案頭暫存資料夾的Adobe Learning Manager？ {#howtocleanupadobecaptivateprimefordesktoptempfolder}

### Windows {#clean-previous-installation-1}

1. 若要開啟[執行]對話方塊，請按&#x200B;**Windows鍵+ R**。
1. 鍵入&quot;**%TEMP%**&quot; （不含引號）並按Enter。
1. 刪除名為「**elthor**」的資料夾。

### MAC OS X {#MacOSX-4}

1. 開啟「尋找器」。
1. 若要開啟&#x200B;**移至資料夾**&#x200B;對話方塊，請按&#x200B;**Cmd + Shift + G**&#x200B;鍵。
1. 輸入&quot;**/var/folders**&quot; （不含引號）並按Enter。
1. 在搜尋列中搜尋「**elthor**」。
1. 刪除名為「**elthor**」的資料夾。

## 如何為案頭專案找到Adobe Learning Manager？ {#howtolocateadobecaptivateprimefordesktopprojects}

### Windows {#Windows-2}

1. 若要開啟[執行]對話方塊，請按&#x200B;**Windows鍵+ R**。
1. 輸入&quot;**~/Documents/My Adobe Learning Manager專案**&quot; （不含引號），然後按Enter鍵。
1. 您或您的Adobe Learning Manager管理員可能已變更預設專案資料夾位置。 請聯絡您的管理員，以取得尋找和清理專案的更多協助。

### MAC OS X {#MacOSX-5}

1. 開啟「尋找器」。
1. 若要開啟&#x200B;**移至資料夾**&#x200B;對話方塊，請按&#x200B;**Cmd + Shift + G**&#x200B;鍵。
1. 輸入&quot;**~/Documents/My Adobe Learning Manager專案**&quot; （不含引號），然後按Enter鍵。

   您或您的Adobe Learning Manager管理員可能已變更預設專案資料夾位置。 請聯絡您的管理員以取得更多協助，以尋找及清理專案。

## 如何清除先前安裝的Adobe Learning Manager案頭應用程式？ {#howtocleanuppreviousinstallationsofadobelearningmanagerdesktopapp}

### Windows {#Windows-3}

1. 若要開啟&#x200B;**執行對話方塊，**&#x200B;按&#x200B;**Windows鍵+ R**。
1. 輸入regedit並搜尋「**HKEY_LOCAL_MACHINE \\SOFTWARE\\Classes\\Installer\\**」（不含引號）或「**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Installer\\UserData\\S-1-5-18\\Products\\**」（不含引號），然後按Enter鍵。
1. 尋找名為Adobe Learning Manager的資料夾，並尋找先前的安裝。 刪除登入專案。  您可以按F3鍵找到該鍵。

### MAC OS X {#MacOSX-6}

將檔案從以下路徑移至垃圾桶，然後清空垃圾桶： &quot;**/Applications/Adobe Learning Manager/Users/Shared/Adobe/Learning Manager Assets/1.0**&quot;。
