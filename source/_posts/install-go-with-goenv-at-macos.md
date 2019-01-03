---
title: Install Go with goenv at macOS
date: 2018-09-21 17:22:11
tags:
---

This is a note on how to install [goenv](https://github.com/syndbg/goenv) on macOS and how to use it.

## 1. Install goenv

### Install goenv.

```shell
$ git clone https://github.com/syndbg/goenv.git ~/.goenv
```

### Add the following to `.bash_profile`

```sh
# goenv
export GOENV_ROOT="$HOME/.goenv"
export PATH="$GOENV_ROOT/bin:$PATH"
eval "$(goenv init -)"
```

### Load `.bash_profile` in shell

```shell
$ source .bash_profile
```

## 2. How to Use goenv　( Install and manage Go )

### How to check which version you can use

```shell
$ goenv install -l
```

### How to check which version you insatlled

```shell
$ goenv versions
```

### How to install the specified version of Go

```shell
$ goenv install 1.10.3
```

*Run this command after you install a new version of Go*

```shell
$ goenv rehash
```

### How to use the specified version of Go at global

```shell
$ goenv global 1.10.3
```

How to use the specified version of Go at local ( directory ).

```shell
$ goenv local 1.10.3
```

This command will create `.go-version` file at current directory.

## 3. How to use dep

dep is package manager of golang.

```shell
$ go get -u github.com/golang/dep/cmd/dep
```

## 4. How to Update goenv

```shell
$ cd $(goenv root)
$ git pull
```
