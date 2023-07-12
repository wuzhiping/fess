Docker for Fess
=====
sudo apt-get update
<br>
sudo apt-get install docker-compose-plugin

第一步 设置vm.max_map_count
OpenSearch/Elasticsearch needs to set vm.max_map_count to at least 262144. See Important settings.

# linux 教程
# https://opensearch.org/docs/latest/install-and-configure/install-opensearch/index/#important-settings

# 检查当前值
cat /proc/sys/vm/max_map_count

# To increase the value, add the following line to /etc/sysctl.conf:
vm.max_map_count=262144

# Then run sudo sysctl -p to reload. 
sudo sysctl -p

第二步 run

git clone https://github.com/codelibs/docker-fess.git
cd docker-fess/compose
docker compose -f compose.yaml -f compose-opensearch2.yaml up -d


UI : http://localhost:8080
Admin UI: http://localhost:8080/admin/
账户密码   == 》 admin /admin
=====

See [Docker Images](https://github.com/codelibs/docker-fess/pkgs/container/fess/versions).

## What is Fess?

Fess is very powerful and easily deployable Enterprise Search Server. You can install and run Fess quickly on any platforms, which have Java runtime environment. Fess is provided under Apache license.

Fess is OpenSearch/Elasticsearch-based search server, but knowledge/experience about OpenSearch/Elasticsearch is NOT needed because of All-in-One Enterprise Search Server. Fess provides Administration GUI to configure the system on your browser. Fess also contains a crawler, which can crawl documents on Web/File System/DB and support many file formats, such as MS Office, pdf and zip.

For more info, access [Fess official documentation](http://fess.codelibs.org/).

## Getting Started

### Kernel settings

OpenSearch/Elasticsearch needs to set vm.max\_map\_count to  at least 262144. See [Important settings](https://opensearch.org/docs/latest/install-and-configure/install-opensearch/index/#important-settings).

### Run Fess

You can access http://localhost:8080 from the host OS with:

```console
$ git clone https://github.com/codelibs/docker-fess.git
$ cd docker-fess/compose
$ docker compose -f compose.yaml -f compose-opensearch2.yaml up -d
```
For more details, please see [compose](https://github.com/codelibs/docker-fess/tree/master/compose).

## Build

### Fess

To build docker images, run as below:

```console
$ docker build --rm -t ghcr.io/codelibs/fess:<tag name> ./fess/<version_dir>/
```

### OpenSearch

```console
$ docker build --rm -t ghcr.io/codelibs/fess-opensearch:<tag name> ./opensearch/<version_dir>/
```

### Elasticsearch

```console
$ docker build --rm -t ghcr.io/codelibs/fess-elasticsearch:<tag name> ./elasticsearch/<version_dir>/
```

## License

[Apache License 2.0](LICENSE)
