# Acceptable Use Policy (AUP)

| Metadata | Details |
| :--- | :--- |
| **Organization** | NexusPay Technologies Inc. |
| **Document ID** | POL-SEC-02 |
| **Version** | 1.0.0 |
| **Classification** | Internal |
| **Owner** | Information Security Department |
| **ISO 27001:2022 Ref** | Controls 5.9, 5.10, 6.7, 7.7, 8.1 |

---

## 1. Purpose
To establish security standards and operational expectations for employees and contractors utilizing NexusPay hardware, networks, digital assets, and communication channels.

## 2. Scope
Applies to all company-issued laptops, approved BYOD devices, communication channels (Slack, Notion, Google Meet), and data repositories.

## 3. Policy Statements

### 3.1 Device & Endpoint Security Baselines
- **Mandatory MDM**: All endpoints accessing NexusPay systems must be enrolled in the company’s Mobile Device Management platform (Jamf for macOS, Intune for Windows).
- **Full-Disk Encryption**: FileVault (macOS) or BitLocker (Windows) must be turned on with encryption keys escrowed securely in the MDM.
- **Screen Lock**: Devices must automatically lock after **5 minutes** of inactivity.
- **Patch Management**: Critical operating system and browser security updates must be installed within **14 calendar days** of release.

### 3.2 Clear Desk & Clear Screen Standards
- **Clear Screen**: Personnel must manually lock screens when stepping away from workstations (`Cmd + Ctrl + Q` on macOS or `Win + L` on Windows).
- **Remote / Public Working**: In coffee shops, co-working spaces, and airports, privacy screens are mandatory. Working on public, unencrypted Wi-Fi without an active corporate VPN or secure DNS is prohibited.
- **Clear Desk**: Physical notes containing customer PII, API tokens, or architectural diagrams must never be left unattended in shared workspaces.

### 3.3 Shadow IT & Third-Party SaaS
- Employees must not register corporate accounts or route corporate data through third-party SaaS services without prior security evaluation and approval by the GRC team.
- Unauthorized cloud storage platforms (e.g., personal Dropbox, personal iCloud) are blocked on managed devices.

### 3.4 Acceptable Use of Generative AI Tools
- **Public AI Models**: Inputting NexusPay source code, merchant credentials, internal API keys, or customer Personally Identifiable Information (PII) into public Generative AI platforms (e.g., public ChatGPT) is strictly prohibited.
- Only enterprise-sanctioned AI tools that guarantee zero data retention for model training may be used for internal business tasks.

### 3.5 Prohibited Activities
The following activities are strictly forbidden on all company hardware and networks:
- Running port scanners, packet sniffers, or unauthorized penetration testing tools against internal or external networks without explicit authorization.
- Downloading or distributing pirated software, torrents, or copyright-infringing content.
- Storing or transmitting offensive, defamatory, or unlawful material.

## 4. Document Revision History
| Version | Date | Author | Description |
| :--- | :--- | :--- | :--- |
| 1.0.0 | 2026-10-24 | Veera Ranjane | Initial production ISMS baseline release |
