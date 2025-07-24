This intructions makes the conections from Wazuh to Grafana, so in midst of this is ElasticSearch/OpenSearch, FileBeat and Kibana

1. Install Docker-compose
2. Install Wazuh (manager-dashboard-indexer) (SINGLE-NODE)

``` git clone https://github.com/wazuh/wazuh-docker.git -b v4.12.0 ```
this command do: ...

then we have
enter to single-node/generate-indexer-certs.yml
and you need to edit and sent like this
```
# Wazuh App Copyright (C) 2017 Wazuh Inc. (License GPLv2)
version: '3'

services:
  generator:
    image: wazuh/wazuh-certs-generator:0.0.2
    hostname: wazuh-certs-generator
    volumes:
      - ./config/wazuh_indexer_ssl_certs/:/certificates/
      - ./config/certs.yml:/config/certs.yml
    environment:
      - HTTP_PROXY=YOUR_PROXY_ADDRESS_OR_DNS
```
in single-node put this command:
``` docker-compose -f generate-indexer-certs.yml run --rm generator ```

and start wazuh in background ``` docker-compose up -d ```

3. Install Grafana
4. Join Grafana with Wazuh Logs (Indexer)

