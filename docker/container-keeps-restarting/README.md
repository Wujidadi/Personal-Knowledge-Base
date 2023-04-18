# 容器建立後不斷重啟

Docker Compose 拉起來的容器，若初始命令只是 `bash`、`zsh` 之類加載 shell 的指令，  
會在建立後立刻 `exited with code 0`，不是程式也不是設定出錯，所以沒有任何 log，會 debug 到死  
必須在 command 中給它一個永遠在背景執行的指令，才會一直 run 下去，如 `tail -f /dev/null`  
當然當我們的服務寫好，就可以直接 run 這個服務而不必執行上述的背景指令了（前提是你的服務也要是永遠執行的）  
參考資料：[Running Docker Containers Indefinitely#Never Ending Commands](https://www.baeldung.com/ops/running-docker-containers-indefinitely#1-never-ending-commands)
