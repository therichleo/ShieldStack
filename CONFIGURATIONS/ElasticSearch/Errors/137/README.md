# Fixing Elasticsearch Exit Code 137 in Docker

If your Elasticsearch container **automatically stops** after running `docker run` and you see it under the **CREATED** column when checking with:

```bash
docker ps -a
```

…and it shows something like:

```
(137) Exited
```

This means the container was killed, usually because Elasticsearch exceeded the available memory (Exit Code 137 = **Out of Memory**).
The fix isn’t obvious, but here’s how to solve it.

---

## 1. Locate the `jvm.options` File

In your terminal, search for the file:

```bash
find -name "jvm.options"
```

You should see something like this: <img width="1540" height="136" alt="Image" src="https://github.com/user-attachments/assets/782ce2d3-ba7d-418d-9865-656aba409f37" />

---

## 2. Copy JVM Settings

Open that file and **copy all its contents**.

---

## 3. Edit the `jvm.options.d` Directory

Navigate to the `jvm.options.d` directory and open (or create) the `jvm.options` file:

```bash
nano jvm.options
```

It should look like this: <img width="1524" height="130" alt="Image" src="https://github.com/user-attachments/assets/e8968539-ed14-478a-8939-cfc37fa77116" />

---

## 4. Adjust JVM Memory Settings

Paste the copied content into this file and **change** the memory configuration:

* **From:**

  ```
  Xms4g
  ```
* **To:**

  ```
  Xms1g
  ```

Example: <img width="946" height="536" alt="Image" src="https://github.com/user-attachments/assets/cc949d26-c37b-43b1-8bb3-54dda94981d5" />

---

## ✅ Done!

After lowering the memory allocation, restart the container:

```bash
docker restart <container_name>
```

Your Elasticsearch container should now run without automatically stopping.

---
