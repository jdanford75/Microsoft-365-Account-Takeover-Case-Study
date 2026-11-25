# Microsoft 365 Account Takeover & Payment Fraud — Case Study

**Jack Danford · Austin Community College · CSIS 3333 Information Security**

I analyzed a Microsoft-documented campaign in which attackers took over Microsoft 365 sessions and used victims’ mailboxes to try to redirect business payments. I mapped the reported behavior to MITRE ATT&CK and proposed a workflow for investigating suspicious sign-ins and mailbox activity.

[Read the full case study (PDF)](microsoft-365-account-takeover-case-study.pdf)

## What the evidence supports

- Microsoft’s published timeline showed remote mailbox access and a rule that hid replies by archiving them and marking them as read. The public timeline documents attempted fraud. Whether money changed hands remains unverified.
- A suspicious sign-in and a mailbox rule tied to the same account warrant investigation. Connecting both actions to one session requires corroborating evidence, such as a shared session identifier where available.
- Microsoft observed follow-on fraud attempts within minutes. An hourly review could miss that window, so direct session-replay alerts warrant prompt triage where coverage exists.

## Proposed detection and response

Review Microsoft Entra sign-in records alongside mailbox audit events. Check whether VPN use, travel, or ordinary mailbox rules explain the activity. For a confirmed compromise, preserve evidence, revoke affected sessions, remove malicious rules, and verify payment changes independently.

**Scope:** Academic analysis of publicly reported evidence. The detection plan is proposed and untested. The report uses published examples and cites their sources.

[Read Microsoft’s campaign report](https://www.microsoft.com/en-us/security/blog/2022/07/12/from-cookie-theft-to-bec-attackers-use-aitm-phishing-sites-as-entry-point-to-further-financial-fraud/)
