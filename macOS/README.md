# macOS

## 解除與刪除「已鎖定」檔案

有些「已鎖定」檔案/應用程式圖示左下角會顯示一個鎖頭，這時 `右鍵 → 取得資訊 → 一般 → 已鎖定` 的勾勾也無法取消  
必須用以下指令來解除鎖定 (以電腦版 FortiClient 為例)：

```bash
/bin/ls -dleO@ /Applications/FortiClient.app
sudo /usr/bin/chflags -R noschg /Applications/FortiClient.app
```

參考資料：[mac电脑删除软件时提示“不能完成此操作，xxx已锁定”的解决方案 - 掘金](https://juejin.cn/post/7100820901444190216)
> 2023-04-15 在 M2 Max 上安裝 FortiClient 處理公事時誤裝電腦版，要刪除時遇到此問題刪不掉，上網搜尋到這篇
