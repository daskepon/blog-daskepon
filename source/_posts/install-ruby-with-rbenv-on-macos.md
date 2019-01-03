---
title: Install Ruby with rbenv on macOS
date: 2018-09-21 17:18:53
tags:
---

This is a note on how to install [rbenv](https://github.com/rbenv/rbenv) on macOS and how to use it.

## 1. Install rbenv

### Install rbenv.

Before install rbenv, you need to install `xcode-select`.

```shell
$ xcode-select --install
```

Install rbenv.

```shell
$ git clone https://github.com/rbenv/rbenv.git ~/.rbenv
$ cd ~/.rbenv && src/configure && make -C src
```

### Add the following to `.bash_profile`

```sh
# rbenv
export RBENV_ROOT="$HOME/.rbenv"
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
```

### Load `.bash_profile` in shell

```shell
$ source .bash_profile
```

### Install `ruby-build` to build ruby.

```shell
$ mkdir -p "$(rbenv root)"/plugins
$ git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
```

## 2. How to Use rbenv　( Install and manage Ruby )

### How to check which version you can use.

```shell
$ rbenv install -l
```

### How to check which version you insatlled.

```shell
$ rbenv versions
```

### How to install the specified version of PHP.

```shell
$ rbenv install 2.4.3
```

*Run this command after you install a new version of Ruby*

```shell
$ rbenv rehash
```

### How to use the specified version of Ruby at global.

```shell
$ rbenv global 2.4.3
```

How to use the specified version of Ruby at local ( directory ).

```shell
$ rbenv local 2.4.3
```

This command will create `.ruby-version` file at current directory.

## 3. How to use gem

You can use gem.
When you install gem packages global ( `gem install ***` ), the gem packages will installed at current version of ruby directory)( example: `.rbenv/versions/2.4.3/lib/ruby/gems/` ).
So, you shuld use `rbenv rehash` command after install gem packages at global.
I think this is safe because the gem packages installed global is related Ruby version.

example.
```shell
$ gem install bundler
$ rbenv rehash
```

## 4. How to Update rbenv

```shell
$ cd $(rbenv root)
$ git pull
```

## 5. How to Update ruby-build

When a new version of Ruby is released, you need to update `ruby-build`. Otherwise you can not install the new version of Ruby.

```shell
$ cd $(rbenv root)/plugins/ruby-build
$ git pull
```
