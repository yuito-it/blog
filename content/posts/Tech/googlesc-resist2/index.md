---
title: "Google Search Consoleに登録した話 ~sitemap登録~"
discription: "サイトマップ送信して、ちゃんと登録してもらう話。"
date: 2023-08-10T00:00:00+09:00
images: 
    - OGP/Tech/googlesc-resist2.png?{{ .Lastmod.Format "20060102150405" }}
categories: ["Tech"]
tags: ["Hugo","Google Search Console","GithubActions"]
pager: true
weight: -2
toc: true
author: ["Yuito Akatsuki"]
type: article
---
GoogleSearchConsoleって、登録するだけじゃダメで、sitemapとやらをくっつけやなあかんらしいんで、やりました。

## sitemapとはなんぞや

サイトマップとは、GoogleのBotが、サイトが更新されてないかとかを見て回る時の道しるべです。

こいつを登録していないと、Botがサイトを見てくれず、登録されません。
送るファイルの種類としては、

- sitemap.xml
- feed.xml(atomやrss)

## Hugoでは

Hugoでは、このsitemap.xmlのファイルは自動生成されます。
rssは設定が必要なのでめんどいからやりません。今回は割愛します。
`/sitemap.xml`というところに自動生成されます。

## 登録

まず、SearchConsoleのサイトマップタブに飛びます。
{{<figure src="./sitemap.webp" alt="sitemapを登録" width="75%">}}
ここで、新しいサイトマップの追加のところに、sitemap.xmlと入力。
これで送信するだけです。

簡単ですね。

## 自動でアップデートさせる

これが面倒でした。

GithubPagesなので、GithubActionsつかえるやん！！って思って頑張って組みました。

{{<gist yuito-it fa3777cb5b76833ee432eef666d9e199>}}

こんな感じで組みました。
ちなみに、rssやってないので、下の２行は無駄ですww

## まとめ

- SearchConsoleにはsitemapを送れ。
- Hugoならsitemap.xml自動生成される。
- GithubPagesなら自動化もしとけ。

## 追記　(23/8/12)

rssは、/inde.xmlに生成されるようです。
