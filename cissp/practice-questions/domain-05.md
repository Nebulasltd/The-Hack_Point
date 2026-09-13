# Domain 5 Practice Questions: Identity and Access Management (IAM)

Original questions written for self-study, aligned to the domain outline in [`../domains/05-identity-and-access-management.md`](../domains/05-identity-and-access-management.md). Not sourced from any official exam.

---

**1.** A user logs in with a password and then a PIN they've memorized for a second application. Does this constitute multi-factor authentication?

A) Yes, because two credentials were required
B) No, because both factors are "something you know" — MFA requires factors from different categories
C) Yes, as long as the PIN is at least 6 digits
D) No, because PINs are never a valid authentication factor

<details><summary>Answer</summary>

**B.** MFA requires factors from at least two different categories (something you know, have, are). Two "something you know" factors — even if they're different credentials — do not constitute MFA.
</details>

---

**2.** In Kerberos authentication, which component issues the initial Ticket Granting Ticket (TGT) after a user successfully authenticates?

A) The Ticket Granting Service (TGS)
B) The Authentication Service (AS)
C) The Key Distribution Center's database directly, bypassing the AS
D) The Service Provider

<details><summary>Answer</summary>

**B.** The Authentication Service (AS), a component of the KDC, verifies the user's initial credentials and issues the TGT. The TGT is then presented to the TGS to obtain service tickets for specific resources.
</details>

---

**3.** Which access control model assigns permissions dynamically based on a combination of subject, resource, and environmental attributes, such as department, data sensitivity, and time of day?

A) DAC
B) MAC
C) RBAC
D) ABAC

<details><summary>Answer</summary>

**D.** ABAC (Attribute-Based Access Control) evaluates multiple attributes dynamically at access time, making it the most granular and flexible model — commonly used in Zero Trust architectures.
</details>

---

**4.** OAuth 2.0 is best described as:

A) An authentication protocol that verifies user identity
B) An authorization framework that grants scoped access tokens to applications
C) A symmetric encryption standard
D) A federated identity protocol equivalent to SAML in every respect

<details><summary>Answer</summary>

**B.** OAuth 2.0 is an authorization framework — it grants a token scoped to specific permissions (e.g., "read your calendar") but does not, by itself, authenticate the user's identity to the requesting application. OpenID Connect adds that authentication layer on top of OAuth.
</details>

---

**5.** A former employee's accounts remain active for three weeks after their last day due to a delayed offboarding process. This is primarily a failure of:

A) Provisioning
B) Deprovisioning
C) Access review/recertification
D) Federation

<details><summary>Answer</summary>

**B.** Deprovisioning is the timely removal of access when a user leaves or no longer needs it. A delay here is one of the most common real-world audit findings and a direct security risk.
</details>

---

**6.** A biometric system is tuned so that it never lets an unauthorized person through, at the cost of frequently rejecting legitimate users. This system has been tuned to minimize:

A) FRR (False Rejection Rate)
B) FAR (False Acceptance Rate)
C) CER (Crossover Error Rate)
D) Both FAR and FRR equally

<details><summary>Answer</summary>

**B.** Minimizing FAR (never wrongly accepting an impostor) as the priority typically increases FRR (more legitimate users get wrongly rejected) — the two generally trade off against each other; CER is the point where they're equal.
</details>

---

**7.** An organization allows users to log in once and then access several unrelated SaaS applications without re-authenticating, via a trust relationship where the applications rely on the organization's identity provider. This is an example of:

A) MAC
B) Federated identity / SSO
C) Rule-based access control
D) Kerberos exclusively

<details><summary>Answer</summary>

**B.** This describes federated identity with single sign-on — a trust relationship across organizational boundaries where a single authentication event grants access to multiple, independently operated services.
</details>

---

**8.** Compared to RADIUS, which statement about TACACS+ is accurate?

A) TACACS+ encrypts only the password field, like RADIUS
B) TACACS+ encrypts the entire packet body and separates authentication, authorization, and accounting more granularly
C) TACACS+ is a federation protocol, unlike RADIUS
D) TACACS+ cannot be used for network device administration

<details><summary>Answer</summary>

**B.** TACACS+ encrypts the full packet payload (RADIUS encrypts only the password) and provides more granular separation of the AAA functions — commonly preferred for administrative access to network devices.
</details>

---

**9.** A user who moved from the Finance department to Marketing two years ago still retains access to Finance systems they no longer need. This is an example of:

A) Least privilege being correctly enforced
B) Privilege creep
C) Federated identity
D) Just-in-time access

<details><summary>Answer</summary>

**B.** Privilege creep is the gradual, unaddressed accumulation of access rights as a user changes roles over time without old, no-longer-needed access being revoked. Periodic access review/recertification is the control that catches this.
</details>

---

**10.** Which access control model is enforced by the operating system based on classification labels, and cannot be overridden at the discretion of the resource's owner?

A) DAC
B) MAC
C) RBAC
D) ABAC

<details><summary>Answer</summary>

**B.** MAC (Mandatory Access Control) is enforced system-wide based on labels/clearances (implementing models like Bell-LaPadula), and the resource owner cannot override it — unlike DAC, where the owner decides access.
</details>

---

[← Back to CISSP module](../README.md)
