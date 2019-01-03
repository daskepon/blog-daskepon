---
title: Install JVM Languages (Java, kotlin, etc...) with SDKMAN on macOS
date: 2018-09-24 17:27:44
tags:
---

This is a note on how to install JVM Languages (Java, kotlin, etc...) with [SDKMAN](https://sdkman.io/) on macOS and how to use it.
[SDKMAN](https://sdkman.io/) is a tool for managing parallel versions of multiple Software Development Kits ( Mainly JVM Languages ) on most Unix based systems.
It is easy-to-use on macOS.

## Install SDKMAN

```shell
$ curl -s "https://get.sdkman.io" | bash
$ source "$HOME/.sdkman/bin/sdkman-init.sh"
```

By default it will be installed under `~ / .sdkman /` .

Detail is [SDKMAN install page](https://sdkman.io/install) .

## How to use SDKMAN

Detail is
- https://sdkman.io/usage
- https://sdkman.io/sdks

### Example

#### JVM Languages

```shell
$ sdk install java
$ sdk install kotlin
$ sdk install scala
```

#### Frameworks
```shell
$ sdk install springboot
```
