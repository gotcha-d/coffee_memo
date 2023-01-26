# コーヒーアプリ

## 概要
このアプリでできること（したいこと）
* ドリップタイマー
* コーヒー豆とお湯の比率計算
* コーヒー豆に関する情報

## 構成要素
## 使い方
### 環境構築編
1. GitHubからリポジトリをクローン
    ```bash
    git clone https://github.com/gotcha-d/coffee_memo.git
    ```
1. appコンテナにLaravelインストール
    この時点ではlaravelの``app/vendor``ディレクトリがないのでエラーになる
    ```bash
    # appコンテナに入る
    docker-compose exec app bash
    # キャッシュ、エラーログ書き込み用の権限付与
    chmod -R 777 storage bootstrap/cache
    # vendorディレクトリにライブラリ群インストール
    composer install
    ```
1. .envファイルがないので、.env.exampleをコピーして.envにリネーム
    ```bash
    cp .env.example .env
    ```
1. .envのDB設定を次のように書き換え
    ```env
    DB_CONNECTION=pgsql
    DB_HOST=db
    DB_PORT=5432
    DB_DATABASE=coffee_memo
    DB_USERNAME=phper
    DB_PASSWORD=secret
    ```
1. アプリケーションキーを生成
    ```bash
    php artisan key:generate
    ```
1. シンボリックをはる<br>
    システムで作成したファイル等をブラウザからアクセスできるように公開するため
    ```bash
    php artisan storage:link
    ```
1. マイグレーションを実行
    ```bash
    php artisan migrate
    ```
1. appコンテナから抜ける
    ```bash
    exit
    ```