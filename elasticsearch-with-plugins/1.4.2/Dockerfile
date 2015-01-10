# My lovely ElasticSearch with plugins
FROM neglectedvalue/elasticsearch
MAINTAINER Denis Sukhonin <d.sukhonin@gmail.com>

ADD elasticsearch.yml /elasticsearch/config/elasticsearch.yml

RUN /elasticsearch/bin/plugin -install royrusso/elasticsearch-HQ

RUN /elasticsearch/bin/plugin -install mobz/elasticsearch-head

RUN /elasticsearch/bin/plugin -install river-rethinkdb --url http://goo.gl/JmMwTf

VOLUME ["/data", "/logs"]
EXPOSE 9200 9300

CMD ["elasticsearch/bin/elasticsearch"]
