---
title: "#nowwatching なウェブサイトを Misskey へ簡単に投稿する \"Misskey Now\" を開発しました"
date: 2023-02-06T23:00:00+09:00
type: posts
categories:
  - tools
tags:
  - Misskey
  - SNS
  - Browser Extension
---

みなさん、こんにちは。#nowwatching なウェブサイトを Misskey へ簡単に投稿する \"Misskey Now\" を開発しました。

## 使い方

### 1. インストール

インストールします。

|ソース|リンク|備考|
|----|----|----|
|Chrome ウェブストア|(審査中)||
|Firefox Addons|[Misskey Now](https://addons.mozilla.org/ja/firefox/addon/misskey-now/)|Experimental|
|GitHub Release|[GitHub](https://github.com/sasakulab/misskey-now)|開発者モードを有効化してインストールしてください|

ちなみに、開発版をいち早く試したいあなたは、以下のリポジトリをクローンして、[chrome://extensions](chrome://extensions/) や [about:debugging#/runtime/this-firefox](about:debugging#/runtime/this-firefox) よりディレクトリごと読み込むことで試すことができます。

もし良ければ、デバッグなどにご協力いただけると助かります。

### 2. アクセストークン (API キー) を発行する

お使いのインスタンスのアクセストークンを発行してください。

必要な権限は「ノートを作成・削除する」のみです。削除機能はついていませんが。

発行されたらクリップボードにコピーしておきましょう。ここで閉じると二度とトークンを表示できません。

万が一、コピーできていなければ、トークンを作り直してください。

<img src="/assets/images/2023/mk001.png" width="300px">
<img src="/assets/images/2023/mk002.png" width="300px">

### 3. Misskey Now を開く

「拡張機能」ペインに追加されているであろう Misskey Now を開きます。

Settings を開き、`Host` にあなたのインスタンスのホスト名を入れます。

`misskey.io`, `misskey.dev`, `mi.yude.moe` などです。`https://` は必要ありません。

`API Key` に先ほどコピーしたトークンを貼り付けます。

<img src="/assets/images/2023/mk003.png" width="300px">

### 4. 使ってみる

<img src="/assets/images/2023/mk004.png" width="300px">

`Range` は公開範囲です。そう、Misskey で言う、あの地球儀マークとかのやつです。ダイレクト(Direct) は選べません。

<img src="/assets/images/2023/mk005.png" width="300px">

`HashTag` はハッシュタグです。`#nowplaying` など使いそうなのを選びました。`(None)` を選択するとハッシュタグは付与されません。

`Note` に書き散らしたいコメントをお書きください。

`Misskey Now!` をクリックして、ボタンが緑色になり `Success` と表示されれば、送信成功です。

<img src="/assets/images/2023/mk006.png" width="500px">

## 経緯

Twitter が凍結されました。

幸いなことに異議申し立てを数回送ることで、いつの間にか凍結は解除されていました。

しかし、もちろん Twitter も楽しい場所とはいえ、そろそろ他の SNS にもちゃんとアイデンティティを作っておこうかなという気持ちになりました。

そんなこんなで、`mi.yude.moe` インスタンスにいます。@yude さんには本当に頭が上がりません。

せっかくなので、Chrome 拡張機能の勉強もしておこうと、今回作ってみました。

## バグ報告・プルリクエスト

バグ報告や、コードの変更をお待ちしております。

GitHub の issue や Pull Requests、Misskey アカウントにお送りください。

- [Misskey Now / GitHub](https://github.com/sasakulab/misskey-now)
- [@ayato_sasakura@mi.yude.moe](https://mi.yude.moe/@ayato_sasakura)

## 謝辞

KusaReMKN さんが手伝ってくれました。

JavaScript の `fetch` API の使い方がぐちゃぐちゃだったのを修正してくれたり、README を整備してくださったり（Chrome 版が公開されてからマージします）。

本当にありがとうございました。

## おわりに

あなたも、たのしい Misskey ライフを！

おわりです。

## 使用したライブラリなど

- BootStrap v5.0.2 (MIT LICENSE)
