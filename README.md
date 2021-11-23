# Laravelプロジェクト雛形

<pre>
.
├── docker
├── src
└── README.md
</pre>


#### 以下Ubuntu20.04で動作確認

### Laravelを動かすまで

- docker起動
`sudo service docker start`

- dockerディレクトリに移動
`cd docker`

- コンテナ起動
`docker-compose up -d --build`

- PHPコンテナに入る
`docker-compose exec php bash`

- パッケージをインストール
`composer install`

- .env作成
`cp .env.example .env`

- ストレージシンボリックリンク作成
`php artisan storage:link`

- アプリケーションキーを生成
`php artisan key:generate`

- マイグレーション実行
`php artisan migrate`

- パーミッション設定
`chmod -R 777 storage/ bootstrap/cache/`

- 動作確認
`http://127.0.0.1:8888/`

---

### css js コンパイル

- nodeコンテナに入る
`docker-compose exec node bash`

- パッケージインストール
`npm install`

- コンパイル
`npm run dev`
(*エラー時 rm -rf node_modules rm package-lock.json)

---

###メール送信テスト

- phpコンテナに入る
`docker-compose exec php bash`

`php artisan tinker`

`Mail::raw('hello world', function ($message) { $message->to('test@example.com')->subject('hello'); });`

`Ctrl + c で終了`

`http://127.0.0.1:8025/` で確認できる

---

### Minioの確認

`http://localhost:9001/` minio/minio123でログインして確認できる

---

### MEMO

- コンテナ起動
`docker-compose up -d`

- コンテナ削除
`docker-compose down`

- コンテナ、イメージ、ボリューム、ネットワークを一括完全消去
`docker-compose down --rmi all --volumes`

- phpコンテナに接続する（コンテナ名を変えて他のコンテナに接続できる）
`docker-compose exec php bash`

- Laravel install
`composer create-project laravel/laravel example-app`

- VSCode launch.jsonの構成
<pre>
{
  "version": "0.2.0",
  "configurations": [

    {
      "name": "Listen for Xdebug",
      "type": "php",
      "request": "launch",
      "port": 9003,
      "hostname": "0.0.0.0",
      "pathMappings": {
        "/var/www/html": "${workspaceRoot}"
      }
    }
  ]
}
</pre>