# 🛠️ ShieldStack – Configuration

This folder contains detailed configuration steps, common issues, and undocumented solutions encountered during the deployment and scaling of the **ShieldStack** security monitoring architecture.

The goal of this section is to provide clear guidance where official documentation was lacking, incomplete, or misleading — based entirely on real-world implementation during deployment at the **Municipality of Pedro Aguirre Cerda**.

Each subfolder includes screenshots, notes, and fixes that were tested and successfully implemented. These resources are intended to help others replicate, troubleshoot, and understand the full system setup.

```

CONFIGURATIONS/
│
├── ElasticSearch/
│ └── Errors/
│ ├── 137/ → Issues with permissions or disk mount errors.
│ ├── 307/ → Redirect issues and how to fix them in container environments.

├── Grafana/
│ ├── Dynamic-Dashboard/ → How to configure Grafana dashboards to auto-update.
│ ├── Errors/
│ │ └── Datasource/
│ │ ├── 404/ → Missing datasource errors and solutions.
│ │ ├── Failed To Connect to Server/ → Troubleshooting Grafana-OpenSearch connection.
│ ├── Redirect To Dashboard/Canvas ICON/ → How to redirect users directly to dashboards with custom icons.
│ ├── CanvasPanelPanZoom/ → Canvas panel enhancements: zoom, pan, and icon positioning.

├── OpenSearch/ → Basic config, index handling, and cluster tips.

├── Wazuh/
│ ├── Wazuh-Agent/
│ │ ├── Alerts/WindowsCheck4Updates/ → Alert tuning for unnecessary Windows update logs.
│ │ ├── AutomaticAgents/ → Auto-registration and enrollment setup for agents.
│ │ ├── FIM integration/ → File Integrity Monitoring best practices.
│ │ ├── Suricata/
│ │ │ └── Configure alerts/ → How to send Suricata alerts into Wazuh correctly.
│ │ ├── VIRUSTOTAL integration/ → Integrate VirusTotal lookup with Wazuh alerts.
│ ├── Wazuh-Alerts-With-Email-StepByStep/ → Configure alert emails via SMTP with examples.
│ ├── Wazuh-Deploy/Docker/Single-node/ → Clean single-node Docker setup from scratch.
│ ├── Wazuh-Indexer/Configure-Logs/ → Log rotation, retention, and disk management.

```

---

## 🔍 What You’ll Find Here

- ✅ **Real fixes to real problems**: All examples are derived from actual obstacles encountered during deployment.
- 🖼️ **Annotated screenshots**: Visuals and step-by-step guides to complement official docs.
- ⚠️ **Error analysis**: Explanations for common Docker, Grafana, OpenSearch, and Wazuh errors.
- 🧩 **Integration tips**: Especially around **Wazuh ↔ Suricata**, **Wazuh ↔ OpenSearch**, and **Grafana dashboards**.
- 💬 **Comments and undocumented behaviors**: Includes notes where official documentation was unclear, outdated, or missing.
- 📦 **Modular setup and testing**: Advice on isolated component testing using Docker.

---

## 🚀 Contribution and Usage

Feel free to explore, adapt, or expand on these configurations for your own infrastructure. If you encounter a similar problem or found a better solution, you’re welcome to fork and contribute.

This section will continue to grow as the system scales and new challenges arise.

---

> 🧠 _“Most documentation tells you what should work. This folder shows what actually worked.”_
