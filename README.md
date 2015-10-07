# GPUサーバ構築手順 #

## ansibleのインストール ##
ansibleは構成管理ツールです。これを使ってパッケージのインストールや設定などを自動化します。

```sh
$ sudo apt-get install python-pip
$ sudo pip install ansible
```

## ansible用いてCUDAに必要なパッケージをインストールする ##
