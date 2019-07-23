---
title: Initial Server Setting of CentOS 7 - DigitalOcean
date: 2018-09-30 17:30:03
tags:
---

This is a note of the CentOS 7 server setup procedure.

I referred to [Initial Server Setup with CentOS 7　(Digitalocean)](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-centos-7) .

## SSH Login

```shell
$ ssh -i {YOUR_PRIVATE_KEY} root@{SERVER_IP_ADDRESS}
```

## Basic Settings
Do the following with root.

### yum upddate

```shell
# yum update
```

### reboot

After `yum update`, you need to reboot servers.

```shell
# reboot
```

### Settings of SeLinux

Allow connections to port numbers set in `/ etc / ssh / sshd_config` on selinux.

```shell
# semanage port -a -t ssh_port_t -p tcp {SSH_PORT_NUMBER}
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
# systemctl restart sshd.service
```

Check whether the SSH port number has been changed.

```shell
# netstat -an | grep LISTEN | grep {SSH_PORT_NUMBER}
```

## Add user

```shell
# useradd {USER_NAME}
# passwd {USER_NAME}
```

Enable added user to run `sudo`.

```shell
# usermod -aG wheel {USER_NAME}
```

Change user.

```shell
# su {USER_NAME}
```

Add authorized_keys to the user.

```shell
$ cd
$ mkdir .ssh
$ chmod 700 .ssh
$ vi .ssh/authorized_keys # Paste authorized_keys
$ chmod 600 .ssh/authorized_keys
```

Disable ssh login with `root`.

```shell
$ sudo vi /etc/ssh/sshd_config
```

`PermitRootLogin` : `no` .


```shell
PermitRootLogin no
```

Restart sshd

```shell
$ sudo systemctl restart sshd.service
```

## Cloud Firewalls

On the [Cloud Firewalls](https://www.digitalocean.com/docs/networking/firewalls/), you can only SSH login with SSH port number changed this time.
