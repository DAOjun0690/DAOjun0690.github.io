---
title: 前端 Front End
date: 2020-09-16 17:55:59
tags:
 - 程式語言
 - 前端
 - JavaScript
---
* AJAX
<!-- More -->
### AJAX
1. 甚麼是Ajax
>非同步 JavaScript 及 XML（Asynchronous JavaScript and XML，AJAX） 並不能稱做是種「技術」，而是 2005 年時由 Jesse James Garrett 所發明的術語，描述一種使用數個既有技術的「新」方法。這些技術包括 HTML 或 XHTML、層疊樣式表、JavaScript、文件物件模型、XML、XSLT 以及最重要的 XMLHttpRequest 物件。
當這些技術被結合在 Ajax 模型中，Web 應用程式便能快速、即時更動介面及內容，不需要重新讀取整個網頁，讓程式更快回應使用者的操作。

重點在於後面的文字，可與伺服器進行非同步更新，不需要重新載入整個網頁
**每次要吃資料都要重載很多次**
-JavaScript
-HTTP
是我們會使用的東西

• XMLHttpRequest (是JavaScript Object), 後臺發送HTTP請求
• JavaScript DOM , 修改HTML來展示資訊
• HTTP請求和伺服器交互

規劃一個網頁含有AJAX技術
最常見的例子就是 用戶註冊 驗證信箱，驗證信箱或用戶名是否有被重複使用，不用等到全部填完資料才能驗證

### print
https://www.sitepoint.com/delay-sleep-pause-wait/
```JavaScript=
# 以下程式印出的順序：
console.log("Hello");
setTimeout(() => { console.log("World!"); }, 2000);
console.log("Goodbye!");
/* ANS:
Hello
Goodbye!
World!
 */
```
