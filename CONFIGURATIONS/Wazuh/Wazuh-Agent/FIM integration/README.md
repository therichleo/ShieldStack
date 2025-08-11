This is what we are gonna get
<img width="1751" height="687" alt="Image" src="https://github.com/user-attachments/assets/aced8a38-1bdb-468d-a678-8c8a07ec47db" />

So in first we are going to ossec.conf of our wazuh agent, and enter, always I recommend notepad++ because is the best tool for editing this files
<img width="1121" height="493" alt="Image" src="https://github.com/user-attachments/assets/8748116c-23cc-462b-833a-aec5accd58b1" />
<img width="1083" height="601" alt="Image" src="https://github.com/user-attachments/assets/f4e84a3a-2f89-49da-9866-1ded6884666e" />
and we can search with ctrl+F File integrity monitoring and in the disabled place we put no.

and in Defaul files to be monitored we put

<directories check all="yes" report_changes="yes" realtime="yes">C:\Users\<YourUser>\Downloads</directories>

<img width="1332" height="776" alt="Image" src="https://github.com/user-attachments/assets/9a7732f5-191a-44b4-a6e7-1094417207f0" />

and you have to restart wazuh agent.

and with this, all files that we download, is being monitored, the FIM integration always is good to comppany with VIRUSTOTAL, cause that verified the file automatied

