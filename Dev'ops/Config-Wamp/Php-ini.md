## Configuration de l'environnement PHP

Xdebug

    [xdebug]
    zend_extension="c:/wamp64/bin/php/php7.4.0/zend_ext/php_xdebug-2.8.0-7.4-vc15-x86_64.dll"
    xdebug.remote_enable = off
    xdebug.profiler_enable = off
    xdebug.profiler_enable_trigger = Off
    xdebug.profiler_output_name = cachegrind.out.%t.%p
    xdebug.profiler_output_dir ="c:/wamp64/tmp"
    xdebug.show_local_vars=0

Blackfire

    [blackfire]
    ;extension=C:\wamp64\bin\php\php7.3.12\ext\blackfire-php-windows_x64-php-73_nts.dll
    extension=C:\wamp64\bin\php\php7.3.12\ext\blackfire-php-windows_x64-php-73.dll
    blackfire.agent_timeout = 0.25

    ;extension=blackfire.dll
    ;blackfire.agent_timeout = 0.25
    blackfire.log_file = /tmp/blackfire.log
    blackfire.log_level = 4
    BLACKFIRE_AGENT_SOCKET="tcp://127.0.0.1:8307"

OPcache

    [opcache]
    zend_extension="c:/wamp64/bin/php/php7.4.0/ext/php_opcache.dll"
    ; Determines if Zend OPCache is enabled
    ;opcache.enable=1


SQLite
::
    [sqllite]
    extension=php_pdo_sqlite.dll
    extension=php_sqlite3.dll
ou ( selon version )

    [sqlite3]
    ; Directory pointing to SQLite3 extensions
    ; http://php.net/sqlite3.extension-dir
    ;sqlite3.extension_dir =

PostgreSQL

    [PostgreSQL]
    ; Allow or prevent persistent links.
    ; http://php.net/pgsql.allow-persistent
    pgsql.allow_persistent = On


Mail function

    [mail function]
    ; For Win32 only.
    ; http://php.net/smtp
    SMTP = localhost
    ; http://php.net/smtp-port
    smtp_port = 25
