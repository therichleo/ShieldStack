In this guide i am gonna teach you how to configure logs, like modify them, you can remove or add, but in this context i am gonna edit the rule.level of one alert

So in firts, we have this alert: Windows Logon Success with rule.level: 3 and i want to elevate the level rule
<img width="1434" height="39" alt="Image" src="https://github.com/user-attachments/assets/89603733-34f5-43e1-a26c-d3b88482d1b0" />

so i press the alert and this appear, the information of that alert, we need the "file" that is the direction of the alert
<img width="1031" height="323" alt="Image" src="https://github.com/user-attachments/assets/48588be5-71a3-4893-9f5c-a9089cbae9b4" />

now we go to the terminal where is installed the wazuh-manager and search the file.

I am in ubuntu so we make sure that we are in the base files and put "find -name "<file-name>" and the response is a directory, that we gonna copy and paste with a nano before
<img width="1533" height="211" alt="Image" src="https://github.com/user-attachments/assets/66e4ede8-d5a2-433b-9a73-accfe94e6c40" />

Then i edit the level to a 15
<img width="1528" height="304" alt="Image" src="https://github.com/user-attachments/assets/4033b3e7-bdbb-42db-89d7-f9110732c977" />

after  make sure to restart wazuh and the output is like this
<img width="1461" height="82" alt="Image" src="https://github.com/user-attachments/assets/45678491-b885-4a7e-a0db-7dab4c78efa8" />
