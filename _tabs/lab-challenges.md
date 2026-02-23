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

### 🔐 2. Enterprise VPN Architecture
Establishing secure, encrypted wide-area network communications.

* **Site-to-Site IPsec VPN Tunnels:** Architected secure communication channels between remote Cisco routers by configuring ISAKMP Phase 1 (AES encryption, pre-shared key authentication) and IPsec Phase 2 (3DES encryption, SHA-HMAC for data integrity).

### 🕵️‍♂️ 3. Digital Forensics & Traffic Analysis (Blue Team)
Hunting for indicators of compromise (IoCs) within network traffic.
* **PCAP Analysis:** Utilizing **Wireshark** and **tcpdump** to dissect raw `.pcap` files and trace simulated attacker lateral movement.
* **Payload Extraction:** Filtering TCP streams, decrypting RDP traffic using session keys, and extracting malicious artifacts directly from packet captures.

### 🌍 4. Web Application Security & Protocols
Understanding how data travels, resolves, and is manipulated across the internet.
* **Protocol Analysis:** Deep dive into the core mechanics of HTTP/HTTPS protocols, request methods (GET, POST), headers, and cookies to identify web application vulnerabilities.
* **DNS Resolution:** Explored the Domain Name System hierarchy, analyzing record types (A, CNAME, TXT, MX) and understanding how DNS resolves domain names.

### 🖥️ 5. Web Server Infrastructure
Managing and securing the backbone of web applications.

* **Server Architecture & Workflows:** Analyzed the underlying architecture of the "Big Three" web servers (Apache, NGINX, IIS), including their request-handling workflows.
* **HTTP Status Code Diagnostics:** Investigated server-side HTTP response codes (e.g., 200 OK, 404 NOT FOUND, 500 Internal Server Error) to understand web infrastructure health and identify potential misconfigurations.

### ☁️ 6. Cloud Infrastructure (AWS)
Applying the principle of least privilege in cloud environments.
* **Identity and Access Management (IAM):** Architecting secure user groups, roles, and strict JSON-based permission policies for EC2 instances.
* **VPC Configuration:** Building secure Virtual Private Clouds to isolate development and production workloads.

### 🔧 7. Hardware & IoT Integration
Bridging the gap between physical sensors and logical control.
* **Microcontroller Systems:** Designing C++ firmware for multi-sensor safety systems (Fire, Gas, and Sound detection) and troubleshooting real-world circuit voltage drops.

---

## 🏅 Verified Lab Achievements & Certificates
Below are direct links to my completed, verified lab environments detailing the specific tools and protocols I have mastered.

* **[TryHackMe: Intro to Network Traffic Analysis](https://www.linkedin.com/posts/breyn-najoli_completed-intro-to-network-traffic-analysis-activity-7421640450060468224-xm4R?utm_source=share&utm_medium=member_desktop)**
  * **Overview:** A deep dive into packet sniffing and traffic analysis using BPF (Berkeley Packet Filter) syntax to extract actionable intelligence from raw network traffic.

* **[TryHackMe: Web Requests](https://www.linkedin.com/posts/breyn-najoli_completed-web-requests-activity-7423290941878272000-M9Mr?utm_source=share&utm_medium=member_desktop)**
  * **Overview:** An exploration of the core mechanics of HTTP/HTTPS protocols, analyzing request methods, manipulating headers, managing cookies, and understanding status codes.

* **[TryHackMe: DNS in Detail](https://tryhackme.com/room/dnsindetail?utm_campaign=social_share&utm_medium=social&utm_content=share-completed-room&utm_source=copy&sharerId=696528afed5c2786429079a2)**
  * **Overview:** A comprehensive breakdown of the Domain Name System hierarchy, focusing on analyzing record types (A, CNAME, TXT, MX) and resolving domain names.

---
> 💡 *Check out the posts on my main feed for deep-dive technical write-ups on these specific challenges!*
{: .prompt-tip }
