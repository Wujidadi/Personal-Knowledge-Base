# 將 HTML 實體轉換回可讀字元

```javascript
/**
 * 將 HTML 實體轉換回可讀字元
 *
 * @param  {string}  str  包含 HTML 實體的字串
 * @return {string}       HTML 實體被轉換回可讀字元的字串
 */
function unescapeHtmlEntities(str) {
    const doc = new DOMParser().parseFromString(str, 'text/html');
    return doc.documentElement.textContent;
}
```
