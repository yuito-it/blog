---
title: "Google Search Consoleに登録した話 ~とりあえずサイトに登録だけ~"
date: 2023-08-09
categories: ["Tech"]
tags: ["Hugo","Google Analytics","Google Search Console"]
---
いや～、やっぱねぇ、検索に引っかかってもらいたいよね。始めたからには。

## Google Search Consoleに登録する前に
Google Search Console って、実は自分２回目です。

ただ、Hugoのやり方は知らないんで公式のやつとかテンプレートのReadmeとかを読み漁りました。

で、Google Analyticsに登録しとけば、解析もできて、サーチコンソールに入れやすいのを知っていたので、ちょっとやりましょうということで。

## Google Analyticsに登録する
準備物
- Google アカウント
- やる気

で、まず、[GoogleAnalytics](https://analytics.google.com)に行きます。
{{<figure src="./Account.png" alt="アカウントを登録" width="75%">}}
こんなんが出てくるんじゃないかな？(すいません、もうアカウント持ってるんでわかりません。)

アカウント名のところに入力して、下のチェックボックスは基本なにもいじらんでも問題ないです。

次に、プロパティというものを作成します。

これは、１つのアカウントにいっぱい作れるので、ホームページいっぱいになった時でも大丈夫。
{{<figure src="./Propati.png" alt="プロパティを登録" width="75%">}}
で、お金の単位とタイムゾーン設定したら、次へ

ビジネスの目標、これはどういうブログ化によるのでご自身で考えてもらって。

一人だと思うので、小規模を選択、次へ。

ビジネス目標は僕はこんな感じにしました。
{{<figure src="./vision.png" alt="ビジネスの目標" width="75%">}}

で、ウェブを選択。URLには、トップページを入力してください。

僕の場合は
`yuito-it.github.io/blog/`
ストリーム名はどのサイト化識別するためのものなので、サイト名を入力。

で、実装手順が出てきますが無視。

```config.toml
googleAnalytics = 'G-から始まる測定ID'
```
とすればOKです。
これで、pushして放置。

## Search Consoleへ
まず、[GoogleSearchConsole](https://search.google.com/search-console)へ。
{{<figure src="./search-console.png" alt="ビジネスの目標" width="75%">}}
で、urlプレフィックスのほうを選択、入力。

今回僕は、親プロパティの、yuito-it.github.ioが認証済みだったので、その手順はしませんでしたが、認証を求められたら、GoogleAnalyticsを選択。
確認を押せばできるはずです。

## まとめ
GoogleAnalytics使えば解析もできて認証も楽。

ではでは、またどこかで。。。