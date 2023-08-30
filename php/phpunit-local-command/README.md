# 本地使用 PHPUnit 指令

```
XDEBUG_MODE=off ./vendor/bin/phpunit --coverage-text -d zend.enable_gc=0`
```

說明：
* `XDEBUG_MODE=off`: 關閉 Xdebug (若未安裝 Xdebug 可忽略)
* `--coverage-text`: 輸出測試覆蓋率純文字報告
* `-d zend.enable_gc=0`: 關閉 PHP 垃圾回收

更簡化版本：本地測試時執行以下指令即可：
```
XDEBUG_MODE=off ./vendor/bin/phpunit
```
