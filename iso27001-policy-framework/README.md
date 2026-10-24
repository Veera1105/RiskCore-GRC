# NexusPay Technologies Inc. — ISO/IEC 27001:2022 Security Policy Suite

![Standard: ISO/IEC 27001:2022](https://img.shields.io/badge/Standard-ISO%2FIEC%2027001%3A2022-0052CC.svg)
![Target: Stage 1 & Stage 2 Audit](https://img.shields.io/badge/Audit%20Readiness-Stage%201%20%26%202-success.svg)
![Organization: NexusPay Technologies](https://img.shields.io/badge/Entity-FinTech%20SaaS-orange.svg)
![Architecture: AWS Cloud-Native](https://img.shields.io/badge/Infra-AWS%20Multi--Region-232F3E.svg)
![Author: Veera Ranjane](https://img.shields.io/badge/Author-Veera%20Ranjane-blue.svg)

## 1. Executive Summary
This folder contains the foundational **Information Security Management System (ISMS)** documentation suite for **NexusPay Technologies Inc.**, an API-first FinTech payment orchestration platform. 

Aligned with **ISO/IEC 27001:2022**, it establishes governance, identity boundaries, endpoint baselines, and operational resilience required to secure customer transaction data and satisfy third-party certification audits.

---

## 2. Organization Profile & ISMS Scope (Clause 4)
* **Legal Entity**: NexusPay Technologies Inc.
* **Industry**: B2B Cloud FinTech / Payment Gateway SaaS
* **Headcount**: 45 Distributed Full-Time Employees (Remote-First)
* **Lead GRC Consultant / Author**: Veera Ranjane
* **ISMS Scope Statement**:
  > "The scope of the NexusPay ISMS encompasses all corporate processes, systems, and personnel responsible for the architecture, engineering, CI/CD pipeline, and continuous operation of the NexusPay Cloud Payment Orchestration Platform hosted in Amazon Web Services (AWS), along with corporate identity, customer service, and endpoint management systems."

### Technical Infrastructure Baseline
* **Cloud Infrastructure**: Amazon Web Services (Primary: `us-east-1`, DR: `us-west-2`) managed via Terraform.
* **Identity & Access (IdP)**: Google Workspace federated with Okta Enterprise (WebAuthn/FIDO2 MFA enforced).
* **Code & CI/CD**: GitHub Enterprise Cloud with protected branch rules, automated CodeQL SAST, and container scanning.
* **Endpoint Management**: Apple MDM (Jamf) and Microsoft Intune enforcing FileVault/BitLocker full-disk encryption.

---

## 3. Policy Suite & ISO/IEC 27001:2022 Control Mapping

| Policy Document | Scope & Key Themes | ISO 27001:2022 Mapping |
| :--- | :--- | :--- |
| [`00-master-information-security-policy.md`](policies/00-master-information-security-policy.md) | Executive commitment, ISMS governance, organizational roles, and security KPIs | Clauses 5.1–5.3, 6.2; Annex A 5.1 |
| [`01-access-control-policy.md`](policies/01-access-control-policy.md) | Principle of Least Privilege (PoLP), RBAC, JML lifecycle SLAs, MFA, PAM, quarterly reviews | Annex A 5.15, 5.16, 5.17, 5.18, 8.2, 8.5 |
| [`02-acceptable-use-policy.md`](policies/02-acceptable-use-policy.md) | Endpoint security baselines, MDM enforcement, remote working hygiene, clear desk/screen, Generative AI controls | Annex A 5.9, 5.10, 6.7, 7.7, 8.1 |
| [`03-business-continuity-disaster-recovery-policy.md`](policies/03-business-continuity-disaster-recovery-policy.md) | RPO (≤ 1 hr) and RTO (≤ 4 hrs), cross-region immutable backups, automated failover, annual disaster drill | Annex A 5.29, 5.30, 8.13, 8.14 |

---

## 4. Operational Evidence & Audit Artifacts
* [`quarterly-access-review-signoff.md`](audit-evidence-templates/quarterly-access-review-signoff.md): Records user access certification and orphan account deprovisioning.
* [`bcdr-annual-drill-test-report.md`](audit-evidence-templates/bcdr-annual-drill-test-report.md): Validates annual recovery tests against defined RTO/RPO targets.
