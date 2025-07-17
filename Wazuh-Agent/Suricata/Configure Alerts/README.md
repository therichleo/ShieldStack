### Configuring Alerts in Suricata with Wazuh Agent
---
I created this repository because I experienced an issue where Suricata wasn't detecting ICMP (ping) traffic. In this guide, I’ll explain how to configure it properly so that this type of traffic is captured and alerts are generated.
#### Introduction
This is a brief overview of how to configure Suricata within the Wazuh agent to generate alerts based on specific network traffic. I won’t go into too much detail since I’ll include screenshots to illustrate each step clearly.
Verifying the initially captured traffic:
First, I’ll show the traffic that Suricata was capturing while I was performing a ping from one PC to another. As you'll see in the corresponding screenshot, no ICMP packets were being captured, which indicated a misconfiguration.
<div align="center">
  <img width="630" height="325" src="https://github.com/user-attachments/assets/fc659d8e-0e99-4667-9d8a-0d6b6cffcb81" alt="Image" />
  
  <h6>As we can see there is no ICMP packets, so this is the issue, Suricata is not configured to capture ICMP traffic</h6>
</div>

---

* ##### We need to go to this file: <code>C:\Program Files\Suricata\rules\emerging-all.rules</code></p>
<div align="center">
  <img width="495" height="320" src="https://github.com/user-attachments/assets/7943cd62-a5d7-461d-a76e-2799b6fef849" alt="Image" />
</div>

* ##### After this, we will proceed to edit the configuration using Notepad++.
<div align="center">
  <img width="495" height="320" src="https://github.com/user-attachments/assets/fa32cf80-f657-45c4-b4e5-28bb7955c189" alt="Image" />
</div>

* ##### To enable detection for the ICMP protocol, we need to remove the "#" symbol from the alert rules related to ICMP. This action activates the corresponding rules within the configuration.
<div align="center">
  <img width="495" height="320" src="https://github.com/user-attachments/assets/63c74a24-ebfd-41fe-b793-d4aa091497bb" alt="Image" />
</div>

* ##### In the following screenshot, we can observe that ICMP traffic, such as ping requests, is now being captured and recorded in the eve.json file. Additionally, these events are also visible on the Wazuh dashboard.
<div align="center">
  <img width="495" height="320" src="https://github.com/user-attachments/assets/e549c9b1-a7f4-4d6f-ae26-70af66cebdd9" alt="Image" />
  <img width="495" height="320" src="https://github.com/user-attachments/assets/ec418fbe-45d6-4815-888e-baffecc379f1" alt="Image" />
</div>





