---
title: 比較 var 與 let 的作用域
date: 2021-12-16 12:32:16
tags: JavaScript
categories:
- [JavaScript, 變數]
- [JavaScript, 作用域]
---

### var 與 let 比一比
用 let 所宣告的變數範圍又更為聚焦、比 var 更為嚴謹。

#### let 的區塊作用域
這邊以 let 在 if 條件式內宣告一個變數，並發現：
以 let 宣告的變數只能在`大括號的範圍內`被讀取，在大括號以外就無法取得變數的值。


```JS

function tellMyFavoriteSingerLately() {

  if (true) {
    let nameOfTheSinger = 'Bruno Major';
    console.log(nameOfTheSinger, '(使用let來宣告的變數，印出的位置在區塊作用域之內)');
    // 顯示 Bruno Major (使用let來宣告的變數，印出的位置在區塊作用域之內)
    }
 
    console.log(nameOfTheSinger, '(使用let來宣告的變數，印出的位置在函式作用域之內)'); 
    // nameOfTheSinger is not defined
 
   }
   
 tellMyFavoriteSingerLately();
 console.log(nameOfTheSinger, '(印出的位置在函式作用域之外)'); 
 // nameOfTheSinger is not defined

```

`備註`
if 判斷式及 for、while 迴圈皆有大括號語法。

#### var 的函式作用域
這邊以 var 在 if 條件式內宣告一個變數，並發現：
- 在 if 條件式的大括號以外，依然可以讀取得到這個用 var 宣告的變數。
- var 宣告的變數，它的作用域範圍在`整個函式之內`，而在函式之外，就讀不到值了，故顯示 `not defined`。

```JS

function tellMyFavoriteSingerLately() {

    if (true) {
      var nameOfTheSinger = 'Bruno Major';
    }

    console.log(nameOfTheSinger, '(用var宣告變數，印出的位置在函式作用域之內)'); 
		// 顯示 Bruno Major (用var來宣告的變數，印出的位置在函式作用域之內)

  }
  
tellMyFavoriteSingerLately();

console.log(nameOfTheSinger, '(印出的位置在函式作用域之外)'); 
// nameOfTheSinger is not defined

```

#### var 函式作用域的潛在問題

為什麼在 ES6 問世後，越來越少人用 var 來宣告變數？究竟原因為何？

我們或許可試著從接下來的範例來窺知一二：

假如在全域範圍(程式碼第 2 行)先以 var 宣告一個變數 myCarColor 賦予值為 ‘red’，在 if 判斷式內又再一次宣告 myCarColor 並賦予值為 ‘black’，最後印出 myCarColor 得到的結果，是 ‘black’。

由此可得知，以 var 宣告的變數，在這些有大括號 { } 的程式碼（像是 if 判斷式及 for、while 迴圈）作用域範圍不夠精確，將導致大括號內的程式碼會污染到全域變數的問題。

這就不難了解為什麼在 ES6 後，越來越多人愛用 let & const 來宣告變數了。但理解 var 的性質仍是必要的，因為總難免會遇到需要維護舊程式碼的情況。

```JS

var myCarColor = "red";

    if (true) {
        var myCarColor = "black"; 
    }
    
    console.log(myCarColor) // 顯示 black

```