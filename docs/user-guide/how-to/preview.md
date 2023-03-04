---
title: プレビューについて
sidebar_label: プレビューについて
sidebar_position: 4
---
# プレビュー画面を見ながら編集する
このドキュメントの編集も、ホームページの編集も、プレビュー画面を見ながら編集することができます。
## このドキュメントのプレビュー
プレビュー画面では、編集内容を保存するたびに自動的に更新されます。
### Node.jsのインストール
Node.jsをインストールします。  
Windowsの場合は、nodejs.orgからインストーラをダウンロードしてインストールします。[こちら](https://nodejs.org/ja/download/)を参照してください。LTS版のインストールを推奨します。  
Macの場合は、Homebrewを使用してインストールします。`brew install node`を実行してください。
### Docusaurusのインストール
Docusaurusをインストールします。`package.json`があるディレクトリで`npm install`を実行します。
### プレビューの実行
`npm start`を実行します。自動でブラウザが開き、プレビューが表示されます。  

## ホームページのプレビュー
### Hugoのインストール
Hugoをインストールします。  
[こちら](https://gohugo.io/getting-started/installing/)を参照してください。  
Windowsの場合は、zipファイルをダウンロードして解凍し、パスを通します。
### プレビューの実行
`hugo -D server`を実行します。  
任意のブラウザで`http://localhost:1313/`にアクセスするとプレビューが表示されます。