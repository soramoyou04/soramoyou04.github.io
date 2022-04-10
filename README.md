## テーマを反映

```
git clone --depth 1 https://github.com/hexojs/hexo-theme-light themes/light
```

## 新規記事を作成する

```
npx hexo new [layout] <title>
npx hexo new draft example_draft_tilte
npx hexo new post example_post_title
```

### 記事を日付の階層にする
_config.yml を編集する。

```
new_post_name: :year/:month/:day/:title.md
```

|Layout|Path|
|:--|:--|
|post|source/_posts|
|page|source|
|draft|source/_drafts|

## ビルドファイルを GitHub Pages に反映

```
git worktree add public gh-pages
cd public
git add -A
git commit -m "Publishing to gh-pages"
cd ../
git push origin gh-pages
```

[参考：Hugoで1からテーマを作ってGitHub Pagesにデプロイする](https://www.membersedge.co.jp/blog/create-hugo-theme-and-deploy-to-github-pages/)

## 空ブランチを作成する

```
git checkout --orphan gh-pages
```

## 再構築して反映する手順

```
npm run clean
git worktree prune
git worktree add public gh-pages
npm run build
cd public/
git add -A
git commit -m "comment"
cd ../
git push origin gh-pages
```
