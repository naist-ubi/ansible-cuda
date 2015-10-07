# GPUサーバ構築手順 #

## ansibleのインストール ##
ansibleは構成管理ツールです。これを使ってパッケージのインストールや設定などを自動化します。

```sh
$ sudo apt-get install python-pip
$ sudo pip install ansible markupsafe
```

## ansible用いてCUDAに必要なパッケージをインストールする ##

gitでplaybookをローカルにクローンする。

```sh
$ sudo apt-get install git
$ git clone git@gist.github.com:6778b6545c41f0e8c774.git cuda
$ cd cuda
```
ansibleを実行し、必要なパッケージのインストールと設定を行う。  
複数のサーバに対して操作を行うために `hosts` ファイルを用意して `-i` オプションで指定する。

```
[group]
192.168.0.100
192.168.0.101
192.168.0.102
192.168.0.103

[all:vars]
ansible_sudo_pass=”パスワード”
```

```sh
$ ansible-playbook -i hosts cuda.yml
```

### sshの接続でエラーになる場合 ###
暗黙的に `~/.ssh/id_rsa.pub` のssh鍵を使用するためこれを `authorized_keys` に追加しておく必要があります。  
鍵を作っていない場合はパスワードを聞かれ、入力すれば接続できるはずです。

