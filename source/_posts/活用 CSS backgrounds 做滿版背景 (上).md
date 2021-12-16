---
title: 活用 CSS backgrounds 做滿版背景 (上)
date: 2021-12-16 11:49:43
tags: CSS
categories:
- [CSS, 背景]
---

設計網頁版型的時候，經常會用一張滿版圖片來作為主視覺，以 CSS backgrounds 加入背景圖的方式來進行。

最常用來做滿版主視覺的屬性有：
- `background-color`
- `background-image`
- `background-repeat`
- `background-position`
- `background-size`
- `background`

#### 使用 background-repeat 節省背景圖檔容量

首先，就先來談談，background-image, background-repeat, 與  background-color 的搭配應用，以及該如何節省背景圖檔的容量！

在製作素面背景的時候，假設有一張背景圖的大小為寬 1200 px、高 675 px，當這張圖整張上傳的時候，檔案大小為 154KB。乍看一張背景圖檔不過是154 KB 不是特別有感，但如果你的網頁有300人次瀏覽，那麼就是46MB的流量了，長期累積下來也相當驚人。

<img src="https://miro.medium.com/max/700/1*88f2yr8WT2x1v4Ct0ZImAA.png">

當遇到這樣的情況，建議可以先在 PS 用切片工具把背景圖切一小段下來，經過切圖之後的背景圖檔，只剩下一小塊約 21KB 左右的檔案大小，接著再使用這張裁切後的小圖，就同樣能達到原先直接用 background-image 置入一整張大圖的效果，節省流量！


<img src="https://miro.medium.com/max/283/1*qRIO5W5JGKW-eLTHGQi-QA.png">

不過，當容器內有文字，版面自動向下擴充時，由於背景的顏色有漸層，會產生畫面中顏色不連續的情形。

<img src="https://miro.medium.com/max/700/1*T7P1md_1tWaM1IOZUVn1VQ.png">

不過，當容器內有文字，版面自動向下擴充時，由於背景的顏色有漸層，會產生畫面中顏色不連續的情形。所以這一張裁切後的小圖，還需搭配 background-repeat: repeat-x，以 X 軸重複顯示的方式來填滿視窗的背景，另外同時也要記得吸取不連續段落之間最下方的顏色，作為 background-color 背景色，就能解決顏色不連貫的問題了！

```CSS
.box{
    width: 1200px;
    background-image: url('./img/bg2.png');
    background-repeat: repeat-x;
    background-color: #3fa9f5;
}
```

## 總結：
### 善用 background-repeat 節省檔案大小
用背景圖進行版面設計時，必須考量到網頁效率問題，畢竟一張大的圖檔是很吃容量的，能預先考慮到背景圖該如何裁切能使其容量最精簡，對使用者來說，瀏覽網頁效率也能提高：
background-repeat: no-repeat; 大張圖檔，只顯示一次
background-repeat: repeat-x; 以X軸為基準重複
background-repeat: repeat-y; 以Y軸為基準重複

### 交互運用 background-color 與 background-image
當高度沒有寫固定，背景會隨容器中的內容增加而自動向下延伸，導致背景顏色出現不連貫時，可以填入 background-color 作為容器中背景圖的延伸，以求整體版面一致性。


