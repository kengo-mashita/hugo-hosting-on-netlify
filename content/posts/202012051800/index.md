---
title: "HUGOでブログ作成"
date: 2020-12-06T18:32:10+09:00
draft: false
categories: ["HUGO"]
tags: ["HUGO"]
---

## はじめに

静的サイトジェネレータである [HUGO](https://gohugo.io/) を使用してブログを作成する。

## インストール

```sh
brew install hugo
```

バージョン確認

```
hugo version
```

## サイト作成

```sh
hugo new site tech-blog
```

- "tech-blog"の箇所は好きな名前で。

## テーマ追加

1. 公式サイトから好きなテーマを選ぶ。  
[Themes](https://themes.gohugo.io/)

- 今回は[MemE](https://github.com/reuixiy/hugo-theme-meme)にした。(ミニマルなデザインでカッコいい)  

- 適用方法については、README.mdの手順に沿って実行する。

2. Gitサブモジュールを追加する

```zsh
cd tech-blog
git init
git submodule add --depth 1 https://github.com/reuixiy/hugo-theme-meme.git themes/meme

```

3. 設定ファイルを適用させる

```zsh
rm config.toml && cp themes/meme/config-examples/en/config.toml config.toml
```

- このファイルを修正してサイトをカスタマイズする。まずはサンプルをコピーする。

4. 記事を作成する

```
hugo new "posts/hello-world.md"
hugo new "about/_index.md"
```

- これでPostsとAboutに記事が追加された。あとはmdファイルを修正すれば良い。


## 実行

ローカル環境で実行してみる。

```zsh
hugo server -D
```

-D はドラフト記事も表示させる。
mdファイルの Front matter 部分に、draft = true と書くと公開されない。 



起動に成功したら確認してみよう。
```
http://localhost:1313/
```

あとは記事を書いたり、設定を修正したりして自分のサイトを作成していこう。

## サンプル
### シンタックスハイライト

```go
package main

import "fmt"

func add(x int, y int) int {
	return x + y
}

func main() {
	fmt.Println(add(25, 25))
}
```

### 画像とか

![robot](robot.png)