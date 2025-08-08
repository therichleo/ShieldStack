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
