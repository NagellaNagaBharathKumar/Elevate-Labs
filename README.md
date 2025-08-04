# Task 1: Scan Your Local Network for Open Ports

## Objective
To identify open ports and potential risks on devices in the local network using Nmap.

## Tools Used
- Nmap
- Wireshark (optional)

## Steps Followed
1. **Identified Local IP Range:**
   Used `ipconfig` (on Windows) to find the local IP and subnet.
   - Detected subnet: `192.168.1.0/24`

2. **Performed a TCP SYN Scan and Saved as text file:**
   Ran the following command:
   - nmap -sS 192.168.1.0/24 -oN scan_results.txt

3. Analyzed the output to identify live hosts and open ports.

4. Noted device vendors using MAC addresses.

5. Researched services and associated vulnerabilities.

6. Optionally captured and reviewed packets with Wireshark. 

## Scan Summary
| IP Address | Open Ports | MAC Vendor |
| --- | --- | --- |
| 192.168.1.1 | 23 (filtered), 53, 80, 443 | ZTE – Likely a router |
| 192.168.1.2	| 80, 554	| CP Plus – IP camera |
| 192.168.1.17	| None	| Unknown |
| 192.168.1.19	| 22	| AzureWave – Possibly a laptop |
| 192.168.1.26	| All ports filtered	| AzureWave – Unknown device |
| 192.168.1.29	| None	| Unknown |
| 192.168.1.43	| 135, 139, 445, 902, 912, 2869, 3306, 7070	| Windows PC with database services |
| 192.168.1.52	| None	| Unknown |

## Security Observations
| Port |	Service |	Risk/Comments |
| --- | --- | --- |
| 23	| Telnet (filtered)	| Insecure protocol; should be disabled or replaced with SSH |
| 22	| SSH	| Ensure strong password/authentication |
| 80/443 |	HTTP/HTTPS	| Web interfaces; ensure they are password protected and up-to-date |
| 554	| RTSP	| Streaming protocol, likely used by cameras; secure with credentials |
| 445 |	SMB |	Vulnerable to exploits like EternalBlue; patching and firewall needed |
| 3306 |	MySQL	| Sensitive if exposed; ensure authentication and restrict access |
| 902/912	| Management Services	| Verify if still needed; may expose backdoors |
| 7070	| RealServer	| Obsolete service; remove if unnecessary |

## Conclusion
This task helped me learn how to use Nmap to map my local network, identify open ports, and understand the security implications of running various services. It emphasizes the importance of network hygiene and regular audits to protect against vulnerabilities.
