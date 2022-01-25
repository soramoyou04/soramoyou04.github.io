---
title: VS Code で x11 Fowarding の設定する（Windows）
date: 2021-10-31 14:58:41
tags:
---

環境
Wnindow10
kali linux

kali linux にソースを置き、VS Code で SSH接続 してプログラムelectron などデスクトップ


インストールする
VcXsrv Windows X Server
https://sourceforge.net/projects/vcxsrv/

```
$ sudo apt install x11-apps
```

`sshd`

```
$ /etc/init.d/sshd
```

```
X11Forwarding yes
X11UseLocalhost no
PasswordAuthentication yes
```

```
$ /etc/init.d/sshd reload
```

VS Code で SSH 接続時に実行する batプログラムを作成する。

`x11ssh.bat`

```
set DISPLAY=localhost:0.0
ssh %*
```

`~/User/{user}/.ssh/config`

```
Host *
    ForwardX11 yes
    ForwardX11Trusted yes
```

echo $DISPLAY
