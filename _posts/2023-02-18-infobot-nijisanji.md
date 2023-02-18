---
title: "もうすぐ始まる「にじさんじ」ライバーの配信をお知らせする Misskey ボットを作成しました"
date: 2023-02-18T21:00:00+09:00
type: posts
categories:
  - tools
tags:
  - Misskey
  - SNS
  - にじさんじ
  - VTuber
header:
  image: "/assets/images/header/nijibot_header.png"
---

もうすぐ始まる「にじさんじ」ライバーの配信をお知らせする Misskey ボットを作成しました。

アカウントは [@infobot_2434@misskey.io](https://misskey.io/@infobot_2434) です。

お使いの Mastodon や Misskey, Pleroma など ActivityPub に対応している SNS でフォローできます。

ぜひご利用ください。

## スクリーンショット

<img src="/assets/images/2023/nijibot003.png" width="400px">

<img src="/assets/images/2023/nijibot004.png" width="400px">

## 背景

<img src="/assets/images/2023/nijibot001.png" width="400px">

<img src="/assets/images/2023/nijibot002.png" width="400px">

### 文章

Twitter API が部分的に廃止されました。

凍結祭りでずっと凍結していました。

もはやこのブログも、Twitter への[呪詛を書く](https://blog.sasakulab.com/tools/misskey-now#%E7%B5%8C%E7%B7%AF)ブログになりつつありますが、とにかく Twitter でやってたことをなるべく Misskey にも移植したいと思うようになっていました。

また、いつから.link が廃止されたことをきっかけに、データの取得方法をアップデートする必要もあり、今回実行に移しました。

## コード・実行環境

### 実行環境

Google Apps Script で動作しています。

無料なので、お財布に優しいですね！

### コード

中学生の頃に書いた、~~爆笑~~ソースコードを流用しています。~~よくこんなので動いたな。~~

正直全部書き直そうかとも思いましたが、動いているものを書き換えるのもよくなさそうだったので、リファクタリングは今後徐々にやっていこうと思います。

リポジトリは以下です。もしよければ手伝ってください。

[Sasakulab / misskeyniji](https://github.com/sasakulab/misskeyniji)

## おわりに

このツールは非公式です。にじさんじ公式にお問い合わせをしないようにお願いいたします。

サービスは予告なく終了する恐れがあります。

「にじさんじ」及び各ライバーの商標やサムネイルを含む各配信は、ANYCOLOR 株式会社及び各ライバーに帰属します。

おわりです。
