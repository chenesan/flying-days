Jan. 2018
===

## 01/03, Wed.

### 技術

* 判斷兩個DOM節點在DOM tree上的先後順序，可以使用`Node.compareDocumentPosition`，不需要大費周章traverse tree啦。
* *Rule of Three*: 如果一段code重複了三次，就代表應該把共用的邏輯抽出來了。因為如果這段邏輯有錯，而又到處都是重複的code，就要改很多地方，改很多地方就很容易出錯。但是抽出共用邏輯需要思考，也有時間的成本，因此適度即可(因此不是Rule of Two的緣故)[出處](https://en.wikipedia.org/wiki/Rule_of_three_(computer_programming))

### 趣聞
* **總匯三明治**原來只有臺灣才有!!它的前身是*Club Sandwich*，是十九世紀club的一道經典三明治，裡面塞培根、萵苣、蕃茄(對，就是最近麥當勞在賣的**BLT牛肉堡**)。club在以前被翻譯成**總會**，雖然說現在不常看到這個用語，但像**夜總會**就是個例子。

    不過，可能是當時的人看到**總會三明治**總會搞不懂它是什麼東西吧，慢慢的它的名字就變成了**總匯三明治**，可能是被名字影響了(總匯=好像什麼都有)，裡面塞的東西也就愈來愈豪華了。[出處](http://www.foodnext.net/science/scsource/paper/4975371433)

## 01/04, Thu.

### 技術

* [Five Tips for Working with Redux in Large Applications](https://techblog.appnexus.com/five-tips-for-working-with-redux-in-large-applications-89452af4fdcb)：今天讀pocket存了好久的這篇文章，談一些用redux的小撇步，包含：
    * 用一組索引的陣列和一個key => data的map來儲存資料
    * 用selector取資料
    * 將原本的data物件、編輯中的data物件以及其它的UI state分開
    * 在不同的頁面中適當的共用(以及不共用)資料
    * 相同的reducer和action邏輯(例如分頁、行為相似的api呼叫)可以用一組reducer/action creator factory包起來避免重複
    * 在redux和view之間建立一層中間層，讓state和view可以解耦

    這些點之前就讀過一兩次，而這篇算是和工作經驗做個印證吧。我自己實作的感覺是：

    * reducer/action creators/redux sagas factory可以節省非常多的code，但是如果寫的太死，或者api有微妙的差異，就會顯得難以修改。適度的保留函數的彈性、甚至先讓重複的程式碼重複，避免過早優化，都是要注意的事。
    * 在不同的頁面上共用資料的寫法，最近才在專案中用到。像是分類等一段時間都不會變動而又常常在不同地方用到的資料，就很適合額外拉出來，可以節省邏輯的程式碼以及request。
    * 保留編輯狀態的寫法目前還沒有用在專案裡面過，但應該對管理後台類型的網站很有用。
    * 公司之前的專案都是依api來切reducer，一開始進去的時候也沒有特別想過，寫起來就綁手綁腳的(例如同時有不同的地方要叫同一個api)。還是依照頁面來切reducer才是正解啊。