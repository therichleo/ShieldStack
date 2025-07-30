In first we have to go to settings of the dashboard that gonna be dynamic (that one have all data changing) and go to variables, add new variable, and put information, in my case, i have 3 wazuh agents and put all the information like this:

<img width="779" height="896" alt="Image" src="https://github.com/user-attachments/assets/6e996207-0f49-4f5e-873d-22f481c10a7a" />

then we are gonna create a panel that his query is like this, in the top left we saw agent_id: 001, cause the variable its created and is in 001 agent
<img width="1168" height="819" alt="Image" src="https://github.com/user-attachments/assets/f4c9cd4c-12da-401c-86d9-a9d4785644a4" />

then if we created a basic dashboard, we saw different results

<img width="1493" height="679" alt="Image" src="https://github.com/user-attachments/assets/b5b9a4f8-00e3-4094-802b-ee040bbc21a2" />

<img width="1493" height="679" alt="Image" src="https://github.com/user-attachments/assets/1a3226a1-e62b-4af8-9a1e-75ecf95a6874" />

<img width="1493" height="679" alt="Image" src="https://github.com/user-attachments/assets/9e496e3d-c566-4867-94c6-3790537726d3" />

and in my case i vinculate a canvas dashboards to icons that redirect to this dynamic-dashboard, in the link you have to write the variable, if you dont know how to redirect dashboards from an icon, you can see the respository

<img width="1499" height="484" alt="Image" src="https://github.com/user-attachments/assets/90a3fbd9-403b-4e4e-9a26-eeea4a81be85" />

<img width="1159" height="445" alt="Image" src="https://github.com/user-attachments/assets/a6b11ff1-e07f-4079-bde6-28e3f6e39d03" />

and like this you can have a functional dynamic dashboards
