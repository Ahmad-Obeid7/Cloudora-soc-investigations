# Project 02 — Payroll Phishing Investigation

**Incident ID:** CLD-IR-0002  
**Scenario:** Payroll-themed credential phishing campaign with two compromised accounts  
**Severity:** P1  
**Environment:** Synthetic Cloudora SOC engagement

## Overview

This investigation began when an employee reported a suspicious payroll email impersonating Cloudora HR.

The investigation combined raw email-header analysis with message-trace data and cloud sign-in telemetry to determine campaign scope and identify compromised users.

The investigation confirmed:

- **40 employees targeted**
- **6 users clicked** phishing links
- **2 users submitted credentials**
- **2 accounts compromised:** Freya Lynn and Ryan Boyd
- Attacker access to Outlook Web for both victims
- SharePoint Online access through Freya's account
- Two phishing variants using spoofing and a lookalike domain
- A legitimate newsletter investigated and cleared as a false positive

## Investigation Workflow

1. Triaged the employee-reported phishing email.
2. Examined raw `.eml` headers and the Received chain.
3. Analyzed SPF, DKIM, DMARC and Microsoft composite authentication results.
4. Identified sender and Reply-To mismatches.
5. Compared malicious messages with legitimate Cloudora payroll email.
6. Distinguished spoofed mail from a lookalike-domain variant.
7. Validated message-trace and sign-in datasets.
8. Scoped campaign delivery, quarantine actions and recipient counts.
9. Identified users who clicked and users who submitted credentials.
10. Correlated credential submissions with subsequent cloud sign-ins.
11. Confirmed attacker access from Amsterdam using Windows 11 / Chrome.
12. Identified near-miss users who received phishing emails but did not click.
13. Drafted user communications and created detection logic linking phishing clicks to foreign sign-ins.

## Key Findings

### 1. Variant A — spoofed Cloudora sender

Variant A used `payroll@cloudora.io` as the visible sender, but SPF, DKIM and DMARC failed. The message originated from attacker-controlled infrastructure and used a mismatched Reply-To and fraudulent payroll URL.

### 2. Variant B — lookalike domain

Variant B passed SPF, DKIM and DMARC because it was genuinely sent from the attacker's own lookalike domain. This demonstrated an important email-security principle:

> Authentication passing does not prove that a sender is the legitimate brand; it proves that the message is authorized for the domain it actually came from.

### 3. Credential theft and account compromise

Freya Lynn and Ryan Boyd submitted credentials through phishing links. Later successful sign-ins from `198.18.7.200` in Amsterdam using Windows 11 / Chrome were inconsistent with their normal activity and confirmed attacker use of the harvested credentials.

### 4. Post-compromise activity

- Freya's account was used to access Microsoft 365, Outlook Web and SharePoint Online.
- Ryan's account was used to access Microsoft 365 and Outlook Web.

## Skills Demonstrated

- Phishing triage
- Raw email-header analysis
- SPF / DKIM / DMARC analysis
- Received-chain tracing
- Lookalike-domain analysis
- Message-trace investigation
- KQL correlation
- Credential-compromise validation
- Cloud sign-in analysis
- False-positive analysis
- Incident scoping
- User communication drafting
- Detection engineering

## Evidence

See the `email-samples/` directory for synthetic message samples, `screenshots/` for the investigation evidence, and `report/` for the completed incident report.

## Training Disclaimer

All domains, IP addresses, user identities and phishing samples in this project are synthetic. The `.example` domain is reserved and non-resolvable.
