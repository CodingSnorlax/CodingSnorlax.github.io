---
title: 認識 const 的特性
date: 2021-12-16 13:34:11
tags: JavaScript
categories:
- [JavaScript, 變數]
- [JavaScript, 作用域]
---

<img src="https://miro.medium.com/max/1400/0*g1_rI1aLr_8A20xB">

### const 的使用時機
用 const 來宣告的變數，被稱為「常數 (constant) 」，常數只可被讀取，但不允許更動。

那什麼時機會用到 const 來宣告一個變數呢？例如：天上有一個太陽，太陽的數量是恆常不變的、或是一筆商品的定價，或任何你在開發上不希望被更動的資料等。

### const 宣告的變數特性

#### 區塊作用域
const 與 let 一樣，兩者所宣告的變數都是存在於區塊作用域，因此在 { } 外，將讀取不到值。

```JS

{
   const today = '2021/10/13';
}

console.log(today);  // 顯示 today is not defined.

```
#### 不可重複宣告同一個變數及重新賦予值

const 宣告過的變數，除了不可再一次用 const 重複宣告，也不可再重新賦予值。

當以 const 宣告 sunNum 這個變數，並賦予值為 1，又要再一次用 const 宣告這個變數的時候，主控台回傳告知 sunNum 這個變數已經被宣告過了。

接下來，如果要將 sunNum 重新賦予值為 100 的時候，也會得到主控台回傳「賦予值到常數」這個動作的報錯。


```JS

const sunNum = 1;
const sunNum = 2; 
// Uncaught SyntaxError: Identifier 'sunNum' has already been declared


sunNum = 100; 
// Uncaught TypeError: Assignment to constant variable.

```
<br>
<br>

### 參考資料與圖片出處：
- JavaScript 變數作用域 Variable Scope
- JavaScript 那個 let, const, var 到底差在哪？
- 語法與型別
- [JS學徒特訓班] JavaScript ES6 : var, let, const 差異
- Why don’t we use var anymore?
- Var, Let, and Const — What’s the Difference?
- How JavaScript variable scoping is just like multiple levels of government
- [JavaScript] Javascript 的作用域 (Scope) 與範圍鏈 (Scope Chain)：往外找
- 02 var、let、const 與 ES6 簡介
- 我知道你懂 hoisting，可是你了解到多深？
- Photo credit to David Monje on Unsplash

