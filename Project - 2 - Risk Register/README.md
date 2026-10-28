# ShopSphere GRC Cybersecurity Risk Assessment

## Executive Summary
This project demonstrates an end-to-end qualitative cybersecurity risk assessment for **ShopSphere**, a simulated e-commerce platform. The assessment evaluates threats to business-critical assets, establishes inherent risk scores using a qualitative $3 \times 3$ matrix, outlines control-based remediation strategies, and calculates residual risk post-treatment.

All data, formulas, and dashboards were implemented in **Microsoft Excel** using automated lookups, conditional formatting, and PivotTables.

> *Note: ShopSphere is a simulated operational environment designed for educational and portfolio demonstration purposes.*

---

## Risk Assessment Methodology
The methodology aligns with **NIST SP 800-30 Rev. 1** principles, evaluating risk as a function of **Likelihood** and **Impact**:

$$\text{Risk Score} = \text{Likelihood} \times \text{Impact}$$

### 1. Assessment Scales
Both variables are assessed on a 3-point qualitative scale:

| Level | Rating | Likelihood Definition | Impact Definition |
| :---: | :---: | :--- | :--- |
| **1** | Low | Unlikely to occur; limited threat capability or exposure | Negligible effect; minor operational or financial loss |
| **2** | Medium | Moderate probability; known threat vector with basic controls | Serious effect; noticeable operational disruption or localized breach |
| **3** | High | Highly probable; active threat targeting or unmitigated vector | Critical effect; severe financial, regulatory, or operational disruption |

### 2. Risk Determination Scoring Ranges
Calculated scores map to the following organizational risk tiers:

| Score Range | Risk Rating | Operational Response Priority |
| :---: | :---: | :--- |
| **1 – 2** | Low | Acceptable; monitor via continuous operations |
| **3 – 4** | Medium | Moderate; implement targeted compensating controls |
| **6 – 9** | High | Unacceptable; requires immediate remediation and executive oversight |

### 3. $3 \times 3$ Qualitative Risk Matrix

| Impact $\downarrow$ \ Likelihood $\rightarrow$ | Low (1) | Medium (2) | High (3) |
| :--- | :---: | :---: | :---: |
| **High (3)** | 3 (Medium) | 6 (High) | 9 (High) |
| **Medium (2)** | 2 (Low) | 4 (Medium) | 6 (High) |
| **Low (1)** | 1 (Low) | 2 (Low) | 3 (Medium) |

---

## Risk Register Data

| Risk ID | Asset | Threat Source | Vulnerability | Inherent Likelihood | Inherent Impact | Inherent Score | Inherent Rating | Risk Treatment | Mitigation Plan | Risk Owner | Residual Likelihood | Residual Impact | Residual Score | Residual Rating | Status |
| :---: | :--- | :--- | :--- | :---: | :---: | :---: | :---: | :---: | :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| **R-001** | Customer Database | Cybercriminal | Lack of MFA on privileged/admin accounts | 2 | 3 | 6 | **High** | Mitigate | Implement MFA for all privileged and administrative accounts | IT Manager | 1 | 3 | 3 | **Medium** | Open |
| **R-002** | Payment Gateway | Cybercriminal | Outdated API component with known security vulnerabilities | 3 | 3 | 9 | **High** | Mitigate | Patch or upgrade the vulnerable API component and perform security testing | Application Engineering Manager | 1 | 3 | 3 | **Medium** | Open |
| **R-003** | Cloud Storage | Unauthorized External User | Misconfigured access permissions exposing storage publicly | 2 | 3 | 6 | **High** | Mitigate | Correct cloud storage access permissions and restrict public access | Cloud Infrastructure Manager | 1 | 3 | 3 | **Medium** | Open |
| **R-004** | Cloud Storage | Unauthorized External User | Misconfigured access permissions exposing storage publicly | 2 | 3 | 6 | **High** | Mitigate | Correct cloud storage access permissions and restrict public access | Cloud Infrastructure Manager | 1 | 3 | 3 | **Medium** | Open |
| **R-005** | Production Server | Ransomware Actor | Backups are accessible from the production environment and are not immutable | 2 | 3 | 6 | **High** | Mitigate | Implement immutable, isolated backups and restrict backup access from production | Application Engineering Manager | 1 | 2 | 2 | **Low** | Open |

---

## Assessment Findings & Treatment Analysis

* **Initial Posture:** 100% of assessed assets ($5/5$) carried an initial rating of **High Inherent Risk**, driven by internet-facing exposures, unpatched API components, and unsegmented backups.
* **Control Implementation:** By establishing technical safeguards (phishing-resistant MFA, immutable isolated storage, dependency patching, and automated bucket permission policies), threat initiation and success likelihoods were systematically reduced from Moderate/High (2–3) to **Low (1)**.
* **Post-Remediation Profile:**
  * **High Risks:** Reduced from **5 to 0** ($0\%$).
  * **Medium Risks:** **4** ($80\%$) — R-001, R-002, R-003, R-004 maintain residual Medium scores because while exploitation likelihood drops to Low (1), data breach impact on customer PII and payment systems remains High (3).
  * **Low Risks:** **1** ($20\%$) — R-005 reduced to Low (Score: 2).

---

## Risk Governance Dashboard

The workbook integrates dynamic PivotTables and PivotCharts to communicate risk posture metrics to stakeholders:

* **Inherent vs. Residual Distribution:** Visualizes the elimination of critical risk tiers across assets.
* **Risk Ownership Breakdown:** Assigns operational accountability across teams:
  * Application Engineering Management: 2 Risks (`R-002`, `R-005`)
  * Cloud Infrastructure Management: 2 Risks (`R-003`, `R-004`)
  * IT Management: 1 Risk (`R-001`)

---

## Technical Excel Competencies Demonstrated
* **Formulas & Automation:** Automated risk rating determinations using nested functions and `VLOOKUP`.
* **Data Validation:** Enforced consistent scoring entries via strict numerical and text drop-downs.
* **Conditional Formatting:** Automated color-coded visual hierarchy (Red = High, Yellow = Medium, Green = Low) mapped directly to risk scores.
* **Reporting & Aggregation:** Structured Excel Tables with dynamic PivotTable slices and executive charts.

---

## Disclaimer
This project is an academic simulation conducted for GRC skill demonstration and portfolio validation. Scenarios, asset configurations, vulnerabilities, and outcomes do not represent any real organization or commercial production network.
