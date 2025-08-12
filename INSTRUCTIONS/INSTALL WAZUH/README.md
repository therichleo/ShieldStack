## 🧱 Deploy Wazuh (Single Node)

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

