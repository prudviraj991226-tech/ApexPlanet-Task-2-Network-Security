# ApexPlanet-Task-2-Network-Security
# 🛡️ Network Security & Scanning Lab

⚠️ **For Educational & Authorized Testing Purposes Only**

This project demonstrates basic **network reconnaissance, port scanning, vulnerability assessment, traffic analysis, and firewall testing** using Kali Linux and Metasploitable2 in an isolated cybersecurity laboratory environment.

---

## 🎯 Project Objective

The objective of this project is to understand and perform:

* 🔎 Network reconnaissance
* 📡 TCP & UDP scanning
* 🔐 Service and version detection
* 💻 Operating system detection
* 🛡️ Vulnerability assessment
* 📊 Network traffic analysis
* 🔥 Firewall testing
* 📝 Security documentation

---

## 🧰 Tools Used

| Tool                 | Purpose                  |
| -------------------- | ------------------------ |
| 🐉 Kali Linux        | Security testing machine |
| 💀 Metasploitable2   | Vulnerable test machine  |
| 🔎 Nmap              | Network & port scanning  |
| 🛡️ OpenVAS / Nessus | Vulnerability scanning   |
| 🦈 Wireshark         | Network traffic analysis |
| 🔥 Firewall          | Port & traffic filtering |

---

# 🔄 Project Workflow

```text
🐉 Kali Linux
      ↓
💀 Metasploitable2
      ↓
🔎 Nmap Scanning
      ↓
🛡️ OpenVAS / Nessus Scanning
      ↓
🦈 Wireshark Analysis
      ↓
🔥 Firewall Testing
      ↓
📝 Report & Documentation
```

---

# 🐉 1. Kali Linux Setup

Kali Linux was used as the security testing machine.

### Find Kali IP Address

```bash
ip -br addr
```

Example:

```text
eth0    UP    192.168.56.101/24
```

📸 Screenshot:

```text
screenshots/kali-ip.png
```

---

# 💀 2. Metasploitable2 Setup

Metasploitable2 was used as the intentionally vulnerable target machine.

### Find Target IP

```bash
sudo arp-scan --localnet
```

Record the Metasploitable2 IP address.

Example:

```text
Kali Linux:       192.168.56.101
Metasploitable2:  192.168.56.102
```

📸 Screenshot:

```text
screenshots/metasploitable-ip.png
```

---

# 📡 3. Connectivity Test

Check whether Kali can communicate with the target:

```bash
ping -c 4 <TARGET-IP>
```

Example:

```bash
ping -c 4 192.168.56.102
```

📸 Screenshot:

```text
screenshots/ping-test.png
```

---

# 🔎 4. Nmap Scanning

Nmap was used to identify open ports and services on the authorized test machine.

## TCP SYN Scan

```bash
sudo nmap -sS <TARGET-IP>
```

## UDP Scan

```bash
sudo nmap -sU <TARGET-IP>
```

## Service Version Detection

```bash
sudo nmap -sV <TARGET-IP>
```

## OS Detection

```bash
sudo nmap -O <TARGET-IP>
```

## Save Scan Results

```bash
nmap -sV -O <TARGET-IP> -oN nmap_report.txt
```

### 📋 Information Collected

* Open ports
* TCP/UDP services
* Service versions
* Operating system information
* Network observations

📸 Screenshots:

```text
screenshots/nmap-tcp.png
screenshots/nmap-udp.png
screenshots/nmap-services.png
screenshots/nmap-os.png
```

---

# 🛡️ 5. OpenVAS / Nessus Vulnerability Scanning

OpenVAS/Greenbone or Nessus Essentials was used to perform vulnerability assessment against the Metasploitable2 test machine.

### Information Collected

* 🔴 Critical vulnerabilities
* 🟠 High vulnerabilities
* 🟡 Medium vulnerabilities
* 🟢 Low vulnerabilities
* Affected ports
* Affected services
* Security recommendations

### Report

The vulnerability scan report is stored in:

```text
vulnerability/vulnerability_report.pdf
```

📸 Screenshot:

```text
screenshots/vulnerability-scan.png
```

---

# 🦈 6. Wireshark Traffic Analysis

Wireshark was used to capture and analyze traffic generated inside the laboratory network.

### Start Wireshark

```bash
wireshark
```

Select the interface connected to the lab network and start capturing.

---

## ICMP Traffic

Generate traffic:

```bash
ping -c 4 <TARGET-IP>
```

Wireshark filter:

```text
icmp
```

📸 Screenshot:

```text
screenshots/wireshark-icmp.png
```

---

## TCP Traffic

Wireshark filter:

```text
tcp
```

📸 Screenshot:

```text
screenshots/wireshark-tcp.png
```

---

## DNS Traffic

Generate a DNS request:

```bash
nslookup example.com
```

Wireshark filter:

```text
dns
```

📸 Screenshot:

```text
screenshots/wireshark-dns.png
```

---

## HTTP Traffic

If HTTP is available on the authorized Metasploitable2 test machine:

```text
http
```

Use this as the Wireshark display filter.

📸 Screenshot:

```text
screenshots/wireshark-http.png
```

---

## FTP Traffic

If FTP is available in the test environment:

```text
ftp
```

Use this as the Wireshark display filter.

📸 Screenshot:

```text
screenshots/wireshark-ftp.png
```

---

## 💾 Save Wireshark Capture

Save the packet capture as:

```text
task2_traffic_capture.pcapng
```

Store it in:

```text
wireshark/task2_traffic_capture.pcapng
```

---

# 🔥 7. Firewall Testing

Firewall testing was performed within the authorized laboratory environment.

### Testing Process

```text
Select Port
    ↓
Check Connectivity
    ↓
Apply/Observe Firewall Rule
    ↓
Test Again
    ↓
Record Result
```

### Record

| Port     | Protocol | Status          | Result     |
| -------- | -------- | --------------- | ---------- |
| `<PORT>` | TCP      | Allowed/Blocked | `<RESULT>` |
| `<PORT>` | TCP      | Allowed/Blocked | `<RESULT>` |
| `<PORT>` | UDP      | Allowed/Blocked | `<RESULT>` |

📸 Screenshot:

```text
screenshots/firewall-testing.png
```

---

# 📊 8. Results

## Nmap

```text
Target IP: <YOUR-TARGET-IP>
Open Ports: <YOUR-RESULT>
Services: <YOUR-RESULT>
OS: <YOUR-RESULT>
```

## Vulnerability Scan

```text
Critical: <YOUR-RESULT>
High:     <YOUR-RESULT>
Medium:   <YOUR-RESULT>
Low:      <YOUR-RESULT>
```

## Wireshark

Protocols analyzed:

```text
ICMP
TCP
DNS
HTTP
FTP
```

## Firewall

```text
Ports Tested: <YOUR-RESULT>
Allowed:      <YOUR-RESULT>
Blocked:      <YOUR-RESULT>
```

⚠️ **Replace all `<YOUR-RESULT>` values with your actual lab results.**

---

# 📁 9. Project Structure

```text
Task-2-Network-Security-Scanning/
│
├── README.md
│
├── 📁 nmap/
│   └── nmap_report.txt
│
├── 📁 vulnerability/
│   └── vulnerability_report.pdf
│
├── 📁 wireshark/
│   └── task2_traffic_capture.pcapng
│
├── 📁 firewall/
│   └── firewall_testing.txt
│
└── 📁 screenshots/
    ├── kali-ip.png
    ├── metasploitable-ip.png
    ├── ping-test.png
    ├── nmap-tcp.png
    ├── nmap-udp.png
    ├── nmap-services.png
    ├── nmap-os.png
    ├── vulnerability-scan.png
    ├── wireshark-icmp.png
    ├── wireshark-tcp.png
    ├── wireshark-dns.png
    ├── wireshark-http.png
    ├── wireshark-ftp.png
    └── firewall-testing.png
```

---

# 🎥 10. Demo Video

The demonstration video covers:

1. Kali Linux setup
2. Metasploitable2 target
3. IP identification
4. Nmap scanning
5. Vulnerability scanning
6. Wireshark analysis
7. Firewall testing
8. Final findings

### 🎬 Demo Video

```text
<YOUR-PUBLIC-VIDEO-LINK>
```

---

# 📝 11. Key Findings

### 🔎 Network Scanning

Nmap was used to identify open ports, services, service versions, and operating-system information.

### 🛡️ Vulnerability Assessment

OpenVAS/Nessus was used to identify vulnerabilities present in the intentionally vulnerable test machine.

### 🦈 Traffic Analysis

Wireshark was used to capture and analyze network protocols and packet-level communication.

### 🔥 Firewall Testing

Firewall testing demonstrated the effect of filtering on network connectivity.

---

# 🏁 12. Conclusion

This project provided practical experience in **network reconnaissance, Nmap scanning, vulnerability assessment, Wireshark packet analysis, and firewall testing**.

The complete exercise was performed in an isolated and authorized cybersecurity laboratory environment.

---

# ⚠️ Disclaimer

This project is intended strictly for **educational and authorized cybersecurity testing purposes**.

All scanning and testing were performed against the intentionally vulnerable **Metasploitable2** test machine in a controlled laboratory environment.

Do not scan or test systems without proper authorization.
