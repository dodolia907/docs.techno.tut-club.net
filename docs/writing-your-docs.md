# ドキュメントの書き方
## 概要
ここではこのドキュメントの書き方について説明します。  
また、TechnoTUTホームページについても同様の手順で書くことができます。  
TechnoTUTホームページの書き方については[こちら](/docs/hp/writing-your-hp.md)をご覧ください。

## 手順
1. このドキュメントのソースをcloneまたはpullします。
2. 作業用のブランチを作成します。
3. 作業用のブランチでドキュメントを編集します。
4. 編集が完了したらpushします。
5. GitHub上でプルリクエストを作成します。
6. 管理者によってプルリクエストが承認されたら、自動でデプロイされます。

### プルリクエストについて
[こちら](https://backlog.com/ja/git-tutorial/pull-request/01/)をご覧ください。

### 書式
このドキュメントはMKDocsを利用しています。MKDocsではMarkdown形式でドキュメントを書きます。   
Markdownの書式については[こちら](https://www.markdown.jp/what-is-markdown/)を参照してください。  
DiscordやSlackなどのチャットツールで使われていることが多いので、既に使っている人はすぐに使えると思います。

### 編集
docsフォルダ内に任意の名前で`.md`ファイルを作成し編集します。  
編集が終わったら、`mkdocs.yml`の`nav`に追加したファイルのパスを追加します。

### プレビュー
#### Pythonのインストール
[こちら](https://www.python.jp/install/windows/install_py3.html)を参照してください。
#### mkdocsのインストール
pip install mkdocsを実行します。  
[こちら](https://www.mkdocs.org/#installation)を参照してください。
#### プレビュー
`mkdocs serve`コマンドを実行し、任意のブラウザで`http://localhost:8000/`にアクセスすると表示されます。