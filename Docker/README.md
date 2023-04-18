# Docker

## 容器建立後不斷重啟

Docker Compose 拉起來的容器，若初始命令只是 `bash`、`zsh` 之類加載 shell 的指令，  
會在建立後立刻 `exited with code 0`，不是程式也不是設定出錯，所以沒有任何 log，會 debug 到死  
必須在 command 中給它一個永遠在背景執行的指令，才會一直 run 下去，如 `tail -f /dev/null`  
當然當我們的服務寫好，就可以直接 run 這個服務而不必執行上述的背景指令了（前提是你的服務也要是永遠執行的）  
參考資料：[Running Docker Containers Indefinitely#Never Ending Commands](https://www.baeldung.com/ops/running-docker-containers-indefinitely#1-never-ending-commands)

## Docker Buildx

參考資料：[【 Container】使用 Buildx 建構多重系統架構的 Docker 映像檔](https://learningsky.io/building-multi-platform-docker-image/)

### 參考指令

```bash
docker buildx build --no-cache --progress=plain --output type=docker --platform linux/amd64,linux/arm64 --rm -t wujidadi/ap:3.4 -t wujidadi/ap:latest ap/3.4 2>&1 | tee $D/docker-build-ap.log
docker buildx build --no-cache --progress=plain --output type=docker --platform linux/amd64,linux/arm64 --rm -t wujidadi/nginx-php:2.4 -t wujidadi/nginx-php:latest nginx-php/2.4 2>&1 | tee $D/docker-build-np.log
docker buildx build --no-cache --progress=plain --output type=docker --platform linux/amd64,linux/arm64 --rm -t wujidadi/ubuntu-tuned:2.4 -t wujidadi/ubuntu-tuned:latest ubuntu-tuned/2.4 2>&1 | tee $D/docker-build-ut.log
```
> 注意：實際執行時，建議複製以上指令到文字編輯器中，再修改成你要的參數，否則很容易因平台配置、tag 標不對等等小問題導致做白工  
> *2023-04-01 的血淚教訓*
