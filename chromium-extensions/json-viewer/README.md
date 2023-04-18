# JSON Viewer

[GitHub](https://github.com/tulios/json-viewer)  
[chrome 線上應用程式商店](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh)

* **Theme:** monokai
* **Add-ons**:
  ```json
  {
    "prependHeader": false,
    "maxJsonSize": 400,
    "alwaysFold": false,
    "alwaysRenderAllContent": false,
    "sortKeys": false,
    "clickableUrls": true,
    "wrapLinkWithAnchorTag": false,
    "openLinksInNewWindow": true,
    "autoHighlight": true
  }
  ```
* **Structure:**
  ```json
  {
    "readOnly": true,
    "lineNumbers": false,
    "lineWrapping": true,
    "foldGutter": true,
    "tabSize": 4,
    "indentCStyle": false,
    "showArraySize": false
  }
  ```
* **Custom Style:**
  ```css
  .CodeMirror {
    font-family: monospace;
    font-size: 13px;
    line-height: 1.5em;
  }
  ```
