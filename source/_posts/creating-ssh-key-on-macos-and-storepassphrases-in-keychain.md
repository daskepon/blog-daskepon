---
title: Creating SSH key on macOS and store passphrases in keychain
date: 2018-09-18 14:52:57
tags:
---

This is a memo of creating SSH key and store passphrases in keychain on macOS.
I referred [Github SSH Setting Guite](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/).

## 1. Generating a new SSH key

```shell-session
$ ssh-keygen -t rsa -b 4096 -C "xxx@example.com"
```

For security, it is important to create it with 4096 bits and set a passphrase for the private key

## 2. Setting SSH config

Setting SSH config for store passphrases in keychain.
Add the following setting to `.ssh / config`.

```shell
AddKeysToAgent yes
UseKeychain yes
IdentityFile ~/.ssh/id_rsa
```

## 3. Starting ssh-agent

Starting ssh-agent.

```shell
$ ssh-add -K ~/.ssh/id_rsa
```

When you want to start ssh-agent automatically when starting the shell. write the following in .bash_profile etc.

```shell
ssh-add -l || ssh-add -K ~/.ssh/id_rsa
```
