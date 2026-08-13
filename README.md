# Wireshark QUIC Traffic Analysis

## Project Overview

This project documents the analysis of a Wireshark packet capture (PCAPNG) containing encrypted network traffic generated during normal web activity. The objective was to identify protocols, endpoints, conversations, DNS activity, and potential security concerns while applying network traffic analysis methodologies used in Security Operations Center (SOC) environments.

The investigation focused on:

- Protocol distribution
- Endpoint identification
- Network conversations
- DNS resolution activity
- QUIC/HTTP3 traffic analysis
- Security assessment and findings

---

## Objectives

- Analyze captured network traffic using Wireshark
- Identify dominant protocols and communication patterns
- Correlate DNS activity with observed network connections
- Investigate large-volume encrypted sessions
- Produce a professional security analysis report
- Document findings using industry-standard reporting practices

---

## Tools Used

| Tool | Purpose |
|--------|---------|
| Wireshark | Packet capture analysis |
| Windows 10 | Analysis environment |
| DNS Analysis | Domain resolution investigation |
| Protocol Hierarchy Statistics | Protocol identification |
| Endpoint Statistics | Host identification |
| Conversation Statistics | Traffic flow analysis |

---

## Capture Information

| Item | Value |
|--------|--------|
| File Format | PCAPNG |
| Capture Duration | 15 minutes 23 seconds |
| Packets Captured | 894,728 |
| Total Data | 977 MB |
| Average Packet Size | 1,092 Bytes |
| Capture Interface | Wi-Fi |

---

## Key Findings

### Finding 1: Protocol Analysis

Protocol hierarchy statistics revealed that QUIC traffic dominated the capture.

| Protocol | Percentage of Packets |
|-----------|----------------------|
| UDP | 77.8% |
| QUIC | 76.6% |
| TCP | 22.2% |
| HTTP | Minimal |
| DNS | Minimal |

Observation:

Modern encrypted web traffic primarily used QUIC over UDP port 443, indicating HTTP/3 communications.

---

### Finding 2: Endpoint Analysis

Primary internal host:

```
192.168.0.199
```

Most active external hosts included:

```
173.194.23.72
173.194.23.9
102.89.94.12
197.210.176.240
142.251.155.119
```

The internal workstation exchanged approximately 977 MB of traffic during the capture period.

---

### Finding 3: Conversation Analysis

Highest-volume conversation:

| Field | Value |
|---------|---------|
| Internal Host | 192.168.0.199 |
| External Host | 173.194.23.72 |
| Protocol | QUIC |
| Port | UDP/443 |
| Packets | 598,598 |
| Traffic Volume | ~702 MB |
| Duration | ~266 seconds |

Observation:

Traffic characteristics were consistent with large-scale encrypted content delivery.

---

### Finding 4: DNS Analysis

Observed DNS requests included:

- www.google.com
- youtube.com
- www.youtube.com
- ogads-pa.clients6.google.com

DNS responses returned multiple Google-owned IP addresses.

Observation:

DNS activity was consistent with legitimate browsing and media streaming behavior.

---

### Finding 5: QUIC Handshake Analysis

Packet analysis confirmed:

- QUIC Initial Packets
- QUIC Handshake Packets
- ACK Frames
- Protected Payload Traffic

Observation:

Traffic transitioned normally from handshake to encrypted payload exchange.

---

## Security Assessment

No indicators of malicious activity were identified during analysis.

Observed traffic was consistent with:

- Web browsing
- Video streaming
- Google services
- YouTube content delivery
- Encrypted HTTP/3 communications

No evidence of:

- Port scanning
- Command-and-control traffic
- Malware communications
- DNS tunneling
- Data exfiltration

was observed.

---

## Skills Demonstrated

- Wireshark Analysis
- Network Traffic Investigation
- Protocol Analysis
- DNS Investigation
- QUIC/HTTP3 Analysis
- Endpoint Analysis
- Traffic Profiling
- Security Reporting
- Network Forensics
- SOC Analyst Methodology

---

## Repository Structure

```text
wireshark-quic-traffic-analysis/
│
├── README.md
│
├── evidence/
│   ├── protocol-hierarchy.png
│   ├── ipv4-endpoints.png
│   ├── udp-conversations.png
│   ├── dns-analysis.png
│   └── quic-handshake.png
│
├── reports/
│   └── traffic-analysis-report.md
│
└── findings/
    ├── finding-01-protocols.md
    ├── finding-02-endpoints.md
    ├── finding-03-conversations.md
    └── finding-04-dns-analysis.md
```

---

## Author

Victor Temitope Adekule

Cybersecurity Analyst | Google Cybersecurity Professional Certificate Graduate | Network Traffic Analysis Enthusiast
