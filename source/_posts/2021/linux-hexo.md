---
title: WSL での Node.js 環境構築し、hexo でブログをはじめる
date: 2021-10-16 00:31:41
tags:
---

## 環境について
WSL は Ubuntu で用意しているものとします。  
まずは更新。

```
$ sudo apt update && sudo apt upgrade -y
```

## nodejs と npm をインストール

```
$ sudo apt install nodejs npm -y
```

## nvm をインストール

nvm の最新バージョンは [GitHub](https://github.com/nvm-sh/nvm) を確認すること。

```
$ sudo apt install curl -y
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
```

インストールが完了したらターミナルを閉じてログインし直します。  
ちゃんとインストールできているかバージョンを確認します。

```
$ node -v
v10.16.3
$ npm -v
6.14.15
$ nvm -v
0.38.0
```

## nvm の使い方

- 利用可能なバージョンを一覧表示する。

```
$ nvm ls-remote
```

- インストール済のバージョンを表示する。

```
$ nvm ls
```

- エイリアス設定を確認する。

```
$ nvm alias
```

node のインストールされているバージョンが古いのでLTS版を指定してインストールします。

```
$ nvm install --lts
$ node -v
v14.18.1
```

参考: [Node.js のバージョン管理ツール nvm の使い方](https://laboradian.com/how-to-use-nvm/)  
参考: [Node.js を Linux 用 Windows サブシステム (WSL2) にインストールする](https://docs.microsoft.com/ja-jp/windows/dev-environment/javascript/nodejs-on-wsl)  
参考: [nvmとは何か？Node.jsのインストールと最新の安定版にアップデートする方法｜バージョン指定と変更（npm）](https://prograshi.com/language/nodejs/nvm-install-update-node/)

## hexo をインストール

```
$ sudo npm install hexo-cli -g
```

```
$ mkdir blogs
# cd blogs
```
