# Hacking Resources

A personal, curated reference for penetration testing and red team work: tools, methodology, cheat sheets, and learning material, organized by phase/category.

> This repo indexes and links to third-party tools and resources. It does not host exploit code or attack infrastructure.

## Legal & Ethical Use

Everything here is for authorized security testing, CTF practice, and personal lab use only:

- Only test systems you own or have **explicit, written authorization** to test (a signed scope/rules-of-engagement document).
- Unauthorized access to computer systems is illegal in most jurisdictions (e.g. the Computer Fraud and Abuse Act in the US, the Computer Misuse Act in the UK, and Tanzania's Cybercrimes Act, 2015).
- When in doubt, don't. Get scope in writing before you touch anything.

## Contents

- [Repo Structure](#repo-structure)
- [Recon & OSINT](#recon--osint)
- [Scanning & Enumeration](#scanning--enumeration)
- [Web Application Testing](#web-application-testing)
- [Exploitation Frameworks](#exploitation-frameworks)
- [Password & Credential Attacks](#password--credential-attacks)
- [Active Directory / Windows](#active-directory--windows)
- [Post-Exploitation & C2](#post-exploitation--c2)
- [Privilege Escalation](#privilege-escalation)
- [Wireless](#wireless)
- [Network & Traffic Analysis](#network--traffic-analysis)
- [Mobile](#mobile)
- [Cloud](#cloud)
- [Forensics & Reverse Engineering](#forensics--reverse-engineering)
- [Reporting](#reporting)
- [Distros & Environments](#distros--environments)
- [Methodology & Frameworks](#methodology--frameworks)
- [Learning Platforms & Practice](#learning-platforms--practice)
- [Certifications](#certifications)
- [Certification Modules](#certification-modules) — deep-dive study modules ([CISSP](cissp/README.md), [CISA](cisa/README.md))
- [Contributing](#contributing)

## Repo Structure

```
hacking-resources/
├── README.md            # this index
├── cheatsheets/          # quick-reference command sheets, one file per topic
├── cissp/                # CISSP certification study module
├── cisa/                 # CISA certification study module
└── notes/
    ├── recon/            # personal recon methodology & notes
    ├── exploitation/      # exploitation notes/write-ups
    ├── post-exploitation/ # post-exploitation & privesc notes
    ├── reporting/         # report templates and writing notes
    ├── cissp/             # personal CISSP study notes/progress
    └── cisa/              # personal CISA study notes/progress
```

The `README.md` is the index of external tools/resources. `notes/` and `cheatsheets/` are where you build up your own material (lab write-ups, CTF solutions, engagement notes) over time. `cissp/` and `cisa/` are standalone certification study modules — domain breakdowns, exam format, and resources, separate from the pentest tool index above.

## Recon & OSINT

- [Amass](https://github.com/owasp-amass/amass) — attack surface mapping and asset discovery (subdomains, DNS)
- [Subfinder](https://github.com/projectdiscovery/subfinder) — passive subdomain enumeration
- [theHarvester](https://github.com/laramies/theHarvester) — emails, subdomains, names from public sources
- [Recon-ng](https://github.com/lanmaster53/recon-ng) — modular web recon framework
- [Maltego](https://www.maltego.com/) — link-analysis OSINT platform
- [Shodan](https://www.shodan.io/) / [Censys](https://censys.io/) — internet-wide device/service search engines
- [SpiderFoot](https://github.com/smicallef/spiderfoot) — automated OSINT reconnaissance
- [OSINT Framework](https://osintframework.com/) — categorized directory of OSINT resources

## Scanning & Enumeration

- [Nmap](https://nmap.org/) — network discovery and port scanning
- [Masscan](https://github.com/robertdavidgraham/masscan) — very high-speed port scanner
- [Naabu](https://github.com/projectdiscovery/naabu) — fast port scanner from ProjectDiscovery
- [Nuclei](https://github.com/projectdiscovery/nuclei) — template-driven vulnerability scanner
- [Nikto](https://github.com/sullo/nikto) — web server scanner
- [enum4linux-ng](https://github.com/cddmp/enum4linux-ng) — SMB/Windows enumeration
- [Nessus](https://www.tenable.com/products/nessus) / [OpenVAS](https://www.openvas.org/) — vulnerability scanners

## Web Application Testing

- [Burp Suite](https://portswigger.net/burp) — intercepting proxy and web app testing platform
- [OWASP ZAP](https://www.zaproxy.org/) — free web app scanner/proxy
- [sqlmap](https://github.com/sqlmapproject/sqlmap) — automated SQL injection
- [ffuf](https://github.com/ffuf/ffuf) — fast web fuzzer
- [gobuster](https://github.com/OJ/gobuster) — directory/DNS/vhost brute-forcing
- [wfuzz](https://github.com/xmendez/wfuzz) — web application fuzzer
- [XSStrike](https://github.com/s0md3v/XSStrike) — XSS detection and exploitation
- [Corsy](https://github.com/s0md3v/Corsy) — CORS misconfiguration scanner
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/) — reference methodology
- [PortSwigger Web Security Academy](https://portswigger.net/web-security) — free interactive web-hacking labs

## Exploitation Frameworks

- [Metasploit Framework](https://github.com/rapid7/metasploit-framework) — exploit development and delivery framework
- [Sliver](https://github.com/BishopFox/sliver) — open-source adversary emulation / C2
- [Cobalt Strike](https://www.cobaltstrike.com/) — commercial adversary simulation platform
- [Exploit-DB](https://www.exploit-db.com/) — public exploit archive (maintained by Offensive Security)
- [searchsploit](https://github.com/offensive-security/exploitdb) — offline Exploit-DB search CLI

## Password & Credential Attacks

- [Hashcat](https://hashcat.net/hashcat/) — GPU-accelerated password recovery
- [John the Ripper](https://github.com/openwall/john) — password cracker
- [Hydra](https://github.com/vanhauser-thc/thc-hydra) — network login brute-forcer
- [CeWL](https://github.com/digininja/CeWL) — custom wordlist generator from a target website
- [SecLists](https://github.com/danielmiessler/SecLists) — the standard collection of wordlists/payloads for security testing

## Active Directory / Windows

- [BloodHound](https://github.com/SpecterOps/BloodHound) — AD attack-path graph analysis
- [Impacket](https://github.com/fortra/impacket) — Python classes for working with network protocols (PsExec, secretsdump, etc.)
- [NetExec](https://github.com/Pennyw0rth/NetExec) — network service enumeration/exploitation (successor to CrackMapExec)
- [Mimikatz](https://github.com/gentilkiwi/mimikatz) — Windows credential extraction
- [Rubeus](https://github.com/GhostPack/Rubeus) — Kerberos abuse toolkit
- [PowerView](https://github.com/PowerShellMafia/PowerSploit/blob/master/Recon/PowerView.ps1) / [PowerSploit](https://github.com/PowerShellMafia/PowerSploit) — AD/Windows recon & post-exploitation PowerShell modules
- [Certipy](https://github.com/ly4k/Certipy) — Active Directory Certificate Services (ADCS) abuse

## Post-Exploitation & C2

- [Sliver](https://github.com/BishopFox/sliver) — cross-platform C2 (also listed above)
- [Empire](https://github.com/BC-SECURITY/Empire) — post-exploitation framework (PowerShell/Python/C#)
- [Chisel](https://github.com/jpillora/chisel) — fast TCP/UDP tunnel over HTTP
- [Ligolo-ng](https://github.com/nicocha30/ligolo-ng) — tunneling/pivoting tool
- [LinPEAS / WinPEAS](https://github.com/peass-ng/PEASS-ng) — automated local privesc enumeration scripts

## Privilege Escalation

- [GTFOBins](https://gtfobins.github.io/) — Unix binaries usable to bypass local restrictions
- [LOLBAS](https://lolbas-project.github.io/) — Living Off the Land Binaries and Scripts (Windows)
- [PEASS-ng (LinPEAS/WinPEAS)](https://github.com/peass-ng/PEASS-ng) — automated privesc checks
- [linux-exploit-suggester](https://github.com/mzet-/linux-exploit-suggester) — kernel exploit suggestion

## Wireless

- [Aircrack-ng](https://www.aircrack-ng.org/) — WiFi security auditing suite
- [Kismet](https://www.kismetwireless.net/) — wireless network detector/sniffer/IDS
- [Wifite](https://github.com/derv82/wifite2) — automated wireless attack tool
- [Bettercap](https://github.com/bettercap/bettercap) — network attacks, MITM, wireless/BLE recon

## Network & Traffic Analysis

- [Wireshark](https://www.wireshark.org/) — packet capture and analysis
- [tcpdump](https://www.tcpdump.org/) — command-line packet capture
- [Responder](https://github.com/lgandx/Responder) — LLMNR/NBT-NS/mDNS poisoner
- [mitmproxy](https://mitmproxy.org/) — interactive HTTPS proxy

## Mobile

- [MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF) — automated static + dynamic mobile app (Android/iOS/Windows) vulnerability scanner, the standard starting point
- [Frida](https://frida.re/) — dynamic instrumentation toolkit (hook methods, bypass checks at runtime, cross-platform)
- [objection](https://github.com/sensepost/objection) — runtime mobile exploration built on Frida; no jailbreak/root required
- [apktool](https://github.com/iBotPeaches/Apktool) — Android APK decompilation/rebuilding (smali, resources)
- [jadx](https://github.com/skylot/jadx) — Android APK/DEX-to-Java decompiler with a GUI, best for reading app logic
- [Drozer](https://github.com/WithSecureLabs/drozer) — Android attack surface assessment (exported components, content providers, IPC)
- [QARK](https://github.com/linkedin/qark) — static analysis for Android source/APKs, flags common vuln patterns
- [Needle](https://github.com/mwrlabs/needle) — iOS security testing framework (binary analysis, storage, IPC, on a jailbroken device)
- [class-dump](https://github.com/nygard/class-dump) / [Hopper](https://www.hopperapp.com/) — iOS Objective-C header/binary reverse engineering
- [Charles Proxy](https://www.charlesproxy.com/) — HTTP(S) traffic interception, alternative to Burp/mitmproxy for mobile testing
- [OWASP MASTG](https://mas.owasp.org/MASTG/) — Mobile Application Security Testing Guide (the methodology reference for everything above)
- [OWASP MASVS](https://mas.owasp.org/MASVS/) — Mobile Application Security Verification Standard (requirements checklist)

Quick-reference commands: [`cheatsheets/mobile.md`](cheatsheets/mobile.md).

## Cloud

- [ScoutSuite](https://github.com/nccgroup/ScoutSuite) — multi-cloud security auditing (AWS/Azure/GCP)
- [Prowler](https://github.com/prowler-cloud/prowler) — AWS/Azure/GCP/K8s security assessment
- [Pacu](https://github.com/RhinoSecurityLabs/pacu) — AWS exploitation framework
- [ROADtools](https://github.com/dirkjanm/ROADtools) — Azure AD/Entra ID recon framework

## Forensics & Reverse Engineering

- [Ghidra](https://github.com/NationalSecurityAgency/ghidra) — software reverse engineering suite (NSA)
- [radare2](https://github.com/radareorg/radare2) / [Cutter](https://cutter.re/) — reverse engineering framework and GUI
- [x64dbg](https://x64dbg.com/) — Windows debugger
- [Volatility 3](https://github.com/volatilityfoundation/volatility3) — memory forensics
- [Autopsy](https://www.autopsy.com/) / [The Sleuth Kit](https://www.sleuthkit.org/) — digital forensics platform and underlying disk-analysis toolset
- [FTK Imager](https://www.exterro.com/digital-forensics-software/ftk-imager) — disk/memory imaging (free)
- [KAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kroll-artifact-parser-extractor-kape) — fast triage artifact collection and processing
- [Eric Zimmerman's Tools](https://ericzimmerman.github.io/) — MFTECmd, RegistryExplorer, EvtxECmd, and other Windows artifact parsers
- [RegRipper](https://github.com/keydet89/RegRipper3.0) — Windows registry parsing/analysis
- [Plaso / log2timeline](https://github.com/log2timeline/plaso) — super-timeline creation from forensic artifacts
- [YARA](https://github.com/VirusTotal/yara) — pattern matching for malware/artifact identification
- [NetworkMiner](https://www.netresec.com/?page=NetworkMiner) — network forensic analysis from pcaps
- [dc3dd](https://sourceforge.net/projects/dc3dd/) / [Guymager](https://guymager.sourceforge.io/) — forensic disk imaging with hashing

Quick-reference commands: [`cheatsheets/forensics.md`](cheatsheets/forensics.md).

## Reporting

- Templates and phrasing live in [`notes/reporting/`](notes/reporting/) as they're built out.
- [PTES Reporting guidelines](http://www.pentest-standard.org/index.php/Reporting) — structure/content reference
- [Pwndoc](https://github.com/pwndoc/pwndoc) / [Sysreptor](https://github.com/Syslifters/sysreptor) — open-source pentest report generation platforms

## Distros & Environments

- [Kali Linux](https://www.kali.org/) — Debian-based pentest distro, tools preinstalled
- [Parrot Security OS](https://www.parrotsec.org/) — alternative pentest/forensics distro
- [Flare-VM](https://github.com/mandiant/flare-vm) — Windows-based malware analysis/RE environment
- [commando-vm](https://github.com/mandiant/commando-vm) — Windows-based pentest environment

## Methodology & Frameworks

- [MITRE ATT&CK](https://attack.mitre.org/) — adversary tactics/techniques knowledge base
- [PTES (Penetration Testing Execution Standard)](http://www.pentest-standard.org/) — end-to-end testing methodology
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/) — web app testing methodology
- [OSSTMM](https://www.isecom.org/OSSTMM.3.pdf) — Open Source Security Testing Methodology Manual
- [NIST SP 800-115](https://csrc.nist.gov/pubs/sp/800/115/final) — technical guide to information security testing

## Learning Platforms & Practice

- [Hack The Box](https://www.hackthebox.com/) — pentest labs and CTF-style machines
- [TryHackMe](https://tryhackme.com/) — guided, beginner-friendly security learning paths
- [PentesterLab](https://pentesterlab.com/) — hands-on web/exploit exercises
- [PortSwigger Web Security Academy](https://portswigger.net/web-security) — free web app security labs
- [OverTheWire](https://overthewire.org/wargames/) — wargame-style Linux/security challenges
- [VulnHub](https://www.vulnhub.com/) — downloadable vulnerable VMs

## Certifications

- [OSCP](https://www.offsec.com/courses/pen-200/) — Offensive Security Certified Professional
- [CRTO](https://www.zeropointsecurity.co.uk/courses/red-team-ops) — Certified Red Team Operator (Zero-Point Security)
- [eJPT / eCPPT](https://elearnsecurity.com/) — INE/eLearnSecurity certifications
- [CEH](https://www.eccouncil.org/train-certify/certified-ethical-hacker-ceh/) — Certified Ethical Hacker (EC-Council)
- [OSWE / OSEP / OSED](https://www.offsec.com/courses/) — advanced Offensive Security certifications

## Certification Modules

Standalone study modules — domain breakdowns, exam format, and resources — kept separate from the pentest/red-team material above since they're a different kind of prep:

- [CISSP](cissp/README.md) — Certified Information Systems Security Professional (ISC2), management-level security certification
- [CISA](cisa/README.md) — Certified Information Systems Auditor (ISACA), IS/IT audit and assurance certification

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Short version: add tools/resources under the right category, keep entries to one line with a link, and don't link anything that isn't a legitimate, maintained project.

## License

[MIT](LICENSE) for the content of this repo (notes, cheat sheets, structure). Linked third-party tools carry their own licenses.
