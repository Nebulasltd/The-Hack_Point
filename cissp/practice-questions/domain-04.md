# Domain 4 Practice Questions: Communication and Network Security

Original questions written for self-study, aligned to the domain outline in [`../domains/04-communication-and-network-security.md`](../domains/04-communication-and-network-security.md). Not sourced from any official exam.

---

**1.** At which OSI layer do switches primarily operate, making forwarding decisions based on MAC addresses?

A) Layer 1 (Physical)
B) Layer 2 (Data Link)
C) Layer 3 (Network)
D) Layer 4 (Transport)

<details><summary>Answer</summary>

**B.** Switches operate at Layer 2, using MAC addresses to forward frames within a local network segment. Routers operate at Layer 3, forwarding based on IP addresses.
</details>

---

**2.** A network monitoring tool detects a port scan in progress and generates an alert, but takes no action to stop the traffic. This tool is functioning as:

A) An IPS
B) A firewall
C) An IDS
D) A proxy

<details><summary>Answer</summary>

**C.** An IDS (Intrusion Detection System) is passive/detective — it alerts on suspicious activity but does not block it. An IPS (Intrusion Prevention System) sits in-line and can actively block traffic.
</details>

---

**3.** Which IPsec component provides encryption (confidentiality) in addition to integrity and authentication?

A) AH (Authentication Header)
B) ESP (Encapsulating Security Payload)
C) IKE alone
D) GRE

<details><summary>Answer</summary>

**B.** ESP provides confidentiality (encryption) plus integrity and authentication. AH provides integrity and authentication ONLY — no encryption.
</details>

---

**4.** An attacker sends forged ARP replies to a target, causing the target to send traffic intended for the default gateway to the attacker's machine instead. This is an example of:

A) DNS cache poisoning
B) ARP spoofing (a Layer 2 MITM technique)
C) A SYN flood
D) DNS tunneling

<details><summary>Answer</summary>

**B.** ARP spoofing/poisoning forges ARP replies to associate the attacker's MAC address with a legitimate IP (often the gateway), enabling a man-in-the-middle position on the local network segment.
</details>

---

**5.** Which network segment is specifically designed to host public-facing services, isolated from the internal network by firewalls on both sides?

A) VLAN
B) Screened subnet / DMZ
C) VPN concentrator zone
D) Extranet

<details><summary>Answer</summary>

**B.** A DMZ (demilitarized zone), implemented today typically as a screened subnet with firewalls on both the external and internal sides, isolates public-facing services from the trusted internal network.
</details>

---

**6.** A reverse proxy is primarily deployed to:

A) Control and filter outbound traffic from internal clients to the internet
B) Sit in front of backend servers to handle incoming requests, provide load balancing, and hide backend infrastructure
C) Encrypt traffic between two VPN endpoints
D) Resolve domain names to IP addresses

<details><summary>Answer</summary>

**B.** A reverse proxy sits on the server side, in front of one or more backend servers, handling and distributing incoming client requests while concealing the backend server details. A forward proxy sits on the client side, controlling outbound traffic.
</details>

---

**7.** Which protocol should replace Telnet for secure remote command-line administration?

A) RDP
B) SSH
C) SNMP v1
D) FTP

<details><summary>Answer</summary>

**B.** SSH (Secure Shell) provides encrypted remote command-line access and should always replace the unencrypted Telnet protocol.
</details>

---

**8.** A DDoS attack that exhausts a server's connection-tracking table by sending a flood of TCP SYN packets without completing the handshake is best classified as:

A) A volumetric attack
B) A protocol attack
C) An application-layer attack
D) A reflection attack only

<details><summary>Answer</summary>

**B.** A SYN flood exhausts a resource (connection state table) related to protocol handling itself, rather than simply consuming bandwidth (volumetric) or targeting application logic (application-layer).
</details>

---

**9.** DNSSEC primarily protects against which type of attack?

A) DNS cache poisoning / response spoofing, by cryptographically authenticating DNS responses
B) DDoS attacks against DNS servers
C) DNS tunneling for data exfiltration
D) Typosquatting

<details><summary>Answer</summary>

**A.** DNSSEC adds cryptographic signatures to DNS responses so a resolver can verify a response genuinely came from the authoritative source and wasn't spoofed/poisoned in transit.
</details>

---

**10.** Which wireless security standard should be preferred over WEP and (where supported) over WPA2, due to stronger encryption and protection against offline dictionary attacks on the handshake?

A) WEP
B) WPA
C) WPA2
D) WPA3

<details><summary>Answer</summary>

**D.** WPA3 improves on WPA2 with SAE (Simultaneous Authentication of Equals), which resists offline dictionary attacks against the handshake — a known weakness of WPA2's 4-way handshake. WEP is fundamentally broken and should never be used.
</details>

---

[← Back to CISSP module](../README.md)
