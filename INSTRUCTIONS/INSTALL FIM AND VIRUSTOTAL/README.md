# 🛠️ Instalación de FIM (File Integrity Monitoring) y VirusTotal en Wazuh

Este documento describe cómo configurar el monitoreo de integridad de archivos (FIM) en el agente de Wazuh y cómo integrar Wazuh con VirusTotal para análisis de archivos sospechosos.

---

## 📁 Configuración de FIM en Wazuh Agent (Windows)

### 1. Editar el archivo de configuración

Ubicación del archivo:

```
C:\Program Files (x86)\ossec-agent\ossec.conf
```

Dentro de la sección `<syscheck>`, agrega la siguiente línea para monitorear la carpeta **Descargas** del usuario actual:

```xml
<directories check_all="yes" report_changes="yes" realtime="yes">C:\Users\<Usuario>\Downloads</directories>
```

> 🔄 **Reemplaza `<Usuario>` con el nombre de usuario correspondiente.**

### 2. Reiniciar el Wazuh Agent

Abre una consola **CMD como administrador** y ejecuta:

```cmd
net stop Wazuh
net start Wazuh
```

### 3. Verificación

Coloca un archivo de texto cualquiera en la carpeta `Descargas`. Si todo está correctamente configurado, el agente debería detectar y reportar la actividad al servidor Wazuh.

---

## 🧪 Integración con VirusTotal en Wazuh Manager (Linux)

### 1. Obtener una API Key

Regístrate en [https://www.virustotal.com](https://www.virustotal.com) y obtén una **API\_KEY** desde tu perfil de usuario.

---

### 2. Configurar el Manager

Edita el archivo de configuración del Wazuh Manager:

```bash
sudo nano /var/ossec/etc/ossec.conf
```

Agrega el siguiente bloque dentro del archivo:

```xml
<integration>
  <name>virustotal</name>
  <api_key>API_KEY</api_key>
  <group>syscheck</group>
  <alert_format>json</alert_format>
</integration>
```

> 🔐 **Reemplaza `API_KEY` por tu clave personal de VirusTotal.**

---

### 3. Reiniciar el Wazuh Manager

Ejecuta el siguiente comando para aplicar los cambios:

```bash
sudo systemctl restart wazuh-manager
```

---

### 4. Prueba del sistema

1. Crea un archivo de texto con el siguiente contenido (archivo de prueba EICAR):

   ```
   X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*
   ```

2. Guarda el archivo dentro de la carpeta `Downloads` del usuario.

3. Si todo está funcionando correctamente:

   * El agente detectará el archivo.
   * El Manager lo analizará con VirusTotal.
   * Verás la alerta correspondiente en el **dashboard de Wazuh**.

> ⚠️ Este archivo **no es un virus real**, pero es detectado por los antivirus como una prueba estándar.

---

## ✅ Resultado Esperado

* Detección en tiempo real de archivos en la carpeta `Downloads`.
* Envío automático de archivos sospechosos a VirusTotal.
* Visualización de alertas en el dashboard de Wazuh.

---
