# PHPUnit 產生覆蓋率報告

> 2023-07-21 感謝 Matt Tang 提供

* 須安裝有 php-xdebug
* 以此指令執行，就不必在 PHP 設定檔中寫死 `xdebug.mode=coverage` 了

```
XDEBUG_MODE=coverage ./vendor/bin/phpunit --coverage-html docs/build/
```
