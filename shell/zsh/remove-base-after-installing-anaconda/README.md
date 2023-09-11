# 安裝 Anaconda 後出現 `(bash)` 字樣的解決方法

> 參考資料：[安装conda后终端出现的(base)字样去除方法](https://www.jianshu.com/p/6cdc9713c4ed)

編輯 `~/.condarc` (不存在可自行創建)，在檔案末尾加入以下內容，然後重啟終端：

```shell
changeps1: False
```
