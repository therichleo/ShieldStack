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
