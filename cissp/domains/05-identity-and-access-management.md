# Domain 5: Identity and Access Management — IAM (13%)

Controlling who/what can access which resources, and how that's proven and managed over time.

## 5.1 Physical and logical access to assets

- Access control applies to both worlds: badges/locks/mantraps (physical) and accounts/permissions/ACLs (logical) — same underlying principles (least privilege, need-to-know).

## 5.2 Identification, authentication, authorization, accountability

- **Identification** — claiming an identity (e.g., typing a username). Not yet verified.
- **Authentication** — proving the claimed identity via one or more **factors**:
  - Type 1: **Something you know** (password, PIN).
  - Type 2: **Something you have** (token, smart card, phone/OTP app).
  - Type 3: **Something you are** (biometrics — fingerprint, iris, facial).
  - Additional/contextual factors sometimes cited: **somewhere you are** (geolocation), **something you do** (behavioral biometrics).
- **Multi-factor authentication (MFA)** requires factors from *different* categories — two passwords is NOT MFA, it's just two Type-1 factors.
- **Authorization** — determining what an authenticated identity is permitted to do.
- **Accountability** — tying actions back to an identity via logging/audit trails; depends on strong authentication + non-repudiation.
- **Biometric metrics**: **FAR** (False Acceptance Rate — wrongly accepts an imposter), **FRR** (False Rejection Rate — wrongly rejects a legitimate user), **CER/EER** (Crossover/Equal Error Rate — the point where FAR = FRR, lower CER = better system).

## 5.3 Identity as a Service (IDaaS) and federation

- **Single Sign-On (SSO)** — authenticate once, access multiple systems. Reduces password fatigue but creates a single point of compromise.
- **Federated identity** — trust relationship across organizational boundaries; a user authenticates with their home organization (Identity Provider) to access a partner's resources (Service Provider).
- **SAML (Security Assertion Markup Language)** — XML-based, common for enterprise/web SSO federation.
- **OAuth 2.0** — authorization framework (grants a token scoped to specific permissions, e.g., "this app can read your calendar") — NOT an authentication protocol by itself.
- **OpenID Connect (OIDC)** — an authentication layer built on top of OAuth 2.0 (adds the identity/ID token OAuth lacks).
- **Kerberos** — ticket-based authentication for internal/enterprise networks. Uses a **KDC (Key Distribution Center)** with an **AS (Authentication Service)** and **TGS (Ticket Granting Service)**; issues a **TGT (Ticket Granting Ticket)**, then service tickets. Vulnerable to clock-skew issues and "Golden Ticket"/"Silver Ticket" attacks if the KDC or service account is compromised.
- **RADIUS/TACACS+** — centralized AAA for network device/remote access authentication; TACACS+ separates authentication, authorization, and accounting (more granular) and encrypts the full packet (RADIUS only encrypts the password).

## 5.4 Authorization mechanisms / access control models

- **DAC (Discretionary Access Control)** — the resource owner decides who gets access (e.g., Windows NTFS permissions, Unix file permissions). Flexible but harder to enforce consistency.
- **MAC (Mandatory Access Control)** — access decided by system-enforced labels/clearances, not the owner (e.g., SELinux, government classification systems) — implements Bell-LaPadula/Biba.
- **RBAC (Role-Based Access Control)** — permissions assigned to roles, users assigned to roles — scales well in enterprises with defined job functions.
- **ABAC (Attribute-Based Access Control)** — access decided dynamically based on attributes of subject, object, and environment (e.g., "allow if department=Finance AND time=business hours AND device=managed") — most flexible/granular, used in Zero Trust architectures.
- **Rule-Based Access Control** — access governed by explicit if/then rules (e.g., firewall ACLs) — not the same as RBAC despite the similar acronym.

## 5.5 Identity and access provisioning lifecycle

- **Provisioning** — creating accounts/granting access when a user joins or changes roles.
- **Access review / recertification** — periodic manager/owner review confirming access is still appropriate (catches privilege creep).
- **Deprovisioning** — timely removal of access when a user leaves or no longer needs it — a top real-world audit finding when delayed.
- **Privilege creep** — accumulation of unnecessary access over time as a user changes roles without old access being revoked.
- **Just-in-time (JIT) access / privileged access management (PAM)** — grants elevated access only for the duration needed, with approval workflows and session recording (e.g., CyberArk, BeyondTrust).

## Key exam tips

- MFA requires factors from different categories — a very commonly tested trap.
- Know Kerberos terminology (KDC, TGT, AS, TGS) — it comes up often, including in the context of attacks (pass-the-ticket, Golden Ticket).
- OAuth authorizes; OIDC authenticates. Don't say "OAuth is used for authentication" on the exam.
- ABAC is the most granular/dynamic model; RBAC is the most common in mid-size enterprises; MAC is the most rigid (used where confidentiality is paramount, e.g., military).
