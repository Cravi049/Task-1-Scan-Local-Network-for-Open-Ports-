# Cyber Security Internship — Task 1: Scan Local Network for Open Ports
**Student:** Ravinshu
**Date:** 2025-09-22


## Objective
Scan my local network using Nmap and analyze packet captures with Wireshark to identify open ports and potential risks.


## Tools Used
- Nmap 7.95
- Wireshark


## Steps performed
1. Determined my network: `192.168.31.0/24`
2. Ran Nmap TCP SYN scan and saved results:
```bash
nmap -sS 192.168.31.237/24 -oN scan_result.txt -oX scan_result.xml
```

3. Captured the network traffic with Wireshark while scanning to observe SYN/SYN-ACK/RST behavior.

## Scan results (summary)

- 192.168.31.1 (router) — Open: 53, 80, 443, 7443, 8080, 8443

- 192.168.31.85 (SetTopBox) — Open: 2869, 33899

- 192.168.31.221 (at608.lan) — All scanned ports closed

- 192.168.31.237 (Ravi.lan) — Open: 22 (SSH), 902 (VMware), 7070 (RealServer)

### Full raw output is available in ```scan_result.txt.```

## Wireshark analysis

- Filters used: ```tcp.flags.syn == 1 ```and``` tcp.flags.syn == 1 && tcp.flags.ack == 1```

- Observed SYN from scanner, SYN-ACK from target, and RST from scanner (Nmap closes the handshake).

- Screenshot: ```screenshots/wireshark_capture.png```

## Security findings & recommendations

- Change default router/IoT device credentials.

- Restrict SSH access to trusted IPs and use key-based auth.

- Close unused ports and apply firewall rules.

- Keep VM/RealServer software up-to-date.

## Files included

- ```scan_result.txt``` — Nmap output

- ```scan_result.xml ```— Nmap XML output

- ```screenshots/nmap_scan.png ```— terminal screenshot

- ``` screenshots/wireshark_capture.png ```— packet capture screenshot
