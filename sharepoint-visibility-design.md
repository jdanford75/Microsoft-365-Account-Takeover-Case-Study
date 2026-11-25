# Microsoft 365 and SharePoint — Visibility Design

**Jack Danford · Austin Community College · CSIS 3333, Lab 8**

I designed a monitoring strategy for a hypothetical Microsoft 365 session compromise followed by unauthorized access to sensitive SharePoint files. The goal was to identify what each data source could tell an analyst and where the evidence would be incomplete.

| Data source | What I would check | Visibility limit |
| --- | --- | --- |
| Microsoft Entra | Account, timestamp, application, source IP, device details, and session identifier when available | A successful sign-in alone cannot establish who used the session. |
| Managed endpoint | Browser connections and endpoint detection records | Coverage applies to the managed device. |
| Network | DNS, proxy, and firewall events from monitored devices and networks | Direct cloud traffic from outside the monitored network may be absent. |
| SharePoint audit | File access and download events, sensitive libraries, and available client details | A recorded download needs business context before it can be classified. |

## What I would test

1. Confirm that identity, SharePoint, and managed-device events arrive centrally with aligned timestamps and sufficient retention. Monitor for missing feeds.
2. Investigate unusual cloud access, conflicting session activity when a shared identifier exists, and sensitive-file downloads that exceed normal activity. Treat account-and-time correlation as a lead when session evidence is missing.
3. Validate the proposed signals with authorized test accounts and non-sensitive files. Include ordinary VPN use and approved bulk downloads to measure false positives before tuning thresholds.

**Scope:** Academic monitoring design for a hypothetical scenario. The proposed detections were untested.

[Microsoft Learn — Audit log activities](https://learn.microsoft.com/en-us/purview/audit-log-activities)
