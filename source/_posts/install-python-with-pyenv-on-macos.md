---
title: Install Python with pyenv on macOS
date: 2018-09-21 17:19:53
tags:
---

This is a note on how to install [pyenv](https://github.com/pyenv/pyenv) on macOS and how to use it.

## 1. Install pyenv

### Install pyenv.

```shell
$ git clone https://github.com/pyenv/pyenv.git ~/.pyenv
```

### Add the following to `.bash_profile`

```sh
# pyenv
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```

### Load `.bash_profile` in shell

```shell
$ source .bash_profile
```

## 2. How to Use pyenv　( Install and manage Python )

### How to check which version you can use

```shell
$ pyenv install -l
```

### How to check which version you insatlled

```shell
$ pyenv versions
```

### How to install the specified version of PHP

```shell
$ pyenv install 3.6.3
```

*Run this command after you install a new version of Python*

```shell
$ pyenv rehash
```

### How to use the specified version of Python at global

```shell
$ pyenv global 2.7.14
```

How to use the specified version of Python at local ( directory ).

```shell
$ pyenv local 2.7.14
```

This command will create `.python-version` file at current directory.

## 3. How to use pip

You can use pip.
When you install pip packages global ( `pip install ***` ), the gem packages will installed at current version of python directory)( example: `./.pyenv/versions/2.7.14/lib/python2.7/site-packages/` ).
So, you shuld use `pyenv rehash` command after install pip packages at global.
I think this is safe because the pip packages installed global is related Python version.

example.
```shell
$ pyenv install ansible
$ pyenv rehash
```

## 4. How to Update pyenv

When a new version of Python is released, you need to update.

```shell
$ cd $(pyenv root)
$ git pull
```
