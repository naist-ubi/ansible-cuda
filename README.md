# GPUサーバ構築手順 #

## ansibleのインストール ##
ansibleは構成管理ツールです。これを使ってパッケージのインストールや設定などを自動化します。

```sh
$ sudo apt-get install python-pip
$ sudo pip install ansible
```

## ansible用いてCUDAに必要なパッケージをインストールする ##

```sh
$ ansible-playbook cuda.yml
```
複数のサーバに対して操作を行う場合は `hosts` ファイルを用意して `-i` オプションで指定する。

```sh
$ ansible-playbook -i hosts cuda.yml
```