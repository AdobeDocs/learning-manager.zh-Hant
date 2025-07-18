---
jcr-language: en_us
title: 管理員常見問題
description: Adobe Learning Manager管理員的常見問題集
contentowner: manochan
exl-id: 8b113a4e-73f4-4cd5-982a-cefdf5388e91
source-git-commit: 0dade561e53e46f879e22b53835b42d20b089b31
workflow-type: tm+mt
source-wordcount: '2462'
ht-degree: 0%

---

# 管理員常見問題

<table>
 <tbody>
  <tr>
   <td><img src="assets/administrator2.png"></td>
   <td>
    <p>請閱讀下文，瞭解與管理員角色相關聯的Learning Manager常見問題。 </p></td>
  </tr>
 </tbody>
</table>

+++我可以大量新增使用者嗎？ 如何進行？

可以，您可以使用CSV上傳功能大量新增使用者。 如需詳細資訊，請參閱此[文章](/help/migrated/administrators/feature-summary/add-users-user-groups.md#bulk-upload-internal-users)。

+++

+++我在為學習者建立登入時輸入的電子郵件ID有誤，我該如何修正？

若要修正使用者登入，您必須在Learning Manager中匯入CSV。 範例CSV檔案會附加在此頁面底部，以供您參考。 由於電子郵件被視為個人的唯一識別碼，因此無法編輯。 請依照下列步驟執行：

1. 在CSV中新增具有正確電子郵件ID的相同使用者，並將他的電子郵件ID新增到範例CSV中的「員工經理的電子郵件」欄，以確保他仍然擔任其他使用者的經理。
1. 將您帳戶中的其他使用者新增至CSV，包括您自己
1. 在Learning Manager管理員應用程式 — >使用者 — >新增 — >匯入CSV上匯入此檔案
1. 將所有欄位（如對話方塊中的提示）對應至對應的CSV欄。
1. 按一下「儲存」。

使用者應已新增至學習者頁面。

[Learning Manager範例CSV.csv](https://helpx.adobe.com/content/dam/help/en/captivate_prime/learning-manager-sample-csv.zip)

+++

+++如何設定警報？

在Adobe Learning Manager 1.0版本中，您可以建立通知。 如需詳細資訊，請參閱[通知問題](/help/migrated/administrators/feature-summary/user-notifications.md)。

+++

+++如何為課程新增憑證？

Adobe Learning Manager不提供課程的憑證。 但是，管理員可以按一下左側面板中的「徽章」索引標籤，為每個課程建立徽章。 當管理員將學習者註冊到課程時，他還可以將徽章與課程相關聯。

+++

+++如何匯入憑證的簽章？

Adobe Learning Manager沒有匯入憑證或徽章簽章的功能。

+++

+++我可以設定課程的行事曆嗎？ 如何進行？

在Adobe Learning Manager 1.0版中，我們沒有任何布建可設定課程的行事曆。

+++

+++如何直接註冊輪候學習者？

當名額有限時，學習者會根據其註冊順序等候任何教室課程。 管理員可以為任何教室課程選擇等候名單中的學習者，並分配名額以取代名額限制。 學習者會在管理員配置位子後立即註冊課程。

1. 以管理員身分登入後，請按一下左窗格中的「課程」 。
1. 從可用課程清單中，按一下您選擇的任何教室課程的課程名稱。 新頁面隨即出現，內含課程的詳細資訊。
1. 按一下課程詳細資訊頁面左窗格中的「輪候表」。 頁面上會顯示等候中列出的學習者清單。
1. 選取學習者並按一下「分配名額」 ，將學習者直接註冊至課程，取代名額限制。

如需詳細資訊，請參閱[輪候和出席](/help/migrated/administrators/feature-summary/waitlist-attendance-management.md)功能。

+++

+++如何記錄教室模組學習者的出勤率？

是，您可以依照下列步驟記錄出席情況：

1. 以管理員身分登入後，請按一下左窗格中的「課程」 。
1. 從可用課程清單中，按一下您選擇的任何教室模組/課程的課程名稱。 新頁面隨即出現，內含課程的詳細資訊。
1. 選取學習者並按一下「儲存」來記錄課程完成。

如果課程包含多個模組，且學習者僅完成其中一個，您可以選取單一模組並按一下「儲存」 ，標籤學習者的完成狀態。 如果學習者完成課程的所有模組，您可以按一下「全選」選項並按一下「儲存」。

如需詳細資訊，請參閱[輪候和出席](/help/migrated/administrators/feature-summary/waitlist-attendance-management.md)功能。

+++

+++如何加入L3意見回饋選項？

在課程中註冊學習者時，您可以新增L3意見回饋。 請依照下列步驟新增L3意見問題：

1. 以管理員身分登入後，請按一下左窗格中的「課程」 。 所有課程的清單都會顯示在右側頁面。
1. 按一下您要新增L3意見回饋的課程圖磚
1. 按一下左窗格中的執行個體預設值。
1. 按一下L3 — 行為變更意見旁的圓切換按鈕以選取它。
1. 在L3問題下方的文字區域中新增L3意見問題。

+++

+++如何為經理提名課程尋求經理提名？

身為管理員，您可以遵循下列步驟來尋求經理的課程指派：

1. 按一下左窗格中的「課程」
1. 將滑鼠停留在任何Manager指定的課程上，然後按一下&#x200B;**[!UICONTROL Seek Manager Nomination]**。

1. 在執行個體清單中，按一下&#x200B;**[!UICONTROL Managers nominated]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Add Managers]**&#x200B;連結。

1. 新增管理員名稱、分配的座位數，然後按一下勾號以儲存變更。

建立課程時，作者會選擇課程型別為經理指派。

+++

+++如何將學習者註冊至特定課程？

請依照下列步驟為學習者註冊課程：

1. 以管理員身分登入後，請按一下左窗格中的「課程」 。 所有課程清單會顯示在右側頁面。
1. 選擇您要新增學習者的課程，並將滑鼠游標停留在該課程上。
1. 按一下「註冊學習者」並新增學習者名稱。 **注意：**&#x200B;您可以一次新增一或多個學習者。

+++

+++如何將學習者指派給特定技能？

請依照下列步驟將學習者指派給能力：

1. 以系統管理員身分登入後，在左窗格按一下&#x200B;**[!UICONTROL Skills]**。
1. 按一下每個能力的核取方塊，選取一或多個技能，然後按一下頁面右上角的&#x200B;**[!UICONTROL Actions]**&#x200B;下拉式清單。
1. 按一下「指派給使用者」。
1. 開始輸入使用者的名稱，從下拉式清單中選擇，然後按一下&#x200B;**[!UICONTROL Save]**。

   >[!NOTE]
   >
   >您可以按一下「新增更多使用者」並重複第4步，讓多個學習者註冊技能。

+++

+++如何建立學習計畫工作階段？

若要建立學習計畫，請遵循下列步驟：

1. 按一下左窗格中的「學習方案」 。 學習計畫頁面會出現，其中包含現有學習計畫的清單。
1. 按一下頁面右上角的「新增」 。\
   輸入計畫名稱、總覽和說明，然後按一下儲存。
1. 按一下左窗格中的「課程」 。
1. 按一下每個課程圖磚上的+ ，新增一或多個課程。

   >[!NOTE]
   >
   >註冊學習者或執行個體前，您需要發佈學習計畫。

1. 按一下左窗格上的[執行個體]，然後按一下頁面右角的&#x200B;**[!UICONTROL Add new instances]**&#x200B;以包含執行個體的詳細資訊。

如需學習計畫的詳細資訊，請參閱[學習計畫功能。](/help/migrated/administrators/feature-summary/learning-programs.md)

+++

+++如何修改或自訂所有角色的報表？

按一下每個報表右上角的下拉箭頭，以編輯/修改報表。 完成變更後按一下「儲存」 ，檢視修改後的報表。

+++

+++如何修改課程、學習方案和公司設定檔？

您可以在發佈課程或學習計畫後加以編輯。 如需詳細資訊，請參閱[課程](/help/migrated/administrators/feature-summary/courses.md)和[學習計畫](/help/migrated/administrators/feature-summary/learning-programs.md)說明內容。

若要修改公司設定檔，請按一下左窗格的&#x200B;**[!UICONTROL Settings]**，然後按一下頁面右上角的&#x200B;**[!UICONTROL Change]**。

+++

+++如何搜尋課程？

以管理員身分登入後，請按一下左窗格中的「課程」 。 所有可用課程的清單隨即顯示。

搜尋課程有兩種方式：

1. 按一下右上角顯示的搜尋圖示。 搜尋欄位隨即顯示。 輸入課程名稱或與課程相關的任何關鍵字，以尋找您的課程。
1. 使用篩選器篩選課程清單。

您可以按一下這些選項中的每一個，依狀態篩選課程，例如「全部」、「已發佈」和「已淘汰」。 您也可以按一下「能力」並選取每個能力，根據能力進行搜尋。

根據您的選擇，您可以檢視經過篩選的課程清單，並選取所需課程。

+++

+++我可以變更應用程式的主題嗎？ 如何進行？

可以，您可以根據組織的需求，變更Learning Manager應用程式的主題和品牌。 提供一組五個代表性影像，用來在套用您的應用程式之前預覽您的顏色主題變更。 分別按一下影像左側和右側的&lt;和>符號來瀏覽這些影像以進行預覽。

按一下左窗格上的&#x200B;**[!UICONTROL Branding]**&#x200B;以更新您的組織名稱、變更子網域、記錄樣式和主題。 按一下這些主題旁的&#x200B;**[!UICONTROL Edit]**&#x200B;以修改內容。

如需詳細資訊，請參閱[色彩主題與品牌說明](/help/migrated/administrators/feature-summary/themes.md)。

+++

+++如何設定課程的徽章？

1. 以管理員身分登入後，請按一下左窗格中的「徽章」 。
1. 按一下所顯示頁面右上角的「新增」 。
1. 新增徽章名稱。
1. 按一下上傳徽章並按一下儲存，即可上傳徽章。

+++

+++如何為課程設定gamification點數？

您可以遵循下列步驟，為學習者設定gamification點數：

1. 以管理員身分登入後，請按一下「Gamification」 。 此時會出現一個頁面，內含銅、銀、金和白金等層級的清單，以及每個層級要達到的所需點數。 有任務和對應點清單可供使用。
1. 按一下每個任務旁的「編輯」圖示以設定/修改點。

如需詳細資訊，請參閱[Gamification功能](/help/migrated/administrators/feature-summary/gamification.md)。

+++

+++如何為經理和學習者建立報告？

您可以依照下列步驟建立報表：

1. 按一下左窗格中的「報表」 。 報告摘要頁面隨即顯示。
1. 在「報表」頁面上，按一下右上角的&#x200B;**[!UICONTROL Add]**。

   **[!UICONTROL Add Report]**&#x200B;對話方塊出現。

1. 填寫所有必填欄位，然後按一下「儲存」。

只有管理員和管理員可以建立或檢視報表。 如需詳細資訊，請參閱[報告功能](/help/migrated/administrators/feature-summary/reports.md)。

+++

+++如何變更為學習者、經理和作者角色？

您可以將帳戶登入切換為其他角色，例如學習者、經理和作者，而無需登出您的帳戶。

1. 按一下頁面右上角個人資料圖片旁邊的下拉箭頭。\
   隨即出現快顯功能表。
1. 選取每個可用的角色，以取得個別角色帳戶的存取權。

+++

+++如何為使用者包含通知？

經理、作者和學習者可以看到根據課程活動的通知。 管理員可以按照以下步驟為所有使用者啟用/停用通知：

1. 按一下左窗格中的[電子郵件範本]，然後選擇[一般]、[使用者註冊]、[完成]和[意見回饋]標籤。
1. 從下列事件中，按一下每個事件旁的「否/是」切換按鈕，然後選擇「是」以啟用通知。 按一下「否」停用傳送特定事件的通知。

+++

+++如何允許課程的外部註冊？

Adobe Learning Manager提供將外部部門成員或組織的外部員工註冊到應用程式的功能。

1. 按一下左窗格上的&#x200B;**[!UICONTROL Users]**。
1. 按一下左窗格上的&#x200B;**[!UICONTROL External]**。
1. 按一下頁面右上角的&#x200B;**[!UICONTROL Add]**。

   新增使用者對話方塊就會顯示。

1. 新增設定檔名稱、經理電子郵件、分配的名額、到期資訊。 您也可以將影像新增至外部設定檔。
1. 按一下&#x200B;**[!UICONTROL Save]**。

管理員可以複製註冊URL並將其傳送到外部註冊群組。 外部使用者可註冊、登入Learning Manager應用程式並存取其課程。

+++

+++如何為L1意見回饋新增問卷？

建立意見調查表，供學習者完成課程後使用。 依預設，有三種範例問題可供使用。 請依照下列步驟建立問卷。

1. 按一下左窗格中的「意見回饋」 。 回饋意見調查表視窗隨即顯示。
1. 按一下&#x200B;**[!UICONTROL Edit]**&#x200B;以新增/修改問卷。

您可以新增一組問卷，並在不需要時選擇不顯示。 按一下核取方塊以啟用/停用特定問題。

+++

+++如何設定技能與等級？

1. 按一下Administrator視窗左窗格中的「能力」。
1. 按一下「新增」以新增能力。
1. 新增能力名稱、摘要，以及每個層次對應的學分。

   依預設，每個能力都可使用具有0個信用額的單一層次。

1. 按一下&#x200B;[!UICONTROL **新增層級**]，為每個能力新增層級，然後按一下[儲存]。 您最多可以新增5個層級。

儲存能力後，您便無法從能力中移除層次。 管理員也可以為學習者指派特定能力和層級。

+++

+++如何設定組織課程的計費系統？

1. 在左窗格按一下&#x200B;[!UICONTROL **帳單**]。

   帳單資訊會顯示在頁面上。

1. 按一下「[!UICONTROL **訂閱**]」標籤。
1. 在「學習者套裝」欄位中輸入您要訂購的套裝數量，然後按一下頁面右上角的「下訂單」 。

   根據您組織中的學習者人數選擇套件數量，然後下訂單。 若是採購單導向程式，請寄信至[learningmanagersales@adobe.com](mailto:learningmanagersales@adobe.com)。

1. 輸入您的聯絡資訊、選擇信用卡型態、提供信用卡詳細資料，然後按一下「完成訂單」。

如需詳細資訊，請參閱[帳單管理](/help/migrated/administrators/feature-summary/billing-management.md)功能。

+++

+++我可以自訂憑證設計嗎？ 如何進行？

在Adobe Learning Manager中，您可以發行徽章來辨識學習者。 如需詳細資訊，請參閱徽章功能。  另請參閱認證功能。

+++

+++如何設定我的公司設定檔？

1. 以系統管理員身分登入後，在左窗格按一下&#x200B;**[!UICONTROL Company Info]**。
1. 按一下頁面中的各個選項，新增公司設定檔、子網域、標誌。

+++

+++如何新增課程？

若要新增課程，您需要切換作者角色。 您只能根據狀態為&#x200B;**[!UICONTROL Complete]**、**[!UICONTROL Published]**&#x200B;和&#x200B;**[!UICONTROL Retired]**&#x200B;的課程來檢視可用課程清單。

若要檢視課程，請按一下左窗格上的&#x200B;**[!UICONTROL Courses]**。 如需詳細資訊，請參閱[建立課程](/help/migrated/administrators/feature-summary/courses.md)

+++

+++如何將不同的角色新增至應用程式？

若要新增使用者，請遵循下列步驟：

1. 以管理員身分登入後，請按一下左窗格中的使用者。 您也可以按一下視窗左窗格中的「快速入門」並按一下「新增使用者」來新增使用者。
1. 若要新增使用者，請按一下頁面右上角的「新增」 。

依預設，所有新使用者都會獲指派學習者角色。 您可以按一下頁面右上角的&#x200B;**[!UICONTROL Actions]**&#x200B;並選擇&#x200B;**[!UICONTROL Assign Role]** > **[!UICONTROL Make Author]**&#x200B;或&#x200B;**[!UICONTROL Make Admin]**，將管理員或作者角色指派給學習者。

如需新增學習者、作者及管理員的詳細資訊，請參閱[新增使用者](/help/migrated/administrators/feature-summary/add-users-user-groups.md)功能。

+++

+++如何為學習者變更背景影像？

聯絡Learning Manager支援團隊。

+++

+++我可以在哪裡找到我的Learning Manager帳戶ID？

您可以從開啟Learning Manager的瀏覽器取得帳戶ID。

*/app/admin？i_qp_user_id=12761637&amp;**accountId=6849***

+++

+++是否有我可以提取的報告，或某人可以為我提取的報告，為我顯示LMS中所有課程的清單？

可以，您可以提取&#x200B;**[!UICONTROL Training Report]**，其中包含學習管理系統中的所有課程、學習計畫、認證。 若要下載報表，請遵循下列步驟：

1. 以管理員身分登入。
2. 按一下&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Custom Reports]** > **[!UICONTROL Excel Reports]** > **[!UICONTROL Trainings Report]**。
3. 從下拉式清單中選取&#x200B;**[!UICONTROL All Trainings]**。
4. 按一下&#x200B;**[!UICONTROL Download]**。

+++

+++我可以在哪裡下載應用程式的案頭版本？

請依照下列步驟下載案頭版本：

1. 以管理員身分登入。
2. 按一下&#x200B;**[!UICONTROL Social Learning]** > **[!UICONTROL Settings]**。
3. 在&#x200B;**[!UICONTROL Download Configuration]**&#x200B;下，根據您的作業系統按一下超連結。

+++
