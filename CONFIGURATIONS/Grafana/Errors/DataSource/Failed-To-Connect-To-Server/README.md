# 🔐 Fixing Grafana Data Source TLS Authentication Error

When connecting Grafana to a secured data source, you might encounter an **authentication/TLS verification error**.

---

## 1. The Problem

If authentication is enabled on your data source (e.g., Basic Auth), you may see an error like this:

<div align="center">
  <img src="https://github.com/user-attachments/assets/0d473e58-92fa-4a4f-bfeb-9f821875b4f1" width="50%" />
</div>

---

## 2. The Solution

This is an easy fix if you have authentication options enabled.
In this example, **Basic Auth** is being used.

**Steps to fix:**

1. Go to your **Data Source settings** in Grafana.
2. Enable **Skip TLS Verify**.

<div align="center">
  <img src="https://github.com/user-attachments/assets/3fda7593-2f78-4323-9b22-970f64e17434" width="50%" />
</div>

---

## 3. Final Result

After saving the settings, the connection should work without TLS verification issues:

<div align="center">
  <img src="https://github.com/user-attachments/assets/b7915800-d552-42d2-a4c0-2981400ec9ea" width="50%" />
</div>

---

✅ With this simple change, your Grafana data source will connect successfully.

---
