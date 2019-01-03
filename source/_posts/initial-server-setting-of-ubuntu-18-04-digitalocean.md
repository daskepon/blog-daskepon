---
title: Initial Server Setting of Ubuntu 18.04 - DigitalOcean
date: 2018-09-30 17:31:05
tags:
---

This is a note of the Ubuntu 18.04 server setup procedure.

I referred to [Initial Server Setup with Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04) .

## SSH Login

```shell
$ ssh -i {YOUR_PRIVATE_KEY} root@{SERVER_IP_ADDRESS}
```

## Basic Settings
Do the following with root.

### update libraries by apt-get

```shell
# apt-get update
# apt-get dist-upgrade
```

### reboot

After `apt-get dist-upgrade`, you need to reboot servers.

```shell
# reboot
```

### SSH Settings for security

```shell
# vi /etc/ssh/sshd_config
```

Edit the following. Change port number of ssh.

```shell
PasswordAuthentication no
Port {SSH_PORT_NUMBER} ( 1024 to 65535 )
```

Restart sshd.

```shell
# service ssh restart
```

Check whether the SSH port number has been changed.

```shell
# lsof -i:{SSH_PORT_NUMBER}
```

### Setting of ufw

Allow connections to port numbers set in / etc / ssh / sshd_config on ufw.

```shell
# vi /etc/ufw/applications.d/openssh-server
```

Change the "port number" on the last line.

```
[OpenSSH]
title=Secure shell server, an rshd replacement
description=OpenSSH is a free implementation of the Secure Shell protocol.
ports={SSH_PORT_NUMBER}/tcp
```

Enable ufw.

```shell
# ufw app list
# ufw allow OpenSSH
# ufw enable
# ufw status
```

## Add user

```shell
# adduser {USER_NAME}
```

Enable added user to run `sudo`.

```shell
$ usermod -aG sudo {USER_NAME}
```

Add authorized_keys to the user.

```shell
$ cd
$ mkdir .ssh
$ chmod 700 .ssh
$ vi .ssh/authorized_keys #  Paste authorized_keys
$ chmod 600 .ssh/authorized_keys
```

Disable ssh login with `root`.

```shell
$ vi /etc/ssh/sshd_config
```

`PermitRootLogin` * `no` .

```shell
PermitRootLogin no
```

Restart sshd.

```shell
$ sudo service ssh restart
```

## Cloud Firewalls
On the [Cloud Firewalls](https://www.digitalocean.com/docs/networking/firewalls/), you can only SSH login with SSH port number changed this time.
