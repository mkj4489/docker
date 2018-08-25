# docker
- Dockerで開発環境の構築方法
- Docker自体は、Go言語で書かれている。

- Docker のインストール
  - https://store.docker.com/editions/community/docker-ce-desktop-windows

- バージョンの確認
  - docker --version


```docker run hello-world```
  - https://hub.docker.com/_/hello-world/

- docker hub
  - https://hub.docker.com/

### Dockerイメージとは
- コンテナ実行に必要なファイルをまとめたファイルシステム
- AUFSなどの特殊なファイルシステムが使用されている
- イメージのデータはレイヤーで構成され、読み取り専用
- Dockerイメージに同じレイヤーがあれば、差分のみダウンロードを行う。（Dockerイメージの継承）

#### whalesay コンテナの実行
- 好きな言葉をクジラに話させるイメージ
```
docker run docker/whalesay cowsay Hello!
________
< Hello! >
 --------
    \
     \
      \
                    ##        .
              ## ## ##       ==
           ## ## ## ##      ===
       /""""""""""""""""___/ ===
  ~~~ {~~ ~~~~ ~~~ ~~~~ ~~ ~ /  ===- ~~~
       \______ o          __/
        \    \        __/
          \____\______/
```
          
### ローカルのdocker imageの管理
- ローカルのdockerイメージの確認
```docker images```
- タグ付け：リポジトリ名(my_walesay)をつけるコマンド
``` docker tag docker/whalesay my_whalesay```
- タグ付け(repo1)するコマンド
``` docker tag docker/whalesay my_whalesay:repo1```
- イメージの詳細情報を表示するコマンド
```docker inspect my_whalesay```
- ローカルのイメージを削除するコマンド
```docker rmi docker/whalesay```
- イメージを取得するコマンド(tag名を指定しない場合は、latestが取得される。latestが最新とは限らない)
```docker pull docker/whalesay```

### Dcokerfileを使用したイメージビルド方法
```vim Dockerfile```
```
FROM docker/whalesay:latest

RUN apt-get -y update && apt-get install -y fortunes

CMD /usr/games/fortune | cowsay
```
- Dockerfileからイメージ（この場合は、docker-whaleという名前）をビルドするコマンド(カレントディレクトリのファイルでビルドなので、最後に.がある)
```docker build -t docker-whale . ```
- 上記コマンドはDockerfileが変更されない限り、キャッシュされる。キャッシュしたくない場合は以下で実行。
```docker build --no-cache -t docker-whale```

### Docker Hubに登録する
- https://hub.docker.com/add/repository/
- Docker Hubにログインする場合
  ```docker login```
- Dcoker Hubにおけるタグ付けルール
```<Docker ID>/<イメージ名>:<タグ名>```
- pushするコマンド
```docker push <Docker ID>/<イメージ名>:<タグ名>```
  
