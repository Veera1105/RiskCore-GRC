# Access Control & Identity Management Policy

| Metadata | Details |
| :--- | :--- |
| **Organization** | NexusPay Technologies Inc. |
| **Document ID** | POL-SEC-01 |
| **Version** | 1.0.0 |
| **Classification** | Internal |
| **Owner** | Information Security Department |
| **ISO 27001:2022 Ref** | Controls 5.15, 5.16, 5.17, 5.18, 8.2, 8.5 |

---

## 1. Purpose
This policy defines the technical and operational controls governing access to NexusPay systems, applications, source code, and AWS cloud environments to ensure only authorized identities perform verified operations.

## 2. Scope
Applies to all identity accounts, service roles, machine-to-machine integrations, and administrative access channels across NexusPay.

## 3. Policy Statements

### 3.1 Authentication & Multi-Factor Authentication (MFA)
- **Centralized Identity**: All corporate and production access must be routed through the primary Identity Provider (Okta integrated with Google Workspace).
- **Mandatory MFA**: Multi-Factor Authentication is enforced for 100% of workforce accounts. Supported authenticators are hardware security keys (FIDO2/WebAuthn) or time-based one-time passwords (TOTP). SMS and voice-call authentication are strictly prohibited.
- **Password Standards**: Master passwords for password managers must contain a minimum of 16 characters. System passwords generated for SaaS accounts must be randomized to at least 20 characters.

### 3.2 Authorization & Principle of Least Privilege (PoLP)
- **Default Deny**: All network, database, and repository access is configured to "Deny All" by default.
- **Role-Based Access Control (RBAC)**: Access is mapped directly to job function tiers (e.g., Engineer, Support Lead, Billing Admin).
- **Segregation of Duties (SoD)**:
  - Engineers who write code do not possess write permissions to merge pull requests into the production `main` branch unilaterally.
  - Employees with database read permissions do not have administrative access to change payment routing configurations.

### 3.3 Joiner-Mover-Leaver (JML) Management
- **Joiners**: Provisioning occurs only upon an approved Jira ticket originating from People Operations with hiring manager sign-off.
- **Movers**: Role changes trigger an immediate access review; previous permissions must be stripped within **3 business days**.
- **Leavers**: 
  - Standard departure: Accounts disabled via Okta within **4 hours** of the employee's final working hour.
  - Involuntary termination: Accounts terminated immediately, concurrently with the HR departure conversation.

### 3.4 Privileged Access Management (PAM)
- Direct root/admin account access to AWS production environments or production PostgreSQL databases is disabled.
- Engineers require temporary, logged, time-bound session credentials (AWS IAM Identity Center session or ephemeral SSH via Teleport) tied to an approved Jira change ticket.
- Break-glass emergency admin credentials must be secured in a dual-custody digital safe; any access triggers immediate PagerDuty alerts to the Security Lead (Veera Ranjane).

### 3.5 Quarterly Access Reviews
- The Head of GRC (Veera Ranjane) oversees a mandatory **Quarterly Access Review** covering AWS IAM, GitHub Enterprise, Okta, and Google Workspace.
- System owners must review and electronically certify user access rosters within 10 business days of quarter-end. Inactive accounts (>60 days) are decommissioned.

## 4. Document Revision History
| Version | Date | Author | Description |
| :--- | :--- | :--- | :--- |
| 1.0.0 | 2026-10-24 | Veera Ranjane | Initial production ISMS baseline release |
