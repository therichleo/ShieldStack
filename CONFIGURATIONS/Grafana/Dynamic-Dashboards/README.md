# 🧩 How to Create a Dynamic Dashboard in Grafana (Wazuh Agents Example)

## 1. Set Up a Variable

First, go to the **dashboard settings** of the one you want to make dynamic — this will be the dashboard where data updates based on the selected variable.

* Navigate to **Settings → Variables**.
* Click on **Add variable**.
* Fill in the details. In this example, we have 3 Wazuh agents.

<div align="center">
  <img src="https://github.com/user-attachments/assets/6e996207-0f49-4f5e-873d-22f481c10a7a" width="50%" />
</div>

---

## 2. Create a Panel With a Dynamic Query

Now create a panel and use the variable in the query. As shown below, the `agent_id` selected is `001`, thanks to the variable setup.

<div align="center">
  <img src="https://github.com/user-attachments/assets/f4c9cd4c-12da-401c-86d9-a9d4785644a4" width="70%"/>
</div>

---
