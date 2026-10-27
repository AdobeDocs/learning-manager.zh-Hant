---
description: 了解 Go1 完成 webhook 如何幫助 Adobe Learning Manager 捕捉課程完成紀錄，即使學習者提前關閉瀏覽器
jcr-language: en_us
title: Go1 完成追蹤與 webhook
exl-id: 25c9c401-905f-4408-89ac-ac630a45a0c7
source-git-commit: aaea92d190b8ab22ce9f08c309faf5caa0b58a69
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%
---

# Go1 完成追蹤與 webhook

## 概觀

Adobe Learning Manager 現在支援基於 webhook 的 Go1 內容完成追蹤。 此強化提升了 Go1 與 Learning Manager 之間課程完成同步的可靠性。 即使學習者在完成課程後立即退出課程玩家，完成事件仍會被捕捉。

Go1 利用 webhook 在學習者完成課程時，將課程完成通知傳送給學習管理員。 學習管理員會獨立於學習者的瀏覽器工作階段接收並處理這些完成事件。

Go1 也會重試 webhook 的傳遞，直到 Learning Manager 確認收到完成事件為止。 這有助於防止遺漏或不完整的學習紀錄。

## 這項增強解決的問題

過去，完成度追蹤依賴Go1玩家與學習管理員之間的溝通，而學習者的瀏覽器會話則保持活躍。 若學習者在完成狀態尚未完全處理前關閉瀏覽器視窗或離開，完成紀錄可能會遺失。

結果是：

* 課程完成紀錄可能不會出現在學習者成績單中。
* 管理員可以發現實際完成與記錄完成之間的差異。
* 錯過的完成事件無法自動恢復。

## 活動工作流程

1. 學習者啟動並完成 Go1 課程。
1. Go1 記錄完成。
1. Go1 會將完成的 webhook 傳送給 Learning Manager。
1. 學習經理會驗證並接受完成事件。
1. 學習經理會更新學習者的完成狀態。
1. 如果 Learning Manager 沒有回應該事件，Go1 會自動重試傳送。

## 常見問題

**這項變更是否需要管理員設定**

不，這項變更不需要任何管理員設定。

**現有的Go1課程會受到影響嗎？**

不，現有的Go1課程不會受到影響。 此強化提升了 Go1 內容的完成同步。

**如果學習者提前關閉瀏覽器會發生什麼事**

Go1 會獨立於學習者的瀏覽器會話中傳送完成的 webhook。 即使學習者退出課程玩家，Go1 仍會不斷重試交付，直到學習管理員確認完成事件。
