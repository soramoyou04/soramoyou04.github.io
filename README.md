## ブランチを分けて管理する方法
#### 引用サイト
[Hugoで1からテーマを作ってGitHub Pagesにデプロイする](https://www.membersedge.co.jp/blog/create-hugo-theme-and-deploy-to-github-pages/)

1つのリポジトリに2つのブランチを使用する方法です。プロジェクトのページで、 gh-pages を使う場合の説明をします。


まず同様に任意のプロジェクト名でリポジトリを作成してください。以下プロジェクト名を PROJECT とします。
PROJECT リポジトリ作成時は、次の画像のように何もファイルを作らないようにしてください(ローカルでコミット済みのため面倒になる)。


まず作成したサイトをリモートにプッシュします。
```
# Hugoのサイトディレクトリに移動
cd ~/quickstart
# ユーザ名を入れる
USERNAME=ユーザ名
# プロジェクト名を入れる
PROJECT=プロジェクト名
# リモートリポジトリを追加
git remote add origin git@github.com:${USERNAME}/${PROJECT}
# リモートにプッシュ
git push -u origin master
```
それから、 master ブランチとは独立したブランチ gh-pages を作成し、空のコミットを追加した上でプッシュします。
(Preparations for gh-pages Branchで書かれているコマンドとほぼ同じです)

```
# orphan(孤立)ブランチの作成
git checkout --orphan gh-pages
# 全てのファイルを削除して空にする
git reset --hard
# 空コミットを追加
git commit --allow-empty -m "Initializing gh-pages branch"
# リモートにプッシュ(originで登録されているため公式のコマンドと異なる)
git push origin gh-pages
# masterブランチに戻る
git checkout master
```
次に、 gh-pages を public ディレクトリにチェックアウトします。

```
# Hugoが作成したファイルを一旦削除
rm -rf public
# publicディレクトリにgh-pagesブランチをチェックアウト(公式のコマンドと異なるが内容は同じ)
git worktree add public gh-pages
```

それから、Hugoを起動してできたファイルを gh-pages ブランチにコミットし、リモートにプッシュします。

```
# ビルド
hugo
# gh-pagesのワークツリーに移動
cd public
# 作成されたHTMLファイルをコミット
git add -A
git commit -m "Publishing to gh-pages"
cd ..
# リモートにプッシュ
git push origin gh-pages
```

しばらく待ってから、 https://USERNAME.github.io/PROJECT/ にアクセスしてください。Hugoでビルドされたサイトが表示されるはずです。

公式サイトのPut it Into a Scriptに書かれている publish_to_ghpages.sh は、先ほどの手順をスクリプト化したものです。
