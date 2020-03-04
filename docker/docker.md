# docker
## イメージ
### images
	docker images [オプション]
イメージを一覧表示する。
### pull
	docker pull [オプション] イメージ名
イメージをレジストリから取ってくる。
### rmi
	docker rmi [オプション] <イメージ名> [<イメージ名> ...]
イメージを削除する。

## コンテナ
### run
	docker run [オプション] <イメージ名> [コマンド] [引数 ...]
新しいコンテナを実行する。
#### オプション
##### -d, --detach
コンテナをバックグラウンド実行する。
##### -i, --interactive
コンテナに標準入出力を割り当てる。
##### -t, --tty
コンテナに擬似端末を割り当てる。
##### -e, --env
	-e 変数名=値
環境変数を指定する。
##### --name
	--name <コンテナ名>
コンテナ名を指定する。
##### -p
	-p <ホスト側>:<コンテナ側>
ホストとコンテナの間のポートフォワード設定
#### よくやりそうな起動例
##### ubuntuのコンテナubutu-contaierを起動して、シェルを起動する。
	docker run -it --name ubuntu-container ubuntu
##### nginxを起動して、ポートを1234に割り当てる。
	docker run -d --name niginx-container -p 1234:80 nginx

### ps
	docker ps [オプション]
#### オプション
##### -a, --all
全てのコンテナを表示する。(デフォルトでは実行中のみ表示する。)
##### -q
IDだけ表示する。
#### よくやりそうな起動例
##### 全てのコンテナを表示する。
	docker ps -a
##### 全てのコンテナを削除する。
	docker rm $(docker ps -a)

### rm
	docker rm [オプション] <コンテナID> [<コンテナID> ...]
コンテナを削除する。
