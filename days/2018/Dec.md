# 2018, Dec.

## 12/12, Wed.

忙完一輪之後又重新開張啦。

### 技術

* [Tasks, microtasks, queues and schedules](https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/)

講解 task 和 microtask 的差異。

前者通常是event handler或`setTimeout` callback的觸發，後者則是`Promise`或`MutationObserver`的callback。

後者要求在沒有正在執行中的javascript時立刻執行。前者則是由瀏覽器自行安排，可以保證執行順序正確就好，因此 microtask 的執行比 task 優先。

可以配合[這篇](https://nolanlawson.com/2018/09/01/a-tour-of-javascript-timers-on-the-web/)一起服用。

## 12/13, Thu.

### 技術

* [Flow 和 TypeScript 的比較](https://jamie.build/adopting-flow-and-typescript.html)

作者大意是說，TypeScript你要做標記才能推論型別，但Flow你什麼都不標就可以推論型別抓出錯誤了。所以採用Flow可以很快的得到回報(高的型別覆蓋率(?))。

Well但這個作者本身就有參與flow的開發啊 XD。其實一直很想試著引進靜態型別，前不久有嘗試用TypeScript在一個很小的 side project 上，但當時一邊寫到有點沒勁，一邊發現跳了一些很怪的TypeScript error很懶得解，愈寫愈卡，後來就放棄寫下去了。但感覺這還是趨勢啦。如果有人用過這兩個東西可以分享一下哈哈。

## 12/16, Sun.

### VSCode

* 今天才知道原來 `ctrl` + `-` 可以跳到游標的上一個位置 XD

### 求職經驗

大概算是告一段落了，有時間可能可以寫一篇，大概幾個印象：

* 公司們對於在職求職者(我在求職信的一開始就會提到自己目前的狀況)的應對大概可以分成幾種類型：

  1. 在上班時段打來約面試，會特別詢問求職者現在方不方便接電話
  2. 在上班時段打來約面試，不在意現在是上班時段，也不會特別詢問求職者是否方便現在接聽
  3. 簡訊/email約下班後的電話時間

  個人覺得3最舒服但少見，1可以理解也最常見，2的話就有點令人覺得不太尊重

* 另外會在一開始就直接描述面試流程的還是很少，好一點的去之前問會講大概的狀況，有的則是完全不太講...從求職者的角度來說，如果在一開始就會先講面試流程，對公司的印象會加很多分。

* 通常丟求職信後的一兩個工作天內會有回覆，但過一週才回覆也是可能的，所以不用丟出去隔天沒回就焦慮起來。

* 關於能力需求和薪水、環境的一些觀察：

  * 一般前端能力要求有經驗非senior的職缺，薪資範圍大多落在 60 ~ 100w / yr 的區間。外商比起非外商，徵才資訊的薪資範圍，一個月通常要多1.5w起跳...所以英文很重要(倒)。有機會開到百萬以上的缺其實還是蠻多的。
  * `Senior` 這個詞的意思見仁見智。真實狀況嘛，有的希望有一定的年資(即使requirement沒有寫，還是直接在寄信後的一小時內被打槍 XD)、有的希望有主導過一定大小的專案、有的則只要有經驗和作品就會打來約。
  * 六到七成的前端工程師職缺的 requirement 會包含 React，然後八成也會有 Redux，剩下一到兩成是 Vue，再剩下的則是 jQuery / 只寫有使用過框架經驗佳，不知道實際上想找什麼樣的人。
  * 有在 requirement 寫到跟測試或 CI/CD 相關的公司有一些，但也沒那麼多。
  * 很多都會把 Performance Optimization 當作 plus，實際用 lighthouse 去跑他們家的網站通常都慘不忍睹。

    題外話，我還沒看過半個臺灣製造的平台/工具網站在 lighthouse 上的總分數或效能(performance)分數是綠色的 (包括我自己做過的XD) 。圖片和 JS 的 loading 都還是蠻大的，有的雖然有做 code splitting 但是 initial js bundle (gzipped) 還是五百KB起跳。

    我想，臺灣手機用戶幾乎都使用4G網路，每秒十幾到二十幾 Mbps (這是測網速的速度，實際可能再低一些些)在跑了，所以可能不會因為頻寬導致網站效能差。對比 lighthouse 考量不同國家網路環境未必會都像先進國家那麼好，多半都是用 3G Fast，大約 1Mbps 當作測量基準，一量下去就會出很多問題。產品流量如果幾乎都來自臺灣/4G網路，就不會覺得這是個問題，所以也不會那麼急著優化了。
  * 平常用心寫東西 / 貢獻開源專案，對會用心看履歷或 github 的人資 / 面試官，是有好印象的。
  * 面試的技術內容，大部分是蠻常見的(closure/prototype/this/置中的N種方法/React lifecycle method)。沒碰到過演算法題目，不過可能只是運氣好。有些問題則是會順著做過的專案往下問。

## 12/18, Tue.

### 小發現

* 今天才知道原來 ctrl + ` 是開終端機。(呆)
* 早上在 Firefox 的 network panel 找 html pretty print 功能的時候才發現 [Firefox的developer tools原來很多是用react + redux做的](https://github.com/devtools-html/)!([官方網站](https://firefox-dev.tools/))。

## 12/24, Mon.

上週三後身體一直不太舒服，眼睛腫頭昏昏鼻子過敏，可能是空氣不好的緣故吧。一週什麼也沒寫。

沒有健康的身體想做什麼都困難呀。

### firefox

最近IE Edge宣佈將要放棄他們自己開發的渲染引擎改用Chromium，加上讀了這篇[講瀏覽器多樣性重要性的文章](https://adactio.com/journal/14608)，最近把mac上面的預設瀏覽器再次移到firefox。大約一兩年前我也移過一次，當時覺得開發工具不順手，現在回來用覺得好多了。尤其DOM檢視器還會直接在節點旁邊標`event`(按一下可以顯示全部的事件處理器；chrome雖然也可以看但操作路徑長得多)或`flex`等等的小tag，挺舒服的。唯一的小缺點大概就是沒辦法和 chrome 一樣 pretty print html response 了吧。之後再來研究手機移到firefox使用上是不是一樣順...

另外發現duckduckgo搜出來的東西也比以前準確(我在firefox預設使用duckduckgo)。印象中以前只要是查技術問題多半都要切到google(**!g**)，現在這樣的狀況有改善一些。不過在找不到東西的時候還是難免會想「duckduckgo找不到，google應該會有」，唉唉。

### 排版

* [簡單做好中文排版](https://wanderer.tw/%E7%B0%A1%E5%96%AE%E5%81%9A%E5%A5%BD%E4%B8%AD%E6%96%87%E6%8E%92%E7%89%88/)講了很多有趣的小細節，像是：

  * 怎麼區分繁體和簡體字型
  * 中台港日的系統字差異
  * 中英混排的時候怎麼對齊兩邊又不影響字距



