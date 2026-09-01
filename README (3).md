# Network Traffic Analysis Using Wireshark and Zeek (Simulation)

Cybersecurity project analyzing live network traffic using both interactive packet inspection (Wireshark) and automated flow-based analysis (Zeek), with a comparison of what each tool surfaces.

## 🎯 Objective

Capture and analyze real network traffic to understand normal traffic patterns and demonstrate packet-level and flow-level analysis skills relevant to a SOC/analyst role.

## 🛠️ Tools & Environment

- **OS:** Linux Mint 22.3 (Cinnamon), run in a VirtualBox VM
- **Packet capture:** Wireshark 4.2.2 / TShark
- **Flow analysis:** Zeek 8.2.1

## 📁 Repository Contents

| File / Folder | Description |
|---|---|
| `Network_Traffic_Analysis_Report.docx` | Full report — methodology, findings, and Wireshark vs. Zeek comparison |
| `my_traffic_capture.pcap` | Raw packet capture (43,092 packets, ~47 MB) |
| `zeek_analysis/` | Zeek output logs (`conn.log`, `dns.log`, `ssl.log`, `weird.log`, etc.) |
| `screenshots/` | Wireshark analysis screenshots (DNS, ICMP, TLS/SNI filtering) |

## 🔍 Key Findings

- **789 DNS packets** — including background OS/browser telemetry alongside manual lookups
- **166 TLS Client Hello packets** — showed that encrypted HTTPS traffic still leaks destination domains via the SNI field
- **Zeek's `weird.log`** automatically flagged protocol anomalies (247× connection reuse, checksum issues) that would otherwise require manual digging in Wireshark

## 📊 Wireshark vs. Zeek

| | Wireshark | Zeek |
|---|---|---|
| **Style** | Manual, packet-level | Automated, flow-level |
| **Best for** | Deep-dive on a specific stream | Fast triage across a full capture |
| **Anomaly detection** | Manual | Automatic (`weird.log`) |

## 👤 Author

Abhinav Anand — PBEL Cohort 2 Cybersecurity Program
