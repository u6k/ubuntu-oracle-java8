# ubuntu-oracle-java8

Dockerコンテナ(ubuntu:latest)にoracle-java8をインストールします。

## 確認したいこと

* Dockerコンテナにoracle-java8をインストールして、最低限の動作確認としてバージョン情報を表示できること。

## 前提条件

* VirtualBox
    * Windows、またはOS Xの場合。
    * `cinst virtualbox`(Windowsの場合)、`brew install virtualbox`(OS Xの場合)などでインストール可能です。
* Docker Machine
    * Windows、またはOS Xの場合。LinuxはDockerホスト構築が必要ないため、不要。
    * `cinst docker-machine`(Windowsの場合)、`brew install docker-machine`(OS Xの場合)などでインストール可能です。
* Docker Client
    * Linuxの場合。

## 確認手順

Windowsを前提に説明しますが、Docker Machineが使えるならどのOSでも大差無いはずです。

### Dockerホストを構築

```
docker-machine create --driver virtualbox test
```

Dockerホストにsshログインします。

```
docker-machine ssh test
```

### Dockerイメージを構築

Dockerホスト内で、Dockerfileをダウンロードします。

```
git clone https://github.com/u6k/ubuntu-oracle-java8.git
```

Dockerイメージを構築します。かなり時間がかかります。

```
docker build -t u6k/ubuntu-oracle-java8 .
```

イメージ一覧を表示して、構築したイメージが含まれていることを確認します。

```
docker images
```

### Dockerコンテナを実行

構築したイメージを実行します。成功すると、Javaバージョン情報が表示されます。

```
docker run u6k/ubuntu-oracle-java8
```
