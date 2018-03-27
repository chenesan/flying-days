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

## 03/08, Thu.

### 技術

* 嘗試找找看javascript的自動重構工具，卻好像找不太到。open source中最接近的應該是[這個](https://github.com/cmstead/js-refactor)，不過是在VSCode上的插件，atom上雖然有同一個作者做的插件，但是用上去常常跑出錯誤...倒是看到WebStorm有[支援](https://www.jetbrains.com/help/webstorm/refactoring-javascript.html)，有點想玩玩看啊啊。

## 03/09, Fri.

### 技術

* 終於把*Working Effectively With Legacy Code*的前兩個部分看完了，可是今天好累所以筆記和心得什麼的就交給明天了(欸)。

## 03/10, Sat.

### 技術

* *Working Effectively With Legacy Code* 第二十二章：*I need to change a monster method and I can't write tests for it.*
    * 因為為大型函式寫測試很困難，因此這章介紹了清理大型函式的一些方法。
    * 作者將大型函式分為兩種類型：
        * Bulleted Method: 指沒有太深的語句嵌套和縮進，程式碼看起來像一段一段的列表，每一段做的事情可能都不一樣。
        * Snarled Mehtod: 指只有單一個很深的嵌套、複雜的縮進。
        * 實際上的大型函式總是在這兩者之間。就是往直的長或往橫的長呢。
    * 作者建議在重構大型函式的時候使用自動化的重構工具來幫助抽取函式。手動容易犯錯，諸如忘記把變數丟進被抽取的方法、不小心override原本有的方法、搞錯signature等等。(但是如前天搜尋的結論，實在找不到javascript的呢...)
    * 真的不得不手動的話，作者還是介紹了一些技巧：
        * Introduce Sensing Variable: 在要編輯的方法中，加入一個變數來偵測方法是不是正確的行為，並且把這個變數設為類別的公有成員。這樣我們就可以在測試中用它來判斷行為是不是被保留，於是可以安心的搬移邏輯。
        * Extract what you know: 從簡單的、小的地方開始，作者引入了coupling count的概念，coupling count是指被抽取的方法中，輸入和輸出的數量總和。例如：
        
            ```javascript
        function max(a, b) {
            return (a > b) ? a : b
        }
            ```

            這個方法的coupling count就是3(兩個參數 + 一個回傳值)。作者建議從coupling count很小的地方開始，特別是那些coupling count = 0的部分。通常這些地方都是一些command，我們可以安心地搬移邏輯而不用擔心值的傳遞。
        * Gleaning Dependencies: 即使有時要抽取的邏輯都纏在一起，太過龐大，無法完全測試，但你仍然可以測試其中一小部分可以測試的邏輯，至少可以確保在抽取之後，行為沒有變化。
        * Break out a method object: 把方法包在一個新的類別裡面，邏輯抽取到唯一的`run`方法中，原本方法的參數變為建構子的參數，中間變數則作為成員變數，舊的類別在方法中就只負責建構這個新類別並執行`run`。這樣的好處是可以直接針對新類別作測試和重構。
    * 最後作者提到了一些建議
        * Skeletonizing vs Finding Sequence：假設有這麼一段邏輯：

            ```javascript
            if (year < 6 || year > 65) {
                var ticket = new discountTicket(mileage)
                bank.sendTicket()
            }
            ```
            Skeletonizing指的就是分別抽取條件句和內容的程式碼，讓它變成：
            
            ```javascript
            if (isDiscountTicket(year)) {
                sendDiscountTicket(bank, mileage)
            }
            ```
            而Finding Sequence則是直接把整個if語句抽取成一個方法：
            
            ```javascript
            sendDiscountTicket(bank, year, mileage)
            function sendDscountTicket(bank, year, mileage) {
                if (year < 6 || year > 65) {
                    var ticket = new discountTicket(mileage)
                    bank.sendTicket()
                }
            }
            ```

            我們在重構時往往會在這兩種結構間取捨。
        * 抽取出來的方法總是可以在之後放到新的類別裡，因此在完全重構完之前，不妨先把它留在原本的類別裡。
        * 從小的地方開始(跳針)
        * 做好可能會重新重構的心理準備。這不代表一開始的重構是無用功；它們引導你看出更好的架構。
* *Working Effectively with Legacy Code* 第二十三章：*How do I know that I'm not breaking anything?*
    * 這章介紹了一些在寫程式時減少犯錯的方法。
    * Hyperware Editing: 盡量在能夠得到反饋的狀況下寫程式，例如存檔後自動化測試，盡可能清楚知道此刻做的改動會影響的所有事情。作者甚至提倡在每一次按下按鍵時就執行測試。
    * Single-Goal Editing: 指修改程式碼時一次只做一件事。不因為做了某件事的中途發現有其它事要做就跳去做別的。
    * Preserve Signature: 在搬移程式碼邏輯的時候，保留函式的變數聲明，如此可以確保搬過去的程式碼不會漏掉原本的東西。
    * Lean on the Compiler: 在做修改的時候，有時我們不確定這個修改會影響多少地方要跟著變動。此時可以先直接修改，讓編譯器報錯，如此可以看到所有需要跟著做修改的地方。但要小心被繼承的override method雷到。
* *Working Effectively with Legacy Code* 第二十四章：*We feel overwhelmed. It isn't going to get any better.*
    * 雞湯文XD不過總之，和人的連結(無論是工作伙伴或是社群)是背後的動力呢。

## 03/11, Sun.

本日休刊。今天懶洋洋的不想做事(欸)

## 03/12, Mon.

### 技術

* *[黑客攻防技術寶典：瀏覽器實戰篇](http://www.books.com.tw/products/CN11386118) ([The Browser Hacker's Handbook](https://www.amazon.com/Browser-Hackers-Handbook-Wade-Alcorn/dp/1118662091))*：因為對前端的資安沒什麼概念，於是就開始啃這本啦。
    * 對瀏覽器的攻擊過程分成三個階段：初始化、持久化、攻擊。
        * 初始化指的是讓瀏覽器遇見並運行攻擊的程式碼。
        * 持久化指的是保持對瀏覽器的控制，並嘗試進行進一步的攻擊。
        * 攻擊則包含好幾種可能：
            * 繞過同源政策，這也是其它攻擊手段仰賴的一部分。
            * 攻擊網路(TCP層以下)
            * 攻擊插件(Adobe Reader、Flash、Java)
            * 攻擊擴充功能(extension)
            * 攻擊用戶
            * 攻擊Web應用
            * 攻擊瀏覽器

    * 一些廣為流傳的原則實際上是沒有用的：
        * 健壯性法則(伯斯塔爾法則(Postel's law))：發送時要保守、接收時要開放：但實際上接收時開放就是帶來更多風險。
        * 外圍安全防線謬論：假設攻擊者是由外而內攻破防線；實際上，瀏覽器提供了很多洞，不可能由外而內的防護。

    * 瀏覽器本身其實也有做一些防護措施：
        * HTTP header，例如CSP、secure cookie、HttpOnly cookie、nosniff、Strict-Transport-Security、X-Frame-Options
        * 反射型XSS過濾
        * Sandbox
        * 反釣魚網站(黑名單)
        * 擋mixed content(用HTTPS丟一開始的請求，卻用HTTP丟接續的請求)
    * 初始化最常見的手法就是XSS，包含幾種類型：
        * 反射型(reflected XSS)：在url中填入惡意程式碼，後端吐回一個帶有那一段惡意程式碼的回應，於是瀏覽器就會執行那一段程式碼。
        * 存儲型(stored XSS)：在url中填入惡意程式碼，瀏覽該url時，會將該段程式碼儲存在資料庫，使得網站其它地方跟著被植入惡意程式碼。
        * DOM XSS：類似反射型，只是它只利用client javascript做XSS。
        * 通用型XSS：指利用瀏覽器自身或者插件、擴充功能的缺陷進行XSS
        * XSS病毒：指能夠感染其它瀏覽器的XSS，例如歷史上第一個XSS病毒 [Samy](https://zh.wikipedia.org/wiki/%E8%90%A8%E7%B1%B3_(%E8%AE%A1%E7%AE%97%E6%9C%BA%E8%A0%95%E8%99%AB))。點擊被感染的用戶主頁會導致自己的用戶頁面也被埋入XSS。

## 03/13, Tue.

### 技術

* *The Browser Hacker's Handbook*：今天讀到XSS之外的初始化手法，包含：
    * 社交工程(釣魚網站)。現在已經有很多拷貝既有網站的工具，只要花點錢買domain和server，要假造一個看起來和原網站一樣的網站並不困難。
    * 中間人攻擊，通常是發生在應用層以下(無線網路、ARP(Address Resolution Protocol)下毒、DNS下毒)等等，但也可能在[瀏覽器](https://en.wikipedia.org/wiki/Man-in-the-browser)發生。
    * 利用網站本身的缺陷
    * 廣告網路
* [We Write CSS Like We Did in the 90s, and Yes, It’s Silly](https://alistapart.com/article/we-write-css-like-we-did-in-the-90s-and-yes-its-silly)：作者提到三件至今還是沒定論/不受重視的事：
    * Declaratoin Sorting
    * Selector Sorting
    * Declaration Repetition
    
    Declaration/Selector Sorting我覺得似乎有道理。但減少重複宣告這件事，我覺得就像下面的回應說的，以DRY為由去減少repetition，在CSS當中並沒有幫助理解。或許還是交給clean-css吧。
    
## 03/14, Wed.

### 技術

* *The Browser Hacker's Handbook*：今天讀到通信和持續攻擊的一些方式。
    * 除了XHR輪詢、webSocket等等，還可以通過DNS請求來隱敝地跟server通信。
    * 假iframe、解不完的confirm、底層popup、mitB劫持等等都是拖時間的好方法。

## 03/15, Thu.

本日休刊。

## 03/16, Fri.

### 技術

* *The Browser Hacker's Handbook*：今天讀到躲避惡意程式碼檢測的方式，主要可以分成兩種想法：
    * 對原始碼進行編碼
        * base64，例如`eval(atob("YWxlcnQoJ2hlbGxvIHdvcmxkJyk="))`。
            * 你說`eval`這麼evil的東西會被抓包？那            `[].constructor.consturctor(atob("YWxlcnQlcnQoJ2hlbGxvIHdvcmxkJyk="))`？
            * 或者`setTimeout("YWxlcnQlcnQoJ2hlbGxvIHdvcmxkJyk=")`？(setTimeout可以對字串做eval!)
        * [空白符編碼](https://www.defcon.org/images/defcon-16/dc16-presentations/defcon-16-kolisar.pdf)，tab是0，whitespace是1，把ASCII轉成這兩者的編碼。由於許多反模糊工具會忽略空白，這就有了可乘之機。
        * 沒有數字和字母也可以寫javascript!
            * `!""`是`true`，`![]`是`false`。
            * `{} + []`會得到`0`
            * `0 + true`會得到`1`
            * 任何變數加上空字串或空陣列會變成字串，例如`1+""`會變成`"1"`
            * 實際上已經有工具([JJencode](http://utf-8.jp/public/jjencode.html)、[AAencode](http://utf-8.jp/public/aaencode.html))可以用了。
    * 模糊原始碼
        * 隨機命名變數和方法。混合`.`和`[]`對object求值
        * 用`setTimeout`執行程式碼，由於檢測軟體常常會設下時限，超過時限就放棄檢測，所以可以嘗試繞過。
        * 使用不同的上下文作為資料來源
        * 用`callee`取得函數自身，由此可以把函數轉成字串，攻擊者可以自行檢查函數是否被檢測軟體動過手腳，倘若字串長度不同，則不執行惡意程式。
        * 利用js引擎自身的奇怪特性可以有針對瀏覽器的browser detection：例如`"\v"=="v"`只在IE有效。

## 03/17, Sat.

### 想法

* 如果不知道最新最好的做法會發生什麼事情？回到手邊的事情上，有些時候即使不知道或許也沒有關係。
* 如果看到別人開發出很厲害的東西，那並不代表做不出那些東西的自己不好，而只是代表自己和別人不一樣，無論是基因、環境、性格、擅長與不擅長的事。

    兔子沒辦法像烏龜一樣游泳；或許兔子真的也可以游泳，但即使不會，也沒有什麼好焦慮的，因為那就是兔子啊。
    
    兔子在故事裡總是因為貪睡而跑不贏烏龜，但那也沒什麼好焦慮的，因為那就是兔子啊。
    
    兔子不需要是烏龜。
    
    
## 03/18, Sun.

### 技術

* *The Browser Hacker's Handbook*：今天讀到繞過同源政策(SOP)的方式。
    * SOP把相同主機名、協議和port的頁面視為同一個來源，如果其中一個不一樣，就不是同源的資源，瀏覽器會擋住對非同源資源的取得。
    * 瀏覽器的不同部分會有各自對應的SOP，DOM對應的SOP和Java、Flash等plugin對應的SOP其實是不同的，行為也不一樣。
    * 繞過SOP最多的還是插件和瀏覽器自身的缺陷。另外有些網站把CORS的`Access-Control-Allow-Origin`設成wildcard也是不Ok。

## 03/19, Mon.

### 技術

* *The Browser Hacker's Handbook*：今天則讀到了繞過SOP之後可以做的事情，包含：
    * 把瀏覽器當成代理伺服器攻擊其它網站或竊取用戶資料
    * 利用界面劫持欺騙或迫使用戶觸發攻擊行為
    * 判斷用戶是否瀏覽過特定網站，由於cache過的網站載入速度比起沒有瀏覽過的網站要快很多，可以透過測量載入速度來做判斷。

* [Checkbox vs Radio Buttons](https://www.nngroup.com/articles/checkboxes-vs-radio-buttons/)：簡單的說，會互斥的單選題用radio，不互斥的複選題用checkBox，然後選項要簡短。

## 03/20, Tue.

本日休刊。

## 03/21, Wed.

### 技術

* *The Browser Hacker's Handbook*：
    * Cookie因為有限制大小，舊的cookie是可能被新加進去的cookie擠掉的。
    * 我原本以為有了HttpOnly就是安全的，但其實只要有XSS，攻擊者完全可以把瀏覽器當proxy拿只有帶Cookie才能拿的資料。所以最大的問題還是XSS呢 (倒)
* [Logging Errors in Client-Side Applications](https://www.sitepoint.com/logging-errors-client-side-apps/)：介紹一些前端做log的工具

## 03/22, Thu.

### 技術

* [讓我們來談談 CSRF](https://blog.techbridge.cc/2017/02/25/csrf-introduction/)：一篇CSRF的簡介，總之就是讓伺服器無法區分這到底是不是使用者自願產生的請求呢。解法有Referer、csrf token、Double Submit Cookie、Same Site Cookie。想想自己手邊的專案...

## 03/23, Fri.

### 技術

* [OWASP 2017 Top 10](https://www.owasp.org/images/7/72/OWASP_Top_10-2017_%28en%29.pdf.pdf)：存參。意外的發現CSRF沒有在榜上呢，因為大家會去注意的緣故，只有5%的app有這個問題。

### 想法

* 最近寫得愈來愈少，一來專案在忙，回到家多半沒什麼力氣；二來比較不那麼急著想知道那麼多事情，或者說，有點懶吧。但竟然也不覺得自己有那麼不好。關於技術的焦慮仍然不會消失，只是不那麼惱人了。可以更好的話很好，但不更好也無妨。

    不過還是會繼續寫下去。
    
## 03/24, Sat.

### 技術

* [EditorConfig](http://editorconfig.org/)：今天發現的東東，一致化編輯器的格式像是tab vs space、一行字數限制等等。
* [Responsive Components: a Solution to the Container Queries Problem](https://philipwalton.com/articles/responsive-components-a-solution-to-the-container-queries-problem/)：基於父容器大小而變化的container query一直是大家都想要的功能，但是由於[種種原因](https://www.xanthir.com/b4PR0)(Circular dependency和效能問題)一直沒有被實作。Chrome 64出現了[ResizeObserver API](https://developers.google.com/web/updates/2016/10/resizeobserver)，會在元素的大小變化時呼叫callback，於是可以用js做到container query。ResizeObserver目前已經有到IE9的[Polyfill](https://github.com/que-etc/resize-observer-polyfill)，使用MutationObserver和IE的MutationEvent來實作，雖然效能可能會是另外的問題。

## 03/25, Sun.

### 技術

* [eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier)：記得以前好像一時想找搭配prettier的eslint plugin找不到，今天才發現其實還是有的啦。
* [Houdini: Maybe The Most Exciting Development In CSS You've Never Heard Of](https://www.smashingmagazine.com/2016/03/houdini-maybe-the-most-exciting-development-in-css-youve-never-heard-of/)：這篇文章介紹了[CSS houdini](https://github.com/w3c/css-houdini-drafts)。
    * 簡單的說，CSS的新特性一直以來都發展得很慢。原因在於網站開發者很難控制CSS的行為。不像javascript，可以利用transpile + polyfill的做法，使得開發者在開發時可以使用瀏覽器未實作的語法；CSS很難使用瀏覽器未實作的功能，原因是polyfill太難做，從parsing、layout、painting到composite，幾乎沒有太多開發者可以插手的餘地。
    * 為此，有人就開始提議在瀏覽器實作一系列的CSS API，讓開發者可以控制CSS。如此即使瀏覽器尚未支援某個CSS特性，開發者也可以自己寫code去控制CSS來polyfill。
    * 目前Houdini大部分還停留在草稿階段，但各大瀏覽器的vendor已經對此有所討論，也一致認為這是將來瀏覽器發展的特性之一。再過幾年很可能就能使用Houdini api來實作客製化的CSS特性。

## 03/26, Mon.

### 閒書

* [匱乏經濟學](http://www.books.com.tw/products/0010660478)：最近在讀這本書，算是行為經濟學的科普呢，談的是匱乏對於人的行為造成的影響。
    * 首先什麼是匱乏？**擁有的比你感覺所需的還要少**。窮人覺得錢不夠多，忙人覺得時間太少，寂寞的人覺得沒人陪伴，匱乏以不同的形式出現在人的生活中。
    * 匱乏為我們的思考和行為帶來兩個主要的影響：

        1. 聚焦(focusing)：匱乏讓我們專注在不足的東西上面，例如趕死線、精打細算、或者孤獨者對表情的較佳敏感度。這讓我們在不足的事情上表現變好(相較於不虞匱乏者)。
        2. 隧道效應(tunneling)：另一方面，因為我們如此關心匱乏，我們的思考被匱乏所佔據而容易忽略其它重要的事務，這就是隧道效應，也就是目標禁制(goal inhibition)，處理目前迫切的目標，反而讓你難以想到其它事情，而這讓人在其它事情上的表現變差，包含認知容量(cognitive capacity，包含了解決問題、抽象思考的能力)以及執行控制力(executive control，包含了管理認知活動，控制衝動、計畫等等的能力)都會因此下降。在書中，作者將這些負面的影響稱之為**認知頻寬稅負**(bandwidth tax)
    * 匱乏容易製造出更多匱乏：在做選擇的時候，有餘裕的人(作者稱之為「寬鬆」的處境)不必擔心選擇帶來的損失，選擇不會帶來錯誤，有自由不做任何選擇隨意而行；而匱乏者必須擔心較差的選擇帶來的損失，較差的選擇對匱乏者而言即是犯錯，因此匱乏者更容易面臨失敗。加上，前述的認知頻寬稅負，導致匱乏者更容易做出衝動而較不好的決定。因此，匱乏者往往愈來愈匱乏。

## 03/27, Tue.

### 感冒休刊一日