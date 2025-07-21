First of all, we need to install docker and docker compose, you can have docker already but is not the same, in my case I prefer to reinstall all from 0.

all of this is in your wazuh server or that pc or operation system that is the manager

- We need to increase mmap with this following comand ``` sysctl -w vm.max_map_count=262144 ```
- 
