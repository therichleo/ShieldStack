### Configuring Alerts in Suricata with Wazuh Agent
###### I created this repository because I experienced an issue where Suricata wasn't detecting ICMP (ping) traffic. In this guide, I’ll explain how to configure it properly so that this type of traffic is captured and alerts are generated.
#### Introduction
This is a brief overview of how to configure Suricata within the Wazuh agent to generate alerts based on specific network traffic. I won’t go into too much detail since I’ll include screenshots to illustrate each step clearly.
1. Verifying the initially captured traffic:
First, I’ll show the traffic that Suricata was capturing while I was performing a ping from one PC to another. As you'll see in the corresponding screenshot, no ICMP packets were being captured, which indicated a misconfiguration.