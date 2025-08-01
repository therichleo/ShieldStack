# Wazuh + Grafana Integration Guide

This guide walks you through connecting **Wazuh** to **Grafana**, using **OpenSearch** (or **Elasticsearch**) as the intermediary for indexing data, and **Filebeat** + **Kibana** for log forwarding and visualization.

---

## 🔧 1. Install Docker & Docker Compose

### 📌 Set virtual memory map count

```bash
sudo sysctl -w vm.max_map_count=262144
```

This increases the maximum number of memory map areas a process can have. It's required by Elasticsearch/OpenSearch to run correctly.

---

### 📦 Install Docker

```bash
curl -sSL https://get.docker.com/ | sh
```

Downloads and installs the latest stable version of Docker.

```bash
sudo systemctl start docker
```

Starts the Docker service so containers can be run.

---

### 🧰 Install Docker Compose

```bash
curl -L "https://github.com/docker/compose/releases/download/v2.12.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

Downloads Docker Compose v2.12.2 binary for your system.

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

Grants execution permissions to Docker Compose.

---

## 🧱 2. Deploy Wazuh (Single Node)

### 🔁 Clone Wazuh Docker Repository

```bash
git clone https://github.com/wazuh/wazuh-docker.git -b v4.12.0
cd wazuh-docker/single-node
```

Clones the Wazuh Docker stack repository (single-node version) and navigates into the folder.

---

### 🛠️ Edit Certificate Generator File

Edit the file `generate-indexer-certs.yml` and make sure it looks like this:

```yaml
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

This config sets up the container to generate SSL certificates required by OpenSearch.

---












