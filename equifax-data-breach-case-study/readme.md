<a href="https://github.com/Alielkhidir/SOC-Labs"><img src="../badges/back-to-soc-labs.png" alt="Back to SOC Labs" height="30"></a>

# Case Study: The 2017 Equifax Data Breach

Final project from the IBM Cybersecurity Capstone course (Coursera). I analyzed a real-world data breach using a standard case study template: root cause, actions taken, effectiveness, successes and failures, impact, lessons learned, recommendations, and conclusion. This analysis is my own work and wording, based on public sources.

| | |
|---|---|
| **Level** | Beginner |
| **Date** | Nov 2025 |
| **Type** | Research and analysis (case study) |
| **Source** | IBM Cybersecurity Analyst Professional Certificate (Capstone, Coursera) |
| **Sources used** | U.S. House Oversight Committee report and FTC settlement announcement (see References) |

## IBM Badge Earned

<table>
  <tr>
    <td width="150" align="center">
      <a href="https://www.credly.com/badges/e485ee17-62c9-48fd-92bd-43ddc82d7843"><img src="../badges/ibm-breach-case-studies.png" alt="IBM badge: Cybersecurity Breach Case Studies" width="130"></a>
    </td>
    <td>
      <b>Cybersecurity Breach Case Studies</b><br>
      Issued by IBM through Coursera on 24 Nov 2025. This project was part of the coursework for earning this badge.<br><br>
      <a href="https://www.credly.com/badges/e485ee17-62c9-48fd-92bd-43ddc82d7843">Verify on Credly →</a>
    </td>
  </tr>
</table>

## The Breach at a Glance

| | |
|---|---|
| **Company** | Equifax, a major consumer credit reporting agency |
| **People affected** | About 147 million (later estimates reached about 148 million) |
| **Data exposed** | Names, dates of birth, Social Security numbers, addresses, and other personal information |
| **Entry point** | An unpatched Apache Struts flaw (CVE-2017-5638) on an internet-facing web application |
| **Time inside the network** | 76 days before detection |
| **Outcome** | Settlement of at least $575 million, executive departures, lasting loss of trust |

## Skills Demonstrated

- Case study analysis and structured security reporting
- Vulnerability and patch management analysis
- Incident response evaluation (detection, containment, disclosure)
- Governance, risk, and compliance thinking
- Translating technical failures into business impact and actionable recommendations

---

## Introduction

The 2017 Equifax breach exposed the personal data of about 147 million people, including Social Security numbers, birth dates, and addresses. Attackers exploited a known flaw in the Apache Struts web framework (CVE-2017-5638) that Equifax had not patched, and they stayed inside the network for 76 days before being detected. The case highlights failures in vulnerability management, governance, monitoring, and data protection. It led to a settlement of at least $575 million, executive departures, and a lasting loss of public trust. It remains one of the clearest real-world examples of how delayed patching and weak oversight can turn one unpatched system into a company-wide crisis.

## The Vulnerability

| | |
|---|---|
| **CVE** | CVE-2017-5638 |
| **Component** | Apache Struts 2 (Jakarta Multipart parser) |
| **Type** | Remote code execution through a crafted request header |
| **Severity** | Critical (CVSS 10.0) |
| **Affected Equifax system** | The online consumer dispute portal |

## Key Timeline

| Date (2017) | Event |
|---|---|
| March 7 | Apache Struts flaw CVE-2017-5638 is disclosed and a patch is released |
| March 9 | Equifax's internal security team circulates the alert, but the vulnerable system is not patched |
| May 13 | Attackers first gain access through the unpatched web application |
| July 29 | Equifax notices suspicious traffic after fixing its inspection tool |
| July 30 | The attacker's access is blocked |
| September 7 | Equifax publicly announces the breach |

---

## Case Study Analysis

### 1. Root Causes

1. **Failure to patch a known vulnerability.** A fix for CVE-2017-5638 had been available for roughly two months. Equifax received alerts but never patched the affected internet-facing system, and its vulnerability scan did not detect the exposure.
2. **Weak ownership and communication.** The patch alert did not reach the people responsible for the vulnerable system, and there was no clear accountability or reliable asset inventory to make sure critical patches were applied. The FTC notes that the security team ordered patching within 48 hours but did not follow up to confirm it was done.

### 2. Actions Taken

1. **Incident response and containment.** Once the suspicious activity was found, the security team blocked the traffic, took the affected application offline, and brought in an outside cybersecurity firm and law enforcement to investigate.
2. **Disclosure and remediation.** Equifax notified regulators and the public and offered affected people identity protection and credit monitoring. A later settlement also required it to build a comprehensive information security program.

### 3. Effectiveness and Timeliness

- **Incident response (effective but late).** Blocking the attacker the day after discovery worked. However, the attackers had already been inside for 76 days. The monitoring tool that should have exposed the data theft had an expired certificate and could not inspect encrypted traffic, so detection happened by chance, not by design.
- **Disclosure (slow and uneven).** The public announcement came about six weeks after discovery. The consumer response was criticized for confusing messaging and website problems, and credit monitoring did not fully address the long-term identity theft risk of leaked Social Security numbers.

### 4. Successes, Gaps, and Failures

- **Success:** After detection, Equifax contained the attack quickly, cooperated with regulators and law enforcement, and later invested heavily in security improvements.
- **Gap:** Weak patch management, sensitive data stored without adequate protection (including some unencrypted data and credentials left in accessible locations), and poor network segmentation that let attackers move between systems.
- **Failure:** Not detecting the intrusion for 76 days because the inspection tool was not working.

### 5. Impact on the Organization

1. **Financial and regulatory (short and long term):** A settlement of at least $575 million with the FTC, CFPB, and states, plus legal, investigation, and remediation costs, and the departure of senior executives including the CEO, CIO, and CISO.
2. **Reputational and strategic:** A severe loss of consumer and partner trust, closer regulatory scrutiny, and a lasting association with one of the largest breaches in history, affecting the company's core business of handling sensitive data.

### 6. Lessons Learned

1. **Patching needs ownership, tracking, and verification.** Knowing about a vulnerability is not enough. Organizations need a complete asset inventory, clear responsibility for each system, and scans that confirm the patch was applied.
2. **Defense in depth and working monitoring matter.** Encryption, segmentation, and least-privilege access limit the damage once attackers get in, and detection tools must be maintained (for example, certificates renewed) or they give a false sense of security.

### 7. Recommendations for Future Actions

| | Do | Avoid |
|---|---|---|
| 1 | Implement automated patch and vulnerability management with a maintained asset inventory, fixed deadlines for critical CVEs, and follow-up scans. | Relying on emailed alerts and manual processes for critical fixes. |
| 2 | Adopt a zero-trust architecture with network segmentation, encryption of sensitive data, strict access control, and regular health checks on monitoring tools. | Flat networks and implicit trust of internal systems. |

### 8. Conclusion

The Equifax breach shows that a single unpatched system, combined with weak governance and broken monitoring, can cause catastrophic harm at massive scale. The pattern is common across major breaches: the root cause is often a known, fixable weakness rather than a sophisticated attack. For organizations that hold sensitive data, strong architecture, proactive policies, accountable patching, and real-time monitoring are essential, and regulators now expect them.

---

## The SOC Perspective

This section looks at the breach the way a SOC analyst would. It is my own analysis of how the attack could have been caught.

**Attack path mapped to MITRE ATT&CK (illustrative)**

| Stage | Technique |
|---|---|
| Initial access | T1190 Exploit Public-Facing Application |
| Persistence | T1505.003 Web Shell |
| Credential access | T1552.001 Credentials In Files |
| Using the credentials | T1078 Valid Accounts |
| Exfiltration | T1041 Exfiltration Over C2 Channel |

**Where detection could have happened**

| Weak point | What a SOC could have monitored |
|---|---|
| Critical CVE left unpatched | Asset inventory and vulnerability scans, with every critical CVE tracked until it is confirmed closed |
| Exploit attempts against the web application | Web server logs, WAF, and IDS alerts for the exploit pattern |
| Web shells on the server | File integrity monitoring and unusual processes started by the web server |
| Credentials in plain-text files | Logins to many databases from one account, and alerts on lateral movement between segments |
| Data theft over encrypted traffic | Database query volume and outbound traffic, plus health checks on the inspection tool, including alerts when its certificate is about to expire |

## How This Connects to My Other Labs

- **Patching and system hygiene:** [Windows & Linux Admin Labs](../cybersecurity-windows-linux-admin-labs/)
- **Network segmentation and firewall rules:** [Network Design & Firewall Security Lab](../network-design-and-firewall-security-lab/)
- **A structured response process:** [Incident Response & Digital Forensics Plan](../incident-response-and-forensics-plan/)

## References

1. U.S. House of Representatives, Committee on Oversight and Government Reform. (2018, December). [*The Equifax Data Breach: Majority Staff Report.*](https://oversight.house.gov/wp-content/uploads/2018/12/Equifax-Report.pdf)
2. Federal Trade Commission. (2019, July 22). [*Equifax to Pay $575 Million as Part of Settlement with FTC, CFPB, and States Related to 2017 Data Breach.*](https://www.ftc.gov/news-events/news/press-releases/2019/07/equifax-pay-575-million-part-settlement-ftc-cfpb-states-related-2017-data-breach)

---

## What I Learned

- How one known, unpatched vulnerability can lead to a major breach
- Why detection depends on tools being maintained, not just installed
- How to connect technical failures to business, legal, and reputational impact
- How to turn lessons learned into clear, actionable recommendations

*This project was provided by IBM. This analysis is my own work and wording, based on public sources.*
