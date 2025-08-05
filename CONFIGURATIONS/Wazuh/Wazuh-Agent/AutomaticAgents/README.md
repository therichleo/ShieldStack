in firstly we have to go to the route of manage_agents
i am in docker single-node so we enter in the wazuh-manager with docker exec -it single-node-wazuh-manager-01 /bin/bash
then go to ./var/ossec/bin/manage_agents
and is gona appears a display that is like that:
<img width="422" height="232" alt="Image" src="https://github.com/user-attachments/assets/7441332f-0b6b-4e5f-962c-8f1cbea18e22" />
so we put A
the name is just a random name or a name that we like
and for the IP if you dont have static IPs just put "any"
then thta give you a key, we save that key.

If we need 10 new agents, we need to do this 10 times.

In the pc of the agents we have to install the wazuh agent, but the installer, not with command, so when we insatall the application, that is gona ask for a key, so we put the key, and this is like the aumatic agents work

//arreglar
