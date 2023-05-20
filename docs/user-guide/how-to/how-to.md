---
title: このドキュメントの編集方法について
sidebar_label: 編集方法
sidebar_position: 1
---
# 概要
ここではこのドキュメントとTechnoTUTホームページの編集方法について説明します。

## 構成
このドキュメントとTechnoTUTホームページはGitHubとCloudflare Pagesで構成されています。
PushされるたびにGitHub Actionsがビルドし、Cloudflare Pages上にデプロイされます。内容を書き換えるには、GitHub上のリポジトリを編集する必要があります。

## 手順
全体の手順は以下の通りです。  
1. このリポジトリをfolkします。  
2. folkしたリポジトリをローカルにcloneします。  
3. ローカルで執筆用のbranchを作成します。  
4. `npm install` を実行して、必要なパッケージをインストールします。
5. 執筆を行います。  
6. 一段落したら、`npm start` を実行します。Webブラウザが自動的に開き、編集した内容が確認できます。  
7. 問題が無ければ、pull requestを送信します。
8. 管理者によってプルリクエストが承認されたら、自動でデプロイされます。