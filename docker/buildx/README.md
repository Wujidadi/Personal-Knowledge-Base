# Docker Buildx

參考資料：[【 Container】使用 Buildx 建構多重系統架構的 Docker 映像檔](https://learningsky.io/building-multi-platform-docker-image/)

## 參考指令

```bash
docker buildx build --no-cache --progress=plain --push --platform linux/amd64,linux/arm64 --rm -t wujidadi/ap:3.5 -t wujidadi/ap:latest ap/3.5 2>&1 | tee $D/docker-build-ap.log
docker buildx build --no-cache --progress=plain --push --platform linux/amd64,linux/arm64 --rm -t wujidadi/nginx-php:2.5 -t wujidadi/nginx-php:latest nginx-php/2.5 2>&1 | tee $D/docker-build-np.log
docker buildx build --no-cache --progress=plain --push --platform linux/amd64,linux/arm64 --rm -t wujidadi/ubuntu-tuned:2.5 -t wujidadi/ubuntu-tuned:latest ubuntu-tuned/2.5 2>&1 | tee $D/docker-build-ut.log
```
> 注意：實際執行時，建議複製以上指令到文字編輯器中，再修改成你要的參數，否則很容易因平台配置、tag 標不對等等小問題導致做白工  
> *2023-04-01 的血淚教訓*
