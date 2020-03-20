Configuration de l'environnement PHP 
====================================



Xdebug
::
    [xdebug]
    zend_extension="c:/wamp64/bin/php/php7.4.0/zend_ext/php_xdebug-2.8.0-7.4-vc15-x86_64.dll"
    xdebug.remote_enable = off
    xdebug.profiler_enable = off
    xdebug.profiler_enable_trigger = Off
    xdebug.profiler_output_name = cachegrind.out.%t.%p
    xdebug.profiler_output_dir ="c:/wamp64/tmp"
    xdebug.show_local_vars=0

Blackfire
::
    ;[blackfire]
    ;extension=c:/wamp64/bin/php/php7.4.0/ext/blackfire.dll
    ;blackfire.agent_timeout = 0.25

OPcache
::
    [opcache]
    zend_extension="c:/wamp64/bin/php/php7.4.0/ext/php_opcache.dll"
    ; Determines if Zend OPCache is enabled
    ;opcache.enable=1
