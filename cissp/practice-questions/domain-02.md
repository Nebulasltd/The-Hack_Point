# Domain 2 Practice Questions: Asset Security

Original questions written for self-study, aligned to the domain outline in [`../domains/02-asset-security.md`](../domains/02-asset-security.md). Not sourced from any official exam.

---

**1.** Who is ultimately accountable for deciding the classification level of a dataset and approving who may access it?

A) Data custodian
B) System owner
C) Data owner
D) Data processor

<details><summary>Answer</summary>

**C.** The data owner (typically a senior/executive role) is accountable for classification decisions and access approval. The custodian implements the technical controls the owner specifies.
</details>

---

**2.** A company replaces credit card numbers in its database with randomly generated values, keeping a separate secure lookup table to reverse the process when needed for payment processing. This technique is:

A) Anonymization
B) Masking
C) Tokenization
D) Hashing

<details><summary>Answer</summary>

**C.** Tokenization replaces sensitive data with a non-sensitive token and is reversible via a separate lookup table — commonly used for payment card data (PCI DSS scope reduction).
</details>

---

**3.** Which data sanitization method provides the highest assurance that data cannot be recovered from a solid-state drive (SSD), given that overwrite-based clearing is unreliable on SSDs due to wear leveling?

A) Clear (single-pass overwrite)
B) Degauss
C) Destroy (physical destruction)
D) Formatting the drive

<details><summary>Answer</summary>

**C.** Degaussing doesn't work on SSDs (no magnetic platters), and overwrite-based "clear" is unreliable due to wear leveling redirecting writes away from the original physical cells. Physical destruction is the only method guaranteeing no recovery for SSD media.
</details>

---

**4.** Under GDPR, replacing a data subject's name with a reference code, while keeping the mapping between code and name in a separate, access-restricted file, is best described as:

A) Anonymization
B) Pseudonymization
C) Tokenization
D) Data masking

<details><summary>Answer</summary>

**B.** Pseudonymization replaces identifiers with a pseudonym, remaining reversible with additional (separately held) information — GDPR treats this differently from true anonymization, which is irreversible and takes data outside GDPR's scope entirely.
</details>

---

**5.** Which role determines the purposes and means of processing personal data under GDPR terminology?

A) Data processor
B) Data controller
C) Data custodian
D) Data subject

<details><summary>Answer</summary>

**B.** The data controller determines *why* and *how* personal data is processed. The data processor acts on the controller's behalf/instructions.
</details>

---

**6.** A legal hold has been issued for a set of records that would normally have been destroyed under the organization's retention policy this month. What is the correct action?

A) Proceed with scheduled destruction since policy takes precedence
B) Suspend destruction of the records covered by the hold until it is lifted
C) Destroy the records but retain a summary
D) Transfer the records to a third party for safekeeping

<details><summary>Answer</summary>

**B.** A legal hold suspends normal retention/destruction schedules for records reasonably anticipated to be relevant to litigation, regardless of what the standard retention policy would otherwise require.
</details>

---

**7.** An organization labels documents "Internal Use Only," "Confidential," and "Public" and defines handling rules for each. This activity is primarily:

A) Risk assessment
B) Data classification and marking
C) Access provisioning
D) Threat modeling

<details><summary>Answer</summary>

**B.** Assigning sensitivity levels and applying labels/markings that drive handling requirements is data classification and marking.
</details>

---

**8.** Which of the following is the BEST reason an organization should avoid indefinite data retention, even when storage is inexpensive?

A) It violates the CIA triad
B) It increases breach exposure and potential legal liability for data no longer needed
C) It is always illegal
D) It reduces data integrity over time

<details><summary>Answer</summary>

**B.** Over-retention increases the amount of data exposed in a breach and can create liability for failing to dispose of data per regulatory/contractual requirements — cost of storage isn't the primary concern.
</details>

---

**9.** A security baseline defines the minimum hardening configuration for all servers. When a specific server needs additional or fewer controls due to its unique role, the process of adjusting the baseline to fit is called:

A) Classification
B) Scoping and tailoring
C) Sanitization
D) Provisioning

<details><summary>Answer</summary>

**B.** Scoping determines which baseline elements apply to a given system; tailoring adjusts the baseline's specific controls to fit that system's actual risk/requirements.
</details>

---

**10.** Which of the following best distinguishes a data custodian from a data owner?

A) The custodian decides classification; the owner implements technical controls
B) The custodian implements the technical controls the owner specifies; the owner is accountable for the asset
C) They are interchangeable terms for the same role
D) The custodian is always a third-party vendor

<details><summary>Answer</summary>

**B.** The owner is accountable and makes classification/access decisions; the custodian is the technical role (often IT/security staff) that carries out backups, access provisioning, and protection per the owner's direction.
</details>

---

[← Back to CISSP module](../README.md)
