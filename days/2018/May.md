# 2018, May.

## 05/01, Tue.

### 技術

* [用jquery中途修改react render出來的node，再讓react做新的render的話會出問題。jquery最好只在空的node上做事](https://github.com/facebook/react/issues/6802)

## 05/05, Sat.

### 技術

* [WTF is jsx](https://jasonformat.com/wtf-is-jsx/)：其實大家都知道就是`React.createElement` ，內文有寫到一個簡單的實作 (實際上可以看 [hyperscript](https://github.com/hyperhype/hyperscript) ) 。裡面還有稍微提到一下 JSX 比起其它 template 語言有什麼不同，不用再額外去搞那些 for loop 語法和擔心髒髒的 `eval` 是件好事啊。

## 05/07, Mon.

### 技術

* `git diff --name-status [SHA1] [SHA2]` 可以一眼看出的看修改的檔名和狀態。 `git diff --stat [SHA1] [SHA2]` 則會顯示像 `git pull` 時顯示的檔案列表和行數，在想掃過協作者修改過哪些檔案的時候比較好用。