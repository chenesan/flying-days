# 2018, Dec.

## 12/12, Wed.

忙完一輪之後又重新開張啦。

### 技術

* [Tasks, microtasks, queues and schedules](https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/)

講解 task 和 microtask 的差異。

前者通常是event handler或`setTimeout` callback的觸發，後者則是`Promise`或`MutationObserver`的callback。

後者要求在沒有正在執行中的javascript時立刻執行。前者則是由瀏覽器自行安排，可以保證執行順序正確就好，因此 microtask 的執行比 task 優先。

可以配合[這篇](https://nolanlawson.com/2018/09/01/a-tour-of-javascript-timers-on-the-web/)一起服用。