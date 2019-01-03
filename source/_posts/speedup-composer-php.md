---
title: SpeedUp Composer (PHP)
date: 2018-10-05 17:32:07
tags:
---
This is a note of the way to speed up `composer install`.

### Use mirror
If you live Asia or South America, use composer mirror.

https://packagist.org/mirrors

This is an example of setting when using Japanese mirror.

```shell
$ composer config -g repos.packagist composer https://packagist.jp
```

### Use prestissimo

[prestissimo](https://github.com/hirak/prestissimo) is composer parallel install plugin.

```shell
$ composer global require hirak/prestissimo
```
