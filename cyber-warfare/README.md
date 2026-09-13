# Cyber Warfare

State and state-affiliated conflict conducted through cyberspace: doctrine, law, threat actors, and the frameworks used to analyze it. This module is reference/analytical material — legal frameworks, publicly attributed threat actor profiles, and documented historical incidents — not offensive tooling. For hands-on ICS/SCADA assessment tooling, see the section near the bottom of this file.

## Scope: what counts as "cyber warfare"

The term gets used loosely; the distinctions matter because they carry different legal, doctrinal, and response implications:

- **Cyber warfare** — cyber operations conducted by or attributable to a state, in connection with or as a substitute for armed conflict, intended to cause damage, disruption, or coercive effect against another state.
- **Cyber espionage** — state-sponsored intelligence collection (data theft) without an intent to damage or disrupt. Legally and normatively treated very differently from warfare-level operations, even when the same threat actor group conducts both.
- **Cybercrime** — financially motivated activity, typically non-state, though increasingly used *by* states for plausible deniability (see Hybrid/gray-zone activity below).
- **Hacktivism** — ideologically motivated, non-state (or loosely state-tolerated) activity; sits ambiguously alongside state operations when a government tacitly permits or encourages "patriotic hacker" activity against a foreign target.
- **Hybrid / gray-zone warfare** — cyber operations combined with information warfare, economic pressure, and deniable proxy action, deliberately kept below the threshold that would trigger a conventional or collective-defense military response. Increasingly the default mode of state cyber conflict — see the 2026 trend note below.
- **Information warfare / influence operations** — manipulating the information environment itself (disinformation, coordinated inauthentic behavior, election interference) rather than compromising systems. A distinct discipline from network intrusion, but frequently run by the same state apparatus and often paired with it (e.g., hack-and-leak operations).

## Legal and doctrinal frameworks

- **[Tallinn Manual 2.0](https://ccdcoe.org/research/tallinn-manual/)** — the most authoritative (though non-binding) academic analysis of how existing international law applies to cyber operations, produced under NATO CCDCOE auspices. Covers both the law governing resort to cyber force (*jus ad bellum*) and the law governing conduct during cyber operations in armed conflict (*jus in bello*).
- **UN Charter Article 2(4) / Article 51** — the baseline question in *jus ad bellum* analysis: does a given cyber operation rise to the level of a "use of force" or an "armed attack" (triggering a state's right to self-defense)? Most cyber operations to date have been deliberately calibrated to stay below this threshold.
- **Law of Armed Conflict (LOAC) / International Humanitarian Law (IHL)** — once an armed conflict exists, cyber operations conducted as part of it are still bound by distinction (combatants/civilians), proportionality, and precaution — e.g., a cyberattack on a power grid supplying both military and civilian/hospital loads raises the same proportionality analysis as a kinetic strike would.
- **NATO Article 5 and cyberspace** — NATO declared in 2014 that a cyberattack could trigger collective defense under Article 5, and in 2016 recognized cyberspace as an operational domain alongside land, sea, air, and space.
- **UN GGE and OEWG norms** — the UN Group of Governmental Experts and Open-Ended Working Group processes have produced (non-binding, contested) norms of responsible state behavior in cyberspace, including that states should not knowingly allow their territory to be used for internationally wrongful cyber acts, and should not target the other side's critical infrastructure or CERTs/CSIRTs even during peacetime tension.
- **Attribution as a policy act, not just a technical one** — public attribution of a state-sponsored campaign (naming a government, not just a group) is a diplomatic/legal decision made above the technical analysts, typically requiring a confidence threshold and often coordinated multilaterally (e.g., joint advisories co-signed by multiple national CERTs). Treat vendor/government attribution claims as assessed judgments with stated confidence levels, not mathematical proof.

## Threat actor taxonomy

Different organizations name the same threat actor differently — there is no single naming authority. Common conventions:

- **Mandiant/Google**: `APT` + number (APT28, APT29, APT41)
- **CrowdStrike**: animal + adjective, animal indicates nation (BEAR = Russia, PANDA = China, CHOLLIMA = North Korea, KITTEN = Iran) — e.g., Fancy Bear, Cozy Bear
- **Microsoft** (post-2023 weather-themed scheme): weather phenomenon + nation-indicating adjective (Typhoon = China, Blizzard = Russia, Sleet = North Korea, Sandstorm = Iran) — e.g., Volt Typhoon, Midnight Blizzard
- Older/still-used codenames: Sandworm, Lazarus Group, OilRig, APT groups are frequently rebranded or merged as research evolves — treat any single name as a snapshot, not a permanent identity.

Selected, publicly attributed groups frequently referenced in reporting (attribution as stated by the cited government/vendor sources — always confirm current attribution against primary reporting before relying on it in engagement material):

| Group (common names) | Publicly attributed to | Notable activity |
|---|---|---|
| APT28 / Fancy Bear / Forest Blizzard | Russia, GRU (military intelligence) | DNC 2016 hack-and-leak, targeting of political/military organizations across NATO members |
| APT29 / Cozy Bear / Midnight Blizzard | Russia, SVR (foreign intelligence) | SolarWinds supply-chain compromise (2020), long-running espionage against government/think-tank targets |
| Sandworm / Seashell Blizzard | Russia, GRU Unit 74455 | Ukraine power grid attacks (2015 BlackEnergy, 2016 Industroyer), NotPetya (2017), Olympic Destroyer |
| Volt Typhoon | China, per joint CISA/NSA/FBI/international-partner advisory (2024) | Living-off-the-land pre-positioning inside US critical infrastructure (water, energy, transportation) — see case study below |
| APT41 | China, per Mandiant/DOJ reporting (indictments issued) | Dual-use group conducting both state espionage and financially motivated intrusions |
| Lazarus Group / APT38 | North Korea, per US Treasury/FBI designations | Sony Pictures (2014), WannaCry (2017), extensive cryptocurrency theft funding state programs |
| APT33 / APT34 (OilRig) | Iran, per Mandiant/industry reporting | Targeting of energy sector and regional government targets |

## Critical infrastructure as a target class

- CISA defines **16 critical infrastructure sectors** in the US (energy, water/wastewater, financial services, healthcare, transportation, communications, and others) — each has a designated Sector Risk Management Agency. Most national frameworks use a similar sector taxonomy.
- **Pre-positioning** — establishing and maintaining stealthy, long-term access inside critical infrastructure networks well before any decision to cause disruption, so that disruptive capability exists on demand during a future crisis. This is the defining feature of the Volt Typhoon campaign (see case studies) and a major 2025–2026 industry concern: analysts have described the risk of adversaries who have spent years pre-positioning inside infrastructure activating that access simultaneously during a future geopolitical crisis.
- **Living off the land (LOTL)** — using legitimate, built-in system administration tools (PowerShell, WMI, native OS binaries) rather than custom malware, specifically to blend in with normal administrator activity and evade signature-based detection — the technique that made Volt Typhoon unusually hard to detect via traditional means.

## Frameworks and analytical models

- **[MITRE ATT&CK](https://attack.mitre.org/)** (Enterprise) and **[MITRE ATT&CK for ICS](https://attack.mitre.org/matrices/ics/)** — the standard taxonomy for describing adversary tactics/techniques; the ICS matrix specifically covers techniques against industrial control systems (distinct tactics like "Impair Process Control" and "Impact" that don't map to enterprise IT).
- **Cyber Kill Chain** (Lockheed Martin) — Reconnaissance → Weaponization → Delivery → Exploitation → Installation → Command & Control → Actions on Objectives. Widely used but criticized as too linear for modern, non-malware-based (LOTL) intrusions.
- **Diamond Model of Intrusion Analysis** — models an intrusion event as four core features (Adversary, Capability, Infrastructure, Victim) and their relationships, useful for pivoting analysis and campaign clustering.
- **Unified Kill Chain** — a more recent synthesis combining the Cyber Kill Chain and MITRE ATT&CK into 18 phases across In/Through/Out network stages, addressing the linear kill chain's gaps.
- **NIST Cybersecurity Framework (CSF)** and **ISA/IEC 62443** — the primary defensive/resilience frameworks for general enterprise (NIST CSF) and industrial control systems specifically (IEC 62443, covering security levels, zones and conduits for OT network segmentation).

## Case studies

Full write-ups (target, technique, attribution, and doctrinal significance) for the incidents that most shaped how cyber warfare is understood and governed: [`case-studies.md`](case-studies.md) — covers Estonia 2007, Georgia 2008, Stuxnet, the 2015/2016 Ukraine grid attacks, NotPetya, the Viasat KA-SAT hack, SolarWinds, and Volt Typhoon.

## ICS/SCADA & critical infrastructure security tooling

Defensive/assessment tooling relevant to the OT (operational technology) environments most often targeted in cyber warfare scenarios:

- **[GRASSMARLIN](https://github.com/nsacyber/GRASSMARLIN)** (NSA, open-sourced) — passive network mapping tool purpose-built for ICS/SCADA environments, avoids active scanning that can disrupt fragile OT devices.
- **Wireshark with ICS protocol dissectors** — Modbus, DNP3, S7comm, EtherNet/IP dissectors for analyzing OT network traffic; see [`../cheatsheets/`](../cheatsheets/) for general Wireshark usage.
- **[Conpot](https://github.com/Cymmetria/conpot)** — an ICS/SCADA honeypot for research and detection tuning.
- **[OpenPLC](https://www.openplcproject.com/)** — open-source PLC runtime, useful for building a safe lab environment to study ICS protocols without touching real infrastructure.
- **Shodan / Censys** (see the main [recon tools](../README.md#recon--osint)) — routinely used to identify internet-exposed ICS/SCADA devices; also routinely used by adversaries for the same purpose, which is itself a standard finding in critical-infrastructure risk assessments.
- **NIST SP 800-82** — Guide to Operational Technology (OT) Security, the standard reference for ICS-specific security controls.

## Policy and doctrine bodies

- **[NATO CCDCOE](https://ccdcoe.org/)** (Cooperative Cyber Defence Centre of Excellence, Tallinn) — publisher of the Tallinn Manual, runs the annual Locked Shields exercise (the largest live-fire cyber defense exercise globally).
- **UN Office for Disarmament Affairs** — home of the GGE/OEWG norms processes referenced above.
- **CISA** ([cisa.gov](https://www.cisa.gov/)) — publishes joint advisories (often co-signed with NSA, FBI, and international partner agencies) that are the primary public-attribution mechanism for US-relevant state-sponsored activity.
- Policy/research bodies frequently cited in this space: [CSIS](https://www.csis.org/programs/strategic-technologies-program) (Strategic Technologies Program), [Atlantic Council's DFRLab](https://www.atlanticcouncil.org/programs/digital-forensic-research-lab/), and [RAND](https://www.rand.org/topics/cyber-warfare.html).

## Learning resources

- **Books**: *Sandworm* (Andy Greenberg) — the definitive account of the Sandworm/GRU campaigns including NotPetya; *This Is How They Tell Me the World Ends* (Nicole Perlroth) — the zero-day market and state cyber-weapon development; *Cyber War* (Richard A. Clarke) — an early, foundational (if now dated in specifics) doctrinal treatment; the Tallinn Manual 2.0 itself for the legal framework.
- **Courses/certifications**: SANS ICS curriculum — [ICS410/GICSP](https://www.sans.org/cyber-security-courses/ics-scada-cyber-security-essentials/) (ICS/SCADA security essentials) and [ICS515/GRID](https://www.sans.org/cyber-security-courses/ics-active-defense-incident-response/) (ICS active defense and incident response) are the standard entry points for OT-focused security work; NATO CCDCOE offers cyber defense courses and hosts Locked Shields.
- **Ongoing reporting**: CISA cybersecurity advisories, Mandiant/Google Threat Intelligence group reporting, Microsoft Threat Intelligence blog, and the annual reporting from national CERTs are the primary sources for current, evolving attribution — treat any specific attribution claim in this module as a snapshot and verify against current primary reporting before relying on it.

## Notes

Track your own analysis, engagement-relevant threat actor tracking, or exercise write-ups in [`notes/cyber-warfare/`](../notes/cyber-warfare/).
