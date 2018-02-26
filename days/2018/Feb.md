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

## 02/04, Sun.

### 技術

* [Let’s make multi-colored icons with SVG symbols and CSS variables](https://medium.freecodecamp.org/lets-make-your-svg-symbol-icons-multi-colored-with-css-variables-cddd1769fca4)：用css variable來達成一組svg多種不同配色的目的。這是icon font做不到的事情之一唷。

## 02/05, Mon.

### 抬頭一望，也寫了一個月呢

其實還蠻累的。來談談一些困難吧。

最困難的還是**找到固定寫筆記的時間**吧。最前面是挑晚上回家之後寫，剛開始還新鮮所以很有成就感，但是晚回家的日子就傷腦筋了，想著不能斷更所以硬著頭皮寫，寫完常常都很晚了，隔天起床精神就會不好，工作進入狀況的速度慢了許多。

之後則是想著改成早上出門前來寫，但只要是晚回家晚睡覺的日子，早上就很難準時爬起來寫，加上天氣冷，就會更想賴床。

而且**並不是每天都有時間騰出來「好好」讀一些材料**。平日能夠讀東西的時間，大致上只有早上、搭車上下班和晚上回家後了。早上想賴床，搭車上班想補眠，晚上有事情，搭車回家累到不想讀，哼哈哈哈，真是完美的一天(咦)。誰叫我家離公司一小時遠呢。

再者，**不是每一篇文章都有料**，一個月下來，網路文章和書本比起來，書本還是能找到最多收穫的來源，特別是特定領域的經典書。網路上的文章有用的，多半是一些小技巧(例如前不久提到的實作多顏色svg icon)或跟框架有相關的概念/實作(例如redux duck type)，然而讀下來發現沒什麼內容的狀況也不少。但是困擾的是，實體的技術書籍多半都有一點高度或厚度，不是可以輕鬆帶著走的東西，所以就沒辦法想讀就讀了。結果，如果那天像上面說的沒什麼時間讀書，就只好趁搭車的時候讀網路文章了，而有些可能是地雷，最後發現比較有收穫的，反而都是些跟UI比較有關的內容XD

抱怨完了，來談談好處。每天做筆記最棒的地方是**它讓你看到一天、一個禮拜、半個月下來到底學了多少東西**。我常常對學了多少東西感到很不踏實，筆記記下的內容雖然不是全部，但確實是我下班時間學到的(跟技術相關)東西的...至少七八成有吧。它讓你看到一個禮拜可以累積的知識的量，讓你知道，超英趕美不可能，但每天累積還是可以有一些小成就。相對心裡會踏實一點。

還有一點不自言的好處是，**每天都會學到一點東西**，扣掉作者公休什麼的，為了不讓習慣斷掉，你總會去找一點東西來讀，所以一定會有所得。只是，這個所得是不是真的那麼值，就不一定了。零碎時間的理解多半想得不夠深，我覺得最有所得的時候，還是在那些能夠認真讀個二三十分鐘的好書的時候啊。

結論啊，果然是像[深度工作力](http://www.books.com.tw/products/0010758381)說的，要開出一段無人打擾的時間專注才行呢。

簡單的說：

* 要有固定時間，或至少每天都要排出可以專心的一段時間。
* 就想法的所得而言，書比網路文章要多而且也比較深入。不過框架用法、開發/建置工具、瀏覽器特性等等還是要讀網路文章。

也在思考以我的生活形態，到底應不應該每天都更新呢？如果有辦法，其實還是該每天空出一段時間的，但不管起床或睡前，看來也是得花點工夫呢，人生啊到底該不該這麼累呢(離題)。

## 02/06, Tue.

### 技術

* 回去讀了[Clean Code](http://www.books.com.tw/products/0010579897)的前三章。
    * 其實大多數的事都是知道的，可是回到實際工作上，還是很容易寫出`accountInfo`這樣的東西啊。
    * 關於匈牙利命名法(或任何夾帶型別的命名)，因為書中主要以Java/C#等等有靜態型別的語言為主，在想或許Javascript還是可以適用的...啊啊Typescript什麼的...
    * 倒是，命名有助於搜尋這件事情，好像是在工作一陣子之後才特別有感。沒好好命名的話真的很難找code啊。
    * 函數要抽象到舒服又看得懂的程度真的好難，現在還是常常劈哩啪啦的寫長長的函數QQ。第三章最後的範例我覺得很漂亮，可是說不定也會有人覺得抽太多了。

### 工作

* [Learning At Work](https://jvns.ca/blog/2017/08/06/learning-at-work/)：昨天才談到一點學習焦慮今天就在codeTengu上看到這篇了呢XD，談了一些在工作中學東西的方法。

### 趣聞

* [IFTTT](https://ifttt.com/)：可以把一堆服務串在一起的東西，還沒玩過但是好像很有趣，詳細一點的介紹看[這篇](https://www.computerworld.com/article/3239304/mobile-wireless/what-is-ifttt-how-to-use-if-this-then-that-services.html)

## 02/07, Wed.

### 技術

* 繼續讀Clean Code關於註解、編排、物件與資料結構的部分
    * 註解應當被視為一種為表達意圖失敗的彌補。它代表你想不出好方法用程式碼說出你的意圖，只好用註解了。整潔的程式碼本身具備一定的表達力，當想到使用註解時，很可能代表程式碼需要再弄乾淨。
    * 註解受人詬病的，就是沒辦法和程式碼一起被更新，註解一旦寫下去就可能成為將來的謊言，誤導或干擾將來負責維護的人。所以註解愈少愈好。
    * 檔案大小的範圍，盡可能不要超過一定的行數，以作者的專案Fitnesse來說，最大的檔案也不超過500行。而大多數的檔案少於200行。
    * 編排可以從垂直和水平的角度來劃分：
        * 垂直而言，由上而下按照函式呼叫的順序作編排，即被呼叫的函式放在呼叫它的函式的上面，如果抽象得當的話，讀它的人可以一路由最上層的抽象讀到底層。另外，相關的函式或局部變數應該要盡可能靠近被使用的地方。這些做法可以減少在檔案中不斷上下滑動瀏覽的窘境。
        * 水平而言，不要超過120個字元。其它縮排、留空等自不待言，Javascript可以交給 [prettier](https://prettier.io/)。

    * 結構化的寫法容易增加新的函式，但不容易增加新的資料型別；物件導向的寫法容易增加新的資料型別，但不容易增加新的函式。簡直像在繞口令嘛。`A.f()`和`f(A)`的差別呢...
    * **德摩特爾法則(The Law Of Demeter)**：一個類別C的方法f，應該只能呼叫以下事項的方法，否則就是事件知道了其它物件的內部運作：
        * C自身
        * 任何由f產生的物件
        * 作為參數傳給f的物件
        * C類別中實體變數持有的物件
    * 不是所有的東西都要寫成物件。而對於資料結構來說，違反德摩特爾法則則是ok的。
    
* [Software Complexity Is Killing Us](https://www.simplethread.com/software-complexity-killing-us/?utm_campaign=CodeTengu&utm_medium=email&utm_source=CodeTengu_115)：終究程式設計師的第一要務是創造價值，而不是去處理軟體複雜度(後者只是前者的一個面向)。作者的想法是，大多數的專案其實不需要那麼複雜的工具，而複雜的工具其實變相增加了開發的難度，讓開發者更難實作真正需要被實作的邏輯，開發的速度因此就變慢了。這很可能讓更多需要軟體的人轉向所謂的Low Code Platform，即不需要懂得寫程式，透過拖拉等簡單方式就可以建造軟體的平台。顯然，我們不會想要跟這些平台產生的code打交道，更嚴重的是，一旦平台本身倒了，產生的軟體可能也會跟著倒。仔細想想，前端現在也是愈來愈複雜，但是工作上碰到的需求，目前最多的也還是CRUD，簡單`$.ajax`一下就好的事情啊。先不論只是CRUD究竟能有什麼價值，我們真的有享受到新工具帶來的好處嗎？到底在什麼時候應該用____(可填入redux、react或任何新玩意兒)，什麼時候不需要呢？整體來說，我自己現在還是寫得挺舒服的，但是是該想一想呢。

## 02/08, Thu.

### 技術

* [React, Redux and JavaScript Architecture](https://jrsinclair.com/articles/2018/react-redux-javascript-architecture/)：很有意思的文章，解釋了為什麼(Why, not how)要用React和Redux。作者從一個簡單的toggle實作講起。簡單的說：
    * 隨著元件的內容和操作增加，元素的變動愈來愈複雜。如果我們只看DOM，我們很難看出來現在的DOM代表UI的什麼狀態，很容易出錯。因此開發者開始希望可以把元件的狀態和DOM的操作分離出來，用元件的狀態(state)來決定現在DOM的樣子(view)。
    * 然而，如果直接用jquery硬寫狀態代表的html(e.g. `$.html()`)，每次狀態變化都會導致整個DOM tree被重新create，這樣效能很差。一些文章談到React的時候，之所以說「DOM操作很吃效能」，就是在說不能夠重新創建整個元件的所有元素，效能太差。原本最一開始html + jquery的解法，只操作了需要變動的部分，因此沒有效能的問題。
    * React的virtual DOM解決了這個問題，它透過比較狀態變更前後的virtual DOM tree，只更新有需要更新的節點。(這個比較演算法，根據 [JavaScript’s History and How it Led To ReactJS](https://thenewstack.io/javascripts-history-and-how-it-led-to-reactjs/)的說法，從O(n^3)演變到現今的O(n)，才得以真正用在實際應用。)。因此React的價值，在於讓我們輕鬆的把元件的state從DOM操作中分離出來，又不會因此損耗過多的效能。
    
        是說，如果有一天browser可以內建virtual DOM的api的話，說不定React的優勢就沒那麼大了(嗎)
    * 為了表達在某個狀態下的view，React導入了JSX，讓它寫起來像是原本在寫html一樣。相較於原本html + jquery的寫法，JSX讓我們對元件的描述從imperative變成declarative的風格，不用擔心DOM操作的細節。(說到imperative和declarative的差別，大概就像十分逼近法和x^(1/2)那樣的差異：你會希望計算機可以直接幫你開好根號，而不是自己手動十分逼近法)
    
        不過讀到這裡我在想，JSX和其它可以有變數和javascript操作的模板語言(ejs, handlebar...)，除了可以嵌套component之外，其實也沒有差多少...吧?

    * Redux則帶來兩個好處，一則如[You might not need redux](https://medium.com/@dan_abramov/you-might-not-need-redux-be46360cf367)所說：
    
        > The tradeoff that Redux offers is to add indirection to decouple “what happened” from “how things change”.
    
    Redux幫助開發者把「發生了什麼事」(action)給獨立出來，得到一組action的序列，藉此可以做到重現使用者操作、回溯歷史、同步操作等等複雜的app需要的功能。另外一方面它也把「事情該怎麼做」給獨立出來，這讓同一份邏輯(reducer)得以在不同的地方被重複使用。
    
    * 另一個Redux帶來的好處，則是它把整個app的state放在一起，藉由react-redux把state丟給component做為props，這減少了原本只有React時必須由最上層的component一路丟props下到底層的麻煩。對於有大量global state會影響局部元件的頁面來說很方便。另外，這也可以讓原本需要據有state的component變為`PureComponent`，render會更快一些。
    
    * 不過如果，東西沒有複雜到切出state和view有明顯的好處，那其實可以不用React呢。至於Redux，如果不需要把action特別分離出去，也沒有大量的global state，那其實也是可以不用的。

## 02/09, Fri.

尾牙，被灌酒，公休一日。

## 02/10, Sat.

### 技術

* [Please stop using Local Storage](https://www.rdegges.com/2018/please-stop-using-local-storage/)：作者叫你別再用localStorage了。

    主要的原因是它對XSS一點辦法也沒有。拜npm之賜，第三方腳本可能從許多你不知道的地方被放到你的app來，我們很難確信裡面沒有任何惡意程式。而一旦假設被XSS了，localStorage的東西就一定會被看光光。偏偏大家開發的時候都會偷懶，往裡面塞使用者身份、信用卡資料、JWT token(被打臉)啦等等，這其實超危險的啊。至於解決的方法嘛，作者則提到session id + cookie + httpOnly的解法，讓browser讀不到cookie，詳細的方法嘛...明天再來今天書展好累XD
    次要的原因則像是5MB大小上限、同步阻塞、只能塞字串、不能在service worker使用、不能離線使用等等。說到離線讀取資料，作者還提到了IndexDB的cacheAPI，雖然edge和safari還不支援但看起來挺有用的。

### 人蔘

* [Improving Ourselves to death](https://www.newyorker.com/magazine/2018/01/15/improving-ourselves-to-death)：有點長的文章，作者談到對最近這一波科學化的自我提昇(self optimization)風潮的反思，包含追求完美的弊病，以及自我提昇可能並沒有讓人活得更好。雖然作者說的是美國人的情形，我覺得臺灣也慢慢有這樣的風潮，閒著沒事逛逛誠品就知道了。我自己也是會研究一點life hack或者productivity的人，我想它對生活和工作還是有些幫助，不過我想，不必為了更好而更好，回到生活的現場，想要做到的事情自然而然就會浮上來了，那時再來煩惱也不遲。

## 02/11, Sun.

### 技術

* [Single Page Application Is Not a Silver Bullet](https://blog.bloomca.me/2018/02/04/spa-is-not-silver-bullet.html)：因為SPA的bundle size比起plain html大太多了，多半要佔據好幾百KB甚至MB(gzipped)，而對行動裝置來說compile javascript也很花時間，結果，作者發現他最近改版的網站變成SPA後，反而比原先的版本慢了一倍。
    當然這可以藉由code splitting減少bundle size得到改善，而且理論上bundle如果沒有變更的話，應該只有第一次連上網站時才需要下載，其後都可以直接用cache的版本。不過即使如此，只要網站夠大(Airbnb、Medium、Twiiter)，通常也有幾百KB起跳的bundle，得花上好幾秒載入。
    
* [Protecting Your Cookies: HttpOnly](https://blog.codinghorror.com/protecting-your-cookies-httponly/)：接著昨天的話題。在Set-Cookies header中加上`httpOnly`，javascript就不能夠讀取cookie了。另外昨天的文章還提到了另外兩點：
    * 加上`secure=true`：只有加密連線才能設cookie
    * 加上`SameSite=strice`：只有同源網站才能使用cookie，擋CSRF。
    
## 02/12, Mon.

### 技術

* 讀了Clean Code的第十四章，看作者怎麼從頭清理一個模組，感覺意會勝於言傳啊(茶)
* [To serve man with software](https://blog.codinghorror.com/to-serve-man-with-software/)：終究，咱們寫東西還是為人服務，使人過得更好、成為一個更好的人哪。

    是為了人。

    (同場加映：[小printf](https://ferd.ca/the-little-printf.html))

## 02/13, Tue.

### 技術

* [Simple React Patterns](http://lucasmreis.github.io/blog/simple-react-patterns/)：講了一些React慣用的寫法，即使寫了一年，手法大概都看過，但仍不習慣，例如render props(讓user傳入render函式)、Provider(用context讓所有下層的component可以共享同一份狀態)。

## 02/14, Wed.

### 技術

* *Working Effectively With Legacy Code*：讀了序言和第一章：
    * 這本書在談的是怎麼**有信心地**修改程式碼。不是談怎麼做出好的設計或好的程式碼。
    * 根據作者的定義，legacy code指的就是**沒有測試的程式碼**。因為沒有測試，我們就很難安心的修改程式碼，即使程式碼本身再怎麼乾淨、設計再怎麼精簡，只要缺少測試，就不能放心。
    * 而話說回來，為什麼要修改程式？不外乎四個原因：
        * 增加feature
        * bugfix
        * 改善設計
        * 優化性能
    * feature和bugfix的判斷常是主觀的，對需求方是bugfix的事情，對程式設計師而言卻可能是全新的feature。在此，作者提出了從**行為**出發的觀點：如果一個修改增加了新的行為，那就是增加feature；如果一個修改沒有增加新行為，僅修改了舊的行為，那就是bugfix。
    * 而從修改舊行為這件事情出發，我們注意到，會修改舊行為的只有bugfix，增加feature、改善設計、優化性能的意圖都不會改變既有的行為。而我們做修改時最害怕的，就是破壞既有的良好行為，無意間引入新的bug。因此，我們需要測試。

* [nwb](https://github.com/insin/nwb)：最近在工作上用到它，和 create-react-app一樣，是 starter kit，但也支援 preact、inferno和 vanilla app，還有 [React component](https://github.com/insin/nwb#react-components-and-libraries)。create-react-app個人覺得很適合App，dev server開起來很快，可是也有一些限制，像是沒辦法簡單的import `src`外面的程式碼，非得折騰`eject`不可(如果有簡單的解法拜託請告訴我 QQ)。這對開發library裡面的 demo/dev App來說有點惱人。相較之下 nwb雖然慢一些，測試框架用的還是 karma(目前[好像正在導入jest](https://github.com/insin/nwb/issues/173)，不過手動改一下測試指令也很簡單)，但就沒有這個限制。而且 nwb也搞定了 library的建置指令。覺得如果想開發 react component的 library給別人用的話，目前感覺起來還蠻方便的。

## 02/15, Wed.

### 技術

* [npx](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b)是一個執行 npm script/binary的工具，從 npm v5.2.0。以往要執行package中的binary(如mocha、jest、create-react-app)必須要全局安裝，藉由npx我們可以一行執行下載的dev dependency中的binary，或者甚至一行下載package、執行binary、砍掉package，而不需要像以往全局安裝，方便一些。

## 02/16, Thu.

### 技術

* [用javascript做視差滾動](https://daverupert.com/2018/02/cheapass-parallax/)

## 02/17, Fri.

### 技術

* [The cost of javascript](https://medium.com/dev-channel/the-cost-of-javascript-84009f51e99e)：一篇很完整的介紹如何優化javascript載入速度的文章。幾個有趣的點：
    * javascript的載入時間包含兩部分：下載和處理(parse、compile、execution)。
    * 大家經常輕忽處理javascript所需的時間，同樣大小的圖片和javascript code比起來，後者所需要的處理時間可能會更多。
    * 下載時間的優化技巧包含： 
        * 只載入需要的程式碼，包含code splitting、tree shaking、只載入大型library(moment、lodash)的必要部分等等，詳細的trick可以讀[這一篇](https://iamakulov.com/notes/webpack-front-end-size-caching/)。
        * 最小化，例如uglifyJS。
        * 壓縮檔案，最少gzipped一下；最近還出現了[Brotli](https://www.smashingmagazine.com/2016/10/next-generation-server-compression-with-brotli/)，據說檔案大小會比gzip少個幾%甚至1x%，雖然Edge和Safari還不支援這種Encoding，
        * Cache，包含使用max-age、eTag等等header來告訴瀏覽器何時下載新的檔案。或者，使用filename hashing來確保每次建構的bundle檔名不同。
    * 處理時間的優化技巧包含：
        * 只載入需要的程式碼(同上)。
    * 綜合來說，影響下載時間的是網路環境，而影響處理時間的則是device的運算速度(C/GPU、cache、RAM)。不會只有一個factor，所以，按照網站主要使用者的環境選擇要優化的項目吧(利用google analytic可以知道網站使用者的device的基本資訊)。不過基本上，載入的程式碼愈少愈好就是了。
    * 幾個有趣的數字：
        * 市面上最高性能和平均性能的device相比，javascript的載入時間可以相差2x~5x。以CNN為例，在文章當時，iPhone8約需要4秒來載入js，而平均水準的Moto G4則需要13秒；
        * 文章提供的js parse cost裡面，最快的前三名都是iphone/ipad，其中前兩名都是safari。不過接下來則是macbook on chrome。
        * [HTTP Archive](http://beta.httparchive.org/reports/state-of-javascript#bytesJs)調查前500000個網站，發現有50%的網站需要14秒使用者才能與之互動，而它們要花4秒的時間來處理javascript。
    * 最後作者提到一些優化的策略：
        * [PRPL](https://developers.google.com/web/fundamentals/performance/prpl-pattern/)：原本是PWA裡面的優化策略，但也可以泛指任何的web app：
            * 送initial route需要的資源
            * 渲染initial route
            * pre-cache其它的route
            * 需要時，再lazy-load/  create其它的route
        * [Progressive Bootstrapping](https://twitter.com/aerotwist/status/729712502943174657)：

            server side rendering是現在常見的渲染方式，server端先一次把需要的html渲染好，client端再載入所有需要的js，這樣的方法，在html載入到js載入完成之間會有一段時間，用戶雖然能看到view卻無法與之互動。
            Progressive Bootstrapping指的則是，在一開始的html中只夾帶必要的html、css、javascript，如此使用者可以很快的和頁面互動，其餘的feature則隨後再載入。
            
            其實看連結的圖就可以一目了然了XD

    文末還有不少和載入優化相關的其它文章，附帶一提，作者[Addy Osmani](https://addyosmani.com/)也是在web performance這一塊很有名的工程師。
    
* [Multi-factor Authentication](https://en.m.wikipedia.org/wiki/Multi-factor_authentication)：雖然是維基文章，但簡要地介紹了MFA的概念，常聽到2FA就是指用到2個元素來做認證的認證步驟。常見的簡訊認證碼，就是利用手機(something user possesses)來強化認證的困難度。

## 02/18, Sun.

### 技術

* *Working Effectively With Legacy Code*：讀到第二章 *Working with Feedback*。
    * 修改程式碼可以分為兩種： Edit and Pray和 Cover and Modify。差別並不在於程式設計師是否足夠小心，而在於後者有測試幫助我們確保修改不會破壞東西。
    * 承上，既然測試對修改有很大的幫助，為什麼大家不這麼做？原因是
        * 測試需要的時間太長了，沒辦法立刻得到反饋。
        * 測試涉及太多部分，出錯時很難立刻得知是程式的哪一部分出錯。
    * 承上，所以作者認為應該要有一組快速、又能幫助迅速定位錯誤的單元測試，幫助我們作修改。對作者來說，單元測試的定義即在於(1)它夠快(< 0.1s)(2)它能迅速確定錯誤的部分
    * 承上，為了為既有的程式碼寫測試，我們會發現有些程式碼會依賴於其它部分，例如資料庫、連線、第三方函式、其它類別，為這些程式碼寫測試變得很困難，因為為了使用它你必須幫它準備好這些依賴。為此，我們需要修改程式碼，隔離這些依賴，讓單元變得可以測試。但這裡就有一個矛盾：*為了修改程式碼，必須寫測試；但為了寫測試，又必須修改程式碼*。對於這個兩難，作者首先認為，可以用更高一層的測試來避免產生依賴的問題；另外，作者在這本書也會提到一些保守性的、逐步破除依賴的技巧，減少在沒有測試的狀況下破除依賴的危險。(不過我覺得，這終究還是回歸到程式設計師本身足夠小心與否的問題，上述的兩難書中其實沒有提出能說服人的解法呢。)最後作者也提到，破除依賴使程式碼可測試，可能也會讓設計變得比原本醜陋或冗餘，這裡必須自行拿捏可測試性和設計之間的分寸。
    * 經過這樣一段論述，作者提出了一組完整的，修改程式的流程：
        1. Identify change points.
        2. Find test points.
        3. Break dependencies.
        4. Write tests.
        5. Make changes and refactor. 
        這本書剩下的章節要談的，也就是這五個步驟中可能碰到的種種困難及解方(以一種Q&A的形式)。
        
## 02/19, Mon.

### 技術

* *Working Effectively With Legacy Code* 第三章： *Sensing and Seperation*。
    * 更仔細的說，需要破除依賴的原因，通常有二：
        * Sensing：我們希望不透過依賴物就能知道功能運作的結果。
        * Separation：我們希望不透過依賴物就能建立被測試的物件(或功能)
    * 這本書大多在談Separation的技巧。而關於Sensing，這一章則介紹了一個技巧：Fake Collaborators。
        * 針對我們用來知道結果的外部class的行為，建立一個interface；此後我們建立一個fake object的class實作這個interface，使被測試的class可以使用fake object；同時也實作測試程式碼用來得知測試結果的方法，使得測試通過呼叫這些方法來得知單元工作的結果。

## 02/20, Tue.

### 技術

* *Working Effectively With Legacy Code* 第四章： *Seams*。
    * 這一章介紹的是seams(接縫)的概念。接縫指的是程式碼當中，**不需要改動程式碼本身**，即可以改變其行為的地方。
    * 為什麼需要接縫？上一章提到，為了知道功能運作的結果以及建立被測試的單元，需要破除依賴。破除依賴常常需要修改原始碼，可能會很麻煩。如果程式碼本身有接縫，我們就可以從外部環境來改變程式碼的行為，排除掉測試環境下不需要的依賴，就可以不用改原始碼來破除依賴，會讓建立測試變得輕鬆許多。
    * 而接縫有哪些呢？作者提到了三種：
        * Preprocessing Seams：指程式語言如C、C++、Lisp等提供編譯前的preprocessing(例如macro)，可以改變程式碼的行為。
        * Link Seams：指在連結時期改變程式碼的行為。例如透過import path的設定，使得程式碼載入不同的library。
        * Object Seams：是OOP特有的接縫。利用繼承，我們可以在方法中增加某個父類別的參數，讓外部的方法呼叫者丟不一樣的子類別的實例給被測試的類別使用，而改變方法的行為。
        * 作者建議在通常狀況下使用Object Seams，因為前兩者較難搞懂/維護。然而在很難增加Object Seams的狀況下，有時也可以考慮Preprocessing/Link Seams
    * 不過因為這本書主要使用的是靜態型別的語言。在Python或Javascript之類的語言中，可以直接在測試時替換掉實例的屬性，變得可以在執行期間改變程式行為，使得寫測試變得簡單許多。這個論點在單元測試的藝術也有提到：究竟動態語言如Ruby、Python、Javascript到底應不應該考慮可測試性的設計？作者覺得既然它們都可以直接在執行期改變行為，使得寫測試變得簡單，或許就可以不用在乎可測試性設計了。

## 02/21, Wed.

### 技術

* *Working Effectively With Legacy Code* 第五章： *Tools*。
    * 這一章介紹幫助我們寫測試的工具；雖然都是十年前的東西，有些還是我不知道的：
        * Automated Refactoring Tools：用來自動重構
        * Mock Objects：就是Mock Objects
        * xUnit Frameworks：就是xUnit
        * FIT(Framework for Integerated Test)/Fitnesse：用於整合/驗收測試的工具。測試者可以透過在FIT的wiki系統上編輯表格，來表達測試和期待的結果；FIT會自動將表格轉換成測試條件，丟給程式設計師寫好的fixture來執行測試，測試的結果會自動更新到wiki的表格中。不過，為什麼前端開發幾乎看不到這種工具呢？

* [這一篇](https://cdb.reacttraining.com/use-a-render-prop-50de598f11ce)：作者主張render prop的寫法可以完全取代High order component的寫法，基本論點如下：
    * 為了共用component的邏輯，在React剛出來(with es5)的時候，大家都是使用mixin + `React.createClass`的寫法。
    * 後來es6出現了，js終於可以原生支持class了(雖然是語法糖)，React也推出class component來替代原本的`createClass`。但問題來了，es6的class不支援mixin的寫法...
    * 所以HOC就出現了
    * 但是HOC和mixin在作者眼中都有同樣的缺點：
        1. mixin插入了修改state的邏輯；而HOC把props丟到原本不認識這些props的component裡。兩者都會讓我們看不出這些多出來的state/props，究竟是來自我們自己的邏輯，或是從mixin/HOC加進來的。
        2. 命名衝突，只要被包起來的component有同名的state/props就會吃土。
        3. 必須讓包起來的新component行為和舊的一樣，所以要pass不少重複的props，也可能產生bug。

    * 而render props的寫法沒有上述的三個問題，因此作者主張當你想要寫HOC的時候，用render props。

## 02/22, Thu.

### 技術

* *Working Effectively With Legacy Code* 第六章： *I don't have much time and I have to change it*。
    * 從這一章開始進入本書的第二(也是主要)部分：*Changing Software*。每一章的標題都是一個問題，談到改變程式碼的困難。
    * 這一章談的是，當為既有的程式碼寫測試太困難又耗時，而你又想改動它的時候，可以怎麼辦。
    * 作者談到了四個方法，讓你可以對新的邏輯寫測試，又不必破除舊程式碼的依賴：
        * *Sprout Method*：當需要在原本的方法中增加邏輯時，把新的邏輯抽出來變成新的方法，在舊的方法中直接呼叫這個新方法。
        * *Sprout Class*：類似Sprout Method，但是是把新的邏輯抽出來變成一個新類別的方法，在舊的方法中創建這個新類別並呼叫新方法。通常用在舊類別的依賴太多無法在測試中創建實例的時候。
        * *Wrap Method*：和Sprout Method相反，當需要在原本的方法中增加邏輯時，創建一個新的方法，把舊方法的名字換掉，把新方法的名字改成之前的舊方法，然後在新方法中執行要增加的邏輯(把它包成另一個新方法)和既有的舊方法。如此，原本使用舊方法的程式碼並不會知道實作增加了新的行為。
        * *Wrap Class*：類似於Wrap Method，但是是用新的類別包住舊的類別，新的類別中提供和舊的類別一樣的界面。decorator pattern就是Wrap Class的實作模式之一。
    * 這些改寫的方法在初步可能顯得太過麻煩，尤其是在既有的類別責任很多的時候，額外為一個小功能做Wrap Class看起來簡直像在做白工。但作者也提到，程式碼的改善，通常都是由一點一點的小改動累積起來的。所以作者還是建議我們勇敢的去做這些改善。
    * 但我覺得這裡作者談的其實都是「在不動到舊行為的狀況下，增加新行為」，而不是「修改舊行為」，有些時候，你就是要直接修改舊的行為，這些方法是否能幫上忙，就要打個問號了。

## 02/23, Fri.

### 技術

* *Working Effectively With Legacy Code* 第八章： *How do I Add A Feature?*。

    第六章出現了好幾次對第八章的引用，所以就先跳過來看這一章。這章想說的就是怎麼加入新的行為；只有兩個重點，一個是TDD，一個是Programming By Difference。
    * TDD的部分相信前面看了那麼多筆記大概也很熟悉了(?)所以就不贅述XD總之，不管是修改既有行為或增加新行為，作者認為TDD是很好的實踐。
    * Programming By Difference則是指用繼承實作新的feature。倘若舊的類別需要長出新的行為，就創造一個新的類別繼承舊的類別並且override原本的方法。好處是寫起來足夠無腦，壞處則是繼承多了容易搞不清楚哪個類別才是幹實事的。
    * 在此作者也提到里氏替換法則(Liskov Substitution Principle)，指的是說，一個子類別的實例應該可以被一個父類別的實例所替換，或者說，任何子類別的實例都應該可以當成父類別的實例使用。作者舉了一個反例：

        ```java
        public class Rectangle {
            setWidth() { ... }
            setHeight() { ... }
        }
        
        public class Square extends Rectangle {
            setWidth() { ... }
            setHeight() { ... }
        }
        
        Rectangle r = new Square()
        r.setWidth(3)
        r.setHeight(4)
        ```
        問題來了，`Square`的`setWidth`方法究竟應不應該改變`height`呢？如果為了維持正方形的定義而改變，使用者就會覺得很奇怪，為什麼`setWidth`會影響`height`呢？但如果不改變高度，它就再也不是個正方形了。所以，這裡`Square`的繼承就違反了里氏替換原則。
        
        兩個原則：
        
        1. 不要改寫concrete method
        2. 如果你改寫了，盡可能呼叫被改寫的方法
    
        或者，就乾脆把父類別改成抽象類別，把要改寫的方法改成抽象方法，concrete method一概都交由子類別去實作，作者稱這樣的繼承體系為 normalized hierarchy。這樣的好處是可以直接看出來某個類別的某個方法做了什麼：要嘛它是抽象方法，要嘛它就是實作。
* [Precedence in CSS (When Order of CSS Matters)](https://css-tricks.com/precedence-css-order-css-matters/)：今天才知道原來當兩個 css 選擇器權重一樣的時候，會依照它在 html 中出現的順序來決定那個樣式最後會生效(掩面，這好像是早該知道的事)。為什麼會發現這件事呢？因為今天工作的時候我嘗試修理 開了 [critical](https://github.com/addyosmani/critical)
 之後，頁面會閃動的問題，結果發現 critical output 出來的 css 竟然和原本的 css 順序不一樣，導致本來寫在後面的媒體查詢被前面的樣式覆蓋掉...很奇怪的是 critcal 用[penthouse](https://github.com/pocketjoso/penthouse)來產生 critical css ，但是我在 penthouse 的[線上產生器](https://jonassebastianohlsson.com/criticalpathcssgenerator/)生出來的 critical css 順序卻是正確的。目前還是沒有好解法...

## 02/24, Sat.

### 技術

* *Working Effectively With Legacy Code* 第七章： *It takes forever to make a change*。

    * 這章講到，改程式碼為什麼會花那麼多時間。作者提到三個困難：

        1. 理解困難
        2. 編譯時間過長
        3. 破除依賴困難
        
        本書其餘章節都談到了這些困難的不同面向的解法。
    * 本章的後半部分作者也提到如何透過將界面和實作分開來避免因實作變更而造成的重新編譯，如此可以緩解編譯時間過長的問題。另外這也符合依賴倒置原則(Dependency Inversion Principle)：
        * 較高階層的模組不應依賴於低階層的模組；兩者都應依賴於抽象
        * 抽象不應依賴於實作細節，而實作細節應依賴於抽象
        * 總之就是依照interface辦事啊。

## 02/25, Sun.

### 技術

* *Working Effectively With Legacy Code* 第九章： *I can't get this clas into test harness*。

    * 這一章在講，當沒有辦法把被測類的類別加到測試裡面的時候該怎麼辦。可能碰到的困難大致分成四個：

        1. 沒辦法簡單地生成實例
        2. 加進去之後測試沒辦法簡單地build
        3. 建構子有很麻煩的副作用
        4. 我們想要測在建構子中發生的事。
    
        以下一一談及可能遇到的問題及解決的方法。
    * *Irritating Parameter*：泛指建構子的參數列中，有很難建構的實例參數，它可能需要和第三方依賴連結。
        * 作者建議嘗試在測試中生成實例時，先從最簡單的不帶任何參數開始，再看編譯器報錯來找出困難點。
        * 解決方法：抽出該參數類別的介面，然後實作一個測試專用的假的類別來實作該介面，如此我們就可以把這個假的類別當成參數傳進去。
        * 作者在這裡也提到其它概念，例如允許test code為了測試破壞封裝、允許test code為了簡化生成物件的過程而傳入null值，等等。
    * *Hidden Dependency*：和*Irritating Parameter*不同，*Hidden Dependency*指的是不在參數列中，卻在建構子中被創建出來的依賴。
        * 解決方法：把這個依賴加到參數列中。為了避免因為多加參數而到處修改建構該物件的程式碼，可以保留原本的建構子，新增一個增加參數的建構子，然後讓原本的建構子創建該依賴，把它丟進新的建構子裡頭。或者也可以使用default argument。
    * *Construction Blob*：指的是當建構子創建了一大堆物件的時候，或者建構子使用參數創建物件後，又用它們創建其它新物件的時候，此時如果都把依賴搬到參數列，參數列會變得很長而不好維護。當我們想透過被生成的物件做測試就會變得很困難。
        * 解決方法：
            
            1. *Extract and Override Factory Method*：把這一堆生成新物件的程式碼抽取出來作為一個方法，在測試中創建子類別覆寫這個方法，並在測試中用這個子類別做測試。
            2. *Supersede Instance Variable*：額外寫一個setter讓我們可以傳入新的實例取代生成的實例。
    * 其餘的還沒讀完，明天待續(?)
        
## 02/26, Mon.

### 技術

* *Working Effectively With Legacy Code* 第九章： *I can't get this clas into test harness*。

    * 繼續昨天未完的：
    * *Irritating Global Dependency*：指建構子或方法中用到全局物件的狀況。通常是因為用了 singleton pattern 的緣故。
    * 解決方法：
        1. *Introduce Static Setter*：創建一個靜態的setter，允許傳入這個單例類別的實例來設定現在的實例。
        2. 放寬單例模式的private constructor，改成protect或public。
        3. 繼承該依賴的類別，如此便可以在測試中生成該物件並丟進1的static setter來滿足依賴。
* [itemtype](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/itemtype)：今天才知道的html attribute，用來標記結構化資料，可以幫助搜尋引擎抓取資訊，例如商品、電影評分、文章等等。標記的格式按照 [schema.org] (http://schema.org/) 。