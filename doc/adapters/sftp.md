### Documentation for Gaufrette SFTP adapter

*N.B.* SFTP adapter is not recommended to use due to https://bugs.php.net/bug.php?id=64169. It is recommended to use
[PHPSeclibSFTP adapter](phpseclib_sftp.md) instead.

#### Prerequisites

* [PHP-SSH](https://github.com/Herzult/php-ssh)
* [SSH2 extension](http://www.php.net/manual/en/book.ssh2.php)

You can install it via:

```bash
composer require herzult/php-ssh:^1.1
pecl install ssh2-beta
```

#### Configuration

```php

$configuration  = new Ssh\Configuration('localhost', 2222);
$authentication = new Ssh\Authentication\Password('gaufrette', 'gaufrette'); // for other options, check php-ssh docs

$session   = new Ssh\Session($configuration, $authentication);

$adapter   = new Gaufrette\Adapter\Sftp($session->getSftp());
$fs = new Gaufrette\Filesystem($adapter);
```
