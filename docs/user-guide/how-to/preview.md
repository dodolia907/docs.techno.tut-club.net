# プレビュー画面を見ながら編集する
このドキュメントの編集も、ホームページの編集も、プレビュー画面を見ながら編集することができます。
## このドキュメントのプレビュー
プレビュー画面では、編集内容を保存するたびに自動的に更新されます。
### Pythonのインストール
[こちら](https://www.python.jp/install/windows/install_py3.html)を参照してください。
### mkdocsのインストール
`pip install mkdocs`を実行します。  
[こちら](https://www.mkdocs.org/#installation)を参照してください。
### プレビュー
`mkdocs serve`コマンドを実行し、任意のブラウザで`http://localhost:8000/`にアクセスすると表示されます。
## ホームページのプレビュー
### Hugoのインストール
Hugoをインストールします。  
[こちら](https://gohugo.io/getting-started/installing/)を参照してください。  
Windowsの場合は、zipファイルをダウンロードして解凍し、パスを通します。
### プレビューの実行
`hugo -D server`を実行します。  
任意のブラウザで`http://localhost:1313/`にアクセスするとプレビューが表示されます。