---
layout: page
icon: fas fa-laptop-code
title: Lab Challenges
order: 5
---

Welcome to my **Lab Challenges** dashboard. 

In cybersecurity and cloud engineering, theoretical knowledge must be backed by hands-on execution. This section serves as a living log of my ongoing simulations, digital forensics challenges, and network architecture builds.

---

### 🌐 1. Network Architecture & Security (Cisco Packet Tracer)
Designing secure, resilient network topologies from the ground up.
* **Secure Layer 2 Infrastructure:** Segmented network traffic into designated VLANs (e.g., VLAN 10, 333, 999) and deployed 802.1Q trunking with dedicated native VLANs to harden the environment against common threats.
* **Switch Security Configuration:** Restricted unauthorized access by configuring Port Security (including absolute/inactivity aging and sticky MAC addresses with protect violation modes), PortFast, and BPDU Guard.
* **DHCP Threat Mitigation:** Implemented DHCP Snooping to actively prevent rogue DHCP services from compromising the network.
* **Wireless LAN (WLAN) Configuration:** Configured secure wireless local area networks, ensuring proper access control and seamless integration with the broader wired infrastructure.

### 🕵️‍♂️ 2. Digital Forensics & Traffic Analysis (Blue Team)
Hunting for indicators of compromise (IoCs) within network traffic.
* **PCAP Analysis:** Utilizing **Wireshark** and **tcpdump** to dissect raw `.pcap` files and trace simulated attacker lateral movement.
* **Payload Extraction:** Filtering TCP streams, decrypting RDP traffic using session keys, and extracting malicious artifacts directly from packet captures.

### ☁️ 3. Cloud Infrastructure (AWS)
Applying the principle of least privilege in cloud environments.
* **Identity and Access Management (IAM):** Architecting secure user groups, roles, and strict JSON-based permission policies for EC2 instances.
* **VPC Configuration:** Building secure Virtual Private Clouds to isolate development and production workloads.

### 🔧 4. Hardware & IoT Integration
Bridging the gap between physical sensors and logical control.
* **Microcontroller Systems:** Designing C++ firmware for multi-sensor safety systems (Fire, Gas, and Sound detection) and troubleshooting real-world circuit voltage drops.

---

## 🏅 Verified Lab Achievements & Certificates
Below are direct links to my completed, verified lab environments detailing the specific tools and protocols I have mastered.

* **[TryHackMe: Intro to Network Traffic Analysis](https://www.linkedin.com/posts/breyn-najoli_completed-intro-to-network-traffic-analysis-activity-7421640450060468224-xm4R?utm_source=share&utm_medium=member_desktop)**
  * **Overview:** A deep dive into packet sniffing and traffic analysis. This lab covered the practical use of BPF (Berkeley Packet Filter) syntax to filter noise and extract actionable intelligence from raw network traffic to identify anomalies.

* **[TryHackMe: Web Requests](https://www.linkedin.com/posts/breyn-najoli_completed-web-requests-activity-7423290941878272000-M9Mr?utm_source=share&utm_medium=member_desktop)**
  * **Overview:** An exploration of the core mechanics of HTTP/HTTPS protocols. This module involved analyzing request methods (GET, POST), manipulating HTTP headers, managing cookies, and understanding status codes to identify web application vulnerabilities.

* **[TryHackMe: DNS in Detail](https://tryhackme.com/room/dnsindetail?utm_campaign=social_share&utm_medium=social&utm_content=share-completed-room&utm_source=copy&sharerId=696528afed5c2786429079a2)**
  * **Overview:** A comprehensive breakdown of the Domain Name System hierarchy. This lab focused on analyzing record types (A, CNAME, TXT, MX) and understanding how DNS resolves domain names—a critical skill for network troubleshooting and identifying DNS-based attack vectors.

---
> 💡 *Check out the posts on my main feed for deep-dive technical write-ups on these specific challenges!*
{: .prompt-tip }
