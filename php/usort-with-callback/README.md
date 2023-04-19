# `usort` 帶參數排序多維陣列

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
