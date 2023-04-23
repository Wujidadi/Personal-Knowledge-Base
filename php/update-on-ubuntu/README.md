# 更新 Ubuntu 上的 PHP 套件庫並更新

> 以 PHP 8.2 為例

參考資料：[How To Install PHP 8.2 on Ubuntu 22.04|20.04|18.04 | ComputingForGeeks](https://computingforgeeks.com/how-to-install-php-8-2-on-ubuntu/)

1. `add-apt-repository -y ppa:ondrej/php`
2. `apt update`
3. `apt install -y php8.2 php8.2-{bcmath,fpm,xml,mysql,zip,intl,ldap,gd,cli,bz2,curl,mbstring,pgsql,opcache,soap,cgi}`
