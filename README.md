e107mediawiki
=============

Плагин добавляющий возможность входа в MediaWiki с использованием БД e107 v1

Установка
---------

Архив распаковать в /папка_с_вики/extensions/

В файл LocalSettings.php добавить

```php
// Отключение регистрации
$wgGroupPermissions['*']['createaccount'] = false; 


// Отключение возможности редактирования статей гостями
$wgGroupPermissions['*']['edit'] = false;
$wgGroupPermissions['*']['createpage'] = false;
$wgGroupPermissions['*']['createtalk'] = false;


// Настройки плагина
global $wgAuthE107_MySQL_Host, $wgAuthE107_MySQL_Username, $wgAuthE107_MySQL_Password, $wgAuthE107_MySQL_Database, $wgAuthE107_TablePrefix;

$wgAuthE107_MySQL_Host		= 'localhost'; // E107 MySQL Host Name.
$wgAuthE107_MySQL_Username	= 'your_mysql_user'; // E107 MySQL Username.
$wgAuthE107_MySQL_Password	= 'your_mysql_password'; // E107 MySQL Password.
$wgAuthE107_MySQL_Database	= 'your_mysql_table'; // E107 MySQL Database Name.
$wgAuthE107_TablePrefix		= 'e107_'; // E107 MySQL Database TablePrefix.
$wgAuthE107_ForumMsg		= 300; // Минимальное кол-во сообщений на форуме е107 для регистрации
$wgAuthE107_Class			= 'Wiki'; // Класс пользователей для которых регистрация доступна независимо от сообщений форума

// Подключение плагина
require_once("$IP/extensions/AuthE107/AuthE107.php");
$wgAuth = new AuthE107();
```

По умолчанию для входа пользователь должен быть не забаненным и иметь 300 сообщений на форуме, либо быть администратором, либо быть в группе Wiki.