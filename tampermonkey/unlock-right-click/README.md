# 破解鎖右鍵及防拷貝

## 一般

範例為[哩哔轻小说](https://tw.linovelib.com)

```javascript
// ==UserScript==
// @name         Enable Select, Copy and Context Memu - linovelib
// @namespace    http://tampermonkey.net/
// @version      0.2
// @description  Enable select in linovelib (哩哔轻小说)
// @author       Wujidadi
// @match        https://tw.linovelib.com/novel/*
// @grant        none
// ==/UserScript==

(function() {
    'use strict';
    const eventList = ['onselectstart', 'oncopy', 'oncontextmenu'];
    eventList.forEach(event => {
        document[event] = function() {
            return true;
        };
    });
})();
```

### 複雜

範例為[起點中文網](https://www.qidian.com/)  
也適用於[一卡通交易紀錄查詢頁面](https://www.i-pass.com.tw/Inquire/Index)

```javascript
// ==UserScript==
// @name         Enable Select, Copy and Context Memu - Qidian
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  Enable select in Qidian (起点)
// @author       Wujidadi
// @match        https://read.qidian.com/chapter/*
// @match        https://vipreader.qidian.com/chapter/*
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

    /* 須恢復正常功能的事件類別 */
    const eventList = ['selectstart', 'copy', 'contextmenu'];

    /* 各事件恢復正常功能的方法 */
    const enableSelectCopyAndContextMenu = function(e) {
        e.stopImmediatePropagation();
        return true;
    };

    /* 等待官方 JS 就緒的毫秒數 */
    const waitTime = 3000;

    /* 主要程式碼 */
    setTimeout(() => {
        /* 清除所有 interval */
        const intervalId = window.setInterval(function(){}, Number.MAX_SAFE_INTEGER);
        for (let i = 1; i < intervalId; i++) {
            window.clearInterval(i);
        }

        /* 指派方法給各類事件使之恢復正常功能 */
        eventList.forEach(e => {
            document.addEventListener(e, enableSelectCopyAndContextMenu, true);
        });
    }, waitTime);
})();
```
