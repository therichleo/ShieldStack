## **ShieldStack – Enterprise Security Monitoring Architecture**

**ShieldStack** is an enterprise-grade security monitoring solution developed during my professional internship at the **Municipality of Pedro Aguirre Cerda**. The system is designed to centralize log collection, threat detection, and real-time infrastructure visibility using open-source tools.

This project is currently deployed and being actively scaled. During the **fifth week**, the goal is to onboard **100 endpoints**, with a projected expansion to over **500 devices** across the municipality's network infrastructure.

---

### 📌 **Project Goals**

* Implement a scalable and centralized security monitoring system for municipal infrastructure.
* Leverage open-source tools to reduce licensing costs while maintaining enterprise-level visibility and detection.
* Provide intuitive dashboards for security, system health, and activity monitoring.
* Enable geospatial visualization of all monitored assets using a custom municipal layout.

---

### 🏗️ **System Architecture Overview**

```
[Municipal Computers] → [Wazuh Agent / Filebeat] → [Wazuh Manager (Docker Single Node)]
                                    ↓
                                [OpenSearch]
                                    ↓
                         [Grafana + Custom GeoMap]
```

---

### 🧱 **General Architecture Overview**

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

### 📊 **Included Dashboards**

The pilot phase includes a set of dashboards and panels to visualize:

* Security events and alerts by severity, source IP, and affected hosts.
* System health metrics and performance of monitored endpoints.
* File integrity monitoring (FIM) changes.
* Authentication and user behavior patterns.
* Network activity and potentially malicious traffic.

> These dashboards are built using both **Kibana** (for security-focused visualizations) and **Grafana** (for operational metrics and alerting).
