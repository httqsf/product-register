# Product Register（製品登録アプリケーション）

製品の登録・管理を行うためのシンプルなウェブアプリケーションです。

## システム要件

* Ruby 2.5.9
* Rails 5.2.8.1
* PostgreSQL (データベース)

## 環境構築方法

### Dockerを使用する場合

#### リポジトリをクローンした後、以下のコマンドを実行
```
docker-compose up -d
```

#### コンテナが起動していることを確認できたら、マイグレーションを実行
```
docker-compose exec web rails db:create db:migrate
```


## 使用方法

1. ブラウザで `http://localhost:3000` にアクセスします
2. 「New Product」をクリックして新しい製品を登録できます
3. 製品名、価格、ベンダー（製造元）を入力して登録します
4. 登録済みの製品は一覧で確認でき、編集・削除も可能です

## データベース構成

製品（Products）テーブル:
* name: 製品名（文字列）
* price: 価格（整数）
* vendor: ベンダー名（文字列）

## 開発情報

* 開発環境のセットアップには Docker と Docker Compose を使用しています
* PostgreSQL をデータベースとして使用しています
* テストの実行方法: `rails test`

## CI/CD構成

### GitHub Actions

このプロジェクトでは、GitHub Actionsを使用して継続的インテグレーション（CI）を実装しています。
すべてのプッシュおよびプルリクエストに対して、以下のテストが自動的に実行されます：

1. Dockerコンテナのビルドと起動
2. テスト用データベースの作成
3. テスト用データベースのマイグレーション
4. テストの実行

GitHub Actionsの設定ファイルは `.github/workflows/test.yml` にあります。実行環境はDocker Composeを使用しているため、ローカル開発環境と同じ構成でテストが実行されます。
