Mar. 2018
===

## 03/01, Thu.

### 技術

* *Working Effectively With Legacy Code* 第十二章： *I need to   make many changes in one area. Do I have to break dependencies for all classes involved?*。
    * 這一章其實是接著上一章的effect sketch往下講。談到interception point和pinch point的概念。
    * *interception point*：指針對某個變化，程式碼中任何可以測試該變化的地方。 
    * *pinch point*：指effect sketch中路徑集中起來的點。代表你可以透過測試它來知道很多方法造成的effect。
    * 一般而言，我們會選擇離修改的方法最接近的interception point寫測試，但有的時候最近的interception point可能有很多依賴而不好寫測試；又或者，你想要同時在相關連的地方做很多修改，你想要寫一組測試就可以知道有沒有破壞行為。此時選擇在pinch point(通常也是高階一點的抽象)上做測試，可能會是比較好的選擇。
    * pinch point除了可以幫助我們寫測試，它還可以幫助我們釐清類別的職責。當我們在一個類別的effect sketch中找到pinch point，通常代表我們可以把與之相關的方法和變數抽出來作為類別，得到更好的抽象和封裝。

## 03/02, Fri.

### 技術

* *Working Effectively With Legacy Code* 第十三章： *I need to   make a change, but I don't know what tests to write.*。
    * 嗯好，所以要測什麼？
    * 一般而言我們想到測試的用途會想到**找出bug**，但作者認為測試更重要的用途是**保留行為**。
    * 一旦有了一組保留系統行為的測試，將來它就可以幫你偵測對程式碼的改變是不是有錯誤，這可以省下很多時間和錯誤。
    * 但怎麼知道現在的系統有什麼樣的行為呢？
    * *Characterization Test*：

        1. 寫一個測試，或者既有的測試。
        2. 寫下一個斷言讓測試失敗。
        3. 運行測試，讓它出錯
        4. 根據出錯的訊息修改你的測試，直到斷言描述了系統現在的行為讓測試通過。
        5. 回到第一步寫下一個測試。

        如此你就可以得到一組測試，描述系統現在的行為。如果在中間的過程發現bug也沒關係，先把行為保留下來，因為可能有其它人依賴bug的行為。
    * 有了characterization test之後，便可以開始做你想做的修改，此時可以一邊確保是否所有的conversion(if/else)都被這組測試測到。一組好的characterization test應該會包含同一條程式路徑的不同分支。
 
## 03/03, Sat.
 
### 技術

* PWA
    * 就是希望網站用起來像原生App一樣，包含一些特性：
        * 可離線使用
        * 背景同步，在離線時送出的資料可於連線恢復後自動送出
        * 全螢幕使用，splash screen，沒有url bar
        * 可推送通知
    * 之所以能做到PWA，要仰賴service worker api。service worker是一個在背景下運行的javascript線程，它在網頁被載入時被安裝，其後在每次進入該url時都會啟動，可以做的事情包括：
        * 控制cache和request。在每次頁面要丟出新的請求時，都可以決定要不要用cache代替。因此可以做到離線使用。
        * 推送通知
        * 背景同步
* *Working Effectively With Legacy Code* 第十四章：*Dependencies on libraries are killing me.*
* *Working Effectively With Legacy Code* 第十五章：*My application is all API calls.*
    * 這兩章或許該合在一起看？總之，API或library都是我們改不了的東西，作者提到兩個對使用API的程式碼寫測試的策略：

        1. Skin and Wrap the API：指在API外面增加一層wrapper，wrapper，這層wrapper可以在生產環境呼叫API，在測試環境呼叫fake object。通常在API較簡單而且可以輕易製造API的fake object的場景使用。
        2. Responsibility-Based Extraction：指針對使用API的程式碼，切出職責並抽出類別。通常在API較複雜而且不易製作fake object時使用。
* *Working Effectively With Legacy Code* 第十六章：*I don't understand the code enough to change it.*
    * 介紹了一些trace code的方法。但其實也就是：
        * 畫圖，不一定要是UML，但它可以幫助你觀察和溝通。
        * 把程式列印出來(列印!)，在上面做標示，例如當你想切類別的職責時，就可以用奇異筆把屬於某一個職責的方法標出來；或者，函式很長的時候，可以把函式的每個片段標示出來，有助理解。
        * Scratch Refactoring，反正有git，你可以試著不管測試先重構看看，重構的過程可以增加理解。
        * 去掉dead code，減少理解的阻力。反正有git。

## 03/04, Sun.

### 技術

* *Working Effectively With Legacy Code* 第十七章：*My application has no structure.*
    * 這章談到一些搞清楚系統架構的方法。關於這個主題，作者推薦[Object-Oriented Reengineering Patterns](https://www.amazon.com/Object-Oriented-Reengineering-Patterns-Engineering-Programming/dp/1558606394)這本書，網路上可以直接找到它的[pdf](http://scg.unibe.ch/download/oorp/OORP.pdf)。
    * *Telling the Story of the System*：由兩個人進行，A從「這個系統的架構是什麼」開始問起，另一個人B給一段系統架構的簡短描述，而A再從B的描述中挑出最重要的部分詢問，直到講完了整個系統的核心架構。
    * 為了讓描述簡短，描述者必須簡化事實，而這會導致描述看起來像在說謊，顧是可以思考：
        * 有沒有可能再修改架構，以至於簡化的版本比較不會像說謊？
        * 如果今天要加入一個新特性，要加在哪裡，才可以保持原本這段敘述的正確性？
        * 哪些部分才是系統的重點？如果換個方式說，會不會更完整的表達這個系統？
    * [*Naked CRC* ](https://software.professionals.wiki/learn-do-grow:naked-crc)
    * *Conversation Scrutiny*：當團隊中談及系統架構的時候，應該去注意對話和實際程式碼的落差，兩者出入很大的時候，問清楚為什麼。可能是程式碼不符合設計，或者團隊不夠了解程式碼。

* *Working Effectively With Legacy Code* 第十八章：*My test code is in the way.*
    * 這章則談到測試程式碼的一些convention，避免干擾到production code。
    * 類別命名：
        * 測試類別：`Test` suffix。 ex. `CheckingAccount` => `CheckingAccountTest`。這樣在編輯器裡頭測試程式碼就會在原類別的檔案的隔壁。
        * Fake：`Fake` prefix。 ex. `CheckingAccount` => `FakeCheckingAccount`。這樣可以避免和原類別混淆。
        * Testing Subclass：`Testing` prefix。ex. `CheckingAccount` => `TestingCheckingAccount`，原因類似於`Fake`的prefix。
        * 不過我想就是兩點：(1)不要和原本要測的類別混淆(2)好找
    * 放在哪裡？
        * 作者的建議是放在和production code同一個資料夾，省去在資料夾中翻來找去的麻煩。如果在生產環境下需要去除測試程式碼，透過好的命名規範可以直接寫腳本在建置時去掉。

## 03/05, Mon.

### 技術

* *Working Effectively With Legacy Code* 第十九章：*My project is not object oriented. How do I make safe changes?*
    * 這章介紹了一些沒有Object seam下可以用的hack。包含macro、function pointer等等。
    * 比較有趣的是最後作者提到，整個procedural program其實就是一個大object包含著很多個public method，再加上一個main function開頭：

    ```c++
    class program
    {
        public:
        /*
            any function used in procedural program
        */
    }
    int main(int ac, char **av) {
    program the_program
    return the_program.main()
    }
    ```
    
## 03/06, Tue.

### 技術

* *Working Effectively With Legacy Code* 第二十章：*This class is too big and I don't want it to get any bigger.*
    * 這一章談怎麼把巨大的類別切細。
    * 但首先，為什麼要這麼做呢？
        * 難讀。難以判斷effect。
        * 不易同時工作。
        * 封裝了太多東西，以致於被包起來的私有方法難以測試。
    * 如果我現在沒有時間...
        * Sprout Class/Method
    * 好吧，我有時間了，可是，要切到多細呢？
        * Single Responsibility Principle 
    * 有道理，可是職責是很模糊的東西，我要怎麼知道這個類別有哪些職責？
        1. Method Grouping: 把類別的所有方法攤開來，寫下它們的名字和類型(public/private/protected)，試著從方法名找出看起來較有關聯的方法。
        2. Looking for Hidden Methods: 觀察private/protected methods；如果一個類別有很多私有方法，通常它們可以被抽取成新的類別。
        3. Looking for Decisions that can change: 有時候單靠方法名不易判斷職責，方法可能太長，包含了數個不同的操作(decisions)。把它們分別抽取成新的方法，為它們命名，回頭來看通常可以得到不同的觀點。
        4. Looking for Internal Relationships: 從成員變數的角度出發，觀察每一個成員變數在哪些方法中被用到。可以為它們畫圖––為每一個成員變數和方法畫一個圓，畫箭頭讓成員變數指向它們被使用的方法，從這樣的圖可以看出成員變數和方法的關聯，通常聚在一起的變數和方法就可能是潛在的新類別。
        5. Looking for Primary Responsibility：試著用一句話描述類別的職責。這可以幫助你決定最重要的職責，找出其它可以抽取出來的職責。
        6. 如果上述的每一招都不行，試著做Scratch Refactoring。
        7. 回頭想想現在要做的修改是什麼；而它和職責有什麼關係？
        8. 回家念書、讀其它人的程式碼，看過愈多好的設計就愈知道可以怎麼做會比較好。
    * 好像很多招，可是實際上這樣的重構應該很危險吧？
        * 不一定要把所有的職責都切出來；只取需要的部分便可。
        * 萬一缺少測試，作者另外在書中也介紹了把方法和變數移到新類別的步驟。

## 03/07, Wed.

### 技術

* *Working Effectively With Legacy Code* 第二十一章：*I'm changing the same code all over the place.*
    * 整章談到了去除duplication code的一個例子，一些心得：
        * 如果不知道從哪裡下手，先從看起來較小的、簡單的部分開始。其餘的頭緒會自然出現。
        * 如果兩個方法看起來大致是相同的，把不一樣的部分分別抽取出來，往往可以把兩個方法合而為一。
        * 當我們去除了重複程式碼之後，往往可以得到一群小而專注在一件事上的方法/類別，每一個所做的事情都不是其它方法做的，需要修改行為時，往往只有一個地方需要修改：這就是程式中的正交性(orthogonality). 
* [第三方CSS也很危險啦](https://jakearchibald.com/2018/third-party-css-is-not-safe/)： 可以偷密碼、追蹤瀏覽路徑、改畫面、讀網頁內容(透過`@font-face`)...真的還是自己來啊。
* [一些css的雜技](https://medium.com/@peedutuisk/lesser-known-css-quirks-oddities-and-advanced-tips-css-is-awesome-8ee3d16295bb)：其實很多都有看過啦。列舉幾個比較神祕/沒看過的：
    * margin不是什麼時候都會collapse。
    * `:target`可以選擇經由hash被導航到的元素
    * `content`除了文字還可以塞圖(`url`)、quote、counter
    * *lobotomized owl*：

    ```css
    // before

    li {
        margin-bottom: 10px;
    }

    li:last-child {
        margin-bottom: 0;
    }

    // after

    li + li {
        margin-bottom: 10px;
    }
    ```
    可愛又強大(欸)
* [7 Practical Tips for Cheating at Design](https://medium.com/refactoring-ui/7-practical-tips-for-cheating-at-design-40c736799886)：覺得這篇對設計不太行的前端如我簡直是福音啊QAQQ介紹了很多有用的懶人設計小知識(?)
    * 製造階層除了字的大小，還可以使用字重和深淺。字重盡可能不要低於400，太輕的字在小size的狀況下看不清楚。
    * 如果背景有顏色，不要用灰色的字。如果背景是白色的，用灰的字色可以有效的減少對比；非白色的背景則有兩招：
        1. 使用透明度較高(opacity稍低)的白色字
        2. 使用和背景色相近的字色
    * 如果有用到陰影，記得加入垂直的offset讓它看起來符合自然的光影(從上到下)
    * 如果想製造區塊的間隔，不要全部都用border，還可以用：
        * box-shadow
        * 不同的背景色
        * 增加區塊間的間距
    * 如果你需要使用放大的icon，不要直接把font-awesome的icon拿來放大，因為它們通常是在16~24px的尺寸下繪製的，若用在3x以上的大小，就會顯得細節不足、空空的。如果需要大的icon，建議可以用個形狀把小icon包起來，或者有錢的話直接使用[Heroicons](http://www.heroicons.com/)或[iconic](https://useiconic.com/)這一類可以在較大尺寸下使用的icon package。
    * 如果區塊的設計有點平淡，可以加上一段顏色相近的單邊border，看起來會比較有設計感。
    * 不是所有的按鈕都要用背景色(刪除就用大紅背景白字按鈕、新增就用大綠背景白字按鈕、bootstrap萬歲！(被打))。依照使用介面中動作的階層，可以把按鈕分成三級：
        * 最重要的動作對應的按鈕應該最明顯，實心、高對比。
        * 次重要的動作對應的按鈕仍應該清楚但不需要特別強調，稍低一點的對比、白底有色邊框都是好選擇。
        * 最後較不重要的動作則應該可以被發現到，但不應吸引注意，一般的連結樣式通常足矣。