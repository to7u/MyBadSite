# README

## 操作

### 起動コマンド

docker-compose up -d

### 各ポートについて

metasploitable2:8010
bwapp:8020
badstore:8030
dvwa:8040
juiceshop:8050

### 各サービスへのアクセス方法

http://localhost:{各ポート番号}


### 各サービスについて

### bwapp

まずはじめに/install.phpへアクセスしインストールを行う

その後、トップよりID"bee"、PASS"bug"でログインできる

### dvwa

認証情報

ID:"admin"、PASS"password"

---

## docker container 個別実行版コマンド

ホスト側のポートは適宜、任意のものを指定すること 

### kali

imageファイルを直接取得することでも可能

Dockerfileからimageを作成
cd kali
docker build -t my_kali .  /bin/zsh

imageからcontainerを作成
docker run --name my_kali -itd my_kali

### metasploitable2

複数ポートのフォワーディングをする場合にはスクリプト化するか、composerで起動するのが良い
docker run --name metasploitable2 -dit -p tleemcjr/metasploitable2 /bin/bash

### bwapp

docker run --name bwapp -dit -p 8020:80 raesene/bwapp

### badstore

docker run --name badstore -dit -p 8030:80 jvhoof/badstore-docker

### dvwa

docker run --name dvwa -dit -p 8040:80 vulnerables/web-dvwa

### juiceshop

docker run --name juiceshop -dit -p 8050:3000 bkimminich/juice-shop

---

## 各コンテナへのアクセス方法

### dockerを使用している場合

今回はbashを使用しているが別のシェルでも可能
docker exec -it {コンテナ名　または コンテナID} /bin/bash


### docker composerを使用している場合

docker-compose exec {サービス名} bash

例：
docker-compose exec kali zsh

---