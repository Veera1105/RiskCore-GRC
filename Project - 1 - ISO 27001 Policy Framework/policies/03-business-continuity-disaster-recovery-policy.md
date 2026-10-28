# Business Continuity & Disaster Recovery (BCDR) Policy

| Metadata | Details |
| :--- | :--- |
| **Organization** | NexusPay Technologies Inc. |
| **Document ID** | POL-SEC-03 |
| **Version** | 1.0.0 |
| **Classification** | Internal |
| **Owner** |Information Security Department|
| **ISO 27001:2022 Ref** | Controls 5.29, 5.30, 8.13, 8.14 |

---

## 1. Purpose
To ensure the resilience, continuous availability, and structured recovery of NexusPay payment infrastructure, databases, and business services following critical operational disruptions, infrastructure failures, or cyberattacks.

## 2. Scope
Applies to the NexusPay cloud payment processing engine hosted in AWS, supporting microservices, continuous integration pipelines, and critical data stores.

## 3. Normative Policy Statements

### 3.1 Recovery Metrics (RPO & RTO)
The NexusPay engineering platform is architected and tested to adhere to the following operational recovery thresholds:
- **Recovery Point Objective (RPO)**: **≤ 1 Hour**  
  *Maximum allowable data loss window during a disaster event.*
- **Recovery Time Objective (RTO)**: **≤ 4 Hours**  
  *Maximum allowable duration to restore payment orchestration APIs to operational availability.*

### 3.2 Backup Architecture & Immutability
- **Automated Snapshots**: Production databases (AWS Aurora / RDS PostgreSQL) execute automated continuous transaction log archiving alongside automated hourly snapshots.
- **Cross-Region Replication**: Production backups in primary region `us-east-1` are automatically replicated to disaster recovery region `us-west-2`.
- **WORM / Immutability**: Backup storage buckets (AWS S3) are configured with Object Lock in Compliance Mode to prevent accidental or malicious deletion.
- **Encryption**: All backups are encrypted at rest using AWS KMS Customer Managed Keys (CMK) with AES-256.

### 3.3 Annual Disaster Recovery Testing & Validation
- NexusPay must execute an active Disaster Recovery drill at least **once every 12 months**.
- The test must validate:
  1. Restoration of the latest production snapshot into a sandboxed VPC in the secondary AWS region (`us-west-2`).
  2. Execution of end-to-end automated payment API sanity tests.
  3. Measured recovery duration against documented RTO and RPO benchmarks.
- A post-drill assessment report must be delivered to the CEO and Head of GRC (Veera Ranjane) within 5 business days of drill completion.

### 3.4 Crisis Communications & Incident Command
- If production downtime extends beyond **30 minutes**, an incident is escalated to Disaster status.
- The VP of Engineering assumes the role of Incident Commander.
- The public status page (`status.nexuspay.io`) must be updated within **15 minutes** of declaring an operational disruption, with status updates published at minimum every 30 minutes until resolution.

## 4. Document Revision History
| Version | Date | Author | Description |
| :--- | :--- | :--- | :--- |
| 1.0.0 | 2026-10-24 | Veera Ranjane | Initial production ISMS baseline release |
