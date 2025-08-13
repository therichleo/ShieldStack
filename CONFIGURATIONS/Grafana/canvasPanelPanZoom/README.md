# 🖱️ Enabling Pan & Zoom in Grafana Canvas

By default, the **Pan & Zoom** option in Grafana’s Canvas panel may be disabled.
Here’s how to enable it via the `grafana.ini` configuration file.

---

## 1. Locate the `grafana.ini` File

You can search for the file using:

```bash
find / -name "grafana.ini"
```

Once found, open it in a text editor.
Use **`Ctrl + W`** to search for the `features_toggles` section.

---

## 2. Enable `canvasPanelPanZoom`

Inside the `[features_toggles]` section, make sure the following line exists:

```ini
canvasPanelPanZoom = true
```

If it’s missing, add it manually.
It should look like this:

<div align="center">
  <img src="https://github.com/user-attachments/assets/7b9e74b2-0b24-4e47-afe1-a504d5fb518c" width="50%" />
</div>

---

## 3. Restart Grafana

After saving changes, restart Grafana for them to take effect:

```bash
sudo systemctl restart grafana-server
```

---

## 4. Verify in Grafana

* Go to **Grafana**.
* Add a **Canvas panel**.
* In the panel options, you should now see **Pan & Zoom** enabled.

<div align="center">
  <img src="https://github.com/user-attachments/assets/8106d3be-e63b-4ed4-a358-c9e79f492e5c" width="50%" />
</div>

---

✅ With this configuration, you can now freely move and zoom in your Canvas panels.

---
