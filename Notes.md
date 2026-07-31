# Notes: Cybersecurity Fundamentals, Networking, Cryptography & Linux Cheat-Sheet

## 1. Cybersecurity Basics

### CIA Triad
- **Confidentiality** – Only authorized people/systems can access the data. Achieved via encryption, access control, authentication.
- **Integrity** – Data is accurate and not tampered with, in transit or storage. Achieved via hashing (MD5, SHA-256), checksums, digital signatures.
- **Availability** – Systems and data are accessible when needed. Achieved via redundancy, backups, DDoS protection.

### Common Threat Types
- **Phishing** – Fake emails/websites trick users into giving up credentials or clicking malicious links.
- **Malware** – Malicious software (viruses, worms, trojans, ransomware) designed to damage or gain unauthorized access.
- **DDoS (Distributed Denial of Service)** – Flooding a server with traffic from multiple sources to make it unavailable.
- **SQL Injection** – Attacker inserts malicious SQL code into input fields to manipulate/extract database data.
- **Brute Force** – Repeatedly guessing passwords/keys until the correct one is found.
- **Ransomware** – Malware that encrypts victim's files and demands payment for the decryption key.

### Attack Vectors
- **Social Engineering** – Manipulating people psychologically into revealing confidential information (e.g., pretexting, baiting).
- **Wireless Attacks** – Exploiting weak Wi-Fi encryption, rogue access points, or packet sniffing on unsecured networks.
- **Insider Threats** – Employees or trusted individuals misusing their access to harm the organization.

---

## 2. Networking Basics

### OSI Model (7 Layers)
1. **Physical** – Raw bit transmission over physical medium (cables, radio).
2. **Data Link** – Node-to-node data transfer, MAC addressing (e.g., Ethernet).
3. **Network** – Logical addressing and routing (IP).
4. **Transport** – End-to-end communication, reliability (TCP/UDP).
5. **Session** – Managing sessions/connections between applications.
6. **Presentation** – Data translation, encryption, compression.
7. **Application** – End-user services (HTTP, FTP, DNS).

### TCP/IP Suite
- Simplified 4-layer model: **Network Access → Internet → Transport → Application**
- TCP = connection-oriented, reliable (handshake, retransmission).
- UDP = connectionless, faster, no guaranteed delivery.

### DNS & HTTP/HTTPS
- **DNS** translates domain names (e.g., google.com) into IP addresses.
- **HTTP** – unencrypted web traffic (port 80).
- **HTTPS** – HTTP secured with SSL/TLS encryption (port 443).

### IP Addressing, Subnetting, NAT
- IPv4 address = 32-bit, split into Network + Host portion using a subnet mask.
- **Subnetting** divides a network into smaller sub-networks for efficient IP management.
- **NAT (Network Address Translation)** maps private IPs to a public IP, allowing multiple devices to share one public IP.

---

## 3. Cryptography Basics

- **Symmetric Encryption** – Same key used to encrypt and decrypt (e.g., AES-256, used in our OpenSSL demo).
- **Asymmetric Encryption** – Public key encrypts, private key decrypts (e.g., RSA). Used in SSL/TLS handshakes.
- **Hashing** – One-way function producing a fixed-size fingerprint of data (MD5, SHA-256). Used for integrity checks, not reversible.
- **Digital Certificates / SSL/TLS** – Certificates issued by a trusted CA to verify server identity and enable encrypted communication (HTTPS).

**Hands-on performed:** Encrypted a text file using `openssl enc -aes-256-cbc`, decrypted it back, verified integrity with `diff` (no difference found), and generated SHA-256/MD5 hashes for the original file.

---

## 4. Linux Command Cheat-Sheet (used in this task)

| Command | Purpose |
|---|---|
| `pwd` | Print current working directory |
| `ls -l` | List files with permissions, owner, size |
| `chmod 700 file` | Change file permission (owner: read/write/execute only) |
| `chown` | Change file owner |
| `ifconfig` | Show network interface details (IP, MAC, packets) |
| `ping -c 5 <ip>` | Send 5 ICMP echo requests to test connectivity |
| `traceroute <host>` | Show the route (hops) packets take to reach a destination |
| `netstat -tuln` | Show listening TCP/UDP ports and active connections |
| `apt install <pkg>` | Install a package (Debian/Kali package manager) |

---

## 5. Tool Familiarization Summary

| Tool | Purpose | What we did |
|---|---|---|
| **Wireshark** | Packet capture & analysis | Captured live ICMP (ping) traffic between Kali and Metasploitable2, inspected Ethernet/IP/ICMP headers |
| **Nmap** | Network/port scanning | Scanned Metasploitable2, found 20+ open ports (ftp, ssh, http, mysql, vnc, etc.) |
| **Burp Suite** | Web application proxy | Launched Burp Suite Community Edition, confirmed dashboard/tabs load correctly |
| **Netcat** | Network debugging | Verified port 80 (HTTP) is open and reachable on target machine |

---

## Lab Environment
- **Attacker Machine:** Kali Linux (VMware) – IP 192.168.234.128
- **Target Machine:** Metasploitable2 – IP 192.168.234.131
- **Network Mode:** Host-only/NAT adapter (isolated lab network)
