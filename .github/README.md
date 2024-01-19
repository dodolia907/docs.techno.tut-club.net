# TechnoTUT Docs
このリポジトリは、TechnoTUTのドキュメントを管理するためのリポジトリです。[こちら](https://docs.technotut.net/)から閲覧できます。  
Docusaurusを使用して作成されており、PushするとGitHub Actionsによって自動的にビルドされ、Cloudfare Pagesにデプロイされます。 

開発用コンテナのDockerfileは、`.devcontainer/Dockerfile`にあります。Dockerfileにコミットすると、GitHub Actionsによって自動的にビルドされ、GitHub PackagesにDockerイメージがアップロードされます。  
```
docker pull ghcr.io/technotut/dev.technotut.net:main
```
このDockerイメージを利用し、GitHub Codespaces または DockerとVisual Studio Code を用いた開発を行うことができます。詳しくは次章を参照してください。

## 環境構築
複数の方法による環境構築に対応しています。
- [GitHub Codespaces](codespaces.md)
- [Docker](docker.md)
- ローカル環境

ローカルでの開発には、Node.jsのインストールが必要です。

## 編集について
TechnoTUT Docsでは　`pull request` によるドキュメントの編集を受け付けています。  
編集するには、以下の手順を行ってください。  
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