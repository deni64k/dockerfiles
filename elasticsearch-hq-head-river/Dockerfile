# My lovely ElasticSearch with plugins
FROM java:openjdk-7-jre
MAINTAINER Denis Sukhonin <d.sukhonin@gmail.com>

ENV ES_VERSION 1.4.2

RUN wget -q https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-$ES_VERSION.tar.gz -O - | tar zxvf - && \
    mv /elasticsearch-$ES_VERSION /elasticsearch && \
    rm /elasticsearch/lib/sigar/*freebsd* && \
    rm /elasticsearch/lib/sigar/*macosx* && \
    rm /elasticsearch/lib/sigar/*solaris* && \
    rm /elasticsearch/lib/sigar/*winnt* && \
    rm /elasticsearch/bin/*.exe

ADD elasticsearch.yml /elasticsearch/config/elasticsearch.yml

RUN /elasticsearch/bin/plugin -install royrusso/elasticsearch-HQ

RUN /elasticsearch/bin/plugin -install mobz/elasticsearch-head

RUN /elasticsearch/bin/plugin -install river-rethinkdb --url http://goo.gl/JmMwTf

VOLUME ["/data", "/logs"]
EXPOSE 9200 9300

CMD ["elasticsearch/bin/elasticsearch"]
