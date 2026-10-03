# Cloudora SOC Investigations

A portfolio of simulated Security Operations Center (SOC) investigations built around **Cloudora**, a fictional B2B HR software company.

The projects demonstrate practical incident-response skills across cloud identity, email security, phishing analysis, KQL threat hunting, account-compromise scoping, MITRE ATT&CK mapping, and response recommendations.

> **Training environment:** Cloudora, its users, infrastructure, IP addresses, domains, and incidents are synthetic and used only for defensive security training.

## Investigations

| Project | Incident | Core skills |
|---|---|---|
| [CLD-IR-0001](./project-01-account-takeover/) | Password spray → account takeover → MFA persistence → BEC staging | KQL, identity investigation, account baselining, persistence analysis, incident scoping, MITRE ATT&CK |
| [CLD-IR-0002](./project-02-phishing-investigation/) | Payroll-themed credential phishing with two compromised accounts | Email header analysis, SPF/DKIM/DMARC, message trace, phishing scoping, KQL correlation, compromise validation |

## Tools & Technologies

- Azure Data Explorer / Kusto Query Language (KQL)
- Microsoft Sentinel-compatible hunting logic
- Microsoft 365 / Exchange Online security concepts
- Email header analysis
- SPF, DKIM and DMARC
- MITRE ATT&CK
- Incident triage, scoping and reporting

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
    ├── queries/
    ├── email-samples/
    ├── screenshots/
    └── report/
```

## Disclaimer

These investigations use synthetic training data and reserved infrastructure. They are documented to demonstrate defensive security analysis and SOC investigation methodology.
