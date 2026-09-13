# Domain 4: Communication and Network Security (13%)

Network architecture, protocols, components, and attacks. Overlaps heavily with practical networking knowledge.

## 4.1 Network models

- **OSI Model (7 layers)** — Physical, Data Link, Network, Transport, Session, Presentation, Application ("Please Do Not Throw Sausage Pizza Away"). Know what operates at each layer:
  - L1 Physical — cabling, hubs, repeaters.
  - L2 Data Link — switches, bridges, MAC addresses, ARP, PPP.
  - L3 Network — routers, IP, ICMP, routing protocols.
  - L4 Transport — TCP/UDP, ports, segmentation, reliability.
  - L5 Session — session establishment/teardown (NetBIOS, RPC).
  - L6 Presentation — data formatting/encryption/compression (SSL/TLS conceptually spans 5–6).
  - L7 Application — HTTP, FTP, SMTP, DNS, the protocols users/apps interact with directly.
- **TCP/IP Model (4 layers)** — Link, Internet, Transport, Application — the practical model actual networks run on; maps roughly onto OSI.
- **TCP three-way handshake**: SYN → SYN-ACK → ACK. Connection-oriented, reliable, ordered. UDP is connectionless, unreliable, faster (used for DNS queries, streaming, VoIP).

## 4.2 IP addressing and protocols

- **IPv4** — 32-bit, dotted decimal, address exhaustion drove NAT/IPv6 adoption.
- **IPv6** — 128-bit, built-in IPsec support (optional in practice), no broadcast (uses multicast), simplified header.
- **NAT/PAT** — translates private to public addresses; provides an incidental (not a real) security benefit by hiding internal addressing.
- **DNS** — hierarchical name resolution; **DNSSEC** adds cryptographic authentication of DNS responses to prevent cache poisoning/spoofing.
- **DHCP** — dynamic IP assignment; rogue DHCP servers are an attack vector.
- **ARP** — resolves IP to MAC address; **ARP spoofing/poisoning** is a classic L2 MITM attack.

## 4.3 Secure network architecture design

- **Segmentation** — VLANs, subnets, physically separate networks; limits blast radius and lateral movement.
- **DMZ (Demilitarized Zone)** — a buffer network segment hosting public-facing services, isolated from the internal network by firewalls on both sides.
- **Screened subnet** — the modern (dual-firewall) implementation of a DMZ.
- **Network Access Control (NAC)** — enforces device compliance (patch level, AV status) before granting network access (802.1X).
- **Software-Defined Networking (SDN)** — separates the control plane from the data plane for centralized, programmable network management.
- **Micro-segmentation** — fine-grained, often workload-level segmentation, core to Zero Trust network design.

## 4.4 Secure network components

- **Firewalls**: packet-filtering (stateless, L3/L4 rules), stateful inspection (tracks connection state), proxy/application-layer (inspects L7 content), next-gen (NGFW — adds IPS, application awareness, TLS inspection).
- **IDS vs. IPS**: IDS is passive/detective (alerts only); IPS is active/preventive (can block in-line). Both can be signature-based (known patterns, low false positives, misses novel attacks) or anomaly/behavior-based (detects unknown attacks, higher false-positive rate).
- **Proxies**: forward proxy (client-side, controls/filters outbound traffic), reverse proxy (server-side, load balancing, SSL termination, hides backend servers).
- **Load balancers**: distribute traffic; also provide availability/redundancy.
- **Endpoint security**: EDR/XDR (Endpoint/Extended Detection and Response) for host-level visibility and response.

## 4.5 Secure communication channels

- **VPN**: site-to-site vs. remote-access; **IPsec** (network-layer, uses AH for integrity/authentication and ESP for confidentiality+integrity, operates in transport mode [payload only] or tunnel mode [entire packet, used for site-to-site]) vs. **TLS-based VPN** (SSL VPN, easier through firewalls, often clientless).
- **TLS** (successor to SSL, which is deprecated/insecure) — secures application-layer traffic (HTTPS, etc.); handshake negotiates cipher suite and exchanges keys.
- **Remote access**: RDP, SSH (replaces insecure Telnet), always paired with strong authentication (MFA) for remote access.
- **VoIP security**: SRTP for media encryption, separate VLAN from data traffic, toll fraud risk.
- **Multimedia collaboration**: video conferencing security — encryption, waiting rooms, meeting authentication (relevant post-2020 threat landscape).

## 4.6 Network attacks

- **Denial of Service (DoS/DDoS)**: volumetric (bandwidth exhaustion), protocol (e.g., SYN flood exhausts connection state tables), application-layer (e.g., HTTP flood targeting a specific resource).
- **On-path/Man-in-the-Middle (MITM)**: ARP spoofing, rogue access points, SSL stripping.
- **DNS attacks**: cache poisoning, DNS tunneling (exfiltration via DNS queries), typosquatting.
- **Wireless attacks**: rogue APs, evil twin, WEP/WPA cracking (WEP is fundamentally broken; use WPA3 where possible), deauthentication attacks, Bluetooth attacks (bluejacking, bluesnarfing).
- **Sniffing/eavesdropping**: passive traffic capture on unencrypted or improperly segmented networks (mitigated by switching + encryption, not by switching alone).

## Key exam tips

- Know the OSI layers cold, both order and what device/protocol lives at each — this is tested very directly and repeatedly.
- IDS = detect only; IPS = detect AND block. Don't confuse them.
- IPsec AH = integrity/auth only (no encryption); ESP = encryption + integrity. AH+ESP together is possible but uncommon in practice.
