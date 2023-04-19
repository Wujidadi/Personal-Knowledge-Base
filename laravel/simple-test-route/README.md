# 簡單的測試路由

寫在 `routes/web.php`：
```php
<?php

Route::get('dev/test', function() {
    $headers = [
        'Content-Type' => 'application/json; charset=UTF-8'
    ];
    $httpStatus = 200;
    $content = collect([
        'name' => 'dev',
        'status' => 'testing',
        'array' => [
            'one' => 1,
            'two' => 2
        ]
    ]);
    return response($content, $httpStatus)->withHeaders($headers);
});
```
