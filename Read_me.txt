Task 1 – Nmap TCP SYN Scan & Wireshark Analysis

🎯 Objective:
To perform a TCP SYN scan on the local network using Nmap to identify open ports, analyze the results, and capture scan activity using Wireshark. Additional detailed scans were also performed for deeper insight.

🛠 Tools Used:
- Nmap v7.95
- Wireshark
- Kali Linux (or compatible OS)
- Virtual Network (10.0.2.0/24)

📍 Steps Performed:

1. Identified IP Address & Subnet:
Command used: ip a
- Local IP: 10.0.2.15
- Subnet Range: 10.0.2.0/24
Saved in: ip_info.txt

2. Performed TCP SYN Scan:
Command used: nmap -sS 10.0.2.0/24 -oN scan.txt
- Detected live hosts and open ports
- Output saved in scan.txt

3. Analyzed Nmap Results:
Summary of scan.txt stored in scan_analysis.txt

IP Address   | Open Ports         | Services
------------------------------------------------------------
10.0.2.2     | 135, 445, 902, 912 | msrpc, microsoft-ds, VMware/auth services
10.0.2.3     | None               | All ports filtered
10.0.2.15    | None               | All ports closed (my system)

🔬 Wireshark Packet Analysis:

Captured TCP SYN packets sent by Nmap during the scan.

Filter used:
tcp.flags.syn == 1 && tcp.flags.ack == 0

- Shows stealth scan behavior (no full TCP handshake).
- Files:
  - nmap_capture.pcapng
  - wireshark_analysis.txt
  - screenshot.png

🧪 Additional Scans Performed:

1. Aggressive Scan (nmap -A 10.0.2.0/24):
- Detected service versions, OS fingerprints, and traceroutes
- Found VMware Authentication services on host 10.0.2.2
- Guessed virtual environments (QEMU, VirtualBox)
- Output saved in: aggressive_scan.txt

2. Targeted Host Scan (nmap -sS 10.0.2.2):
- Confirmed open ports on specific host 10.0.2.2
- Revalidated 135, 445, 902, 912
- Output saved in: host_10.0.2.2.txt

📁 Files Included:

scan.txt               – TCP SYN scan of subnet
ip_info.txt            – Interface and IP configuration
scan_analysis.txt      – Summary of scanned hosts
wireshark_analysis.txt – Packet capture explanation
nmap_capture.pcapng    – Wireshark capture file
screenshot.png         – Screenshot showing filtered SYN packets
aggressive_scan.txt    – Aggressive scan with OS & service detection
host_10.0.2.2.txt      – Targeted scan of 10.0.2.2
README.txt             – Project documentation

✅ Conclusion:

This task provided hands-on practice in:
- Identifying hosts and services using Nmap
- Performing stealth (SYN) scans
- Observing network traffic with Wireshark
- Enhancing analysis using aggressive and focused scanning

It reinforced the importance of network reconnaissance and understanding how services expose potential attack surfaces.
