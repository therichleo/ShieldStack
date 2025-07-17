### Configuring Alerts in Suricata with Wazuh Agent
I created this repository because I experienced an issue where Suricata wasn't detecting ICMP (ping) traffic. In this guide, I’ll explain how to configure it properly so that this type of traffic is captured and alerts are generated.
#### Introduction
This is a brief overview of how to configure Suricata within the Wazuh agent to generate alerts based on specific network traffic. I won’t go into too much detail since I’ll include screenshots to illustrate each step clearly.
Verifying the initially captured traffic:
First, I’ll show the traffic that Suricata was capturing while I was performing a ping from one PC to another. As you'll see in the corresponding screenshot, no ICMP packets were being captured, which indicated a misconfiguration.
<p align="center">
  <img width="630" height="325" src="https://github.com/user-attachments/assets/fc659d8e-0e99-4667-9d8a-0d6b6cffcb81" alt="Image" />
</p>
<p align="center">
  
###### As we can see there is no ICMP packets, so this is the issue, Suricata is no configured to capture ICMP traffic
</p>
1. We need to go to this file "C:\Program Files\Suricata\rules\emerging-all.rules"
<p align="center">
  <img width="495" height="319,8" alt="Image" src="https://github.com/user-attachments/assets/7943cd62-a5d7-461d-a76e-2799b6fef849" />
</p>
