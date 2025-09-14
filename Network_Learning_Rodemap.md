### DevOps Engineer Networking Study Roadmap (Part 1)

**Overview:** Networking is the foundation of DevOps. Understanding it helps you better deploy, monitor, and secure your applications and services. This study plan will guide you from a foundational understanding of network models to the core concepts of addressing, protocols, security, and troubleshooting.

**Estimated Study Time:** 2 Weeks

**Recommended Tools:**
* **Wireshark:** A network protocol analyzer that lets you "see" the data packets flowing through your network. It's an excellent tool for understanding protocols and troubleshooting issues.
* **Various Command-Line Tools:** `ping`, `traceroute`, `netstat`, `nslookup`, `dig`, `iptables`, `ufw`, etc.

---

### Week 1: Network Fundamentals & Core Services

This week's goal is to build a high-level understanding of network communication models and to master how devices obtain addresses and find each other using domain names.

* [x] **1. Understand Layered Network Models (OSI & TCP/IP)**
    * [x] **Theoretical Learning:**
        * [x] Learn why layered models are necessary (e.g., to reduce complexity, for standardization).
        * [x] **OSI Model (7 Layers):** Understand the function and purpose of each layer (Physical, Data Link, Network, Transport, Session, Presentation, Application).
        * [x] **TCP/IP Model (4/5 Layers):** Understand its relationship to the OSI model and how it functions in the real world (Link/Network Interface, Internet, Transport, Application).
        * [x] **Core Concept:** Grasp the process of data encapsulation and de-encapsulation—how headers are added and removed as data moves through the layers.
    * [x] **Practice & Tools:**
        * [x] **First Look at Wireshark:** Install Wireshark, capture a simple web browsing session (an HTTP request), and observe the packet structure at different layers (e.g., Ethernet frame, IP packet, TCP segment).

* [ ] **2. IP Addressing and Subnetting**
    * [ ] **Theoretical Learning:**
        * [x] **IPv4 Addresses:** Understand the 32-bit address structure, Classful addressing (A/B/C/D/E), and private IP ranges (e.g., `10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`).
        * [x] **Subnet Mask:** Understand its role in distinguishing the network portion from the host portion of an address.
        * [x] **CIDR (Classless Inter-Domain Routing):** Learn the `a.b.c.d/n` notation, which is the modern, more flexible standard.
        * [x] **Subnetting:** Learn how to divide a large network block into smaller sub-networks to improve address efficiency and security.
        * [x] **IPv6 (Introduction):** Understand the need for IPv6, the format of its 128-bit addresses, and its key differences from IPv4.
    * [x] **Practice & Tools:**
        * [x] Use `ipconfig` (Windows) or `ifconfig`/`ip addr` (Linux/macOS) on your computer to check your IP address, subnet mask, and default gateway.
        * [x] Use an online subnet calculator to practice planning and calculating subnets.

* [x] **3. Core Network Services (DNS & DHCP)**
    * [x] **Theoretical Learning:**
        * [x] **DHCP (Dynamic Host Configuration Protocol):** Understand its workflow (Discover, Offer, Request, Acknowledge - DORA) and how it automatically assigns IP addresses, subnet masks, default gateways, and DNS servers to devices.
        * [x] **DNS (Domain Name System):** Understand its role as the "phonebook of the internet," translating human-readable domain names (like `www.google.com`) into machine-readable IP addresses.
        * [x] Learn about basic DNS record types (A, AAAA, CNAME, MX, NS).
        * [x] Understand the hierarchical structure of DNS (Root -> TLD -> Authoritative servers) and the recursive query process.
    * [x] **Practice & Tools:**
        * [x] Use `nslookup` or `dig` to query the IP address of a domain (e.g., `dig google.com`).
        * [x] Use Wireshark again to capture the DNS query process and observe the DNS request and response packets.

### Week 2: Protocols, Security & Troubleshooting

The goal for this week is to delve into the specific protocols that applications rely on, and to learn how to protect your network and diagnose problems when they occur.

* [ ] **4. Common Network Protocols**
    * [ ] **Theoretical Learning:**
        * [ ] **HTTP (Hypertext Transfer Protocol):** Understand its stateless nature, request/response model, common methods (GET, POST, PUT, DELETE), and status codes (200, 301, 404, 500).
        * [ ] **HTTPS (Hypertext Transfer Protocol Secure):** Understand its difference from HTTP and how SSL/TLS provides encryption, authentication, and integrity for communication.
        * [ ] **FTP (File Transfer Protocol):** Learn its basic working principle, including the command channel and data channel.
        * [ ] **SSH (Secure Shell):** As one of the most important tools for a DevOps engineer, understand how it provides secure remote login and command execution.
        * [ ] **TCP vs. UDP:** Understand the key differences between these two transport layer protocols (connection-oriented vs. connectionless, reliable vs. unreliable) and their respective use cases (HTTP/FTP use TCP; DNS/video streaming often use UDP).
    * [ ] **Practice & Tools:**
        * [ ] Use your browser's developer tools (F12) and inspect the Network tab to observe HTTP/HTTPS requests and responses while loading a webpage.
        * [ ] Use the `ssh` command to remotely connect to a server (if you don't have one, consider a free-tier cloud instance or a local VM).
        * [ ] Use Wireshark to filter and observe SSH and HTTPS traffic (Note: The content will be encrypted, but you can see the protocol handshake).

* [ ] **5. Firewalls and Security Groups**
    * [ ] **Theoretical Learning:**
        * [ ] **Firewall Basics:** Understand their role as a security barrier and how they permit or deny traffic based on rules (source/destination IP, port, protocol).
        * [ ] **iptables:** Learn about this tool for managing the Linux kernel's netfilter firewall. Understand the basic concepts of Tables (filter, nat, mangle), Chains (INPUT, OUTPUT, FORWARD), and Rules.
        * [ ] **UFW (Uncomplicated Firewall):** Learn this user-friendly frontend for `iptables` and how to easily open or close ports with it.
        * [ ] **Security Groups (in Cloud Environments):** If you use a cloud provider (like AWS, GCP, Azure), understand how security groups act as instance-level virtual firewalls.
    * [ ] **Practice & Tools:**
        * [ ] On a Linux VM or server, use `sudo ufw status` to check the firewall status.
        * [ ] Try `sudo ufw allow ssh` and `sudo ufw allow 80/tcp` to open the ports for SSH and HTTP.
        * [ ] (Advanced) Try `iptables -L -n -v` to view the current `iptables` ruleset.

* [ ] **6. Basic Network Troubleshooting**
    * [ ] **Theory & Practice:**
        * [ ] **`ping`:** Learn how to use it to test network connectivity to another host and understand that it operates using the ICMP protocol.
        * [ ] **`traceroute` (or `tracert` on Windows):** Learn how to use it to trace the route that packets take from your computer to a destination host. It's a key tool for diagnosing latency and routing issues.
        * [ ] **`netstat` (or `ss` on modern Linux systems):** Learn how to use it to view network connections, routing tables, and interface statistics. A common use is `netstat -tuln` or `ss -tuln` to see which ports are being listened on.
        * [ ] **Troubleshooting Flow:** Establish a basic troubleshooting methodology: `ping` yourself (`127.0.0.1`) -> `ping` your local gateway -> `ping` a public IP (`8.8.8.8`) -> `ping` a domain name (`google.com`). This flow helps you systematically isolate the problem (local machine, LAN, DNS, or external network).

---