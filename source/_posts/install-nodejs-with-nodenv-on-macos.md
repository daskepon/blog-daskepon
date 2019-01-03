---
title: Install Node.js with nodenv on macOS
date: 2018-09-21 14:59:37
tags:
---

This is a note on how to install [nodenv](https://github.com/nodenv/nodenv) on macOS and how to use it.

## 1. Install nodenv

### Install nodenv

```shell
$ git clone https://github.com/nodenv/nodenv.git ~/.nodenv
$ cd ~/.nodenv && src/configure && make -C src
```

### Add the following to `.bash_profile`

```sh
# nodenv
export PATH="$HOME/.nodenv/bin:$PATH"
eval "$(nodenv init -)"
```

### Load `.bash_profile` in shell

```shell
$ source .bash_profile
```

### Install `node-build` to build Node.js.

```shell
$ git clone https://github.com/nodenv/node-build.git $(nodenv root)/plugins/node-build
```

## 2. How to Use nodenv　( Install and manage Node.js )

### How to check which version you can use

```shell
$ nodenv install -l
```

### How to check which version you insatlled

```shell
$ nodenv versions
```

### How to install the specified version of Node.js

```shell
$ nodenv install 8.11.3
```

*Run this command after you install a new version of Node.js.*

```shell
$ nodenv rehash
```

### How to use the specified version of Node.js at global

```shell
$ nodenv global 8.11.3
```

How to use the specified version of Node.js at local ( directory ).

```shell
$ nodenv local 8.11.3
```

This command will create `.node-version` file at current directory.

## 3. How to use npm

You can use npm.
When you install npm packages global ( `npm install *** -g` ), the npm packages will installed at current version of node.js directory)( example: `.nodenv/versions/8.11.3/lib/node_modules/` ).
So, you shuld use `nodenv rehash` command after install npm packages at global.
I think this is safe because the npm packages installed global is related Node.js version.

example.
```shell
$ npm install grunt-cli
$ nodenv rehash
```

## 4. How to Update nodenv

```shell
$ cd $(nodenv root)
$ git pull
```

## 5. How to Update node-build

When a new version of Node.js is released, you need to update `node-build`. Otherwise you can not install the new version of Node.js.

```shell
$ cd $(nodenv root)/plugins/node-build
$ git pull
```
