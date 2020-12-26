# jmeter_sample
jmeter演習サンプル

演習で直接サーバーに負荷をかけるのも、問題が生じる可能性があるので、
ローカルのDockerコンテナで演習をすすめます。

### 今回使うシナリオファイル（jmx）
https://github.com/takashi-yamada-f/jmeter_sample/blob/main/jmeter_scenario/list.jmx

### アクセスするURLを定義するCSVファイル
https://github.com/takashi-yamada-f/jmeter_sample/blob/main/jmeter_scenario/url.list

### PCにdockerをインストールし起動します。アカウント登録も必要です。
https://www.docker.com/

### git cloneします。
```
$ git clone https://github.com/takashi-yamada-f/jmeter_sample.git
```

### git cloneし演習用dockerコンテナを作成、起動します。

今回は8080ポートで、php70-apacheという名前のコンテナを作成します。
```
$ cd jmeter_sample
$ cd docker
$ docker build --tag php70-apache ./
$ docker run -d --name php70-apache  -p 8080:80 php70-apache
```

dockerコンテナの起動を確認
```
$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                  NAMES
0c9372d58eab   php70-apache   "docker-php-entrypoi…"   57 seconds ago   Up 56 seconds   0.0.0.0:8080->80/tcp   php70-apache
```

コンテナにログインする場合
```
$ docker container exec -ti php70-apache bash
```
Ctrl + D でログアウト

コンテナ上でTOPコマンドを起動。Jmeter実行時のサーバーリソースを監視します。<br>
本来のサーバより、反応にぶいです。。。ここは割り切って使いましょう。
```
# TOP
```
Ctrl + C でログアウト

Apacheのログを表示する
```
$ docker logs [ContainerID]
```

Containerを停止する
```
$ docker stop [ContainerID]
```

Containerを削除するとき
```
$ docker rm [ContainerID]
```

