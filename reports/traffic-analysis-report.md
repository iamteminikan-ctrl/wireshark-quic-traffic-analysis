# Network Traffic Analysis Report

## Executive Summary

A network traffic capture containing 894,728 packets and approximately 977 MB of data was analyzed using Wireshark. The purpose of the investigation was to identify network communication patterns, determine the dominant protocols in use, analyze endpoint activity, and assess whether any suspicious or malicious behavior was present.

The analysis determined that the majority of observed traffic consisted of encrypted QUIC communications over UDP port 443. DNS activity revealed communications with Google and YouTube services. No indicators of compromise (IOCs) or malicious activity were identified.

---

# Scope

The analysis included:

- Protocol Hierarchy Review
- Endpoint Identification
- Conversation Analysis
- DNS Investigation
- QUIC Session Analysis
- Security Assessment

---

# Environment

| Item | Value |
|---------|---------|
| Operating System | Windows 10 |
| Analysis Tool | Wireshark |
| Capture Type | Wi-Fi Traffic |
| File Format | PCAPNG |
| Capture Duration | 15m 23s |

---

# Protocol Analysis

Protocol hierarchy statistics showed:

| Protocol | Packets |
|------------|------------|
| IPv4 | 894,647 |
| UDP | 695,842 |
| QUIC | 686,186 |
| TCP | 198,770 |
| HTTP | 112 |
| DNS | 5,806 |

### Assessment

QUIC accounted for the majority of observed network traffic. This protocol is commonly used by modern web services utilizing HTTP/3.

---

# Endpoint Analysis

The primary internal host was:

```text
192.168.0.199
```

Traffic statistics:

| Metric | Value |
|----------|----------|
| Packets | 894,647 |
| Total Data | 977 MB |
| Transmitted | 21 MB |
| Received | 956 MB |

Top external endpoints included:

| External IP | Traffic Volume |
|-------------|----------------|
| 173.194.23.72 | 702 MB |
| 173.194.23.9 | 11 MB |
| 102.89.94.12 | 24 MB |
| 197.210.176.240 | 7 MB |
| 142.251.155.119 | 4 MB |

---

# Conversation Analysis

The largest observed conversation involved:

| Field | Value |
|---------|---------|
| Source | 192.168.0.199 |
| Destination | 173.194.23.72 |
| Protocol | QUIC |
| Port | UDP/443 |
| Packets | 598,598 |
| Duration | 266.67 seconds |

### Assessment

The traffic pattern was heavily download-oriented and consistent with encrypted content delivery or media streaming.

No abnormal session behavior was observed.

---

# DNS Analysis

Observed DNS requests:

- www.google.com
- youtube.com
- www.youtube.com
- ogads-pa.clients6.google.com

Observed DNS responses:

- 142.251.153.119
- 142.251.150.119
- 142.251.154.119
- 142.251.216.110
- 216.58.223.234

### Assessment

DNS activity aligned with legitimate Google and YouTube services.

No suspicious domains were identified.

---

# QUIC Analysis

Investigation of communications involving:

```text
173.194.23.72
```

revealed:

- QUIC Initial packets
- QUIC Handshake packets
- Protected Payload traffic
- UDP port 443 communications

### Assessment

The session followed the normal QUIC connection lifecycle:

```text
Initial
   ↓
Handshake
   ↓
Protected Payload
```

Traffic was encrypted after session establishment.

No protocol anomalies were detected.

---

# Security Findings

| Finding | Severity |
|------------|-----------|
| Large-volume QUIC traffic | Informational |
| Google/YouTube DNS activity | Informational |
| Encrypted HTTP/3 communications | Informational |
| Suspicious activity detected | None |

---

# Conclusion

The analyzed capture primarily consisted of legitimate encrypted web traffic utilizing QUIC and HTTP/3 protocols. DNS activity correlated with Google and YouTube services, and conversation analysis identified large-volume content delivery sessions. No evidence of malware communication, command-and-control activity, data exfiltration, DNS abuse, or other malicious behavior was observed.

Overall Risk Rating: **Low**

Recommendation:

Continue monitoring encrypted outbound traffic and establish baseline network behavior to support future anomaly detection efforts.
