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

## 01/05, Fri.

### 問題

* 固定大小的元素在RWD當中應該怎麼處理呢？RWD就要讓所有的東西都等比例嗎？(看完*Responsive Web Design*的疑問，也是實作以來一直碰到的問題)
* retina螢幕對圖片的渲染有什麼影響？px、dpi、螢幕解析度、viewport等等的實際意思是什麼，又會怎麼影響開發呢？之前不時會碰到相關的討論但一直沒有弄懂。
* 略讀過[Vue](https://vuejs.org/v2/guide/)的文件後，反而更加困惑了：

    * Vue和React差在哪裡呢？什麼時候會用哪一個？
    * React有什麼不好的地方呢？一直以來都覺得React還算好寫好用，但它總該有不好用的時候。
    * Two-way和One-way binding的意思。

### 技術

* 讀完Ethan Marcotte的*Responsive Web Design*(2011年的書，距今也七年了)，了解當年RWD剛推出時包含的內容。

* [Vue.js](https://vuejs.org/v2/guide/)：為了了解現代前端框架的異同好壞，最近打算摸一點點React之外的東西。大概略讀過了這份guide，引出了更多問題(見上面的問題)

* es6中的`export`語法，按[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)的文件，可以分成兩種，一種是named export：

```javascript
const func = () => {}
const obj = {}
export {
    func,
    obj    
}
// 或者這樣
export const abc = "abc"
export const def = "def"
```
可以一次export多個不同的值，就不用重複寫module的名字了。
另一種是default export。

```javascript
const func = () => {}
export default func
```

好處是`import`default export出來的東西時，可以隨便使用者命名。

這些語法平常都用很久了，不過是最近才發現原來不能這樣寫：

```javascript
// module.js

const funcA = () => { console.log("a")}

export default { funcA }

// client.js
import { funcA } from "module"
// 會報出`module._default.funcA is not a function`的錯
funcA()
```

另外，有時候專案會碰到`require/module.exports`和es6`import/export`混用的狀況，有時也會出現import error的情形，找個時間來研究一下。

### 趣聞

* *夜的盡頭*：現代人常常會為了不能快速入睡、失眠而傷腦筋。然而以前的人在沒有夜間照明的時候，遵守日出日落的作息，睡覺的時候比我們要長得多，實際上，睡眠中間會有一段時間是意識清醒的。他們很可能沒有那麼快睡著，而且他們並不為此擔心。相較之下，今人其實是為了沒有那麼快入睡焦慮太多了。
* 還是*夜的盡頭*：常識認為夜間照明有助犯罪率下降，然而研究發現，夜間照明和犯罪率並沒有顯著的關係，強化夜間照明可能會讓犯罪率下降/上升/不變(雖然書中並沒有進一步提到有沒有其它的中間因素)。實際上，**過強的**照明反而讓你看不清楚眼前的狀況，而有對比的照明才能讓人看清楚景物。人們之所以認為夜間照明對阻止犯罪有效，恐怕是出於人對於黑夜感到害怕的天性。

## 01/06, Sat.

### 技術

* [Towards A Retina Web](https://coding.smashingmagazine.com/2012/08/towards-retina-web/)：接續昨天對retina螢幕及相關術語的問題，今天google到了這篇文章，解決了一半的困惑，簡單的說：

    * px，指的是顯示的最小單位，每個pixel會有它的顏色和亮度等參數，給出一個顯示的結果。device pixel指的是螢幕上畫面的最小單位，螢幕的畫面就是由這些pixel組成的；而css裡面的pixel指的是網頁畫面的最小單位。
    * ppi(pixel per inch)則是screen density的單位，意指device上一英吋所含有的pixel數量。
    * 在一般情形下，css裡一個2px x 2px的區塊，轉換到螢幕(device pixel)也會是2px x 2px的區塊，device-pixel-ratio會是1。
    * retina螢幕，指的則是讓像素的密度增加為一般情形下的兩倍。device-pixel-ratio會是2。上述2px x 2px的區塊，就會用4px x 4px的螢幕區塊顯示，但因為像素密度增加了兩倍，呈現的實際物理大小和一般的螢幕是一樣的。
    * 一些圖片格式也是由px所組成的(jpg, png...)給定一個100px x 100px的網頁區塊，把一張100px x 100px的圖片放上去，在一般螢幕下仍然只用了100px x 100px，沒有問題。
    * 然而在retina螢幕上，這個區塊實際上會用掉200px x 200px的像素點，而看起來和一般的螢幕並沒有兩樣，因為原本的圖片是100px x 100px，map上去也只是重複一樣的顏色，沒有辦法達到讓畫面變得精細的效果。
    * 因此，為了要讓retina螢幕的用戶能夠享受到較高的畫質，我們應該要為他們提供200px x 200px的圖片，才能充分運用到每個像素點。
    
    實際上的實作方法(media query、srcset、picture...)還要再讀讀其它的source。
    
### 趣聞

* 今天頭一次去新北市圖總館，頭一次玩自助取書機，機器跑上跑下的樣子很有趣，也蠻方便的。

## 01/07, Sun.

### 問題

* 怎麼做圖片的載入優化？記得看過medium、google image等等有很多不同的做法，想來研究一下怎麼實作。
* `em`除了在控制文本內容的大小時可以用，好像也常看到它用在layout上，什麼時候用`em`什麼時候用`px`呢？

### 技術

* [Semantic Versioning(semver)](https://semver.org/)：一種版本號的命名方式，目的是為了解決相依性的問題，格式如下：

    給定一個版本號**X.Y.Z**，假設，發佈的軟體包有一組公共的api，這個公共的api應該透過文件或程式碼讓使用者清楚知道。
    * X是主版號(major version)，當新的版本有不相容於舊版本的公共api變更時，更新主版號。
    * Y是次版號(minor version)，當新的版本有相容於舊版本的公共api變更/新增時，更新次版號。
    * Z是修訂號(patch version)，當新版本僅修復問題而不修改公共api時，更新修訂號。
    * 在公共api可以被明確定義出來之前，或者當軟體包仍在快速開發時，使用0.Y.Z的版本號，1.0.0以上的版號都應該有一組穩定、不會隨意變動的公共api。
    
    這麼做的好處是，使用者可以直接判斷這次的更新會不會導致依賴出錯，只要主版本號未變動，便可以放心的更新套件。
    
* [responsive images](https://developer.mozilla.org/zh-TW/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)：接續昨天的討論，可以用`srcset`和`<picture>`來做到圖片載入的媒體查詢。比方說：

    ```html
    <!-- 
    對於device-pixel-ratio為1的一般螢幕，
    載入寬度為600px的圖片；
    對於retina或device-pixel-ratio為2的螢幕，
    載入寬度為1200px的圖片
    如果width > 1000px，圖片寬為50vw；反之則為100vw
    -->
    <img
      src="lion-600w.jpg"
      sizes="(min-width: 1000px) 50vw, 100vw"
      alt="lion"
      srcset="
        lion-600w.jpg 1x
        lion-1200w.jpg 2x    
      "
    />
    ```

    `<picture>`則是類似於`<audio>`和`<video>`，可以在裡頭放入多個`<source>`標記，每個`<source>`標記可以依照圖片格式、媒體查詢讓瀏覽器選擇最適合的圖片，比起`img`更進一步。但缺點是IE11目前不支援，不過已經有人寫了[polyfill](http://scottjehl.github.io/picturefill/)。

## 01/08, Mon.

### 問題

* 貨幣的價值是從哪裡來的呢？

### 技術

* [我是這樣拿走大家網站上的信用卡號跟密碼的](https://medium.com/@CQD/%E7%BF%BB%E8%AD%AF-%E6%88%91%E6%98%AF%E9%80%99%E6%A8%A3%E6%8B%BF%E8%B5%B0%E5%A4%A7%E5%AE%B6%E7%B6%B2%E7%AB%99%E4%B8%8A%E7%9A%84%E4%BF%A1%E7%94%A8%E5%8D%A1%E8%99%9F%E8%B7%9F%E5%AF%86%E7%A2%BC%E7%9A%84-991cb6c4631e)：很有趣的資安文章，簡單的說，拜npm之賜，任何第三方的程式碼都可能在不經意的狀況下埋入惡意程式，因為：

    * 大家裝npm就像喝開水一樣，從沒在管被裝進去的套件裡面到底有什麼。而對其它專案發github PR，裡面夾個`package.json`的更新，很可能就這樣矇混過關，讓其它裝了這個軟體包的人也跟著中。
    * 可以透過javascript偵測developer tool是否開啟，當開啟的時候便不送出惡意的request。
    * 滲透測試是有限度的，有心人隨時可以調整啟動惡意程式碼的頻率和時間。
    * github上的程式碼，不代表真正打包進npm bundle的程式碼，所以看github沒有用。
    * 編出來的bundle可以透過各種奇技淫巧來迴避`grep`之類的惡意關鍵字查詢。
    * CSP(content security policy)是有可能被繞過去的。
    
    總之，至少在關鍵的地方(個人資訊、帳密、信用卡資料...)，能夠不用第三方程式庫就盡量不要，最好是額外用一個iframe包起來，裡面不用任何的第三方程式庫。

### 趣聞

* 依然是*夜的盡頭*：夜間照明對鳥類的影響如此之大，使得鳥類可能判斷錯誤一頭撞上地面或牆壁而死亡。「...一九五四年，喬治亞州某個機場的強力光束，讓五萬隻鳥往地面俯衝而撞死。一九八一年，超過一萬隻鳥在一個週之內，就這樣撞上安大略省境內的某個煙囪。」

## 01/09, Tue.

### 趣聞

* *夜的盡頭*：讀到關於夜空的保育：人們之所以覺得光害沒什麼，是因為人們沒有察覺到夜空的可貴，而當人們意識到眼前的這片天空在將來有可能看不到的時候，就會願意去了解如何減少光害了。

## 01/10, Wed.

### 技術

* [Payment API](https://www.smashingmagazine.com/2018/01/online-purchase-payment-request-api/)：Payment API是便於網頁開發者創建金流的瀏覽器API，最近在tml5.2中發佈。它比起以前自建的表單更加安全，而且使用者只要在瀏覽器中記錄了付款方式，在所有的網站上都可以自動使用同一組資料來付款，對於使用者體驗有很大的幫助，尤其是在不便使用鍵盤輸入的行動裝置上(在行動裝置上有84%的付款被取消)。除了一般的信用卡，也可以串接行動支付如Android Pay、Apple Pay等等。目前在Chrome和Edge以及Samsung的內建瀏覽器已有實作，估計在不久的將來Firefox和Safari也會實作Payment API。

## 01/11, Thu.

### 技術

* [網頁字體的一些事](https://blog.user.today/things-about-fonts/)：今天在設定預設網頁字型時讀到的一篇短文，幾個小要點：

    * `font-family`的設定原則：比較通用的放在後面，因此英文字型要放在前面，否則會被前面中文字型的英文部分吃掉。
    * `font-family`的字型名稱盡量使用英文，這樣非中文語系的用戶也可以讀到正確的字體。例如`Microsoft JhengHei`就會比`微軟正黑體`來得好，後者只有`zh-tw`的語系才可讀懂。
    * 中文字型並不是在任何`font-size`下看起來都一樣，盡量不要用`14px`和`20px`的中文字。
* [找出所有在commit之間被修改過的檔案](https://coderwall.com/p/lz0uva/find-all-files-modified-between-commits-in-git)：`git diff --name-only <start commit> <end commit>`

## 01/12, Fri.

### 趣聞

* *夜的盡頭* (終於讀完了啊)：**Environmental Generation Amnesia**(環境世代失憶症)是由心理學家Peter H. Kahn提出的現象：人們傾向以兒童時期生長的環境作為「自然」的基準線，因此不同的世代對「自然」的認知就會有很大的分歧。隨著時間經過，人類對環境的破壞愈來愈嚴重，成長於被破壞的環境的世代，會認為目前的環境是自然的，而不會認為(在上一世代眼中被破壞殆盡)的環境有任何問題。這對於生態保育是不利的，因為這讓愈新世代的人愈對環境保護缺乏意識。要想解決這件事，就要讓孩童在兒童時期多接觸大自然。回想成長時期在野外的時候其實不多，有機會的話，也很想試著多接觸一些呢。

* [獵戶座](https://zh.wikipedia.org/wiki/%E7%8D%B5%E6%88%B6%E5%BA%A7)：說來慚愧，雖然也曾在物理系打滾兩年，我對天上的星星一無所知。今天才認得它和天狼星。「三星高照」的成語，也正是指參宿一、參宿二、參宿三構成的腰帶。

## 01/13, Sat.

### 技術

* [Don’t do it at runtime. Do it at design time.](https://medium.freecodecamp.org/dont-do-it-at-runtime-do-it-at-design-time-c4f59d1775e4)：如果可以在設計時就決定的事情，不要在執行時期才做，避免影響執行的效能。

## 01/14, Sun.

### 技術

* [scrollama](https://github.com/russellgoldenberg/scrollama)是一個便於實作滾動時畫面變化的套件，倒是有點好奇裡頭是怎麼做的...
* [PERMISSIONS ON THE WEB SUCK](https://philna.sh/blog/2018/01/08/permissions-on-the-web-suck/)和[Permiision UX](https://developers.google.com/web/fundamentals/push-notifications/permission-ux)：現在很多網站都會在頁面載入時就要求推播通知，和蓋版廣告一樣惱人。作者認為，notification本身沒有錯，有錯的是糟糕的UX，簡要的說：

    * 只在使用者真的會有興趣收到通知的情境下使用通知；例如訂單到貨、使用者喜愛的內容訂閱等等，不要在頁面載入時就要求通知，這會讓使用者在還搞不清楚狀況時被搞得很煩。
    * 除了原生的通知權限請求對話框，另外在網站上實作自己的權限請求UI，使用者在點擊了客製的UI後，再去呼叫`pushNotification`丟出原生的對話框，這樣可以確保使用者不會被嚇到。
    * 在管理界面中實作通知的開關，如此一來想要取消訂閱的用戶可以自行關閉通知。許多網站都忘了做這件事情。

    除了網站自身的UX改進，作者也提到瀏覽器也需要更好的通知設定控制，就像現在的瀏覽器可以管理如何阻擋popup一樣，而不是直接開放一個全局選項來擋住通知。否則，一般用戶多半會選擇封鎖所有的通知，而讓所有的網站都沒辦法妥善使用通知功能。
    
## 01/15, Mon.

### 技術

* [Perfect Software: And Other illusions about testing](https://www.amazon.com/Perfect-Software-Illusions-Weinberg-2008-08-29/dp/B01FIX20JW/ref=sr_1_2?ie=UTF8&qid=1516027709&sr=8-2&keywords=perfect+software+and+other+illusions+about+testing)：這本書談的是什麼是測試、為什麼要測試(以及不要測試)、為什麼測試有效(或無效)等等有關測試的文集。先前有看到[中文版](http://www.books.com.tw/products/CN11250759)就一直放在架子上。

    那麼，為什麼要測試呢？：

    * 我們想做各式各樣關於未來的決定，例如要不要吃眼前的食物(可能有毒)、要開車上國5(可能塞車)或走北宜公路(可能繞遠路)、要不要發佈網站(功能可能有問題)。 => 如果你不用做決定(女朋友的菜一定要吃完)，或者你已經下定決心(我就是不想塞車)，或者別人早就打定主意下好決定(老闆說反正明天一定要上線)，那就不需要測試了。正是因為我們想做出決定，而未來充滿不確定的風險，測試可以讓我們得到更多資訊，來避開風險得到比瞎猜要更好的決定。
    * 承上，人不是完美的，如果你覺得自己寫的程式碼一定沒問題，那也不需要測試了。
    * 承上上，測試需要成本，如果它的成本大於風險，那不測試才是理智的選擇。例如，它推遲了產品發佈的時間、耗費太多人力，等等。
    * 承上上上，測試是為了得到資訊來減少風險，如果測試得來的資訊不夠好，沒辦法減少風險，那或許真正該做的是檢討測試的過程，例如測試人員對被測試的專案了解不夠、測試的品質不好，等等。

* [The Cryptopals Crypto Challenges](https://cryptopals.com/)是[matasano security](https://www.nccgroup.trust/uk/)團隊推出的一系列密碼學問題，一共有8組問題48道題目，目的是讓開發者透過解題的過程學習密碼學的知識，了解真實世界的破密和攻擊是怎麼一回事。已經有人做過了，詳細的心得可以讀[這一篇](https://blog.pinboard.in/2013/04/the_matasano_crypto_challenges/)

## 01/17, Wed.

### 技術

* [Perfect Software: And Other illusions about testing](https://www.amazon.com/Perfect-Software-Illusions-Weinberg-2008-08-29/dp/B01FIX20JW/ref=sr_1_2?ie=UTF8&qid=1516027709&sr=8-2&keywords=perfect+software+and+other+illusions+about+testing)：

    * 測試永遠只能是情境的抽樣，不可能顧及所有可能的輸入和操作情況(那將是幾何級數等級的測試量)。因此，不存在**完美**的測試，只存在**足夠好**的測試。
    * 因此我們總是在兩件事之間掙扎：

        1. 希望測試大到可以覆蓋我們有興趣的條件。
        2. 希望測試集小到成本足以接受。

        * 問題：對於那些我們不知道藏身何處、運氣好才抓到的缺陷，要用什麼方法才能盡可能找到？

    * 人們會把測試和「搞清楚問題」、「確認嚴重性」、「解決缺陷」等等的行為混為一談，因此測試者和開發者的責任也因此變得不清楚，一個團隊需要有明確的分工避免在責任歸屬的問題上花太多時間。
    * 從測試的過程本身也可以測試出產品的好壞。例如測試人員是不是足夠了解測試流程、產品經理對測試抱有哪些錯誤的看法、等等。

* Chrome和Safari等webkit系列的瀏覽器，如果使用`background-image`和`background-size: cover`設置背景圖片時，在元素的數量很多的狀況下滾動，就會導致不斷重繪而嚴重掉幀。Firefox反而沒有這個問題。可能的解法包含：
    * 用 `<img>` 
    * `transform: translate3d(0, 0, 0)`會強迫瀏覽器額外為該元素開一層layer並使用GPU去繪製。理論上會比較快但是用太多也可能有反效果。
    * 壓縮圖片大小

## 01/17, Wed.

### 技術

* Javascript Custom Error：[SO](https://stackoverflow.com/questions/1382107/whats-a-good-way-to-extend-error-in-javascript) [另一篇](https://javascript.info/custom-errors)，還沒細讀，雖然實際上很簡單，但讓我發現我忘記原型鏈是怎麼運作的了

### 工作與生活

* [The worst distractions are the ones we love](http://blog.rescuetime.com/james-clear/)：隨手從HN摘來的訪談，幾個要點：
    * 用80%的時間使用已知的知識，用20%的時間去探索新事物。我們常常花太多時間攝取資訊而沒有實作/採取行動，這反而是一種變相的分心。特別是，有些事情唯有在實作當中才能學到。
    * 關於行為改變的動機，作者認為相較想達成的結果，對於自己的身份認知更重要。如果你認為自己是個早起的人，就比較不會允許自己賴床。(但，這有什麼根據我就不得而知了)
    * 關於決定哪些事情重要，作者提到了一個方法：

        * 列出25個你想達成的目標(可以是近期的目標也可以是長期的目標)
        * 圈出5件最重要的目標
        * 此後，將另外20個目標當作打死都不能碰的清單，只專心做圈出來的五個目標，直到達成為止才重新審視這份清單。

        這樣的做法可以幫助你聚焦在最重要的事情上，而不會被那些「有趣，但不那麼重要」的事吃掉注意力，很有趣，覺得對於常常為「要做什麼」而焦慮的人(指自己)應該是挺有用的。
    
    * 習慣除了本身的好壞，它也為你的行動選項定了錨；例如，當我們習慣從口袋拿出手機，接下來的行動選項就會變成「滑臉書」、「看信箱」而不會是「出去走走」、「讀點書」，而這可能影響後續好幾個小時怎麼過。因此，只是改變這個習慣也對生活有很大影響。

### 趣聞

* 感冒要不要吃橘子：如果咳的時候有痰，那麼吃橘子無妨；但如果咳的時候是乾的、喉嚨會癢，那麼吃橘子會讓它更癢。

## 01/18, Thu.

### 技術

* [Resource Timing API](https://developer.mozilla.org/en-US/docs/Web/API/Resource_Timing_API/Using_the_Resource_Timing_API)：瀏覽器用來測量資源載入速度的api，對於資源(如腳本、圖片、css等)的請求，從重導向、dns lookup、tcp交握到response的時間，以及傳輸的流量大小都可以由這個API取得。跨站請求預設無法用這個api取資料，但只要伺服器端在回應標頭加上`Timing-Allow-Origin: *`就同樣能夠得到數值(google、fb等提供的api script都可以測)。對於網速和流量的偵測很有用(例如在網速慢的時候載入較簡單的頁面，足夠快時則載入需要較多資源的完整頁面)。好話說完，可惜的是：
    
    * mobile和桌面的Safari到11之前不支援，而且沒有polyfill。
    * 對於`<video>`、`<audio>`的支援不好，今天實驗發現它得到的流量數值(`PerformanceEntry.transferSize`)沒有隨著載入而變化，而且最後的流量數值也不對，推測應該是因為會分段(buffer)載入的緣故。

    但對於需要作網速偵測的網站仍然是一大福音啦...
    
### 有趣的東西

* [網頁版小畫家](http://jspaint.ml/)：嘿，就是小畫家！github在[此](https://github.com/1j01/jspaint)，jquery還是很厲害的啊。
