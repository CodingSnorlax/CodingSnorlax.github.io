---
title: 比較 var 與 let 的 hoisting
date: 2021-12-16 13:11:28
tags: JavaScript
categories:
- [JavaScript, 變數與記憶體]
- [JavaScript, hoisting]
---

在開始講 var 與 let 的差異之前，要先了解一下，變數宣告的過程 — — 變數的資料究竟要如何儲存到記憶體？

### 變數與記憶體的原理
賦予變數一個新的值，就會產生一個記憶體空間存放，要改變變數的值，必須要透過 =（一個等號）來賦予值。

`備註` 宣告一個變數，但未賦予值，也會產生一個記憶體空間。

#### 宣告變數，但不賦予值

當用 var 宣告一個變數 myFavoriteSinger 但不給它值，在變數宣告的同時電腦也會開啟一個記憶體空間，只是這時還沒有被賦予值，記憶體空間內的資料會是 undefined（如下所示）。

<img src="https://miro.medium.com/max/700/0*Vk-CV3i_MfI7BzxX.png">

#### 宣告變數後，賦予值
然而，當變數被賦予值 var myFavoriteSinger = ‘Bruno Major’，此時變數就會轉向另一個記憶體儲存 ‘Bruno Major’ 這一個字串（如下所示）。

<img src="https://miro.medium.com/max/700/0*sSoU6DZGC2v5OvwZ.png">


### 何謂「抬升(hoisting) 」？
看完了變數宣告的過程，進入正題，何謂「抬升(hoisting) 」？

#### var & undefined
一般來說，程式碼的讀取順序會是由第一行到最後一行，但假設今天在第六行用 var 宣告一個變數 a，不過從第二行就要求印出這個變數 a 的值，結果卻會顯示為 undefined，代表這個變數 a 已被讀取到，只是此時它的值為 undefined。

#### let & 未初始化
同樣地，在第七行用 let 宣告一個變數 b，但在第三行就要先印出 b 的值，得到的結果卻與 var 宣告的變數 a 不同，會顯示「在 ‘b’ 初始化之前無法讀取到 ‘b’ 的值」。

```JS

console.log(a); //undefined
console.log(b); // Uncaught ReferenceError: Cannot access 'b' before initialization

var a = 30;
var a;
let b = 50; 

```
#### 結論
其實不管是用 let 或 var 來宣告的變數都有「抬升」，只是 a 會印出 undefined，而用 let 宣告的變數 b 會顯示「在 ‘b’ 初始化之前無法讀取到 ‘b’ 的值。」

特別值得注意的地方是，被 var 宣告的「變數 a 」有抬升，但變數 a 的值是沒有一起被抬升的，因為第二行的console.log(a) 並沒有印出在第五行 a 賦予的值 (30)。

`註1` 這邊若有想要更深入了解有關抬升的概念，可參閱：我知道你懂 hoisting，可是你了解到多深？
`註2` function 也有 hoisting 的狀況。