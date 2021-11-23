# Laravelプロジェクト雛形

<pre>
.
├── docker
├── src
└── README.md
</pre>


## 以下Ubuntu20.04で動作確認

### docker起動
sudo service docker start

### dockerディレクトリに移動
cd docker

### コンテナ起動
docker-compose up -d --build

### PHPコンテナに入る
docker-compose exec php bash

### Laravelに必要なパッケージインストール
composer install

### .env作成
cp .env.example .env

### ストレージシンボリックリンク作成
php artisan storage:link

### アプリケーションキーを生成
php artisan key:generate

### マイグレーション実行
php artisan migrate

### パーミッション設定
chmod -R 777 storage/ bootstrap/cache/

### 動作確認
http://127.0.0.1:8888/

---

### nodeコンテナに入る
docker-compose exec node bash

npm run dev
(*エラー時 rm -rf node_modules rm package-lock.json)

---

## MEMO
### コンテナ起動
$ docker-compose up -d

### コンテナ削除
$ docker-compose down

### コンテナ、イメージ、ボリューム、ネットワークを一括完全消去
$ docker-compose down --rmi all --volumes

### phpコンテナに接続する（コンテナ名を変えて他のコンテナに接続できる）
$ docker-compose exec php bash

### Laravel install
$ composer create-project laravel/laravel example-app
