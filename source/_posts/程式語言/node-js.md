---
title: node.js
date: 2020-09-17 14:43:07
tags:
 - 程式語言
 - 前端
 - node.js
---
## Node.js
<!-- more -->

Node.js 是什麼呢？根據官網的說法：
| `Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine.`

「runtime」 指的是執行環境，就如同網頁上的 JavaScript 是在瀏覽器的 JavaScript 引擎上執行，Node.js 就是一個能執行 JavaScript 的環境，而 V8 則是主流瀏覽器 - Google Chrome 的 JavaScript 引擎，負責解析、執行 JavaScript，也就是負責實踐 ECMAScript 規範中定義的部份；另外，V8 是開源的專案，有興趣的讀者可以參照 Google Git - V8。

以Node.js解釋Concurrency / Parallelism：
伺服器服務時常卡在I/O存取（檔案上傳、檔案存取)，如果等待I/O的時間過長，伺服器就無法服務其他請求，因此Node.js利用事件驅動，非堵塞I/O模型實踐了良好的共發性：使用者在上傳檔案時，不用等到上傳完成，中間可以去做其他事情，例如臨時決定又要再上傳另一個檔案，或填寫表格中的其他欄位。但由於Node.js仍然本質上屬於單線程，我們可以透過ngnix這種負載平衡工具，實現並行性，也就是利用水平擴展的方式，提高服務品質。
