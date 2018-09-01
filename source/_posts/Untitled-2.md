---
title: 閉包與範圍鍊
tags: JS
notebook: 10前端筆記
---

# 要了解閉包之前要了解何謂「範圍鍊」

內層的 function inner 可以讀取外層宣告的變數，但外層的 outer function 存取不到內層宣告的變數。 若是在自己層級找不到就會一層一層往外找，直到 Global 為止。

>這種行為，我們就稱之為「範圍鏈」(Scope Chain)。

```JS
function outer() {
    // 把 var 拿掉
    b = a * 2;

    function inner(c) {
    console.log(a, b, c);
    }

  inner(b * 3);
}

var a = 1;
outer(a);
```

由於範圍鏈的關係，若是沒有宣告變數 b 則會沿著範圍鏈一路往外尋找這個變數的定義，於是最後就在 global 層生成一個變數。

---

>有個觀念很重要，範圍鏈是在函式被定義的當下決定的，不是在被呼叫的時候決定。

這個就是閉包的核心概念。