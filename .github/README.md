# TechnoTUT Docs
このリポジトリは、TechnoTUTのドキュメントを管理するためのリポジトリです。[こちら](https://docs.technotut.net/)から閲覧できます。  
Docusaurusを使用して作成されており、PushするとGitHub Actionsによって自動的にビルドされ、Cloudfare Pagesにデプロイされます。

## 編集について
TechnoTUT Docsでは　`pull request` によるドキュメントの編集を受け付けています。  
編集するには、以下の手順を行ってください。なお、事前にnode.jsのインストールが必要です。  
1. このリポジトリをfolkします。  
2. folkしたリポジトリをローカルにcloneします。  
3. ローカルで執筆用のbranchを作成します。  
4. `npm install` を実行して、必要なパッケージをインストールします。
5. 執筆を行います。  
6. 一段落したら、`npm start` を実行します。Webブラウザが自動的に開き、編集した内容が確認できます。  
7. 問題が無ければ、pull requestを送信します。

## ディレクトリ構成について
- `docs/` : ドキュメントのソースファイルが格納されています。
- `static/img/` : ドキュメントで使用する画像ファイルが格納されています。