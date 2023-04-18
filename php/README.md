# PHP

## `usort` 帶參數排序多維陣列

範例程式碼：
```php
<?php

$arr = [
    [
        "WMS_ORD_NO" => "O20220110000002",
        "Over_Time" => "35984"
    ],
    [
        "WMS_ORD_NO" => "O20220106000013",
        "Over_Time" => "61"
    ],
    [
        "WMS_ORD_NO" => "O20220106000012",
        "Over_Time" => "36122"
    ]
];

function sorter($c = 1)
{
    return function ($a, $b) use ($c) {
        return ($a['Over_Time'] <=> $b['Over_Time']) * $c;  // Spaceship operator
    };
}

usort($arr, sorter(-1));

var_dump($arr);
```

## 函數參數的型態宣告為 `mixed` 時，必須有預設值 `null`

函數參數宣告型態為 `mixed` 時，預設值必須為 `null`  
否則會報 `Default value for parameters with a class type can only be NULL` 錯誤  
參考資料：[Default value for parameters with a class type can only be NULL - gltttt - 博客园](https://www.cnblogs.com/gltt/p/16503035.html)

## PHP CS Fixer rules

[PHP Coding Standards Fixer](https://cs.symfony.com/doc/rules/index.html)
