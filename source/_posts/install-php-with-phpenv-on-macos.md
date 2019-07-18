---
title: Install PHP with phpenv on macOS
date: 2018-09-21 17:21:05
tags:
---

This is a note on how to install phpenv on mac and how to use it.

## 1. Install phpenv

### Install phpenv

```shell
$ git clone https://github.com/madumlao/phpenv.git ~/.phpenv
```

### Install `php-build` to build php

```shell
$ git clone https://github.com/php-build/php-build.git ~/.phpenv/plugins/php-build
```

### Install libraries to build php

```shell
$ brew install re2c openssl bison libxml2 autoconf automake icu4c libjpeg libpng libmcrypt libzip
```

### If Mojave

```shell
$ sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /
```

*[Homebrew](https://brew.sh/) is needed*

### Add the following to `.bash_profile`

```sh
# phpenv
export PATH="/usr/local/opt/bison/bin:$PATH"
export PHPENV_ROOT="$HOME/.phpenv"
export PATH="$PHPENV_ROOT/bin:$PATH"
eval "$(phpenv init -)"
```

### Load `.bash_profile` in shell

```shell
$ source .bash_profile
```

## 2. How to Use phpenv　( Install and manage PHP )

### How to check which version you can use.

```shell
$ phpenv install -l
```

### How to check which version you insatlled.

```shell
$ phpenv versions
```

### How to install the specified version of PHP.

```shell
$ phpenv install 7.3.7
```

*Run this command after you install a new version of PHP*

```shell
$ phpenv rehash
```

### How to use the specified version of PHP at global.

```shell
$ phpenv global 7.3.7
```

How to use the specified version of PHP at local ( directory ).

```shell
$ phpenv local 7.3.7
```

This command will create `.php-version` file at current directory.

## 3. How to use composer

### Install composer to phpenv

```shell
$ git clone https://github.com/ngyuki/phpenv-composer.git ~/.phpenv/plugins/phpenv-composer
$ phpenv rehash
```

## 4. How to Update phpenv

```shell
$ cd $(phpenv root)
$ git pull
```

## 5. How to Update php-build

When a new version of PHP is released, you need to update `php-build`. Otherwise you can not install the new version of PHP.

```shell
$ cd $(phpenv root)/plugins/php-build
$ git pull
```
