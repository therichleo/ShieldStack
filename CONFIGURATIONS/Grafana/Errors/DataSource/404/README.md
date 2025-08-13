# 🛠 Fixing Grafana Data Source 404 Error

When connecting Grafana to a data source, you might encounter the **404 error** due to an incorrect index name.

---

## 1. The Problem

You may see an error similar to this:

<div align="center">
  <img src="https://github.com/user-attachments/assets/ade12f41-579d-4c8e-b378-99db8611e9c9" width="50%" />
</div>

---

## 2. The Solution

This issue is easy to fix — it’s usually caused by the index name not matching the actual index in your data source.

**Steps to fix:**

1. Go to **Dashboard Settings → Data Source**.
2. Find the **Index Name** field.
3. Change it to the correct index name.
4. *(Tip)* You can keep the same name but make a **minimal change** to simulate an update (e.g., add a space, save, then remove it).

---

✅ After saving, refresh the dashboard and the error should be gone.

---
