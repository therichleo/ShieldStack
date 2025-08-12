# 🛡️ Instalación y Configuración de Suricata en Windows + Integración con Wazuh Agent

Este instructivo permite instalar **Suricata IDS** en Windows, configurar sus reglas, visualizar el tráfico analizado y conectar los logs a **Wazuh Agent** para detección y alertas centralizadas.

---

## 📦 Paso 1: Instalación de herramientas necesarias

1. **Instalar Npcap**
   Descarga e instala desde:
   👉 [https://npcap.com](https://npcap.com)

2. **Instalar Suricata**
   Descarga e instala la versión para Windows desde:
   👉 [https://suricata.io/download/](https://suricata.io/download/)

3. **Descargar reglas de Suricata**
   Descarga las reglas desde:
   👉 [https://rules.emergingthreats.net/open/suricata-7.0.3/emerging-all.rules.tar.gz](https://rules.emergingthreats.net/open/suricata-7.0.3/emerging-all.rules.tar.gz)

4. **Instalar Notepad++**
   Descarga desde:
   👉 [https://notepad-plus-plus.org](https://notepad-plus-plus.org)

---

## ⚙️ Paso 2: Configurar Suricata

1. Abre el archivo de configuración:

   ```
   C:\Program Files\Suricata\suricata.yaml
   ```

   Usa **Notepad++ como administrador**.

2. Dentro de la sección `address-groups`, localiza la línea con `HOME_NET` y reemplaza con la IP del dispositivo:

   ```yaml
   HOME_NET: "<IP-DISPOSITIVO>"
   ```

3. Busca la sección `rule-files:` y realiza lo siguiente:

   * Selecciona todo el bloque y **coméntalo** (Ctrl+Q en Notepad++).
   * Extrae el archivo `emerging-all.rules` a:

     ```
     C:\Program Files\Suricata\rules
     ```
   * En la sección `rule-files:`, agrega:

     ```yaml
     rule-files:
       - emerging-all.rules
     ```

4. Crea una carpeta llamada `filter` dentro de Suricata:

   ```
   C:\Program Files\Suricata\filter
   ```

5. Dentro de esa carpeta, crea un archivo llamado `filter.bpf` y agrega el siguiente contenido (reemplaza con tu IP):

   ```
   host <IP-DISPOSITIVO>
   ```

---

## 🖥️ Paso 3: Ejecutar Suricata manualmente

1. Abre CMD como administrador y ejecuta:

   ```cmd
   wmic nicconfig get ipaddress,SettingID
   ```

   ✅ Guarda el **SettingID** que corresponde a tu IP.

2. Ejecuta Suricata con el siguiente comando (reemplaza `<SettingID>` por el obtenido):

   ```cmd
   "C:\Program Files\Suricata\suricata.exe" -c "C:\Program Files\Suricata\suricata.yaml" -i \Device\NPF_{<SettingID>} -F "C:\Program Files\Suricata\filter\filter.bpf"
   ```

📂 Esto generará archivos de log en:

```
C:\Program Files\Suricata\log
```

👉 Puedes abrir `eve.json` con Notepad++ para ver los eventos analizados por Suricata.

---

## 🔗 Paso 4: Integrar Suricata con Wazuh Agent

1. Edita el archivo de configuración del agente:

   ```
   C:\Program Files (x86)\ossec-agent\ossec.conf
   ```

2. Justo antes del cierre `</ossec_config>`, agrega lo siguiente:

   ```xml
   <localfile>
     <log_format>json</log_format>
     <location>C:\Program Files\Suricata\log\eve.json</location>
   </localfile>
   ```

---

## 🔄 Paso 5: Reiniciar Suricata y Wazuh

* **Detener Suricata:** Pulsa `Ctrl + C` en la terminal donde lo ejecutaste.
* **Reiniciar Wazuh Agent:**

  ```cmd
  net stop Wazuh
  net start Wazuh
  ```

---

## ⚠️ Paso 6: Restaurar reglas originales (opcional)

Si deseas restaurar la configuración original de Suricata:

1. Vuelve a descomentar el bloque original de `rule-files:` en `suricata.yaml`.

2. Vuelve a ejecutar Suricata con el mismo comando:

   ```cmd
   "C:\Program Files\Suricata\suricata.exe" -c "C:\Program Files\Suricata\suricata.yaml" -i \Device\NPF_{<SettingID>} -F "C:\Program Files\Suricata\filter\filter.bpf"
   ```

---

## 🧩 (Opcional) Ejecutar Suricata automáticamente al iniciar el sistema

1. Abre el **Programador de tareas** de Windows.
2. Crea una **tarea básica** y asigna un nombre como `Suricata IDS`.
3. En el desencadenador, selecciona **"Al iniciar el sistema"**.
4. En acción, selecciona **"Iniciar un programa"**:

   * Programa o script:

     ```
     C:\Program Files\Suricata\suricata.exe
     ```
   * Agregar argumentos:

     ```
     -c "C:\Program Files\Suricata\suricata.yaml" -i \Device\NPF_{<SettingID>} -F "C:\Program Files\Suricata\filter\filter.bpf"
     ```
5. Guarda y prueba la tarea.

---

## ⚙️ Nota sobre ajustes adicionales

Suricata permite muchos ajustes avanzados (como tipos de paquetes, protocolos, interfaces, etc). Estos parámetros se encuentran en el archivo `suricata.yaml` y en la documentación oficial:
👉 [https://docs.suricata.io](https://docs.suricata.io)

---
