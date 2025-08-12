## 📊 Install Grafana

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

