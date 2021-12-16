---
title: 圖與文字同時可被搜尋到的技巧：以 h1 包覆 logo
date: 2021-12-16 11:34:20
tags: CSS
categories:
- [CSS, 背景]
- [CSS, logo]
---

當在撰寫網頁時，如果想用 h1 標籤來包覆 logo 圖片，HTML 結構會是：

```HTML
<h1>
    <a href="＃"><img src="">Karen's Coding Notes</a>
</h1>
```

而在 CSS 則可以考慮選用 background-image 來置入 logo 圖片：

```CSS

h1 a {
  background-image: url('https://reurl.cc/mLX1AM')
  background-repeat: no-repeat;
  width: 262px;
  height: 262px;
  text-decoration: none;
  color: #888;
  display: block;
}

```

此時，在瀏覽器上會顯示 logo 圖案，且在圖片之上也會顯示 a 標籤內的文字 Karen's Coding Notes：
<img src="https://i.imgur.com/EeXpz53.png">

到這裡，問題出現了，既然會用 h1 來包覆 logo 圖示，是代表 logo 被認定為這一頁的重要資訊，因為在網頁 SEO 的規則中，h1 意味著主要標題，一個網頁中也只能有一個。

若 h1 是重要資訊，而爬蟲程式卻讀不到標籤內有文字，將會判定不符合 SEO 規定，因此內容不可空白。

因此我們的目標是：
- 在網頁架構中同時有 logo 圖示與字
- 實際在頁面上又只顯示圖示而不要看見字

由於 h1 本身就是一個區塊元素，那麼便可以考慮將文字推出區塊元素的原理，來進行文字的挪移。

做法：
- 用 text-indent: 101% 將文字推出 h1 之外
- 用 overflow: hidden 將溢出區塊的部分都隱藏起來
- 用 white-space: nowrap 強制這一串文字不換行

```CSS
h1 a {
  background-image: url('https://reurl.cc/mLX1AM');
  background-repeat: no-repeat;
  width: 262px;
  height: 262px;
  text-decoration: none;
  color: #888;
  display: block;

  /*  將文字推出 <h1>  */
  text-indent: 101%;
  overflow: hidden;
  white-space: nowrap;
}
```