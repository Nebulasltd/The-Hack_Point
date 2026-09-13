# Domain 3: Security Architecture and Engineering (13%)

The most technically dense domain: security models, evaluation criteria, cryptography, and physical security design.

## 3.1 Secure design principles

- **Threat modeling** integrated into design (see Domain 1 — STRIDE, attack trees).
- **Least privilege** and **defense in depth** (layered controls — no single point of failure).
- **Separation of duties**, **fail-secure vs. fail-open** (fail-secure denies access on failure — appropriate for a door lock; fail-open permits access on failure — appropriate for a fire-exit door).
- **Zero Trust** — "never trust, always verify"; no implicit trust based on network location; continuous verification, micro-segmentation.
- **Trust but verify** (older model) vs. Zero Trust (current best practice).
- **Privacy by design** — build privacy protections in from the start, not bolted on.
- **Shared responsibility model** (cloud) — provider secures the infrastructure "of" the cloud; customer secures what they put "in" the cloud (varies by IaaS/PaaS/SaaS).

## 3.2 Security models (formal, testable concepts)

- **Bell-LaPadula** — confidentiality-focused (military/government). "No read up, no write down" (Simple Security Property: can't read higher classification; *-Property: can't write to lower classification).
- **Biba** — integrity-focused. "No write up, no read down" (inverse of Bell-LaPadula) — prevents low-integrity data from contaminating high-integrity data.
- **Clark-Wilson** — integrity model using well-formed transactions and separation of duties; enforces access via a validated "access control triple" (subject–program–object).
- **Brewer-Nash (Chinese Wall)** — dynamically changes permissions to prevent conflicts of interest (e.g., a consultant can't access two competing clients' data simultaneously).
- **Graham-Denning** — defines how subjects/objects are securely created, deleted, and how rights are assigned.
- **Take-Grant model** — uses a directed graph to show how rights can be passed between subjects.

## 3.3 Evaluation criteria

- **Common Criteria (ISO/IEC 15408)** — international standard; products get an **EAL (Evaluation Assurance Level)** from EAL1 (functionally tested) to EAL7 (formally verified). A **Protection Profile (PP)** defines requirements; a **Security Target (ST)** is the vendor's claims for a specific product.
- **TCSEC ("Orange Book")** — legacy US DoD standard, divisions D (minimal) through A (verified protection); largely superseded by Common Criteria but still tested conceptually.
- **ITSEC** — legacy European equivalent.
- **Certification** — technical evaluation that a system meets security requirements. **Accreditation** — management's formal acceptance of the risk and authorization to operate (e.g., US federal ATO — Authority to Operate).

## 3.4 Security capabilities of information systems

- **Trusted Platform Module (TPM)** — hardware chip for secure key storage, attestation, measured boot.
- **Hardware Security Module (HSM)** — dedicated hardware for cryptographic key management/operations at scale.
- **Secure boot / measured boot** — verifies firmware/bootloader/OS integrity at each stage.
- **Memory protection**: process isolation, ASLR (Address Space Layout Randomization), DEP/NX (Data Execution Prevention).
- **Virtualization**: hypervisor Type 1 (bare-metal, e.g., ESXi, Hyper-V) vs. Type 2 (hosted, e.g., VirtualBox); VM escape as a key risk.

## 3.5 Vulnerabilities in system types

- **Client-based**: applets, local malware, malicious mobile code.
- **Server-based**: data flow control, large-scale data processing risks.
- **Database security**: aggregation (combining low-sensitivity data to infer high-sensitivity info), inference (deducing restricted info from available data), polyinstantiation (multiple rows with the same key at different classification levels to prevent inference).
- **Cryptographic systems**: implementation flaws, side-channel attacks.
- **Industrial Control Systems (ICS/SCADA)**: legacy protocols, availability-over-confidentiality priority, air-gapping considerations.
- **Cloud-based systems**: multi-tenancy risk, misconfiguration (the leading cause of cloud breaches), API security.
- **IoT**: weak/default credentials, limited patching capability, large attack surface.
- **Mobile systems**: device management (MDM), containerization, jailbreak/root detection.
- **Embedded/real-time systems**: resource constraints, safety-criticality (availability/determinism often outweighs confidentiality).

## 3.6 Cryptography

- **Symmetric encryption** — same key for encrypt/decrypt. Fast, used for bulk data. Examples: **AES** (128/192/256-bit, current standard), 3DES (legacy), ChaCha20.
  - Key distribution is the core challenge (needs a secure channel or asymmetric exchange).
- **Asymmetric encryption** — public/private key pair. Slower, used for key exchange, digital signatures, small data. Examples: **RSA**, **ECC** (Elliptic Curve — smaller keys, similar strength, efficient for constrained devices), Diffie-Hellman (key exchange, not encryption itself).
- **Hybrid cryptosystems** — asymmetric to exchange a symmetric session key, then symmetric for bulk data (how TLS works).
- **Hashing** — one-way function producing a fixed-length digest; verifies integrity, not confidentiality. Examples: SHA-256/SHA-3 (current), MD5/SHA-1 (broken/deprecated — collision attacks known).
- **Digital signatures** — hash the message, encrypt the hash with the sender's private key. Provides integrity, authenticity, and non-repudiation. Verified with the sender's public key.
- **PKI (Public Key Infrastructure)**: CA (Certificate Authority) issues certs, RA (Registration Authority) verifies identity before issuance, CRL/OCSP for revocation checking, certificate chain of trust (root → intermediate → leaf).
- **Key management**: generation, distribution, storage, rotation, escrow, destruction. Key length and algorithm strength must match data sensitivity/lifetime.
- **Cryptanalysis attack types**: ciphertext-only, known-plaintext, chosen-plaintext, chosen-ciphertext, brute-force, side-channel (timing, power analysis), birthday attack (exploits hash collision probability).
- **Steganography** — hiding data within other data (vs. cryptography, which scrambles it) — provides obscurity, not confidentiality.

## 3.7 Site and facility physical security design

- **Crime Prevention Through Environmental Design (CPTED)**: natural surveillance, natural access control, territorial reinforcement (design that discourages crime through the physical environment itself).
- **Layered physical defense**: perimeter (fencing, bollards) → building (locks, mantraps) → floor/room (badge access) → asset (cable locks, safes).
- **Data center design**: redundant power (UPS, generators), HVAC, fire suppression (clean agents like FM-200/Novec for equipment areas — water/sprinklers damage electronics), raised floors, fire detection (smoke/heat sensors).
- **Media/equipment protection**: Faraday cages (EM shielding), TEMPEST (protecting against electromagnetic emanation interception).

## Key exam tips

- Memorize Bell-LaPadula ("no read up, no write down") vs. Biba (the inverse) — this is one of the most consistently tested facts on the exam.
- Know symmetric = fast/bulk/key-distribution-problem; asymmetric = slow/key-exchange & signatures/no distribution problem.
- Hashing ≠ encryption: hashing is one-way and provides integrity only.
