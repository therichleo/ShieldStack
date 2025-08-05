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

## 3. Resulting Dashboard View

If we preview the dashboard using the variable, we’ll see different results for each agent:

<div align="center">
  <img src="https://github.com/user-attachments/assets/b5b9a4f8-00e3-4094-802b-ee040bbc21a2" width="50%" />
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/1a3226a1-e62b-4af8-9a1e-75ecf95a6874" width="50%" />
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/9e496e3d-c566-4867-94c6-3790537726d3" width="50%" />
</div>

---

## 4. Linking Canvas Icons to the Dynamic Dashboard

In my case, I linked **Canvas dashboard icons** directly to this dynamic dashboard.

To do this, just **add the variable in the dashboard URL**. If you're not sure how to link dashboards through Canvas icons, check the repository for examples.

<div align="center">
  <img src="https://github.com/user-attachments/assets/90a3fbd9-403b-4e4e-9a26-eeea4a81be85" width="90%" />
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/a6b11ff1-e07f-4079-bde6-28e3f6e39d03" width="90%" />
</div>

---
