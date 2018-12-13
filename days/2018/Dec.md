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