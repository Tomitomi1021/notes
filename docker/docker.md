# docker
## イメージ
### 一覧表示
```
docker images
```
### 取ってくる
```
docker pull <イメージ名>
```
### 削除する
```
docker rmi <イメージ名>
```
### コンテナからイメージを作る
```
docker commit <コンテナ> <イメージ名>
```

## コンテナ
### イメージからコンテナを作る
#### シェルを実行して操作できるようにする。
```
docker run -it --name <コンテナ名> <イメージ名>
```
#### バックグラウンドで実行する。
```
docker run -d  --name <コンテナ名> <イメージ名>
```
#### 環境変数を指定して実行する。
```
	docker run -e 変数名=値 --name <コンテナ名> <イメージ名>
```
### 一覧表示
```
	docker ps -a
```
### 削除
```
	docker rm <コンテナ>
```

## Dockerfile
### Dockerfileからイメージを作成する。
Dockerfileと同じディレクトリで
```
	docker build -t <イメージ名>
```
