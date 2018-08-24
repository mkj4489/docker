# docker
- Dockerで開発環境の構築方法
- Docker自体は、Go言語で書かれている。

- Docker のインストール
- https://store.docker.com/editions/community/docker-ce-desktop-windows

- バージョンの確認
- docker --version


- docker run hello-world
- https://hub.docker.com/_/hello-world/

- docker hub
- https://hub.docker.com/

- Dockerイメージとは
- コンテナ実行に必要なファイルをまとめたファイルシステム
- AUFSなどの特殊なファイルシステムが使用されている
- イメージのデータはレイヤーで構成され、読み取り専用
- Dockerイメージに同じレイヤーがあれば、差分のみダウンロードを行う。（Dockerイメージの継承）
