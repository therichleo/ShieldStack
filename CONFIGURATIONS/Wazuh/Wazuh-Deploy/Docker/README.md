### Deploy Wazuh with Dockers!!
Docker is a tool that allows you to create, deploy, and run applications in containers, which are isolated and lightweight environments. You can also set up a Wazuh server using Docker, which facilitates deployment and scalability.

Wazuh's Docker-based logic is based on separate containers that separate its core functions. There are two deployment modes:
- Single-node (all on one machine): ideal for testing or small environments.
- Multi-node: recommended for production, with high availability and performance.

Both deployments generally separate Wazuh into 3 main containers (3 Dockerfiles):
1. wazuh-manager: responsible for event analysis and correlation.
2. wazuh-indexer: based on OpenSearch, it handles data storage and searching.
3. wazuh-dashboard: graphical interface (UI) for visualizing alerts and metrics.

This separation improves modularity, allows components to be scaled separately, and facilitates maintenance.
