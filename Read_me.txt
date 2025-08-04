Task 1 – Nmap TCP SYN Scan & Wireshark Analysis

🎯 Objective:
To perform a TCP SYN scan on the local network using Nmap to identify open ports, and use Wireshark to analyze the packet behavior during the scan.

🛠 Tools Used:
- Nmap v7.95
- Wireshark
- Kali Linux (or any Linux OS)
- Network Range: 10.0.2.0/24

📍 Steps Performed:

1. Identified IP Address & Subnet:
   Command used: ip a
   - Local IP: 10.0.2.15
   - Subnet Range: 10.0.2.0/24
   (Saved in ip_info.txt)

2. Performed TCP SYN Scan:
   Command used: nmap -sS 10.0.2.0/24 -oN scan.txt
   - SYN packets were sent to common ports
   - Output saved to scan.txt

3. Analyzed Nmap Scan Results:
   - Found 3 live hosts
   - Open ports only on 10.0.2.2
   (Details in scan_analysis.txt)

   Summary:

   IP Address     | Open Ports            | Services
   ---------------------------------------------------------
   10.0.2.2       | 135, 445, 902, 912    | msrpc, microsoft-ds, iss-realsecure, apex-mesh
   10.0.2.3       | None                  | All ports filtered
   10.0.2.15      | None                  | All ports closed (my machine)

🔬 Wireshark Analysis:
- Wireshark was used during the scan to observe SYN packets.
- Applied filter: tcp.flags.syn == 1 && tcp.flags.ack == 0
- Only SYN packets were captured, confirming Nmap’s stealth scan behavior.

Files Included:
- nmap_capture.pcapng – Packet capture file
- wireshark_analysis.txt – Notes from filtered packet inspection
- screenshot.png – Screenshot showing SYN packets

📁 Files in Repository:
- scan.txt               – Nmap scan output
- ip_info.txt            – IP and subnet details
- scan_analysis.txt      – Summary of scan results
- wireshark_analysis.txt – Packet behavior explanation
- nmap_capture.pcapng    – Wireshark capture file
- screenshot.png         – Screenshot of filtered SYNs
- README.txt             – This documentation file

✅ Conclusion:
This task helped me understand:
- How Nmap identifies open ports using TCP SYN scan (-sS)
- What a stealth scan looks like at the packet level using Wireshark
- The importance of network reconnaissance and service exposure
