# docker_1
1 mkdir nextcloud && cd nextcloud
2 git clone https://github.com/truedevops/docker_1.git
3 docker-compose up -d
4 wget https://download.nextcloud.com/server/releases/nextcloud-13.0.1.zip
5 apt install zip - Если есть zip - пропускаем этот шаг
6 unzip nextcloud-13.0.1.zip
7 mv nextcloud php-code/
8 chown -R www-data: php-code
9 Заходим в браузер ip-address хост машины :88
10 настройка через WEB admin(LOG/PASS) каталог data по пути /var/www/html/data  База MySQL/MariaDB
Пользователь базы данных: user
Пароль базы данных: password
Название Базі данных: db
Путь к базе: mysql:3306
Завершить установку.
После установки нужно перезалогинится.

настройка кэширующего сервера memcached -> vim php-code/nextcloud/config/config.php

нужно вставить после строчки  array (
    0 => 'ххх.ххх.хх.х:88',
  ),

'memcache.local' => '\\OC\\Memcache\\Memcached',
  'memcached_servers' =>
  array (
    0 =>
    array (
      0 => 'memcached',
      1 => 11211,
    ),
  ),
