# ShieldStack – Arquitectura de Seguridad Empresarial (Fase Piloto)

**ShieldStack** es un entorno de monitoreo y análisis de seguridad empresarial en fase de prueba, diseñado para ofrecer visibilidad, detección de amenazas y recolección de logs de manera centralizada. Este proyecto integra herramientas de código abierto como **Wazuh**, **Elasticsearch**, **Kibana**, **Filebeat** y **Grafana** para construir una arquitectura SIEM ligera pero escalable.

---

## 📌 Objetivo del Proyecto

- Evaluar la viabilidad técnica y operativa de una solución de monitoreo de seguridad basada en herramientas open-source.
- Implementar una arquitectura SIEM básica que sea fácilmente escalable en entornos empresariales.
- Centralizar la recopilación, análisis y visualización de logs de seguridad.

---

## 🛠️ Tecnologías Utilizadas

| Componente      | Función Principal                                      |
|-----------------|--------------------------------------------------------|
| **Wazuh**       | Detección de amenazas, análisis de logs y control de integridad. |
| **Elasticsearch** | Motor de búsqueda y almacenamiento de eventos.         |
| **Kibana**      | Visualización y exploración de datos de Elasticsearch. |
| **Filebeat**    | Envío ligero de logs a Elasticsearch/Wazuh.            |
| **Grafana**     | Paneles personalizados para métricas y alertas.        |

---

## 🧱 Arquitectura General
[Endpoints/Servidores] → [Filebeat/Wazuh Agent] → [Wazuh Manager]
→ [Elasticsearch] → [Kibana / Grafana]


- Filebeat y los agentes Wazuh recolectan logs y eventos.
- Elasticsearch indexa y almacena los datos.
- Kibana y Grafana ofrecen interfaces para visualización y análisis.

---

📊 Dashboards Incluidos

## 
