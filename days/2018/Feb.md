Feb. 2018
===

## 02/01, Thu.

### 技術

* [I get paid for code that works, not for tests.](https://stackoverflow.com/questions/153234/how-deep-are-your-unit-tests/153565#153565)：Kent Beck在SO的一則回覆：在對程式碼有足夠信心的狀況下，盡可能減少測試。如果覺得會有錯，就寫測試；但如果很有信心，或者認為不會在這麼簡單的地方犯錯，就不一定要寫測試。當然從另一個角度來思考，寫測試並不只是確保不會犯錯，同時也是減少修改程式碼的不確定性，所以這個說法不一定完全有道理...

## 02/02, Fri.

### 技術

* *單元測試的藝術*：編寫可讀的測試
    * 命名，至少要包含：
        * 被測試的單元/方法名稱
        * 測試的場景/條件
        * 期待的結果
    * 將斷言和操作分開，不要放在同一行。
    * 其實就跟平常寫程式碼一樣啦，魔術數字、減少不必要的重複等等原則仍然適用。

## 02/03, Sat.

### 技術

* [Best Practices for Modals / Overlays / Dialog Windows](https://heydesigner.com/blog/best-practices-modals-overlays-dialog-windows/) 講到modal的幾個設計的點：
    * 請把它放在畫面的上方––放太下面的話(正中間)有可能會因為device的高度不足而擋住內容。尺寸請維持在螢幕的50%以下，否則會讓用戶以為跳到新的頁面。
    * 允許用戶使用鍵盤操作，包括focus trap、esc key跳出等等。
    * 要有明顯的關閉按鈕，雖然設計者可能以為用戶會知道按modal外面就可以跳出去，但其實大家還是習慣有按鈕。
    * 允許用戶點按modal外面時可以跳出modal。
    * 標題、內容和按鈕要相符，讓用戶一眼看出來這個modal的用處。
    * 加上適當的backdrop，太暗的話用戶以為跳到別的頁面去了；太亮的話反而modal變的不明顯。
    * 行動裝置使用modal要小心，內容不可以多到超過畫面，操作時也避免讓用戶需要額外放大modal上的UI。
* 承上，[Overuse of Overlays](https://www.nngroup.com/articles/overuse-of-overlays/)則提到了什麼時候使用modal的時機和小問題：
    * 從動作來考慮，modal一般有三個用途：(1)看詳細內容(2)填表單(3)做決定
        * 詳細內容：如果它的內容足夠多以致於你需要加scroll bar，或許可以考慮做成另外一頁；或者，就算要用scroll bar，也要確保此時用戶不會誤觸原頁面的scroll bar，否則用戶可能為了滾動modal的scroll bar而不小心滾動了原頁面的內容。最後，還要考慮如何分享/收藏modal的內容，考慮modal該如何對應url。
        * 填表單：把取消鈕做的明顯一些(可以看裡面的反例)；另外，保留用戶的輸入，讓不小心跳出modal的用戶可以迅速恢復。
        * 做決定：類似於原生的`confirm`對話框。因為用戶通常被大量不重要又煩人的confirm對話框轟炸過，他們常常會連上面的文字都不仔細看就按確認，所以，請把確認鈕做得獨特一點，並且包含對將要發生的事情的敘述(刪除、變更、取消...)。
    * 什麼時間應該出現modal？請盡可能在用戶作了某些操作的狀況下才出現modal，非必要不要自動彈modal(對我就是在說你全版廣告)。裡面提了一個例子是網站在用戶要移動到其它網站時，主動跳modal做銷售，但我還是覺得這很惱人啊。
    * 為什麼這個內容應該放modal而不是獨立的頁面？有三個原因：(1)用戶的操作會導致嚴重而不可恢復的後果(刪東西、改變密碼)(2)網站需要必要的資訊下一步(3)內容很緊急又重要
        * 嚴重後果：請確認真的是很嚴重的後果。並且，針對重複性的作業，應該提供一個 Don't ask me again的checkbox。
        * 收集資訊：也就是上述的填寫表單，同樣，請確認是否真的需要收集這些資訊。
        * 緊急內容：這個緊急對誰而言緊急(用戶/網站/行銷)？什麼時候？一般而言，當網站和用戶站在同一個立場上時，比較可以出於緊急的理由使用modal(例如環境保護的募款、限時的倡議活動...)。
        * 那個，「我們用modal的話可以少設計一個頁面」之類的理由就算了吧。