---
title: "Misskey Now v0.2.0 公開のお知らせ"
date: 2023-02-13T09:00:00+09:00
type: posts
permalink: /tools/misskey-now/update/1
categories:
  - tools
tags:
  - Misskey
  - SNS
  - Browser Extension
---

\Misskey Now v0.2.0 を公開します。[こちら](/tools/misskey-now) もお読みください。

<img src="/assets/images/2023/mk_v0.2.0_001.png" width="300px">

## Ver 0.2.0 の内容

### 複数アカウント（インスタンス）に対応しました

複数アカウントの切り替えに対応いたしました。

「新しいプロファイル」を選択して保存すると、新しいプロファイルが作成されます。

すでに作成されたプロファイルを変更して保存すると、すでにあるプロファイルが更新されます。

<img src="/assets/images/2023/mk_v0.2.0_002.png" width="300px">

### 前バージョンからの設定移行を自動で行う

前バージョンとブラウザに保存されるデータの構造が変更されます。

これに伴うユーザーの皆さまの操作はありません。

### Ctrl + Enter で送信

- Thanks to @KusaReMKN

Note にフォーカスされたあと、Ctrl + Enter でノートが送信されます。

これに伴い、自動で Note にフォーカスされます。

### 各ボタンを押したとき、動作が成功したらボタンの状態を変える

成功・失敗がわかりやすくなりました。

### Misskey Now に統一する

Misskey-Now にしていた名前を Misskey Now に統一しました。

リポジトリ名は今までどおり `misskey-now` です。

### `async`/`await` でコードの書き換え

- Thanks to @KusaReMKN

これにより、偶発的に起こるプロファイルのエラーが発生しにくくなります。

これに伴うユーザーの皆さまの操作はありません。

### `console.log` で表示していた送信リクエストの詳細の廃止

API キーが簡単にログに残っていたため、非表示にしました。

おそらく、今後の更新で、表示・非表示を選択できるようにすると思います。

## 更新・インストール

各拡張機能プロバイダーから利用している場合、**アップデートの審査が完了し次第**、通常は自動更新されます。

拡張機能をインストールして、お待ちください。

|ソース|リンク|備考|
|----|----|----|
|Chrome ウェブストア|[Misskey Now](https://chrome.google.com/webstore/detail/misskey-now/gaanhijofgiahpbmjelcfhccepcgbekh?hl=ja)||
|Firefox Addons|[Misskey Now](https://addons.mozilla.org/ja/firefox/addon/misskey-now/)||
|GitHub Release|[GitHub](https://github.com/sasakulab/misskey-now)||

ちなみに、開発版をいち早く試したいあなたは、以下のリポジトリをクローンして、[chrome://extensions](chrome://extensions/) や [about:debugging#/runtime/this-firefox](about:debugging#/runtime/this-firefox) よりディレクトリごと読み込むことで試すことができます。

もし良ければ、デバッグなどにご協力いただけると助かります。

## 今後の更新

### 診断メーカーなど特定のサイトで、結果を自動でノートに入力する

シェアボタンがないことで一番不都合に感じる場面を Misskey Now によって解決します。

## お問い合わせ

バグ報告などはこちらにご送信ください。

- [Issues · sasakulab/misskey-now](https://github.com/sasakulab/misskey-now/issues?q=is%3Aopen+is%3Aissue)
- [@ayato_sasakura@mi.yude.moe](https://mi.yude.moe/@ayato_sasakura)
