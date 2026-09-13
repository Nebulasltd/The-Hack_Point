# Domain 2: Asset Security (10%)

Information/data lifecycle and protection — classification, ownership, handling, and retention.

## 2.1 Identify and classify information and assets

- **Classification** ranks data by sensitivity (e.g., government: Top Secret / Secret / Confidential / Unclassified; commercial: Confidential / Private / Sensitive / Public).
- Classification drives control selection — higher classification means stronger controls (encryption strength, access restrictions, handling procedures).
- **Asset inventory** is a prerequisite — you can't protect what you don't know you have. Includes hardware, software, data, and (often overlooked) documentation.
- **Declassification** — formal downgrade of classification when sensitivity no longer applies (still needs a documented process).

## 2.2 Roles

- **Data/information owner** — senior role (often an executive) accountable for the asset; decides classification, who can access it, and approves protection requirements. Ultimately liable.
- **Data custodian** — technical role that implements the controls the owner specifies (backups, access provisioning, patching).
- **Data controller** (privacy/GDPR term) — determines the purposes and means of processing personal data.
- **Data processor** — processes personal data on behalf of the controller.
- **System owner** — responsible for the system/platform the data lives on.
- **User/subject** — the individual whose data is processed (data subject) or who uses the system (end user).
- **Business/mission owner** — ensures the asset supports business objectives.

## 2.3 Data protection methods

- **Data at rest** — encryption (full-disk, file-level, database TDE), access controls, physical security.
- **Data in transit** — TLS, IPsec, VPNs.
- **Data in use** — memory protection, secure enclaves, homomorphic encryption (emerging), screen locks, clean-desk policy.
- **Data Loss Prevention (DLP)** — network, endpoint, and storage DLP to detect/block unauthorized exfiltration based on content inspection or classification labels.
- **Digital Rights Management (DRM)** — controls use/copying/distribution of protected content after it leaves the originating system.
- **Tokenization** vs. **masking** vs. **anonymization** vs. **pseudonymization**:
  - Tokenization — replaces sensitive data with a non-sensitive token, reversible via a lookup table (common for PCI/payment data).
  - Masking — obscures part of the data (e.g., showing only the last 4 digits).
  - Anonymization — irreversibly strips identifying information.
  - Pseudonymization — replaces identifiers with pseudonyms; reversible with additional information kept separately (a GDPR-recognized technique, not full anonymization).

## 2.4 Data states and handling requirements

- **Marking/labeling** — physical or digital labels indicating classification (e.g., header/footer "CONFIDENTIAL", metadata tags).
- **Handling** — how data of a given classification may be transmitted, stored, or discussed (e.g., "Secret" data may require a specific approved courier or encrypted channel).
- **Storage** — appropriate media, encryption at rest, environmental controls for physical media.

## 2.5 Asset retention

- **Retention policy** — defined by legal/regulatory/business requirements; both under-retention (destroying records needed for compliance or litigation) and over-retention (unnecessary liability/cost, larger breach exposure) are risks.
- **Legal hold** — suspends normal retention/destruction schedules when litigation is reasonably anticipated.
- **Media sanitization / secure disposal** (NIST SP 800-88 guidance):
  - **Clear** — logical techniques (e.g., overwrite) protecting against simple recovery via standard tools.
  - **Purge** — physical or logical techniques (e.g., cryptographic erase, degaussing) resistant to laboratory recovery.
  - **Destroy** — physical destruction (shredding, incineration, disintegration) — the only option that guarantees no recovery for some media types (e.g., SSD wear-leveling makes overwrite-based clearing unreliable).

## 2.6 Data security controls and compliance

- **Baselines** — minimum security configuration standards (e.g., CIS Benchmarks), then **scoping/tailoring** to fit the specific environment/asset classification.
- **Standards selection**: match the control framework to the data type and regulatory obligation (PCI DSS for cardholder data, HIPAA Security Rule for ePHI, etc.).

## Key exam tips

- Owner vs. custodian is a favorite distinction — owner decides, custodian implements.
- Know that "destroy" is the only sanitization method appropriate for the highest classification levels and for most flash/SSD media.
- Pseudonymization is reversible (with a separate key/mapping); anonymization is not — GDPR treats these very differently.
