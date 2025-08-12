## 🔧 Install Docker & Docker Compose

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

