# 函數參數的型態宣告為 `mixed` 時，必須有預設值 `null`

函數參數宣告型態為 `mixed` 時，預設值必須為 `null`  
否則會報 `Default value for parameters with a class type can only be NULL` 錯誤  
參考資料：[Default value for parameters with a class type can only be NULL - gltttt - 博客园](https://www.cnblogs.com/gltt/p/16503035.html)

## PHP CS Fixer rules

[PHP Coding Standards Fixer](https://cs.symfony.com/doc/rules/index.html)
