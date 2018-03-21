Docker for Fess
=====

See [https://hub.docker.com/r/codelibs/fess/](https://hub.docker.com/r/codelibs/fess/).

## Docker Images

-   [`latest`, `12`, `12.1`, `12.1.1` (*12.1/Dockerfile*)](https://github.com/codelibs/docker-fess/blob/master/12.1/Dockerfile)
-   [`12.0`, `12.0.3` (*12.1/Dockerfile*)](https://github.com/codelibs/docker-fess/blob/master/12.0/Dockerfile)
-   [`11.4.0`, `11.4.4`, `11.4.5`, `11.4.6` (*11.4/Dockerfile*)](https://github.com/codelibs/docker-fess/blob/master/11.4/Dockerfile)
-   [`11.3`, `11.3.0`, `11.3.1`, `11.3.2` (*11.3/Dockerfile*)](https://github.com/codelibs/docker-fess/blob/master/11.3/Dockerfile)
-   [`11.2`, `11.2.1`, `11.2.2` (*11.2/Dockerfile*)](https://github.com/codelibs/docker-fess/blob/master/11.2/Dockerfile)
-   [`11.1`, `11.1.1` (*11.1/Dockerfile*)](https://github.com/codelibs/docker-fess/blob/master/11.1/Dockerfile)
-   [`11.0`, `11.0.4` (*11.0/Dockerfile*)](https://github.com/codelibs/docker-fess/blob/master/11.0/Dockerfile)
-   [`10`, `10.3`, `10.3.4` (*10.3/Dockerfile*)](https://github.com/codelibs/docker-fess/blob/master/10.3/Dockerfile)
-   [`10.2`, `10.2.3` (*10.2/Dockerfile*)](https://github.com/codelibs/docker-fess/blob/master/10.2/Dockerfile)
-   [`10.1`, `10.1.3` (*10.1/Dockerfile*)](https://github.com/codelibs/docker-fess/blob/master/10.1/Dockerfile)
-   [`10.0`, `10.0.4` (*10.0/Dockerfile*)](https://github.com/codelibs/docker-fess/blob/master/10.0/Dockerfile)

## What is Fess ?

Fess is very powerful and easily deployable Enterprise Search Server. You can install and run Fess quickly on any platforms, which have Java runtime environment. Fess is provided under Apache license.

Fess is Elasticsearch-based search server, but knowledge/experience about Elasticsearch is NOT needed because of All-in-One Enterprise Search Server. Fess provides Administration GUI to configure the system on your browser. Fess also contains a crawler, which can crawl documents on Web/File System/DB and support many file formats, such as MS Office, pdf and zip.

For more info, access [Fess official documentation](http://fess.codelibs.org/).

## Getting Started

### Run Fess

You can access http://localhost:8080 from the host OS with:

```console
$ docker run -d -p 8080:8080 --name fess codelibs/fess:latest
```

### Run Fess with Kibana

To monitoring Fess logs with Kibana, run Fess and Kibana with these commands:

```console
$ docker run -d --name fess codelibs/fess:latest
$ docker run -d -e ELASTICSEARCH_URL=http://localhost:9200 \
    --name kibana kibana:latest
```

and import settings with following this [link](https://github.com/codelibs/fess/blob/master/src/main/assemblies/extension/kibana/README.md).

### Run Fess with Your Data/Config

To save data and config for Fess/Elasticsearch, use -v option for mount host directory:

```console
$ mkdir ./data
$ sudo chown 1000:1000 ./data
$ docker run -d -p 8080:8080 --name fess \
    -v $PWD/fess/config:/opt/fess \
    -v $PWD/es/config:/etc/elasticsearch \
    -v $PWD/es/data:/var/lib/elasticsearch codelibs/fess:latest
```

You can put fess_config.properties to fess/config directory.
If you want to use a default setting for Elasticsearch, remove `-v $PWD/es/config:/etc/elasticsearch`.

## Kernel settings

Elasticsearch needs to set vm.max_map_count to  at least 262144. See [Install Elasticsearch with Docker](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html#docker-cli-run-prod-mode).

# License

Apache license.
