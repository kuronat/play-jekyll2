---
layout: post
title:  GiHub PagesによるJekyllブログをProject siteとして作る
date:   2017-11-12 00:49:12 +0900
---

## はじめに
GitHub Pagesは、リポジトリ内にHTMLコンテンツ(またはJekyllプロジェクト)を設置すると静的サイトを公開できるという、GitHubのいち機能である。

- `yourid/yourid.github.io` リポジトリで用意したGitHub Pagesは `http://yourid.github.io` に公開される。ここで `http://yourid.github.io` をUser siteと呼ぶ。
- `yourid/reponame` リポジトリで用意したGitHub Pagesは `http://yourid.github.io/reponame` に公開される。ここで `http://yourid.github.io/reponame` を `yourid/reponame` のProject siteと呼ぶ。

今回は Project site としてJekyllでブログを作成してみる。
テーマとしてはデフォルトのminimaを用いる。

## 作業手順

まず、雛形を生成する。

```
jekyll new play-jekyll2
cd play-jekyll2
```

`play-jekyll2` ディレクトリをGitリポジトリとして`init`し、GitHubにも作成しておこう。

```
git init
hub create
```

ブラウザで動作確認する。ポートは4000番。

```
bundle exec jekyll serve
```

## サブパスを設定

User siteならばこの時点で何もせずpushしてしまえば良い。だがProject siteの場合は、それではURLのパスがずれてしまう。

Project siteの場合、`_config.yml` で `baseurl:` の設定を行えばよい。

```
baseurl: /play-jekyll2
```

## push

あらかじめGitHubリポジトリの設定で、GitHub Pagesを有効化する(今回はmasterブランチとして有効化した)。

リポジトリにコミットされるごとに、JekyllのビルドをGitHub側が行ってくれて便利である。

```
git add .; git commit -m 'update'; git push origin master
```

しばし待てば[Project site](https://kuronat.github.io/play-jekyll2/)にJekyllブログが作成されたことが確認できるだろう。

## テーマ編集

- `open $(bundle show minima)` の内容をリポジトリのディレクトリにコピーする。
- `_config.yml` から `theme: minima` を削る。
- 動作確認をローカルで行いながら、HTMLやCSSを編集する。

## 所感

- テーマいじりはAtomが便利
- minimaデフォルトから要らないものを削ったらイイ感じになった
  - 本リポジトリのコミットログを参照のこと

## 参考文献

1. [Github Pagesで独自ドメイン+プライベートリポジトリもおｋ](http://sonson.jp/blog/2015/01/17/githubpages/)
