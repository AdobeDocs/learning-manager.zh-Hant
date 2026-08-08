---
description: 內容撰寫者主題 JSON 架構中所有屬性的完整參考——包括調色盤標記、字型堆疊、半徑與間距標記、文字角色值、元件屬性及評估樣式。
jcr-language: en_us
title: Adobe Learning Manager 內容作曲家主題 JSON 屬性參考
source-git-commit: ea6d296fa99686136ab08d756a20570a4681d704
workflow-type: tm+mt
source-wordcount: '1899'
ht-degree: 2%

---


# Adobe Learning Manager 內容作曲家主題 JSON 屬性參考

內容撰寫者主題 JSON 檔案中每個屬性的完整參考，包含描述與範例值。

頂層欄位用來識別並描述主題。

## **元資料**

| **財產** | **類型** | **描述** | **板岩價值** |
|--------------|----------|----------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| 身分證 | 字串 | 獨特的主題識別碼。 小寫、僅連字號，無空格或特殊字元。 內部用來參考主題。 | 「石板」 |
| 名稱 | 字串 | 顯示名稱請顯示於課程主題面板中。 | 「Slate」 |
| 版本 | 字串 | 語意版本號。 新主題使用「1.0.0」。 | &quot;1.0.0&quot; |
| 描述 | 字串 | 主題視覺特徵的簡短描述。 | 「溫暖且權威的主題，搭配奶油色背景、Adobe 紅色點綴，以及 Roboto Slab + Roboto 類型系統」 |
| 作家 | 字串 | 主題創作者或團隊名稱。 | 「內容作曲家」 |
| 資料來源 | 字串 | 主題起源。 「shipped」是為了內建主題。 「自訂」用於使用者自創主題。 | 「客製化」 |
| isDefault | 布林值 | 這個主題是否會自動套用到新課程上。 大多數情況下都設為 false。 | 錯誤 |

## **foundation.palette**

構成主題色彩基礎的七個核心色彩標記。 所有元素值皆以 var（--tokenName） 而非硬編碼的十六進位值來參考這些標記。

| **財產** | **類型** | **描述** | **板岩價值** |
|------------------|------------|---------------------------------------------------------------------------------------------------------------------------|-----------------|
| 前景 | 六角形顏色 | 背景上的文字、圖示和使用者介面元素的主前景色。 | #1A1A1A |
| 背景 | 六角形顏色 | 主菜畫布與幻燈片背景色。 | #FAF7F2 |
| 口音 | 六角形顏色 | 品牌強調色彩套用於按鈕、選中的狀態、進度指示器、課程標題及互動式重點。 | #E8001C |
| 背景微妙 | 六角形顏色 | 卡片、面板、導航及元件填充的次要背景色。 | #F0EBE1 |
| 中學 | 六角形顏色 | 邊框、分隔線，以及非啟用的 UI 元素顏色。 | #D9D3C9 |
| 正文初級 | 六角形顏色 | 所有標題與正文內容皆使用原色文字。 | #1A1A1A |
| 正文逆 | 六角形顏色 | 文字顏色用於置於深色或強調色背景的內容，例如強調色上的按鈕標籤。 | #FFFFFF |

## **foundation.fonts**

主題中所有文字角色套用兩種字型堆疊。 元素值中使用 var（--font-heading） 或 var（--font-body） 來參考。

| **財產** | **類型** | **描述** | **板岩價值** |
|--------------|-------------------|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| 標題 | 字型堆疊字串 | 字型家族用於課程標題、主題標題及顯示標題。 加入網路安全的備用方案。 | 「喬治亞州羅伯托板，『時代新羅馬人』，襯線體」 |
| 身體 | 字型堆疊字串 | 用於段落文字、說明文字、測驗題目及介面標籤的字型家族。 加入網路安全的備用方案。 | 「Roboto、-apple-system、BlinkMacSystemFont、『Segoe UI』、無襯線字體」 |

## **基礎.間距**

水平與垂直間距標記作為基準。 元件會利用水平間隔縮放和垂直間隔縮放倍數。

| **路徑** | **類型** | **描述** | **板岩價值** |
|---------------|----------|-------------------------------------|-----------------|
| horizontal.xs | PX 價值 | 最小的水平間距單位 | 4px |
| 水平.s | PX 價值 | 小型水平間距單元 | 8px |
| horizontal.m | PX 價值 | 中等水平間距單元 | 12px |
| 水平.l | PX 價值 | 大型水平間距單元 | 16px |
| horizontal.xl | PX 價值 | 超大水平間距單元 | 24px |
| vertical.xs | PX 價值 | 最小的垂直間距單位 | 4px |
| 垂直.s | PX 價值 | 小型垂直間距單元 | 8px |
| 垂直.m | PX 價值 | 中等垂直間距單元 | 16px |
| 垂直.l | PX 價值 | 大型垂直間距單元 | 24px |
| vertical.xl | PX 價值 | 超大垂直間距單元 | 32px |

## **基礎。半徑**

邊框半徑標記控制元件和卡片的角角圓滑。

| **財產** | **類型** | **描述** | **板岩價值** |
|--------------|----------|---------------------------------------------------------|-----------------|
| 沒有 | PX 價值 | 沒有圓角——有銳利的轉角。 永遠都是「0px」。 | 0px |
| s | PX 價值 | 小半徑，方便細微圓角。 | 4px |
| m | PX 價值 | 中等半徑用於標準卡和零件四捨五入。 | 8px |
| l | PX 價值 | 大半徑可明顯圓滑。 | 16px |
| 滿載 | PX 價值 | 全丸或圓形。 永遠都是「9999px」。 | 9999px |

## **foundation.logo**

| **財產** | **類型** | **描述** | **板岩價值** |
|--------------|----------------|----------------------------------------------------------------------------------------------|-----------------|
| 標誌 | 字串或空 | 課程標頭中標誌圖片的網址或檔案路徑。 設定為 null 表示沒有標誌。 | null |

## **elements.text**

課程中每個命名文字角色的排版屬性。 所有角色共享相同的屬性。

### **文字角色**

| **角色** | **應用於** |
|--------------|------------------------------------------------------------------------------|
| 課程標題 | 課程開場投影片的主標題 |
| 主題標題 | 每個主題投影片頂部的標題 |
| 區塊標題 | 內容組件中的標題，如手風琴標題與卡片標題 |
| 副標題 | 主題投影片中的次要標題 |
| 問題 | 測驗與知識檢查題目文本 |
| 說明 | 圖片與媒體區塊下方的說明文字 |
| 段落 | 內容投影片中的正文 |
| buttonLabel | 按鈕上的文字與行動呼籲元素 |

### **共享文字屬性**

以下屬性適用於上述所有文字角色。

| **財產** | **類型** | **被接受的價值觀** | **描述** |
|--------------------|-----------------------|--------------------------------------------------------------------|---------------------------------------------------------|
| 字體家族 | CSS 變體或字型堆疊 | var（--font-heading）、var（--font-body），或完整的字型堆疊字串 | 此文字角色的字型家族。 |
| 字體大小 | PX 價值 | 任何像素值 | 字體大小。 |
| 字體粗細 | 字串 | 僅支援「粗體」或「一般」——不支援數字 | 字體粗細。 |
| fontStyle | 字串 | 「正常」或「斜體」 | 字體風格。 |
| 色彩 | CSS var 或 hex | 任何透過 var（--tokenName） 或直接十六進位值的調色盤標記 | 文字顏色。 |
| textAlign | 字串 | 「左」、「中間」或「右」 | 橫向文字對齊。 |
| 字母間距 | 字串 | 「正常」、px 值或 em 值 | 角色之間的距離。 |
| 線路高度 | 字串 | 百分比或無單位值 | 線高。 |
| 正文裝飾 | 字串 | 「無」、「底線」或「直線」 | 文字裝飾。 |
| textTransform | 字串 | 「無」、「大寫」、「小寫」或「大寫」 | 簡訊箱轉換。 |
| paddingInlineStart | PX 價值 | 任何像素值 | 左側填充加在文字區塊上。 |
| 段落間距 | PX 價值 | 任何像素值 | 在文字區塊內每個段落下方加空。 |

### **文字角色值 - Slate 主題**

| **角色** | **字體家族** | **字體大小** | **字體粗細** | **fontStyle** | **色彩** | **textAlign** | **字母間距** | **線路高度** | **textTransform** |
|--------------|---------------------|--------------|----------------|---------------|--------------------|---------------|-------------------|----------------|-------------------|
| 課程標題 | var（--字型標頭） | 48px | 粗體 | 正常 | var（--textPrimary） | 中心 | -0.01em | 130% | 沒有 |
| 主題標題 | var（--字型標頭） | 40px | 正常 | 正常 | var（--textPrimary） | 左邊 | 0 | 135% | 沒有 |
| 區塊標題 | var（--字型標頭） | 24px | 粗體 | 正常 | var（--textPrimary） | 左邊 | 0 | 140% | 沒有 |
| 副標題 | var（--font-body） | 20px | 粗體 | 正常 | var（--textPrimary） | 左邊 | 0.01em | 150% | 沒有 |
| 問題 | var（--字型標頭） | 24px | 正常 | 正常 | var（--textPrimary） | 左邊 | 0 | 150% | 沒有 |
| 說明 | var（--font-body） | 13px | 正常 | 正常 | var（--textPrimary） | 左邊 | 0.02em | 170% | 沒有 |
| 段落 | var（--font-body） | 16px | 正常 | 正常 | var（--textPrimary） | 左邊 | 0.01em | 190% | 沒有 |
| buttonLabel | var（--font-body） | 14px | 粗體 | 正常 | var（--textInverse） | 中心 | 0.06em | 125% | 大寫 |

## **元素-結構表面**

這些屬性控制球場固定佈局表面的背景與邊界。

| **元素** | **財產** | **類型** | **描述** | **板岩價值** |
|--------------|--------------|-------------------|---------------------------------------------------|----------------------------|
| 畫布 | 背景 | CSS 變體 | 主菜畫布背景色 | VAR（--背景） |
| 標頭 | 背景 | CSS 變體 | 賽道標頭條 背景色 | VAR（--背景） |
| 標頭 | 邊界 | CSS 邊界字串 | 賽道標題欄的下邊框 | 1px 實心變異（--次要） |
| 頁腳 | 背景 | CSS 變體 | 球場基腳條背景色 | VAR（--背景） |
| 頁腳 | 邊界 | CSS 邊界字串 | 球場基腳桿的頂端邊框 | 1px 實心變異（--次要） |
| 課程標題 | 背景 | CSS 變體 | 課程標題標題區域的背景色 | var（--口音） |
| 主題 | 背景 | CSS 變體 | 每張主題投影片的背景色 | VAR（--背景） |
| 主題 | 邊界 | CSS 邊界字串 | 主題投影片容器周圍的邊框 | 1px 實心變異（--次要） |
| 導航 | 背景 | CSS 變體 | 課程導航面板的背景色 | var（--backgroundSubtle） |
| 導航 | 邊界 | CSS 邊界字串 | 課程導航面板上的邊框 | 1px 實心變異（--次要） |
| 按鈕 | 背景 | CSS 變體 | 主動作按鈕的背景顏色 | var（--口音） |
| 頁碼 | 背景 | CSS 變體 | 分頁控制的背景色 | var（--backgroundSubtle） |

## **元素 - 共享元件屬性**

這些屬性會出現在所有內容區塊元件上：paragraphBlock、videoBlock、imageGrid、accordion、carousel、flipCard 和 timeline。

| **財產** | **類型** | **描述** |
|------------------------|-------------------|---------------------------------------------------------------------------------------------------|
| 背景 | CSS 變體或顏色 | 組件區塊的外部背景。 通常是「透明」的。 |
| 卡片背景顏色 | CSS 變體或顏色 | 在組件內對單張卡片進行背景填充。 |
| 卡片邊界 | CSS 邊界字串 | 每張卡片都加上邊框。 完整的 CSS 簡寫，例如「1px solid var（--secondary）」。 |
| cardShadowOffset（陰影偏移） | 字串 | 卡片投影的 X 和 Y 偏移量，例如「0px 2px 6px」。 |
| cardShadowColor | CSS 變體或顏色 | 卡片投影的顏色。 |
| cardShadowOpacity | 百分比字串 | 卡片陰影的不透明度。 設定為「0%」以去除陰影。 |
| 水平間距縮放 | 數字字串 | 此組件的水平間距標記套用乘數。 「1」使用預設的間距。 |
| 垂直間距縮放 | 數字字串 | 此組件的垂直間距標記套用乘數。 「1」使用預設的間距。 |
| 半徑縮放 | 數字字串 | 乘數套用於半徑標記上。 「1」使用預設半徑。 |
| nestedAccentColor | CSS 變體或顏色 | 元件內巢狀元素的強調色。 僅適用於paragraphBlock。 |

### **共享元件值 - Slate 主題**

| **組成部分** | **卡片背景顏色** | **卡片邊界** | **cardShadowOpacity** |
|----------------|-----------------------------|----------------------------|---------------------------|
| 段落封鎖 | var（--backgroundSubtle） | 1px 實心變異（--次要） | 8% |
| videoBlock | var（--backgroundSubtle） | 1px 實心變異（--次要） | 8% |
| imageGrid | var（--backgroundSubtle） | 1px 實心變音（--重音） | 8% |
| 手風琴 | var（--backgroundSubtle） | 1px 實心變異（--次要） | 8% |
| 旋轉木馬 | var（--backgroundSubtle） | 1px 實心變異（--次要） | 8% |
| 翻轉卡 | var（--backgroundSubtle） | 1px 實心變異（--次要） | 8% |
| 時間軸 | var（--backgroundSubtle） | 1px 實心變異（--次要） | 8% |

## **元素 - 元件專屬性質**

具有特定於單一元件類型的特性。

| **組成部分** | **財產** | **類型** | **描述** | **板岩價值** |
|----------------|--------------------------|----------|------------------------------------------------------------------|-------------------------|
| 段落封鎖 | nestedAccentColor | CSS 變體 | 段落區塊中巢狀元素的強調色 | var（--口音） |
| 翻轉卡 | 卡片正面背景顏色 | CSS 變體 | 翻轉卡正面的背景顏色 | var（--backgroundSubtle） |
| 翻轉卡 | 卡片背面背景顏色 | CSS 變體 | 翻牌背面的背景色——揭示色 | var（--口音） |
| 翻轉卡 | 箭頭顏色 | CSS 變體 | 翻轉指示箭頭圖示的顏色 | var（--textInverse） |
| 標籤 | activeBg | CSS 變體 | 目前選中的分頁背景顏色 | var（--口音） |
| 標籤 | 不活躍Bg | CSS 變體 | 未選取分頁的背景色 | var（--backgroundSubtle） |
| 標籤 | containerBg | CSS 變體 | 分頁列容器的背景顏色 | var（--backgroundSubtle） |
| 時間軸 | 軌道顏色 | CSS 變體 | 時間軸節點間連接線的顏色 | VAR（--次要） |
| 時間軸 | progressCompletedBg | CSS 變體 | 完成時間軸進度標記的填充顏色 | var（--口音） |
| 時間軸 | 進展目前邊界 | CSS 變體 | 當前時間軸進度標記的邊框顏色 | var（--口音） |
| 時間軸 | progressUnreachedBg | CSS 變體 | 尚未到達的時間軸標記填充顏色 | VAR（--次要） |
| 時間軸 | 進展未觸及邊界 | CSS 變體 | 尚未抵達的時間軸標記邊框顏色 | var（--backgroundSubtle） |

## **元素評估**

測驗與知識檢查的性質。

| **財產** | **類型** | **描述** | **板岩價值** |
|----------------------------|----------------|------------------------------------------------------------------------------|-------------------------|
| 背景 | CSS 變體 | 評估區塊的外部背景 | 透明 |
| optionTextColor | CSS 變體 | 答案選項標籤的文字顏色 | var（--textPrimary） |
| optionIndicatorColor | CSS 變體 | 無線電按鈕或勾選框指示器的顏色 | var（--口音） |
| optionSelectedColor | CSS 變體 | 顏色套用於所選選項指示器 | var（--口音） |
| 選項勾選顏色 | CSS 變體 | 勾選圖示顏色 | var（--textInverse） |
| 選項背景顏色 | CSS 變體 | 每個答案選項的背景色 | VAR（--背景） |
| 選項懸浮背景顏色 | CSS 變體 | 懸停選項的背景色 | var（--backgroundSubtle） |
| button背景顏色 | CSS 變體 | 提交或檢查答案按鈕的背景色 | var（--口音） |
| buttonTextColor | CSS 變體 | 提交或檢查答案按鈕標籤的文字顏色 | var（--textInverse） |
| buttonHoverBackgroundColor | CSS 變體 | 懸停按鈕的背景顏色 | var（--口音） |
| 回饋正確顏色 | 六角形顏色 | 正確答案回饋面板的背景色 | #D7F7E1 |
| 反饋不正確顏色 | 六角形顏色 | 錯誤答案回饋面板的背景色 | #FFEBE8 |
| 回饋TextColor | 六角形顏色 | 回饋面板內的文字顏色 | #111111 |
| 選項邊框更正顏色 | 六角形顏色 | 正確答案選項在答案揭曉後顯示邊框顏色 | #079355 |
| 選項邊界不正確顏色 | 六角形顏色 | 答案揭曉後，錯誤選擇選項的邊框顏色 | #D73220 |
| 水平間距縮放 | 數字字串 | 評估部分內水平間距的乘數 | &quot;1&quot; |
| 垂直間距縮放 | 數字字串 | 評量部分垂直間距的乘數 | &quot;1&quot; |
| 半徑縮放 | 數字字串 | 評估組件內邊界半徑的乘數 | &quot;1&quot; |

## **調色盤標記 var（） 參考**

在元素值中使用這些 var（） 表達式來參考調色盤標記。 更新調色盤標記會自動更新所有使用該標記的元素。

| **表達方式** | **參考資料** |
|-------------------------|-------------------------------------|
| var（--前景） | 基礎。調色盤。前景 |
| VAR（--背景） | 基礎。調色盤。背景 |
| var（--口音） | 基礎。調色盤。口音 |
| var（--backgroundSubtle） | foundation.palette.background 微妙 |
| VAR（--次要） | 基礎。調色盤。次要 |
| var（--textPrimary） | foundation.palette.textPrimary |
| var（--textInverse） | foundation.palette.textInverse |
| var（--字型標頭） | foundation.fonts.標題 |
| var（--font-body） | foundation.fonts.body |

## 主題 json 範例

```
{
  "id": "slate",
  "name": "Slate",
  "version": "1.0.0",
  "description": "A warm, authoritative theme with cream background, Adobe red accents, and the Roboto Slab + Roboto type system",
  "author": "Content Composer",
  "source": "custom",
  "isDefault": false,
  "foundation": {
    "palette": {
      "foreground": "#1A1A1A",
      "background": "#FAF7F2",
      "accent": "#E8001C",
      "backgroundSubtle": "#F0EBE1",
      "secondary": "#D9D3C9",
      "textPrimary": "#1A1A1A",
      "textInverse": "#FFFFFF"
    },
    "fonts": {
      "heading": "Roboto Slab, Georgia, 'Times New Roman', serif",
      "body": "Roboto, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif"
    },
    "spacing": {
      "horizontal": {
        "xs": "4px",
        "s": "8px",
        "m": "12px",
        "l": "16px",
        "xl": "24px"
      },
      "vertical": {
        "xs": "4px",
        "s": "8px",
        "m": "16px",
        "l": "24px",
        "xl": "32px"
      }
    },
    "radius": {
      "none": "0px",
      "s": "4px",
      "m": "8px",
      "l": "16px",
      "full": "9999px"
    },
    "logo": null
  },
  "elements": {
    "text": {
      "lessonTitle": {
        "fontFamily": "var(--font-heading)",
        "fontSize": "48px",
        "fontWeight": "bold",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "center",
        "letterSpacing": "-0.01em",
        "lineHeight": "130%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "topicTitle": {
        "fontFamily": "var(--font-heading)",
        "fontSize": "40px",
        "fontWeight": "normal",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0",
        "lineHeight": "135%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "blockHeading": {
        "fontFamily": "var(--font-heading)",
        "fontSize": "24px",
        "fontWeight": "bold",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0",
        "lineHeight": "140%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "subheading": {
        "fontFamily": "var(--font-body)",
        "fontSize": "20px",
        "fontWeight": "bold",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0.01em",
        "lineHeight": "150%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "question": {
        "fontFamily": "var(--font-heading)",
        "fontSize": "24px",
        "fontWeight": "normal",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0",
        "lineHeight": "150%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "caption": {
        "fontFamily": "var(--font-body)",
        "fontSize": "13px",
        "fontWeight": "normal",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0.02em",
        "lineHeight": "170%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "paragraph": {
        "fontFamily": "var(--font-body)",
        "fontSize": "16px",
        "fontWeight": "normal",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0.01em",
        "lineHeight": "190%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "buttonLabel": {
        "fontFamily": "var(--font-body)",
        "fontSize": "14px",
        "fontWeight": "bold",
        "fontStyle": "normal",
        "color": "var(--textInverse)",
        "textAlign": "center",
        "letterSpacing": "0.06em",
        "lineHeight": "125%",
        "textDecoration": "none",
        "textTransform": "uppercase",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      }
    },
    "canvas": {
      "background": "var(--background)"
    },
    "header": {
      "background": "var(--background)",
      "border": "1px solid var(--secondary)"
    },
    "footer": {
      "background": "var(--background)",
      "border": "1px solid var(--secondary)"
    },
    "lessonHeader": {
      "background": "var(--accent)"
    },
    "topic": {
      "background": "var(--background)",
      "border": "1px solid var(--secondary)"
    },
    "navigation": {
      "background": "var(--backgroundSubtle)",
      "border": "1px solid var(--secondary)"
    },
    "button": {
      "background": "var(--accent)"
    },
    "pagination": {
      "background": "var(--backgroundSubtle)",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "paragraphBlock": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "nestedAccentColor": "var(--accent)",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "imageBlock": {
      "background": "transparent",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "videoBlock": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "imageGrid": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--accent)",
      "cardShadowOffset": "0px 2px 8px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "accordion": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "carousel": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "flipCard": {
      "background": "transparent",
      "cardFrontBackgroundColor": "var(--backgroundSubtle)",
      "cardBackBackgroundColor": "var(--accent)",
      "arrowColor": "var(--textInverse)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "tabs": {
      "background": "transparent",
      "activeBg": "var(--accent)",
      "inactiveBg": "var(--backgroundSubtle)",
      "containerBg": "var(--backgroundSubtle)",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "timeline": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "trackColor": "var(--secondary)",
      "progressCompletedBg": "var(--accent)",
      "progressCurrentBorder": "var(--accent)",
      "progressUnreachedBg": "var(--secondary)",
      "progressUnreachedBorder": "var(--backgroundSubtle)",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "assessment": {
      "background": "transparent",
      "optionTextColor": "var(--textPrimary)",
      "optionIndicatorColor": "var(--accent)",
      "optionSelectedColor": "var(--accent)",
      "optionCheckmarkColor": "var(--textInverse)",
      "optionBackgroundColor": "var(--background)",
      "optionHoverBackgroundColor": "var(--backgroundSubtle)",
      "buttonBackgroundColor": "var(--accent)",
      "buttonTextColor": "var(--textInverse)",
      "buttonHoverBackgroundColor": "var(--accent)",
      "feedbackCorrectColor": "#D7F7E1",
      "feedbackIncorrectColor": "#FFEBE8",
      "feedbackTextColor": "#111111",
      "optionBorderCorrectColor": "#079355",
      "optionBorderIncorrectColor": "#D73220",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    }
  }
}
```
