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
