# ElasticSearch Dockerfile

This repository contains **Dockerfile** of [ElasticSearch](http://www.elasticsearch.org/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/neglectedvalue/elasticsearch/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).

## Base Docker Image

* [java:8-jre](https://registry.hub.docker.com/_/java/)

## Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/neglectedvalue/elasticsearch/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull neglectedvalue/elasticsearch`

   (alternatively, you can build an image from Dockerfile: `docker build -t="neglectedvalue/elasticsearch" github.com/neglectedvalue/elasticsearch`)

## Usage

  ```sh
  docker run -d -p 9200:9200 -p 9300:9300 neglectedvalue/elasticsearch
  ```

### Attach persistent/shared directories

  Image provides two volumes `/logs` and `/data`.

  ```sh
  docker run -d -p 9200:9200 -p 9300:9300 -v <data-dir>:/data -v <logs-dir>:/logs neglectedvalue/elasticsearch
  ```

After few seconds, open `http://<host>:9200` to see the result.

# Avalible tags

## `latest`, `1.4.2`

Contains ElasticSearch itself.

## `lovely-plugins`, `1.4.2-lovely-plugins`

Contains ElasticSearch itself and these plugins:

  1. [Elastic HQ][1]

    Sleek, intuitive, and powerful ElasticSearch Management and Monitoring.

    You will find it at `http://<host>:9200/_plugin/HQ`

  2. [elasticsearch-head][2]

    elasticsearch-head is a web front end for browsing and interacting with an Elastic Search cluster.

    You will find it at `http://<host>:9200/_plugin/head`

  3. [River RethinkDB][3]

    This is a plugin for Elasticsearch that pulls in documents from RethinkDB, then indexes new/updated/deleted documents in real time. Elasticsearch gives you the ability to do full-text search.

  [1]: http://www.elastichq.org/
  [2]: http://mobz.github.io/elasticsearch-head/
  [3]: https://github.com/rethinkdb/elasticsearch-river-rethinkdb
