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
[Municipal Computers]
    → [Wazuh Agent / Filebeat] 
    → [Suricata Sensor (Network TAP or Mirror Port)] 
        → [Wazuh Manager (Docker Single Node)]
                             ↓
                         [OpenSearch]
                             ↓
                  [Grafana + Custom GeoMap]
```

---

* **Wazuh** is deployed via **Docker (single-node)** for modular deployment and centralized event processing.
* **Suricata**, an open-source intrusion detection and network monitoring tool, analyzes network traffic and generates alerts.
* **Wazuh Manager** collects log and alert data from agents and Suricata, forwarding everything to **OpenSearch**.
* **Grafana** retrieves data from OpenSearch and displays it in real-time dashboards, including a **custom Canvas focus on GeoMap** panel with the layout of the municipality.

---

<img width="960" height="540" alt="Image" src="https://github.com/user-attachments/assets/fe6ae29a-2243-4a96-aada-523a57630914" />
---

### 🛠️ **Technologies Used**

| Tool           | Role & Functionality                                            |
| -------------- | ----------------------------------------------------------------|
| **Wazuh**      | Threat detection, log analysis, integrity monitoring.           |
| **OpenSearch** | Log indexing, storage, and full-text search capabilities.       |
| **Filebeat**   | Lightweight log shipper to Wazuh                                |
| **Suricata**   | Intrusion detection, traffic inspection, and protocol analysis. |
| **Grafana**    | Dashboards, visualizations, GeoMap panels, and alerting.        |
| **Docker**     | Containerized deployment of the entire Wazuh stack.             |

---

### 📊 **Dashboards & Visualization**

The following panels and dashboards are available for security and operational visibility:

* Security alerts by severity, source, and affected hosts.
* Endpoint health and system metrics.
* File integrity monitoring (FIM) events.
* Authentication logs and user access patterns.
* Network traffic analysis powered by **Suricata**, including:
  
  * Suspicious connections
  * Intrusion attempts
  * Traffic by protocol or source/destination
  
* **Custom Canvas focus on GeoMap Dashboard** displaying endpoint status on the municipal layout:
  
  * 🟢 **Online**
  * 🔴 **Offline**
  * 🟡 **Critical alerts**

 foto aqi tmb

---

### 📁 **Repository Structure**

```
ShieldStack/
│
├── Tracking/
│   └── Weeks/
│       ├── Week 1/
│       ├── Week 2/
│       ├── Week 3/
│       ├── Week 4/
│       ├── Week 5/
│       └── Week 6/
│       → Contains weekly logs, documentation, progress notes, and screenshots.
│
├── Configuration/
│   → Step-by-step guides to configure or troubleshoot components.
│   → Includes personal notes where official docs were unclear, with screenshots.
│
├── Instructions/
│   → How to deploy Wazuh and Grafana together.
│   → Minimal setup instructions without deep configuration.
```

---

### 🚀 **Project Impact & Scaling**

* Currently operational within the municipality’s infrastructure.
* Week 5: onboarding **100 monitored endpoints**.
* Next phase: scale to **500+ devices** for full coverage.
* Centralized platform to reduce manual effort, improve incident detection time, and visualize network health instantly.

---

### 👨‍💻 **About This Project**

This system was designed and implemented as part of my **6-week professional internship** at the **Municipality of Pedro Aguirre Cerda**. I was responsible for:

* Deploying **Wazuh** and **Suricata** with Docker.
* Integrating **OpenSearch** with **Grafana**.
* Designing custom dashboards, including geospatial asset tracking and Suricata alert panels.
* Documenting and troubleshooting configurations for future scalability.
* Establishing the foundation of a real, scalable SIEM solution for public institutions.




