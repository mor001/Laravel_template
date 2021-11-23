# Laravelプロジェクト雛形

<pre>
.
├── docker
├── src
└── README.md
</pre>


## 以下Ubuntu20.04で動作確認

### dockerディレクトリに移動
cd docker

### docker起動
sudo service docker start

### コンテナ起動
docker-compose up -d --build

### PHPコンテナに入る
docker-compose exec php bash

### パーミッション設定
chmod -R 777 storage/ bootstrap/cache/

### nodeコンテナに入る
docker-compose exec node bash

npm run dev
(*エラー時 rm -rf node_modules rm package-lock.json)


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
