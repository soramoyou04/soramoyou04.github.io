
## ビルドファイルを GitHub Pages に反映

```
git worktree add public gh-pages
cd public
git add -A
git commit -m "Publishing to gh-pages"
cd ..
git push origin gh-pages
```

[参考：Hugoで1からテーマを作ってGitHub Pagesにデプロイする](https://www.membersedge.co.jp/blog/create-hugo-theme-and-deploy-to-github-pages/)

## 空ブランチを作成する

```
git checkout --orphan gh-pages
```


The default branch has been renamed!
main is now named master

If you have a local clone, you can update it by running the following commands.

git branch -m main master
git fetch origin
git branch -u origin/master master
git remote set-head origin -a
