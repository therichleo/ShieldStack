# 🧩 Integración de Sysmon con Wazuh Agent (Windows)

> ⚠️ **Créditos**: Esta instalación **no fue creada por mí**. Todo el mérito es para el repositorio original de **JACKnygma**:
> 👉 [https://github.com/JACKnygma/wazuh\_sysmon](https://github.com/JACKnygma/wazuh_sysmon)

Este instructivo se basa en el trabajo realizado por JACKnygma para integrar **Sysmon** en sistemas Windows y vincular sus logs con **Wazuh Agent**, permitiendo una mejor visibilidad y detección de eventos avanzados.

---

## 🛠️ Requisitos

* Sistema operativo **Windows** con Wazuh Agent instalado
* Permisos de administrador
* Notepad++ (opcional pero recomendado)

---

## 🔽 Paso 1: Descargar e instalar Sysmon

1. Descarga Sysmon desde el sitio oficial de Microsoft:
   👉 [https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)

2. Extrae los archivos y colócalos en una carpeta local (ej: `C:\Sysmon`).

---

## ⚙️ Paso 2: Descargar y aplicar configuración personalizada

1. Descarga el archivo de configuración XML personalizado desde el repositorio original:
   👉 [sysmonconfig-export.xml](https://github.com/JACKnygma/wazuh_sysmon/blob/main/sysmonconfig-export.xml)

2. Ejecuta Sysmon en modo administrador con el archivo de configuración:

   ```cmd
   Sysmon64.exe -accepteula -i sysmonconfig-export.xml
   ```

> 📝 Esto instalará Sysmon como un servicio de Windows que comenzará a registrar eventos detallados en el **Visor de eventos**.

---

## 🔗 Paso 3: Integrar los logs de Sysmon a Wazuh Agent

1. Edita el archivo de configuración de Wazuh Agent:

   ```
   C:\Program Files (x86)\ossec-agent\ossec.conf
   ```

2. Justo antes del cierre `</ossec_config>`, agrega lo siguiente para capturar eventos de Sysmon desde el log de eventos de Windows:

   ```xml
   <localfile>
     <log_format>eventchannel</log_format>
     <location>Microsoft-Windows-Sysmon/Operational</location>
   </localfile>
   ```

---

## 🔄 Paso 4: Reiniciar Wazuh Agent

Para aplicar los cambios:

```cmd
net stop Wazuh
net start Wazuh
```

---

## ✅ Verificación

1. Abre el **dashboard de Wazuh**.
2. Genera alguna actividad monitoreada por Sysmon (por ejemplo: ejecutar un proceso, crear archivos temporales, etc.).
3. Verifica que los eventos aparezcan como logs del tipo `sysmon` o bajo el grupo `windows`.

---

## 📚 Más información

* Repositorio original con configuraciones y documentación adicional:
  👉 [https://github.com/JACKnygma/wazuh\_sysmon](https://github.com/JACKnygma/wazuh_sysmon)

* Documentación oficial de Sysmon:
  👉 [https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)

* Documentación oficial de Wazuh:
  👉 [https://documentation.wazuh.com](https://documentation.wazuh.com)

---
