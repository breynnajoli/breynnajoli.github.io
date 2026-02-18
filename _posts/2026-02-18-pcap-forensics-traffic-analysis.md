---
title: "Hunting in the Wires: PCAP Forensics and Network Traffic Analysis"
date: 2026-02-18 20:30:00 
categories: [Cybersecurity, Digital Forensics]
tags: [wireshark, tcpdump, pcap, tryhackme]
---

## The Invisible Battlefield
In cybersecurity, the network never lies. Whether you are hunting for an Advanced Persistent Threat (APT) or completing a digital forensics room on TryHackMe, the truth is always hidden in the packets. 

Recently, I've been expanding my Blue Team and SOC (Security Operations Center) skills by moving beyond basic network configuration and diving deep into **Network Traffic Analysis** using industry-standard tools like `tcpdump` and **Wireshark**.

## The Challenge: Dissecting PCAP Files
Capturing traffic is easy; making sense of it is the real engineering challenge. My recent lab work has heavily focused on analyzing raw `.pcap` files to identify network anomalies and trace attacker lateral movement. 

By analyzing the OSI Model from the ground up—starting with physical Layer 1 and Layer 2 protocols like Ethernet and ARP—I've been practicing how to spot the subtle indicators of compromise (IoCs) that automated tools often miss.

## Decrypting Traffic & Extracting Artifacts
One of the most complex challenges I've tackled recently involves pulling actionable intelligence out of encrypted traffic. My workflow includes:
* **Protocol Deep Dives:** Filtering out the noise in Wireshark to isolate suspicious TCP streams and UDP broadcasts.
* **RDP Decryption:** Utilizing session keys to decrypt Remote Desktop Protocol (RDP) traffic to see exactly what a simulated attacker was doing on a compromised host.
* **File Extraction:** Carving out and reassembling embedded files and malicious payloads directly from the packet captures for further malware analysis.

## Securing the Switch
Of course, detecting an attack is only half the job—preventing it is the other. I pair this forensics work with active **Switch Security Configuration** in Cisco Packet Tracer. By implementing robust VLAN segregation, Port Security, DHCP Snooping, and BPDU Guard, I ensure that the very infrastructure the packets travel on is hardened against spoofing and rogue devices.

## The Takeaway
Cloud security (AWS) and physical hardware engineering rely on a secure network foundation. By mastering tools like Wireshark and `tcpdump`, I am building the analytical mindset required to not just build complex systems, but to actively defend them from the wire up.
