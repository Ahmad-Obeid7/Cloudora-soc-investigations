# Project 01 — Cloud Account Takeover Investigation

**Incident ID:** CLD-IR-0001  
**Scenario:** Executive account takeover through password spraying with MFA persistence and BEC staging  
**Severity:** P1  
**Environment:** Synthetic Cloudora SOC engagement

## Overview

This investigation began with suspicious sign-in activity involving Cloudora CEO Daniel Reeve. The investigation expanded beyond the initial alert and identified a broader three-night password-spray campaign.

The analysis confirmed:

- **26 accounts targeted**
- **2 accounts compromised:** Daniel Reeve and Priya Nair
- **24 additional targeted-but-not-breached accounts**
- **3 attacker IP addresses**
- **114 failed authentication attempts** across the campaign
- An unauthorized **Pixel 6 authenticator app** registered on Daniel's account
- A malicious **RSS Subscriptions** inbox rule hiding finance/invoice-related messages
- SharePoint access through the second compromised account
- A travel anomaly for Omar Farah that was investigated and cleared as benign

## Investigation Workflow

1. Validated sign-in and audit-log ingestion.
2. Triaged Daniel Reeve's suspicious Lagos activity.
3. Built a normal-location baseline for the account.
4. Compared the alert with Omar Farah's legitimate Dubai travel.
5. Identified password-spray infrastructure using failed-login aggregation.
6. Confirmed the three-night attack window.
7. Investigated post-compromise persistence in the audit log.
8. Scoped successful attacker sign-ins to identify additional victims.
9. Checked the second victim for persistence.
10. Built a detection query for low-and-slow password spraying.
11. Produced a combined incident timeline and formal incident report.

## Key Findings

### 1. Password spraying

Three Lagos IP addresses generated failures across many different users while making only a small number of attempts per account. This pattern was consistent with password spraying rather than brute-forcing a single account.

### 2. Daniel Reeve compromise

Daniel's account was successfully accessed from Lagos using Windows 10 / Chrome 125 after preceding failed attempts. His normal activity was London-based.

### 3. Persistence and BEC staging

After gaining access, the attacker:

- Registered an unauthorized authenticator application named **Pixel 6**
- Created an inbox rule named **RSS Subscriptions**
- Configured the rule to hide finance- and invoice-related messages

### 4. Second compromised account

Priya Nair was also successfully accessed from attacker infrastructure, followed by SharePoint Online access.

### 5. False-positive validation

Omar Farah's Dubai sign-ins were assessed as legitimate travel based on timing, successful first-attempt authentication, normal device/browser usage, and repeated activity across multiple days.

## MITRE ATT&CK Mapping

| Tactic | Technique |
|---|---|
| Credential Access | T1110.003 — Password Spraying |
| Initial Access | T1078 — Valid Accounts |
| Persistence | T1098.005 — Device Registration |
| Defense Evasion | T1564.008 — Email Hiding Rules |

## Skills Demonstrated

- KQL threat hunting
- Identity and sign-in log analysis
- Account baselining
- Password-spray detection
- Compromise scoping
- Audit-log investigation
- Persistence analysis
- False-positive validation
- MITRE ATT&CK mapping
- Incident reporting and response recommendations

## Evidence

See the `screenshots/` directory for the investigation trail and `report/` for the completed incident report.

## Training Disclaimer

All data, identities and infrastructure in this project are synthetic and used for defensive training.
