---
title: kali の IP を固定する
date: 2021-10-24 14:23:28
tags: 
- kali
- linux
- network
- ip
---

ローカル接続している開発環境の kali linux に ssh 接続する際に起動毎に ip が変わると困るので、ip を固定する。

`interfaces` ファイルを編集する。

```bash
$ sudo vim /etc/network/interfaces
```

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# -- ここから下を追加する --
# eth0 がネットワークコネクタなので、設定したいコネクタを設定する
# ここでは ip を 192.168.11.60 に固定
# ゲートウェイを 192.168.11.1 に設定

# Local network interface
allow-hotplug eth0
iface eth0 inet static
address 192.168.11.60
netmask 255.255.255.0
gateway 192.168.11.1
```

interfaces ファイルを上書き保存したら再起動する。

```
$ sudo reboot
```
