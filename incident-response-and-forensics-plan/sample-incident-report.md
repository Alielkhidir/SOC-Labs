<a href="https://github.com/Alielkhidir/SOC-Labs"><img src="../badges/back-to-soc-labs.png" alt="Back to SOC Labs" height="30"></a>

[← Back to the Incident Response & Digital Forensics Plan](../README.md)

# Sample Incident Report: Spear-Phishing and Email Server Compromise

> **Note:** This is a fictional, illustrative report written for a training scenario. "SecureSync Corp.", all names, times, counts, and indicators are invented, and the IP addresses and domains use ranges reserved for documentation and examples. It shows how the incident response plan in this repository would be applied.

| Field | Detail |
|---|---|
| Report ID | IR-2025-001 (example) |
| Company | SecureSync Corp. (fictional) |
| Severity | High |
| Status | Closed, with follow-up actions open |
| Prepared by | Security Analyst, Incident Response Team |
| Audience | Executive leadership and technical staff |

**Severity rationale:** sensitive client data on the affected server, confirmed outbound data transfer, and more than one account compromised.

---

## 1. Executive Summary

On a Monday morning, SecureSync's intrusion detection system flagged unusual activity on the corporate email server, which holds sensitive client data and internal communications. Investigation confirmed that attackers had gained access through a spear-phishing email that compromised user mailboxes and gave them a backdoor. Malware on the affected systems was sending data to an unknown external server.

The incident response team contained the attack by disabling compromised accounts and isolating affected network segments, removed the malware, and restored systems from secure backups. Continuous monitoring is now in place and no further malicious activity has been observed.

**Business impact:** Possible exposure of client and internal email data, a temporary loss of email availability for affected users, and a need to notify clients.
**Outcome:** Threat removed, services restored, and the company's first formal incident response plan is being finalized based on the lessons learned.

**At a glance (illustrative figures)**

| Measure | Value |
|---|---|
| Mailboxes compromised | 2 |
| Other systems affected | 1 email server, 3 endpoints |
| Data sent to the external host | About 1.2 GB of email data |
| Time the attackers had access before detection | About 3 days |
| Time from alert to containment | 2 hours |
| Time to full recovery | 3 to 5 days |

---

## 2. Technical Analysis

**Detection.** The IDS raised alerts for anomalous behavior. Log review showed remote logins at odd hours and from unusual locations. Automated scripts captured packets suggesting data was being exfiltrated.

**Attack vector.** A spear-phishing email targeted specific employees. At least one user interacted with it, which exposed their email credentials and let the attackers establish backdoor access.

**Root cause.** Phishing awareness was insufficient, and there was no formal process or multi-factor authentication to stop a stolen password from being used to reach the email server.

**Affected systems.**

- Corporate email server
- Compromised user mailboxes
- Endpoints where malware was present

**Indicators of compromise (fictional examples)**

| Type | Example indicator | Where it was found |
|---|---|---|
| Sign-ins | Remote logins at 02:00 to 04:00 from source IP 203.0.113.45, outside business hours and from an unfamiliar location | Authentication logs |
| Network | Sustained outbound connections from the email server to 198.51.100.77 | Firewall and packet captures |
| Email | Message from `accounts@securesync-billing.example`, a look-alike of the company domain, with a link to `secure-docs-review.example` | Mail gateway and the user's mailbox |
| Host | File `Q3_Invoice_Review.pdf.exe` and a persistence mechanism on infected endpoints | Endpoint protection and forensic images |

**MITRE ATT&CK mapping (illustrative)**

| Stage | Technique |
|---|---|
| Initial access | T1566 Phishing (spear-phishing link or attachment) |
| Persistence and access | T1078 Valid Accounts (stolen credentials) |
| Collection | T1114 Email Collection |
| Exfiltration | T1041 Exfiltration Over C2 Channel |

**Evidence collected.** System and application logs, network traffic captures, the phishing email and attachments, malware samples, and forensic images of compromised devices. Hashes were created at collection and re-verified before analysis, and a chain of custody was kept for each item.

**Timeline (illustrative)**

| Time | Event |
|---|---|
| T-3 days | Spear-phishing email delivered; one user enters their credentials on a fake page |
| T-3 days to T+0 | Attackers log in remotely at odd hours, and data is sent to an external host |
| T+0 h | IDS alert on unusual email server activity |
| T+1 h | Alert confirmed as a likely breach; incident response team activated |
| T+2 h | Compromised accounts disabled; affected network segments isolated |
| T+1 to 3 days | Threat hunt and malware analysis; eradication plan built with threat intelligence |
| T+3 to 5 days | Malware removed, systems restored from secure backups, system-wide checks completed |
| T+5 days onward | Continuous monitoring enabled; post-incident review held |

---

## 3. Response Actions

**Containment (short term)**

- Disabled compromised user accounts to stop further access
- Isolated affected network segments to stop malware spreading and limit exfiltration

**Eradication**

- Hunted for the malware across the environment, guided by threat intelligence on its typical behavior
- Removed malicious code from all infected systems

**Recovery**

- Restored systems from secure backups
- Ran system-wide checks to confirm no residual damage or hidden vulnerabilities
- Enabled continuous monitoring to catch any further compromise attempts

**Communication**

- The communication liaison kept leadership updated during the incident
- Legal and leadership reviewed client and regulatory notification requirements
- A client-facing report explained the incident and the improved security measures

---

## 4. Lessons Learned and Recommendations

**What worked well**

- IDS and logging detected the attack quickly
- Defined roles let the team respond rapidly
- Backups allowed a clean recovery

**Gaps found**

- No formal, documented incident response plan
- Phishing awareness among staff was insufficient
- Threat intelligence sharing and cross-department communication were slower than needed
- The attackers had about three days of access before detection

**Recommendations**

| # | Action | Owner | Priority |
|---|---|---|---|
| 1 | Finalize and approve a formal incident response plan based on NIST | CIO / IR Team Leader | High |
| 2 | Run recurring phishing awareness training and simulations | Security Team | High |
| 3 | Enforce multi-factor authentication on email and remote access | IT Operations | High |
| 4 | Add email filtering that checks links and attachments, and protect the company domain against look-alike spoofing | IT Operations | High |
| 5 | Tune detection rules for off-hours and unusual-location logins | Security Analyst | Medium |
| 6 | Alert on unusual outbound data volume from the email server | Security Analyst | Medium |
| 7 | Set up a process for sharing threat intelligence across departments | IR Team Leader | Medium |
| 8 | Hold regular security drills and review the plan after each one | IR Team Leader | Medium |

---

*Prepared as a portfolio example of the reporting phase of an incident response and forensics process.*
