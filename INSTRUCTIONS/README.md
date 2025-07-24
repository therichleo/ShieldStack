This intructions makes the conections from Wazuh to Grafana, so in midst of this is ElasticSearch/OpenSearch, FileBeat and Kibana

1. Install Docker-compose

put this commando for ... ``` sysctl -w vm.max_map_count=262144 ```

then this command ``` curl -sSL https://get.docker.com/ | sh ```

then ``` systemctl start docker ```

and for installation of docker-compose

``` curl -L "https://github.com/docker/compose/releases/download/v2.12.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose ```

``` chmod +x /usr/local/bin/docker-compose ```

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
```
sudo apt-get install -y software-properties-common
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
sudo apt-get update
sudo apt-get install grafana
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```
4. Join Grafana with Wazuh Logs (Indexer)

In firstly we have to verify if we have opensearch or elasticsearch
``` docker exec -it single-node-wazuh.indexer-1 curl -k -u admin:SecretPassword https://localhost:9200 ```
the output is like this:

So in my case I have OpenSearch, so if you have OpenSearch too, we have to install OpenSearch plugin with this command
``` grafana-cli plugins install grafana-opensearch-datasource ```

and restart ``` sudo systemctl restart grafana-server ```




