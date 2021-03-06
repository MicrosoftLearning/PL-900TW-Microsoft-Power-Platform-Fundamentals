---
lab:
    title: '實驗室 3：如何建立畫布應用程式 (第 2 部分)'
    module: '單元 3：Power Apps 入門'
---

# 單元 3：Power Apps 入門
## 實驗室 2：如何建立畫布應用程式 (第 2 部分)

# 案例

Bellows College 是一個教育組織，校園內有多棟大樓。校園訪客造訪情況目前記錄在紙本日誌中。此資訊並未以一致的方式擷取，而且也無法收集和分析整個校園造訪情形的相關資料。 

校園行政單位想要更新其訪客登記系統，讓保全人員控管各棟大樓的出入狀況，且所有造訪情形都必須由大樓負責人預先登記和記錄。

在整個課程中，您將建立應用程式並執行自動化功能，以便 Bellows College 的行政和保全人員能夠管理及控管校內大樓的出入狀況。 

在此實驗室的第 2 部分中，將建立、設計和建置 Power Apps 畫布應用程式，讓保全人員能夠在建築物入口處使用，以便快速確認和登記訪客。

# 高階實驗室步驟

您將依照以下大綱設計畫布應用程式：

-   使用手機尺寸規格建立應用程式
-   連接至 Dataverse 做為資料來源
-   擷取輸入 (訪客代碼) 並找到訪客資料列
-   設定表單檢視器控制項以顯示訪客資訊
-   使用 Dataverse 檢視填入資源庫
-   處理訪客的簽入和簽出程序

## 先決條件

* 完成**單元 0 實驗室 0：驗證實驗室環境**
* 完成**單元 2 實驗室 1：Microsoft Dataverse 簡介**

## 開始前要考慮的事項

-   保全人員需要快速存取哪些資訊？
-   如果訪客代碼無效，應該如何處理？
-   如果訪客未按照預定時間內到達，應該如何處理？

# 練習 1：建立安全性畫布應用程式

**目標：** 在此練習中，您將建立畫布應用程式。

## 工作 1：建立畫布應用程式

1.  開啟您的 [校園管理] 解決方案

    -   登入 <https://make.powerapps.com>

    -   如果右上方顯示的環境並非您的練習環境，請選取您的**環境**。 

    -   選取 **[解決方案]**。

    -   按一下以開啟**校園管理**解決方案。
    
2.  建立新的畫布應用程式

    -   按一下 **[新增項目]** 並選取 **[應用程式\| 畫布應用程式]**。

    -   在畫布應用程式的空白視窗中，在 [應用程式名稱] 欄位中輸入 **[您的姓氏] 校園安全性**。

    -   在 [格式] 欄位中選取 **[電話]**。

    -   按一下 **[建立]**。
        如此會在新視窗中開啟 [應用程式編輯器]。如果出現 [歡迎使用 Power Apps Studio] 對話視窗，請按一下 **[略過]**。
    
3.  儲存畫布應用程式

    -   按一下 **[檔案]**，然後選取 **[另存新檔]**。
    
    -   檢查是否已選取 **[雲端]**，然後按一下 **[儲存]**。

    -   驗證 **[您的姓氏] 校園安全性**做為名稱，然後按一下 **[儲存]**。
        
    -   按一下左上方的 **[上一步]** 箭頭 (Power Apps 下方) 以返回應用程式。

3.  連接至資料來源 (造訪情形)

    -   按一下 **[檢視] \| [資料來源]**
    
    -   按一下 **[+ 新增資料]**

    -   按一下 **[檢視所有資料表]**
    
    -   選取 **[造訪情形]**，然後等待 [造訪情形] 資料表顯示在 [資料] 索引標籤上。
    
4.  若要保留進行中的工作，請按一下 **[檔案]**，然後按一下 **[儲存]**。使用上一步箭頭返回應用程式。

## 工作 2：顯示訪客資訊

1.  新增搜尋方塊

    -   選取左側導覽列上的 **[樹狀檢視]** 索引標籤。
    
    -   選取 **[Screen1]**。
    
    -   前往 **[插入]** 索引標籤。
    
    -   按一下 **[文字]**，然後選取 **[文字輸入]**。
    
2.  編輯文字輸入物件

    -   在仍選取文字輸入物件時，選取 **Default** 屬性中的文字並清除值。
    
    -   選取 **Hint Text** 屬性，然後輸入 `"Enter visitor code"` 做為值 (包含雙引號)
    
    -   在樹狀檢視中，按一下控制項名稱 (TextInput1) 旁邊的 **[...]**，選取 **[重新命名]**，然後將名稱變更為 `textCode`
    
3.  新增表單檢視

    -   在 **[插入]** 索引標籤上按一下 **[表單]**，然後選取 **[顯示]** (您可能需要按一下功能區右側的向下箭頭才能看到 [表單])
   
    -   拖曳表單以調整位置並對齊畫面底部
   
    -   仍在選取新表單時，先選取 **DataSource** 屬性，然後選取 **[造訪情形]**
   
    -   在 [屬性] 窗格中，將 **[版面配置]** 選取為 **[水平]**

4.  編輯表單檢視

    -   仍在選取新表單時，按一下 **[編輯欄位]**

    -   移除 **[名稱]** 和 **[建立時間]** 欄位

    -   按一下 **[新增欄位]**，然後選取下列欄位：**[實際結束時間]**、**[實際開始時間]**、**[大樓]**、**[預定結束時間]**、**[預定開始時間]**、**[訪客]**
   
    -   按下 **[新增]**
   
    -   拖曳清單中的欄位卡，即可變更選定欄位的順序。建議順序如下：[訪客]、[大樓]、[預定開始時間]、[預定結束時間]、[實際開始時間]、[實際結束時間] (您可以摺疊欄位，以便進行拖曳)
   
    -   按一下 **[X]** 以關閉 [欄位] 窗格
   
5.  仍在選取表單檢視時，選取 [屬性] 窗格上的 [進階] 索引標籤。選取 **[Item]** 屬性，然後輸入 `LookUp(Visits, Code = textCode.Text)` 

6.  若要保留進行中的工作，請按一下 **[檔案]**，然後按一下 **[儲存]**。使用上一步箭頭返回應用程式。

7.  準備測試應用程式

    -   切換至包含解決方案的瀏覽器索引標籤

    -   在快顯視窗中按一下 **[完成]**
   
    -   選取 **[造訪情形]** 資料表
   
    -   選取 **[資料]** 索引標籤
   
    -   按一下目前的檢視名稱 **[現行造訪情形]**，開啟右上方的檢視選取器
   
    -   將檢視變更為 **[所有資料行]**
   
    -   找到不具 [實際開始時間] 或 [實際結束時間] 值的 [造訪情形] 資料列 (即兩個資料列均為空白)。選取並複製此 [造訪情形] 的**代碼**。

8.  測試應用程式

    -   切換至應用程式的瀏覽器索引標籤，然後按下 **F5** 或按一下右上角的 **[播放]** 圖示，預覽應用程式。
   
    -   將複製的值貼至搜尋文字方塊，並確認記錄是否顯示在表單中
   
9.  清除搜尋文字方塊內容
   
10.  按下 **ESC** 以結束執行中的應用程式。

## 工作 3：新增「簽入」和「簽出」按鈕

在此工作中，我們將為使用者建立按鈕以簽入和簽出他們的造訪。 

1. 將搜尋結果儲存在變數中，以便在控制項中重複使用

    * 選取 **[textCode]** 控制項
   
    * 在屬性窗格中，選取 **[進階]** 索引標籤，然後選取 **[OnChange]** 屬性
   
    * 輸入下列運算式：`Set(Visit, LookUp(Visits, Code = textCode.Text))`
    
    > 當使用者在 [textCode] 搜尋方塊中搜尋時，此運算式可將造訪情形儲存在全域變數中。這可讓我們在整個應用程式中使用變數 *Visit*，而不必重新輸入整個查詢運算式。

2. 新增 [簽入] 按鈕

   * 選取 **[插入]** 索引標籤
   
   * 按一下 **[按鈕]**
   
   * 在屬性窗格中，將按鈕 **Text** 屬性變更為「`Check In`」(您可以在現有引號中輸入)
   
   * 在樹狀檢視中按一下按鈕名稱 (Button1) 旁邊的 **[...]**，選取 **[重新命名]**，然後將名稱變更為 `CheckInButton`

3. 新增 [簽出] 按鈕   

   * 按一下 [插入] 索引標籤上的 **[按鈕]** 以插入其他按鈕
   
   * 在屬性窗格中，將按鈕 **Text** 屬性變更為「`Check Out`」(您可以在現有引號中輸入)
   
   * 將按鈕名稱重新命名為 `CheckOutButton`
   
   * 將按鈕置於搜尋方塊下方，然後 **[簽入]** 位於 **[簽出]** 上方 
   
## 工作 4：根據造訪情形資料啟用和停用按鈕

使用者查詢造訪情形後，我們希望其使用 [簽入] 按鈕來簽入該次造訪。若是找到造訪情形的記錄 (非空白)、記錄狀態為現行，且造訪尚未開始 (即實際開始時間值為空白) 時，我們希望啟用 **[簽入]** 按鈕。

1. 選取 **[簽入]** 按鈕，然後在 [屬性] 索引標籤中按一下按鈕的 **Display Mode** 屬性

2. 在函數列中輸入以下運算式：

      ```
      If(!IsBlank(Visit) 
      && Visit.Status = 'Status (Visits)'.Active
      && IsBlank(Visit.'Actual Start'),
          DisplayMode.Edit,
          DisplayMode.Disabled
      )
      ```

   運算式可拆解成下列內容：

   * **!IsBlank(Visit)** - 找到造訪情形的記錄
   * **&&** - 邏輯 AND 運算子
   * **Visit.Status = 'Status (Visits)'.Active** 記錄狀態為*現行*
   * **IsBlank(Visit.'Actual Start')** - [現行開始時間] 欄位中沒有任何資料
   * **DisplayMode.Edit, DisplayMode.Disabled** - 如果符合上述條件，則按鈕將呈現可編輯狀態。如果不符合，則按鈕將維持停用狀態。

當找到造訪情形的記錄 (非空白)、記錄狀態為現行，且造訪情形已開始 (即實際開始時間值非空白) 時，我們希望啟用 **[簽出]** 按鈕。

3. 選取 [簽出] 按鈕，然後在 [屬性] 索引標籤中按一下按鈕的 **Display Mode** 屬性

4. 在函數列中輸入以下運算式：

     ```
     If(!IsBlank(Visit) 
     && Visit.Status = 'Status (Visits)'.Active
     && !IsBlank(Visit.'Actual Start'),
         DisplayMode.Edit,
         DisplayMode.Disabled
     )
     ```

5. 若要保留進行中的工作，請按一下 **[檔案]**，然後按一下 **[儲存]**。使用上一步箭頭返回應用程式。

6. 按下 **F5** 以執行應用程式。 

7. 兩個按鈕應均會停用。輸入您先前複製的代碼值，然後按下 **Tab** 以將焦點從文字方塊移開 (或按一下文字方塊外部)。**[簽入]** 按鈕應呈現啟用狀態。 

8. 清除搜尋方塊內容。

9. 按下 **ESC** 以結束執行中的應用程式。

## 工作 5：完成「簽入」和「簽出」程序

為執行簽入和簽出程序，我們需要按照下列方式更新 Dataverse 造訪情形的資料：

* 當訪客簽入時，請將 *[實際開始時間]* 欄位設為目前的日期和時間
* 當訪客簽出時，請將 *[實際結束時間]* 欄位設為目前的日期和時間 
* 簽出完成後，請將記錄狀態設為非現行，表示該造訪情形已完成

1. 選取 **[簽入]** 按鈕。

2. 將 [進階] 索引標籤上的 **OnSelect** 屬性設為下列運算式。

   ```
   Patch(
       Visits,
       Visit,
       {'Actual Start': Now()}
   );
   Refresh([@Visits]);
   Set(Visit, LookUp(Visits, Code = textCode.Text));
   ```

   此運算式包含下列部分：

   * **Patch(Visits, Visit, {'Actual Start': Now()});**。*Patch* 方法會更新 **[造訪情形]** 資料表，也就是由 **Visit** 變數識別的資料列 (即目前的造訪情形)。運算式會將 *[實際開始時間]* 資料行設為目前的日期和時間 (*Now()* 方法)。
   * **Refresh([@Visits]);**。當基礎值變更時，此運算式會重新整理造訪情形資料列
   * **Set(Visit, LookUp(Visits, Code = textCode.Text));** 此運算式會使用 Dataverse 中的更新資料來更新 *Visit* 變數。
   
   > 當使用者按一下此按鈕時，[造訪情形] 的 [實際開始時間] 將設為目前的日期和時間，而且資料也將重新整理。

3. 選取 **[簽出]** 按鈕。

4. 將 [進階] 索引標籤上的 **OnSelect** 屬性設為下列運算式：

   ```
   Patch(
       [@Visits],
       Visit,
       {
           'Actual End': Now(),
           Status: 'Status (Visits)'.Inactive
       }
   );
   Refresh([@Visits]);
   Set(Visit, LookUp(Visits, Code = textCode.Text));
   ```

   當使用者按一下此按鈕時，[實際結束時間] 將設為目前的日期和時間，[造訪情形] 的 [狀態] 將設為 [非使用中]，而且資料也將重新整理。

5. 若要保留進行中的工作，請按一下 **[檔案]**，然後按一下 **[儲存]**。使用 **[上一步]** 箭頭返回應用程式。

6. 按下 **F5** 或按一下 [播放] 按鈕以執行應用程式。輸入您先前複製的代碼值，然後按下 **Tab** 以將焦點從文字方塊移開。**[簽入]** 按鈕應呈現啟用狀態。

7. 按下 **[簽入]** 按鈕。應該會發生下列情況：

   * **[實際開始時間]** 已設定為目前的日期和時間
   
   * **[簽入]** 按鈕已停用
   
   * **[簽出]** 按鈕已啟用

8. 按下 **[簽出]** 按鈕。

   * **[實際結束時間]** 已設定為目前的日期和時間
   
   * 兩個按鈕均已停用

9. 清除搜尋方塊內容。

10. 按下 **ESC** 以結束執行中的應用程式。

## 工作 6：新增視覺效果指標

提供視覺效果指標時，行動裝置應用程式的實用性會大幅提升。在此工作中，我們將新增可指出訪客是否可以簽入或簽出的圖示。

1. 選取 **[插入]** 索引標籤

2. 選取 **[圖示] \| [新增]**。選取圖示。此時選取哪個圖示都沒關係，因為我們希望這個值為動態值。

3. 調整圖示大小並將其置於按鈕的左側

4. 在圖示的 [進階] 索引標籤中，選取 **[Icon]** 屬性 (在 [設計] 區段中)，然後輸入下列運算式

   ```
   If(
      CheckInButton.DisplayMode = DisplayMode.Disabled 
   && CheckOutButton.DisplayMode = DisplayMode.Disabled,
       Icon.EmojiFrown,
       Icon.EmojiSmile
   )
   ```

5. 若要保留進行中的工作，請按一下 **[檔案]**，然後按一下 **[儲存]**。使用 **[上一步]** 箭頭返回應用程式。

6. 按下 **F5** 以執行應用程式。輸入您先前複製的代碼值，然後按下 **Tab** 以將焦點從文字方塊移開。確認圖示是否顯示苦臉表情符號。

7. 尋找之前尚未使用過的其他代碼值 (其不得包含 [實際開始時間] 或 [實際結束時間] 值)。 

    > 您可以導覽至先前的索引標籤，從已經建立的其中一個 [造訪情形] 中複製其他代碼。也可以選擇執行先前建立的 **[校園教職員]** 應用程式來建立新的造訪情形記錄。確認圖示是否顯示此代碼的笑臉表情符號。

您正在執行的應用程式看起來應近似於下圖：

![畫布執行安全性應用程式](media/3-canvas-app-running.png)

8. 按下 **ESC** 以結束執行中的應用程式。

## 工作 7：發佈應用程式

1. 您仍應在瀏覽器中開啟 [校園安全性] 應用程式。如果尚未開啟，請選取 **[校園安全性]** 應用程式，然後按一下 **[編輯]**。

2. 選取 **[檔案] \| [發佈]** 

3. 選取 **[發佈此版本]**

# 挑戰

* 避免手動輸入造訪情形代碼
* 新增造訪情形的建立驗證
* 新增造訪情形之實際時間和預定時間的驗證 (太早、太晚等)
* 新增造訪情形的詳細狀態，例如訪客的電子郵件顯示和驗證、拒絕出入大樓的原因等
* 單次校園造訪期間的多棟大樓/多次會面/多項檢查。例如，有人可能會在某天造訪校園，而且會在當天於不同時間與多棟大樓中的教職員成員會面。您是否會考慮將*預約*實體帶入解決方案中？
