# Quarterly Access Review Sign-Off Sheet

| Review Metadata | Specification |
| :--- | :--- |
| **Organization** | NexusPay Technologies Inc. |
| **Audit Period** | Q3 2026 (July 1 – September 30, 2026) |
| **System Under Review** | AWS Production & GitHub Enterprise |
| **Reviewer / Owner** | Marcus Chen (VP of Engineering) |
| **Compliance Officer** | Veera Ranjane (Head of Information Security & GRC) |
| **Certification Date** | October 5, 2026 |

---

## 1. Scope of Certification
This review certifies that all active identities, IAM policies, and repository roles assigned in AWS Account (`#8921-1029-4412`) and GitHub Organization (`github.com/nexuspay-io`) follow the Principle of Least Privilege and reflect currently employed personnel.

## 2. Review Findings & Remediation

| Identity / Email | System | Previous Role | Action Taken | Justification |
| :--- | :--- | :--- | :--- | :--- |
| `j.doe@nexuspay.io` | AWS IAM | `PowerUserAccess` | **Revoked** | Employee transitioned to Product team; read-only assigned. |
| `dev-sandbox-key-02` | AWS IAM | Service Account | **Deleted** | Stale API credential inactive for >90 days. |
| `c.smith@nexuspay.io` | GitHub | `Admin` | **Downgraded** | Downgraded to `Triage`; administrative tier no longer required. |

## 3. Formal Sign-Off
I certify that I have conducted an exhaustive review of user access for the systems listed above. All identified orphan, obsolete, or excessive entitlements have been remediated in compliance with the NexusPay Access Control Policy (POL-SEC-01).

- **System Owner Signature**: Marcus Chen  
- **GRC Approval**: Veera Ranjane (Verified & Logged in ISMS Audit Trail)
