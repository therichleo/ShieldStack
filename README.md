# **ShieldStack – Enterprise Security Architecture (Pilot Phase)**

**ShieldStack** is a pilot-stage enterprise security monitoring and analysis environment designed to provide centralized visibility, threat detection, and log collection. This project integrates open-source tools such as **Wazuh**, **Elasticsearch**, **Kibana**, **Filebeat**, and **Grafana** to build a lightweight yet scalable SIEM architecture.

---

## 📌 **Project Objectives**

* Assess the technical and operational feasibility of an open-source-based security monitoring solution.
* Deploy a basic SIEM architecture that can be easily scaled in enterprise environments.
* Centralize the collection, analysis, and visualization of security-related logs.

---

## 🛠️ **Technologies Used**

| Component         | Main Functionality                                                     |
| ----------------- | ---------------------------------------------------------------------- |
| **Wazuh**         | Threat detection, log analysis, file integrity monitoring.             |
| **Elasticsearch** | Event indexing, search engine, and storage backend.                    |
| **Kibana**        | Visualization and exploration of data stored in Elasticsearch.         |
| **Filebeat**      | Lightweight log shipper for forwarding logs to Wazuh or Elasticsearch. |
| **Grafana**       | Custom dashboards for metrics, performance monitoring, and alerting.   |

---

## 🧱 **General Architecture Overview**

```
[Endpoints / Servers] → [Filebeat / Wazuh Agent] → [Wazuh Manager]
                              ↓
                       [Elasticsearch]
                              ↓
                   [Kibana]      [Grafana]
```

* **Wazuh agents** and **Filebeat** collect system logs, events, and security data.
* **Wazuh Manager** processes events and forwards them to Elasticsearch.
* **Elasticsearch** indexes and stores all the incoming logs for efficient querying.
* **Kibana** provides powerful dashboards for real-time data exploration.
* **Grafana** is used for high-level visualizations, custom metrics panels, and alert configurations.

---

## 📊 **Included Dashboards**

The pilot phase includes a set of dashboards and panels to visualize:

* Security events and alerts by severity, source IP, and affected hosts.
* System health metrics and performance of monitored endpoints.
* File integrity monitoring (FIM) changes.
* Authentication and user behavior patterns.
* Network activity and potentially malicious traffic.

> These dashboards are built using both **Kibana** (for security-focused visualizations) and **Grafana** (for operational metrics and alerting).
