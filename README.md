# MachiConnect

## 1. セットアップ手順
このアプリケーションをローカル環境で動作させるための手順です。

 ## 必須要件
  以下のソフトウェアがインストールされていることを確認してください。
 - Git
 - Docker
 - Docker Compose

 ## セットアップ手順
 1.  **リポジトリをクローン**
        まず、このリポジトリをローカルマシンにクローンします。
          git clone git@github.com:yuma33/MachiConnect.git
          cd MachiConnect

 2.  **Dockerコンテナのビルドと起動**
       バックエンド、フロントエンド、データベースのコンテナをビルドし、バックグラウンドで起動します。
       - touch backend/.env.local
       - docker compose build
       - docker compose up

 3.  **データベースの作成**
        コンテナが起動した状態で、Railsアプリケーション用のデータベースを作成します。
          docker-compose exec back rails db:create

 4.  **データベースのマイグレーション**
        データベースにテーブルを作成します。
          docker-compose exec back rails db:migrate

     以上でセットアップは完了です。

 ## その他のコマンド
  **コンテナの停止:**
    docker-compose down

  ##  動作確認方法
  - ローカルサーバーを起動し、ブラウザからアクセスして動作確認を行う
    **フロントエンド (React):** [http://localhost:8000](http://localhost:8000)
    **バックエンド (Rails API):** [http://localhost:3033](http://localhost:3033)
  - 新規登録、ログイン、イベント投稿、検索、参加申込を一通り試す

 ## 使用技術

  **コンテナ技術**
   Docker

  **バックエンド**
   Ruby 3.2.2
   Rails 7.1.2 (APIモード)

  **フロントエンド**
   React
   Node.js 21.5.0
   Tailwind CSS

  **データベース**
   MySQL 8.0

---

## ライブラリ
- sorcery（ユーザー認証）
- その他必要に応じて追加

---

## 実装機能の説明

### イベント情報の掲載・検索機能
- ユーザーはイベント情報を簡単に投稿・閲覧できる
- キーワード・カテゴリ・開催日時での検索が可能

### 参加申込機能
- イベントへの参加申込が可能

### ユーザー登録機能
- メールアドレス・パスワードによる登録・ログイン

---