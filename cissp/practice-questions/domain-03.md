# Domain 3 Practice Questions: Security Architecture and Engineering

Original questions written for self-study, aligned to the domain outline in [`../domains/03-security-architecture-and-engineering.md`](../domains/03-security-architecture-and-engineering.md). Not sourced from any official exam.

---

**1.** A security model enforces "no read up, no write down" to protect confidentiality in a military classification system. This describes:

A) Biba
B) Bell-LaPadula
C) Clark-Wilson
D) Brewer-Nash

<details><summary>Answer</summary>

**B.** Bell-LaPadula is confidentiality-focused: the Simple Security Property prevents reading data at a higher classification ("no read up"), and the *-Property prevents writing data down to a lower classification ("no write down").
</details>

---

**2.** Which model is designed to prevent conflicts of interest by dynamically restricting a consultant's access to a competitor's data once they've accessed one client's data?

A) Biba
B) Graham-Denning
C) Brewer-Nash (Chinese Wall)
D) Take-Grant

<details><summary>Answer</summary>

**C.** The Brewer-Nash model dynamically changes access permissions based on a subject's prior access, specifically to prevent conflicts of interest between competing clients.
</details>

---

**3.** In a Common Criteria evaluation, which document defines the security requirements a class of products must meet, independent of any specific vendor implementation?

A) Security Target (ST)
B) Protection Profile (PP)
C) Evaluation Assurance Level (EAL)
D) Accreditation package

<details><summary>Answer</summary>

**B.** A Protection Profile defines implementation-independent security requirements for a category of product. A Security Target is a specific vendor's claims about how their specific product meets requirements.
</details>

---

**4.** A system has received a certification confirming it technically meets defined security requirements. Before it can be placed into production, management must formally accept the residual risk and authorize its use. This authorization step is called:

A) Certification
B) Accreditation
C) Validation
D) Verification

<details><summary>Answer</summary>

**B.** Accreditation is management's formal acceptance of risk and authorization to operate a system — distinct from certification, which is the technical evaluation confirming the system meets requirements.
</details>

---

**5.** Which cryptographic approach is used by TLS to combine the key-distribution advantage of asymmetric cryptography with the performance advantage of symmetric cryptography?

A) Steganography
B) Hybrid cryptosystem
C) Hashing
D) Homomorphic encryption

<details><summary>Answer</summary>

**B.** A hybrid cryptosystem uses asymmetric cryptography to securely exchange a symmetric session key, then uses that symmetric key for fast bulk encryption of the actual data — exactly how TLS operates.
</details>

---

**6.** A digital signature is created by:

A) Encrypting the entire message with the recipient's public key
B) Hashing the message and encrypting the hash with the sender's private key
C) Hashing the message and encrypting the hash with the recipient's public key
D) Encrypting the message with a shared symmetric key

<details><summary>Answer</summary>

**B.** The sender hashes the message, then encrypts the hash with their own PRIVATE key. The recipient decrypts it with the sender's PUBLIC key and compares it to their own hash of the received message — this proves integrity, authenticity, and non-repudiation.
</details>

---

**7.** Which access control model is enforced by a hardware chip that securely stores cryptographic keys and supports measured/attested boot?

A) HSM only
B) TPM (Trusted Platform Module)
C) DLP
D) SIEM

<details><summary>Answer</summary>

**B.** A TPM is a hardware chip (often on the motherboard) used for secure key storage and boot integrity measurement/attestation. An HSM performs a similar function but is typically a dedicated, higher-throughput external/network device for enterprise key management.
</details>

---

**8.** A database technique that stores multiple rows with the same primary key but different classification levels, specifically to prevent lower-cleared users from inferring the existence of higher-classified data, is called:

A) Aggregation
B) Inference
C) Polyinstantiation
D) Normalization

<details><summary>Answer</summary>

**C.** Polyinstantiation deliberately creates multiple versions of a record at different classification levels so that a lower-cleared user sees a plausible (but different) value rather than detecting that a hidden, higher-classified record exists.
</details>

---

**9.** Which fire suppression agent is preferred in a data center equipment room specifically because it does not damage electronic equipment, unlike water-based sprinkler systems?

A) Water mist
B) Clean agent (e.g., FM-200/Novec)
C) Foam
D) CO2 only, with no other consideration

<details><summary>Answer</summary>

**B.** Clean agents extinguish fire without leaving residue or requiring water, avoiding damage to servers/electronics — the standard choice for data center suppression systems.
</details>

---

**10.** An attacker measures the time a system takes to perform a cryptographic operation to infer information about the secret key being used. This is an example of:

A) A brute-force attack
B) A side-channel attack
C) A chosen-plaintext attack
D) A birthday attack

<details><summary>Answer</summary>

**B.** A side-channel attack exploits information leaked through the physical implementation of a system (timing, power consumption, electromagnetic emissions) rather than attacking the cryptographic algorithm mathematically.
</details>

---

[← Back to CISSP module](../README.md)
