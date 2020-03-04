# docker
## イメージ
### 一覧表示
	docker images
### 取ってくる
	docker pull <イメージ名>
### 削除する
	docker rmi <イメージ名>
### コンテナからイメージを作る
	docker commit <コンテナ> [<リポジトリ名>[:<タグ>]]

## コンテナ
### イメージからコンテナを作る
#### シェルを実行して操作できるようにする。
	docker run -it <イメージ名>
#### バックグラウンドで実行する。
	docker run -d <イメージ名>
#### 環境変数を指定して実行する。
	docker run -e 変数名=値 <イメージ名>
### 一覧表示
	docker ps -a
### 削除
	docker rm <コンテナ>

## Dockerfile
### Dockerfileからイメージを作成する。
	Dockerfileと同じディレクトリで
	docker build
