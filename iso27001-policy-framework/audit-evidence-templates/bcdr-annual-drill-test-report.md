# Annual Disaster Recovery Simulation Report

| Drill Metadata | Specification |
| :--- | :--- |
| **Organization** | NexusPay Technologies Inc. |
| **Drill Execution Date** | September 18, 2026 |
| **Incident Commander** | Marcus Chen (VP of Engineering) |
| **Target Infrastructure** | AWS Aurora PostgreSQL & Payment API Gateway |
| **Scenario Simulated** | Complete outage of AWS Region `us-east-1` (Primary) |

---

## 1. Test Objectives & Benchmarks
- **Target RPO**: ≤ 1 Hour | **Target RTO**: ≤ 4 Hours
- **Objective**: Verify that cross-region read replicas in `us-west-2` can be promoted to standalone primary instances and customer payment endpoints redirected via Route 53 with zero data corruption.

## 2. Timeline of Execution

| Time (UTC) | Action Item | Status | Notes |
| :--- | :--- | :--- | :--- |
| 10:00 AM | Simulation initiated; primary region connectivity severed in sandbox. | Complete | Alarm triggered in PagerDuty within 120 seconds. |
| 10:15 AM | Aurora replica promoted to primary master in `us-west-2`. | Complete | Database operational in DR region. |
| 10:45 AM | ECS tasks & API containers booted via Terraform in DR region. | Complete | Core containers healthy and passing load balancer probes. |
| 11:10 AM | DNS failover simulated via Route 53 health check update. | Complete | Traffic routed to DR gateway. |
| 11:25 AM | 500 automated end-to-end payment API synthetic tests executed. | Complete | **100% success rate (0 failures).** |

## 3. Findings & Performance Metrics
- **Achieved RPO**: **8 minutes** *(Well within ≤ 1 hr target)*
- **Achieved RTO**: **1 hour 25 minutes** *(Well within ≤ 4 hr target)*
- **Identified Gap**: Terraform state lock delay occurred during ECS spin-up in `us-west-2`, adding 12 minutes to recovery time.
- **Corrective Action (CAPA-2026-04)**: Refactor DR Terraform state bucket configuration to use local DynamoDB replica table by November 15, 2026.

## 4. Certification
- **Incident Commander**: Marcus Chen  
- **ISMS Auditor Sign-Off**: Veera Ranjane (Head of Information Security & GRC)
