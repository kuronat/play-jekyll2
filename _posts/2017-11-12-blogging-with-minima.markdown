---
layout: post
title:  Jekyll(minimaテーマ)によるGiHub Pages
date:   2017-11-12 00:49:12 +0900
---

## はじめに
GitHub PagesはHTMLコンテンツ(またはJekyll)をリポジトリ内に設置すると、GitHubで静的サイトを公開できるというGitHubの機能である。

- `yourid.github.io` リポジトリで用意したGitHub Pagesは `http://yourid.github.io` に公開される。ここで `http://yourid.github.io` をUser siteと呼ぶ。
- `yourid/reponame` リポジトリで用意したGitHub Pagesは `http://yourid.github.io/reponame` に公開される。ここで `http://yourid.github.io/reponame` を `yourid/reponame` のProject siteと呼ぶ。

今回は Project site としてJekyllブログを作成してみる。
テーマとしてはデフォルトのminimaを用いる。

## 手順

雛形を生成する。

```
jekyll new play-jekyll2
cd play-jekyll2
```

`play-jekyll2` ディレクトリをGitリポジトリにし、GitHubにも作成しておく。

```
git init
hub create
```

動作確認

```
bundle exec jekyll serve
```

## サブパスを設定しpush

User siteならば何もせずpushしてしまえば良いが、Project siteの場合、 `_config.yml` で `baseurl:` の設定が必要である。

```
baseurl: /play-jekyll2
```

pushする。

```
git add .; git commit -m 'update'; git push origin master
```

これで、Project siteとしてJekyllブログが作成された。

## minimaテーマの編集

```
open $(bundle show minima)
```

の内容をリポジトリのディレクトリにコピーする。


## 参考文献

1. [Github Pagesで独自ドメイン+プライベートリポジトリもおｋ](http://sonson.jp/blog/2015/01/17/githubpages/)
