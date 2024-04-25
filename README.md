# go_web_handson_todo_app

[詳解Go言語Webアプリケーション開発](https://amzn.asia/d/e5GpHGU)  

上記本のハンズオンで作成したアプリケーション

## アプリケーション概要

### 作成するアプリケーション概要
GUIの画面は作成しない。APIのみ作成する。以下、作成するAPIのエンドポイント一覧
| HTTPメソッド | パス | 概要 |
| ---- | ---- | ---- |
| POST | /register | 新しいユーザーを登録する |
| POST | /login | 登録済みユーザー情報でアクセストークンを取得する |
| POST | /tasks | アクセストークンを使ってタスクを登録する |
| GET  | /tasks | アクセストークンを使ってタスク一覧を取得する |
| GET  | /admin | 管理者権限のユーザーのみがアクセスできる |

### 「Beyond the Twelve-Factor App」に準拠したWebアプリケーションの実装
クラウドネイティブアプリ開発によく参考にされる設計指針らしい。  
以下、参考にさせていただいたQiitaの記事
- [Beyond the Twelve-Factor Appを意訳してみた（前半）](https://qiita.com/takurUN/items/b8bf6fa193ffac5ef431)
- [Beyond the Twelve-Factor Appを意訳してみた（後半）](https://qiita.com/takurUN/items/20424b3d3d8d4c97943f)

### アプリケーションの構成
以下の図のようなRDBMSとインメモリデータベースを利用したREST APIサーバー
- MySQL
- Redis

![アプリケーションイメージ](/drawio/app_image.png)


### テストコード
テスト駆動のように先にテストを書く手法は慣れてないと難しいため、以下の順で進める。

1. プロダクションコードの実装
2. プロダクションコードのテストコードを作成
3. テストコードから問題点を探す
4. 3を元にリファクタリングする

### その他使用するもの
- Docker
- GitHub Actions


## 学んだこと

### ghコマンド
ghコマンドをインストールすることで、ローカルからサクッとリポジトリの作成ができた。  
以下リポジトリを作成した時のコマンド

```sh
❯ gh repo create
? What would you like to do? Create a new repository on GitHub from scratch
? Repository name go_web_handson_todo_app
? Description TODO Web Application
? Visibility Public
? Would you like to add a README file? Yes
? Would you like to add a .gitignore? Yes
? Choose a .gitignore template Go
? Would you like to add a license? Yes
? Choose a license MIT License
? This will create "go_web_handson_todo_app" as a public repository on GitHub. Continue? Yes
✓ Created repository Yuji-Momotani/go_web_handson_todo_app on GitHub
  https://github.com/Yuji-Momotani/go_web_handson_todo_app
? Clone the new repository locally? Yes
Cloning into 'go_web_handson_todo_app'...
```

`gh repo create`でリポジトリの作成とcloneが一気にできる。  
コマンド打った後は質問されたことに答えるだけでOK！

もしかして、Alfredの`gh`ってこのコマンドを使っているのか？