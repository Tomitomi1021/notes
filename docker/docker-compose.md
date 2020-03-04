# Docker-compose
詳しい話は[Compose ファイル・リファレンス](docs.docker.jp/compose/compose-file.html)を参照
ここでは逆引きを示す。

## 文法
サービス等をdocker-compose.ymlで定義する。
フォーマットはyamlである。詳しくは[yaml](https://github.com/Tomitomi1021/notes/blob/master/format/yaml.md)を参照。
設定項目はservices,networks,volumesの3つである。

## services
個々のサービスを下のような形式で定義する。(サービスとコンテナが対応する。)
```
services:
  service1:
    service1の設定
  service2:
    service2の設定
```
### Dockerfileを指定する
```
build: <dockerfileのあるディレクトリ>
```
または
```
build:
  context: <Dockerfileがある場所のディレクトリ名またはURL>
  dockerfile: <Dockerfileの代わりになるもの>
  args:	
    - 引数名=値
    - 引数名=値
    ...
  または
  args:
    引数名: 値
    引数名: 値
    ...
```
### ポートフォワード設定
```
ports:
  - "<ホスト側ポート>:<コンテナ側ポート>"
```
### ネットワークの設定
```
networks:
  - <ネットワーク名(ネットワーク設定で定義)>
```
または
```
networks:
  <ネットワーク名>:
    <オプション>
```
#### ipアドレスを振る場合
net1につながるネットワークアダプタにipアドレスを振る例
```
networks:
  net1:
    ipv4_address: <ipv4 アドレス>
    ipv6_address: <ipv6 アドレス>
```
### 環境変数の定義
```
environment:
  - 変数名=値
  - 変数名=値
  ...
```
または
```
environment:
  変数名: 値
  変数名: 値
  ...
```
## networks
個々のネットワークを下のような形式で定義する。
```
networks:
  net1:
    driver: <ドライバー名>
    net1の設定
  net2:
    driver: <ドライバー名>
    net2の設定
  ...
```
ドライバー名は基本的には単一ホスト上ならbridge、swarm上ならoverlay。
より詳しい設定は、ipam設定で行える。書き方は以下の通り。
```
ipam:
  driver: default
  config: 
    - subnet: <サブネットアドレス(CIDR表記)>
      ip_range: <ネットワークアドレス(CIDR表記)>
      gateway:  <ゲートウェイのアドレス(CIDR表記)>
```
## volumes
```
volumes:
  volume1:
    volume1のオプション
  volume2:
    volume2のオプション
  ...
```
