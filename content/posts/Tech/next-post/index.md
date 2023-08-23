---
title: "Hugoで「前の投稿」ボタンが出てこなかった話"
date: 2023-08-10T00:00:00+09:00
images: 
    - OGP/Tech/next-post.png?{{ .Lastmod.Format "20060102150405" }}
categories: ["Tech"]
tags: ["Hugo","md","yml"]
weight: -3
toc: true
description: "Hugoで前(次)の投稿へボタンが出てこなかったのを、解決する話。参考までに..."
author: ["Yuito Akatsuki"]
type: article
---
## 事の発端
友人にこのブログを見せたとき、

「え？他の記事あったん？次へボタンとかなかったけど...」

って言われた。
で、見返すと、確かにない。
自動で出てきそうで出てこないのでどうしたもんかとなりました。

## themesの中身を見て仕組みを確認
まず、どうなってるかを知らんとどうしようもないので、themes/Mainroad/layoutsを確認した。

おそらく、`_default/single.html`が、フツーの記事のテンプレートなのだろう。
どこかに絶対次のページのボタンの設定があるはず...

```md
{{ define "main" }}
~ 省略 ~
{{ partial "authorbox.html" . }}
{{ partial "pager.html" . }}
{{ partial "comments.html" . }}
{{ end }}
```

絶対これやん、`pager.html`。

## pager.html
これの中身を見た。

```html
{{- if .Param "pager" }}
{{- if or (.PrevInSection) (.NextInSection) }}
~省略~
{{- end }}
{{- end }}
```


***「わかんねぇ」***

HTMLもHugoもあんましいじってこなかったので、よくわからん。

ただ、最初の`{{- if .Param "pager" }}`が関係してそう...
ただ、if文の読み方がわからずに色々調べた。
そしたら、なんかこれはpagerというプロパティがあるかを調べてるっぽいことが分かった。

***「何処に書くんや？」***

とおもったけど、多分記事に書くんやろな。
そう思い、適当に数字ぶち込んでみた。

{{<figure src="./1.webp" alt="突如現れた「次の記事へ」ボタン" width="75%">}}

***「いけたー！！」***

というわけで、この、著者照会欄の下に次の記事へボタンなどが追加されましたとさ。

めでたしめでたし。

ではでは。。。

**追記　(23/8/12)**
```toml
---
title: "Hugoで「前の投稿」ボタンが出てこなかった話"
~割愛~
- pager: 4
+ pager: true
+ weight: -3
---
```
なんか、ページの並び順は重要度を示す、weightの数値が低い方が上に表示されるようです。

なので、`weight: -記事番号+1`でいいみたい…

+1は、最初の記事が0だから。
pagerは、オンオフいじるだけなのでこれで。

また追記すると思います。
