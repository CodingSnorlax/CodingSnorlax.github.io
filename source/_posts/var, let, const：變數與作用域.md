---
title: 淺談變數與它們的作用域
date: 2021-12-16 12:04:40
tags: JavaScript
categories:
- [JavaScript, 變數]
- [JavaScript, 作用域]
---

在探討這三者的差異之前，應該要先來談一下，var, let, 和 const 的用途：

當需要電腦協助儲存一筆資料到記憶體的時候，要透過 var, let 或 const 來宣告 (declare) 變數，將資料存到變數裡，變數則會儲存在電腦記憶體，往後再呼叫這個變數，便能拿到這筆資料。

假設要告訴電腦，Karen 有 1 杯茶，Roger 有 3 杯茶，可以怎麼敘述呢？
透過 let 就是在宣告 karenHasTea (變數)，並賦予變數的值為 1。
`註：這邊的等號是賦值運算子的一種。`

```JS

let karenHasTea = 1;
let rogerHasTea = 3;

```

而當一個變數被宣告的同時，也會有一個作用域跟著這個變數，於是你可能又想問，什麼是「作用域 (variable scope) 」？

簡單來說，作用域就是一個變數能夠被存取到的範圍，而這範圍又分為全域作用域和區域作用域。
但是，全域作用域和區域作用域，到底又代表什麼意思呢？我們應該如何理解這兩種區域作用域的範圍？

### 全域作用域 (Global Scope)

前面提到，我們透過 var, let 或 const 來宣告一個變數。
但是假如不透過它們「宣告」變數，直接對變數賦予一個值，這是可以的嗎？
（是的，記者現在實地為您測試…）
假設今天有一個變數為 myName，我賦予它一個字串值 'Karen'：

```JS

myName = 'Karen';

```

然後我再度到 chrome 的 dev tool 呼叫 myName 這個變數，主控台顯示：

<img src="https://miro.medium.com/max/2400/1*I19M8UNGudNcDo--1Gz3AA.png">

由此可知，不透過 var, let 或 const 來宣告，myName 也是可以寫入資料的，只是這時沒有被宣告，它存在的範圍會是在「全域作用域」，既無法確認它來自哪裡，它可以被存取的範圍也有模糊不清的問題(後續將會舉例說明)，未被宣告過的 myName 是一個「全域屬性」，為避免發生遺憾…，

### 請一定要記得宣告你的變數！

宣告變數，像是這樣：

```JS

let myName = 'Karen';

```

被宣告過的變數，可以想像成是在幫一個變數劃出存取範圍。當變數是在函式之外被宣告，它的作用範圍就是屬於全域作用域；相反地，在函式之內被宣告的變數，它的存取範圍就是在區域作用域，而區域作用域又可分為`函式作用域`和`區塊作用域`。
那你可能又會想問，為什麼區域作用域內，又要再分函式作用域和區塊作用域？
以下將開始說明。

### 前情提要：JS 的前世今生
在 JavaScript ES6 出現之前，沒有 let 和 const，只能靠 var 來宣告變數，而 var 宣告的變數就是在「函式作用域」，直到 ES6 之後有了 let 和 const，「區塊作用域」才應運而生。

所以，函式作用域是什麼？它和區塊作用域又有何差別？

### 區域作用域 (Local Scope)
首先，要先來解釋何謂區域作用域？
簡單來說，區域作用域是相對於全域作用域的概念，只要不是在全域的範圍內的，都是屬於區域作用域，像是 function 函式、if 判斷式、for 和 else 的迴圈內的範圍，都是屬於區域作用域，而 JavaScript 的區域作用域又可分為函式作用域與區塊作用域。

#### 函式作用域 (Function Scope)
函式作用域的範圍是在函式之內。

```JS

function tellMyFavoriteSingerLately() {

let myFavoriteSingerLately = 'Bruno Major';

console.log('在函式作用域內的字串', myFavoriteSingerLately); // 顯示 'Bruno Major'

}

tellMyFavoriteSingerLately();

console.log('在函式作用域外的字串', myFavoriteSingerLately); 
// 顯示 myFavoriteSingerLately is not defined.

```

為何函式外的 console.log 會印出 not defined 呢？
因為 myFavoriteSingerLately 這個變數在函式內被宣告後，它的作用域僅限於函式內，在函式外的地方就讀取不到這個變數。

`備註`
undefined 與 is not defined 是不同的，not defined 所指的是這個變數在這個區域是不存在的，根本讀取不到；undefined 則是指出在記憶體中有這一筆變數資料，只是尚未被賦予值。

#### 區塊作用域 (Block Scope)
區塊作用域的範圍是在大括號 { } 之內。

```JS

{
   let myFavoriteSingerLately = 'Bruno Major';
}

console.log(myFavoriteSingerLately);  // 顯示 myFavoriteSingerLately is not defined.

```

為什麼在大括號外的 console.log 會印出 not defined 呢？
因為 myFavoriteSingerLately 這個變數在大括號內被宣告後，它的作用域僅限於大括號內，在大括號以外的地方就讀取不到這個變數。

透過以 let 宣告變數在函式作用域與區塊作用域的例子，解釋了這兩個作用域的涵蓋範圍。在理解了這兩種作用域的範圍後，將在下一篇更進一步探討，var 和 let 的差異。
