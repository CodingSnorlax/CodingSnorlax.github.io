---
title: 比較 var 與 let 的重複宣告
date: 2021-12-16 13:04:11
tags: JavaScript
categories:
- [JavaScript, 變數]
---

### var 與 let 比一比
var 可重複宣告同一個變數，let 不行！
所以 let 語法會替開發者自動過濾，提醒這個變數在前面已被使用過。

### var 可重複宣告變數
以 var 宣告過的變數可以再用 var 重複宣告一次，且變數也能重新賦值。

```JS

var a = 3;
var a = 10;

console.log(a); // a 的值為 10;

a = 66;
console.log(a); // a 的值為 66;

```

### let 不可重複宣告變數
let 宣告過的變數，不能再用 let 重複宣告第二次，但變數可以重新賦值。

```JS

let a = 3;
let a = 10;

console.log(a); 
// Uncaught SyntaxError: Identifier 'a' has already been declared


a = 15;
console.log(a); // a 的值為 15;

```
