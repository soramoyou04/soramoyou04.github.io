---
title: WSL での Node.js 環境構築し、hexo でブログをはじめる
date: 2021-10-16 00:31:41
tags:
---

WSL は Ubuntu で用意しているものとする。  
nodejs をインストールする。

```
$ sudo apt update && sudo apt upgrade
```

```
$ sudo apt install nodejs npm
```

nvm をインストール

```
$ sudo apt install curl
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
```

参考: [Node.js を Linux 用 Windows サブシステム (WSL2) にインストールする](https://docs.microsoft.com/ja-jp/windows/dev-environment/javascript/nodejs-on-wsl)

インストールが完了したらターミナルを閉じてログインし直します。  
ちゃんとインストールできているかバージョンを確認します。

```
$ npm -v
$ nvm -v
```

インストールされているバージョンが古いので LTS版をインストールする。

```
nvm install --lts
```

参考: [Node.js のバージョン管理ツール nvm の使い方](https://laboradian.com/how-to-use-nvm/)


hexo をインストール

```
& sudo npm install hexo-cli -g
```
