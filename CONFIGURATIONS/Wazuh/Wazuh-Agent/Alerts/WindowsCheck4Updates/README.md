This tutorial is so difficult because there is no options in wazuh, grafana, suricata.

So in first we need to check the "event viewer" Then -> Registry of applications and services -> Microsoft -> Windows -> WindowsUpdateClient -> Operational.

So the event id that we need is the event id 26, because this event says about exist updates for windows.
<img width="601" height="230" alt="Image" src="https://github.com/user-attachments/assets/a2119a6b-5fe5-453b-88f9-00a28ef3486f" />

And now for generating this event in CMD we need to pass from CMD to Powershell with this comannd powershell -ExecutionPolicy Bypass 

And then this command for generate event 26:

$UpdateSession = New-Object -ComObject Microsoft.Update.Session

$UpdateSearcher = $UpdateSession.CreateUpdateSearcher()

$SearchResult = $UpdateSearcher.Search("IsInstalled=0")

now we have the command that verify existing windows updates.

So we have to search the ossec.conf and put this in log files


<localfile>
  <log_format>eventchannel</log_format>
  <location>Microsoft-Windows-WindowsUpdateClient/Operational</location>
</localfile>


then restart the wazuh agent and restart the wazuh manager

and is ready

