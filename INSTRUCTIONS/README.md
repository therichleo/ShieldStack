# Installation of the shieldStack Implementation

This guide walks you through connecting **Wazuh** to **Grafana**, using **OpenSearch** (or **Elasticsearch**) as the intermediary for indexing data, and **Filebeat** + **Kibana** for log forwarding and visualization.

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

### 🔐 Generate Indexer Certificates

```bash
docker-compose -f generate-indexer-certs.yml run --rm generator
```

Runs the certificate generator container and removes it after execution.

---

### 🚀 Start Wazuh Stack

```bash
docker-compose up -d
```

Starts all Wazuh containers (manager, dashboard, indexer, etc.) in detached mode.

---

## 📊 3. Install Grafana

```bash
sudo apt-get install -y software-properties-common
```

Enables repository management features.

```bash
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
```

Adds Grafana's official package repo.

```bash
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
```

Imports Grafana’s GPG key to verify package authenticity.

```bash
sudo apt-get update
sudo apt-get install grafana
```

Installs Grafana.

```bash
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```

Starts Grafana and enables it to start on boot.

---

## 🔍 4. Verify Wazuh Indexer Type

### 🧪 Check Indexer (OpenSearch or Elasticsearch)

```bash
docker exec -it single-node-wazuh.indexer-1 curl -k -u admin:SecretPassword https://localhost:9200
```

Runs a curl command inside the Wazuh Indexer container to identify the backend. You'll get output like this:

![OpenSearch curl output](https://github.com/user-attachments/assets/52bef2d7-7ef1-4393-8bde-b50d386f243b)

---

### 🧩 If using **OpenSearch**, install plugin:

```bash
grafana-cli plugins install grafana-opensearch-datasource
sudo systemctl restart grafana-server
```

Installs the OpenSearch plugin and restarts Grafana.

> ⚠️ If you're using **Elasticsearch**, **skip** this step — Grafana has native support.

---

## 🔗 5. Connect Data Source in Grafana

This step is critical — without it, Grafana won't be able to query Wazuh data.

* Go to Grafana: [http://localhost:3000](http://localhost:3000)
* Login (default: admin / admin)
* Go to **Settings → Data Sources → Add Data Source**
* Choose **OpenSearch** or **Elasticsearch** (depending on what you use)
* Enter:

  * URL: `https://localhost:9200`
  * Auth: `admin / SecretPassword`
  * Index name: `wazuh-alerts-*`
* Click **Save & Test**

You should see a success message if all is correct.

Example UI:

![Grafana Data Source config](https://github.com/user-attachments/assets/78993653-65ef-4dd4-8102-a08841913961)

> ⚠️ **Having connection issues?**
> If you run into errors at this stage, don't worry — inside the repository at:
>
> `ShieldStack/CONFIGURATIONS/Grafana/Errors/DataSource/`
>
> You’ll find **common connection problems** along with their **solutions**

---

## ✅ Done!

Your Wazuh environment is now connected to Grafana, and you can start building dashboards.

---






