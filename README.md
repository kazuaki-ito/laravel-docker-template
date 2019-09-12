# laravel-docker-template

docker-composeを利用してlaravelの開発環境を構築するためのテンプレートです。

mac環境を想定しているのでlinuxなどその他環境では微調整が必要となります。

## 環境の起動

①コンテナの起動
```bash
export UID=${UID}
docker-compose up -d
```

②起動確認
```bash
docker-compose ps
     Name                   Command              State                    Ports
-------------------------------------------------------------------------------------------------
template-app     docker-php-entrypoint php-fpm   Up      0.0.0.0:8000->8000/tcp, 9000/tcp
template-nginx   nginx -g daemon off;            Up      0.0.0.0:443->443/tcp, 0.0.0.0:80->80/tcp
```
＃nginxとapp(php-fpmp)コンテナが起動(State=Up)していたらOK

### その他コマンドの実行について

コンテナ上でコマンドを実行する場合下記のように実行する
```
# docker-compose exec app [コマンド]
docker-compose exec app echo test
```

## Laravelのインストール

①templateというフォルダ名でlaravel project を生成
```bash
docker-compose exec app composer create-project --prefer-dist laravel/laravel template 
```

②カレントディレクトリに必要なファイルを移動
```bash
rm -rf template/README.md && rm -rf template/.gitignore && mv template/* . && mv template/.* . && rm -rf template 
```

③ ブラウザで下記URLにアクセス

```
http://localhost/
```

