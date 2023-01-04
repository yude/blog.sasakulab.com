---
title: "Windows 版しか提供されていない Electron バイナリを Wine で動かす"
date: 2023-01-04T20:00:00+09:00
type: posts
categories:
  - programming
tags:
  - Ubuntu
  - Electron
---

あけましておめでとうございます。新年最初のエントリがこれです。

## 注意

各サービスには必ず利用規約が存在します。

今回は、リバースエンジニアリング行為や、得たデータを改変して利用する行為などは行っておりません。

このブログエントリで得た情報を利用して、利用規約および各種法令、公序良俗に反する行為を行わないでください。

なお、このエントリで行った知識をユーザーが被った不利益については、筆者は責任を負いません。ご了承ください。

## Electron とは？

Electron は、JavaScript、HTML、CSS によるデスクトップアプリケーションを構築するフレームワークです。

Electron を利用して構築されているアプリケーション・サービスに著名なものは、"Visual Studio Code" や "GitHub Desktop" などがあります。

Electron の特徴として、クロスプラットフォームなバイナリをかんたんに作り上げることができるという特徴があります。

## 目的

先述したようにクロスプラットフォームをかんたんに実現できる、という特徴のある Electron です。

しかし、残念ながら、一部の不届き企業は、クロスプラットフォームに対応していない（とりわけ Linux には対応する気がない）場合が多いです。

ところで、Electron は、言ってしまえば、内部で Chromium を利用したただのウェブアプリケーションです。

アプリケーションの動作に必要な多くの DLL などはパッケージ化されている可能性が高いです。

つまり、Wine で雑に動かすにはもってこい、かもしれません。

ここだけ読んだら熟練者は続きを読まなくても構いません。いつもどおり Wine を動かすだけです。

## 初心者はここから

### Windows バイナリを手に入れる

#### インストールせず、直接起動できるバージョンのアプリ（ポータブルアプリ）がある場合

ラッキーですね。そのままダウンロードして、Linux に持ってきてください。

必要な場合（自己解凍形式の *.exe ファイルの場合など）は Windows で解凍しておくことをおすすめします。

#### インストーラーがある場合

大抵の場合は、ソフトウェアは、インストールという作業が必要です。

Wine は、インストールでコケる場合が多いので、Windows 環境で先にインストールして、展開されたアプリケーションをフォルダーごとコピーするほうが良いです。

といっても、Electron で開発されたソフトウェアは、大抵の場合、ダブルクリックするだけで UAC を必要とせず展開される場合が多いです。話が早くて助かりますね。

1. Windows 環境でソフトウェアを展開する

2. ソフトウェアが入ったフォルダーを探し当てる

- インストーラーが管理者特権の必要なタイプの場合は、`C:\Program Files` or `C:\Program Files (x86)` が多い
- インストーラーが管理者特権の不要なタイプの場合は、`C:\Users\{Username}\AppData\Roaming\` や、`C:\ProgramData\{Username}` の中にあることが多いです。

迷ったら、デスクトップのショートカットなどからプロパティを見てみましょう。

<img src="/assets/images/2023/ewb001.png" width="300px">

アプリケーションが含まれるフォルダーごと、Linux にコピーします。

### Wine をインストールする

WineHQ をインストールします。[公式ページ](https://wiki.winehq.org/Download)にあるとおりにインストールすれば良いです。

以下に、Ubuntu 22.04 の場合のインストール方法を示します。

```sh
sudo mkdir -pm755 /etc/apt/keyrings
sudo wget -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key
sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/winehq-jammy.sources
sudo apt update
sudo apt install --install-recommends winehq-stable
```

また、`winecfg`を呼び出します

```sh
winecfg
```

正常にダイアログボックスが出てきたら、閉じてください。

場合によっては、`winetricks`などをインストールしても構いませんが、ここでは割愛します。

### Windows バイナリが動作するか確かめる

先ほどの Windows バイナリがあるフォルダに移動します。

そして、以下の通りに起動します。

```sh
wine hoge.exe
```

正常に起動したら成功です。やったね！

## （任意）デスクトップエントリーを作る

このままでも動きますが、起動のたびにターミナルを開くのはナンセンスです。

せっかくなのでショートカットを作りましょう。

### シェルスクリプトを作る

以下のようにして、シェルスクリプトを作ります。

```sh
#!/bin/bash
wine /path/to/applicaton.exe

```

好きな名前で保存し、パスを覚えておきましょう（コピペ可）。

### デスクトップエントリーファイルを作る

`~/.local/share/applications` に移動します。

`{任意の名前}.desktop` ファイルを作成します。

```ini
[Desktop Entry]
Version=1.0
Type=Application
Name={ソフトの名前（表示名）}
Icon={あれば 画像アイコン}
Path={ソフトのフォルダのパス（カレントディレクトリの役割を果たす？）}
Exec={先ほどの シェルスクリプトのパス}
StartupNotify=true
```

例えば、これは Electron とは関係ありませんが、

```ini
[Desktop Entry]
Version=1.0
Type=Application
Name=Firefox
Icon=/home/{user}/software/firefox/firefox.png
Exec=/home/{user}/software/firefox/firefox
Path=/home/{user}/software/firefox/
StartupNotify=true
```

こんな感じです。

すると、ランチャーにソフトウェアが出てきます。

<img src="/assets/images/2023/ewb002.png" width="300px">

あとは、いつもの普通のソフトのように扱ってあげてください。

## おまけ

[#すべての公式アプリをクロスプラットフォームにしろ](https://twitter.com/search?q=%23%E3%81%99%E3%81%B9%E3%81%A6%E3%81%AE%E5%85%AC%E5%BC%8F%E3%82%A2%E3%83%97%E3%83%AA%E3%82%92%E3%82%AF%E3%83%AD%E3%82%B9%E3%83%97%E3%83%A9%E3%83%83%E3%83%88%E3%83%95%E3%82%A9%E3%83%BC%E3%83%A0%E3%81%AB%E3%81%97%E3%82%8D&src=typed_query)
[#すべての公式アプリをLinuxに対応させろ](https://twitter.com/search?q=%23%E3%81%99%E3%81%B9%E3%81%A6%E3%81%AE%E5%85%AC%E5%BC%8F%E3%82%A2%E3%83%97%E3%83%AA%E3%82%92Linux%E3%81%AB%E5%AF%BE%E5%BF%9C%E3%81%95%E3%81%9B%E3%82%8D&src=typed_query&f=top)
[#どうせElectronならLinuxに対応させろ](https://twitter.com/search?q=%23%E3%81%A9%E3%81%86%E3%81%9BElectron%E3%81%AA%E3%82%89Linux%E3%81%AB%E5%AF%BE%E5%BF%9C%E3%81%95%E3%81%9B%E3%82%8D&src=typed_query&f=top)
[#広島に秋月電子通商を](https://twitter.com/search?q=%23%E5%BA%83%E5%B3%B6%E3%81%AB%E7%A7%8B%E6%9C%88%E9%9B%BB%E5%AD%90%E9%80%9A%E5%95%86%E3%82%92&src=typed_query)
[#ついでに山口にも秋月電子通商を](https://twitter.com/search?q=%23%E3%81%A4%E3%81%84%E3%81%A7%E3%81%AB%E5%B1%B1%E5%8F%A3%E3%81%AB%E3%82%82%E7%A7%8B%E6%9C%88%E9%9B%BB%E5%AD%90%E9%80%9A%E5%95%86%E3%82%92&src=typed_query&f=top)
