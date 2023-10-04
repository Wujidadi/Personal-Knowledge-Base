# `brew services` 指令

> 參考資料：[homebrew/services](http://blog.fpliu.com/it/software/HomeBrew/repo/homebrew-services)

| 命令                                     | 說明                                 |
| ---------------------------------------- | ------------------------------------ |
| `[sudo] brew services list`              | 列出當前使用者的所有服務             |
| `[sudo] brew services run <formula>`     | 設置為非開機啟動的服務，並執行該服務 |
| `[sudo] brew services start <formula>`   | 設置為開機啟動的服務，並執行該服務   |
| `[sudo] brew services stop <formula>`    | 停止服務                             |
| `[sudo] brew services restart <formula>` | 設置為開機啟動的服務，並重啟該服務   |
| `[sudo] brew services cleanup`           | 刪除無用的服務                       |
