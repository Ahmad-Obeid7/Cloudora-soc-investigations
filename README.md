# Cloudora SOC Investigations

A hands-on **Security Operations Center (SOC) portfolio** built around **Cloudora**, a fictional B2B HR software company.

This repository contains two end-to-end incident investigations using synthetic cloud, identity and email-security data. The projects focus on how an analyst moves from an initial alert or report to **triage, investigation, scoping, validation, detection, response recommendations and formal reporting**.

> **Training environment:** Cloudora, its users, logs, domains, IP addresses and incidents are synthetic and used only for defensive security training.

## Investigations

### [Project 01 — Cloud Account Takeover](./project-01-account-takeover/)

**Incident:** Password spraying → valid account compromise → MFA persistence → BEC staging

A low-volume password-spray campaign targeted **26 accounts** and resulted in **2 confirmed compromises**. The investigation identified attacker infrastructure, validated a benign travel anomaly, discovered unauthorized MFA registration and a malicious inbox rule, scoped a second victim and produced a reusable password-spray detection.

**Key skills:** KQL threat hunting, identity analysis, account baselining, password-spray detection, audit-log analysis, persistence investigation, incident scoping, MITRE ATT&CK mapping and detection engineering.

➡️ **[View the full Project 01 case study](./project-01-account-takeover/)**

---

### [Project 02 — Payroll Phishing Investigation](./project-02-phishing-investigation/)

**Incident:** Payroll phishing → credential harvesting → cloud-account compromise

A payroll-themed phishing campaign targeted **40 employees** using both direct domain spoofing and an authenticated lookalike domain. **6 users clicked**, **2 submitted credentials**, and both compromised accounts were later accessed by the attacker. The investigation combined raw `.eml` analysis, SPF/DKIM/DMARC interpretation, message tracing and sign-in correlation.

**Key skills:** phishing triage, email-header analysis, SPF/DKIM/DMARC, Received-chain analysis, lookalike-domain investigation, KQL correlation, credential-compromise validation, campaign scoping and detection engineering.

➡️ **[View the full Project 02 case study](./project-02-phishing-investigation/)**

## What This Portfolio Demonstrates

Across both investigations, the work demonstrates practical SOC analyst methodology:

- **Triage:** validate the initial alert or reported email
- **Baseline:** establish what normal activity looks like before judging anomalies
- **Pivot:** move from one user, IP or message to the wider incident
- **Scope:** identify compromised, targeted and unaffected users
- **Correlate:** combine identity, audit, email and message-trace telemetry
- **Validate:** separate confirmed compromise from suspicious-but-benign activity
- **Detect:** convert investigation findings into reusable KQL logic
- **Map:** align observed behavior with MITRE ATT&CK
- **Respond:** document containment, eradication and verification actions
- **Report:** produce formal incident reports with evidence and recommendations

## Tools & Technologies

| Area | Tools / Concepts |
|---|---|
| Querying & hunting | Azure Data Explorer, Kusto Query Language (KQL) |
| Cloud identity | Microsoft 365 / cloud sign-in telemetry |
| Email security | Exchange Online concepts, message tracing, raw `.eml` analysis |
| Authentication | SPF, DKIM, DMARC, Microsoft composite authentication |
| Incident analysis | Account baselining, IOC pivoting, timeline reconstruction |
| Frameworks | MITRE ATT&CK |
| Outputs | Detection queries, investigation screenshots, incident reports |

## Repository Structure

```text
Cloudora-soc-investigations/
├── README.md
├── project-01-account-takeover/
│   ├── README.md
│   ├── data/
│   ├── queries/
│   ├── screenshots/
│   └── report/
└── project-02-phishing-investigation/
    ├── README.md
    ├── data/
    ├── email-analysis/
    ├── email-samples/
    ├── queries/
    ├── screenshots/
    └── report/
```

## Portfolio Notes

Each project README is written as a case study rather than a simple file list. Selected screenshots are embedded directly into the investigation narrative, while the full evidence set, datasets, query files and incident reports remain available in their respective folders.

## Disclaimer

These projects use synthetic training data and reserved infrastructure. They do not represent real Cloudora systems, real victims or a live incident. The repository is intended to demonstrate defensive security investigation skills and SOC methodology.
