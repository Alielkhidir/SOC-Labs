# Case Study: The 2017 Equifax Data Breach

Final project from the IBM Cybersecurity Capstone course (Coursera). I analyzed a real-world data breach using a standard case study template: root cause, actions taken, effectiveness, successes and failures, impact, lessons learned, recommendations and conclusion.

## Skills demonstrated
- Case study analysis and structured security reporting
- Vulnerability and patch management analysis
- Incident response evaluation (detection, containment, disclosure)
- Governance, risk and compliance thinking
- Translating technical failures into business impact and actionable recommendations

---

## Introduction
The 2017 Equifax breach exposed the personal data of about 147 million people, including Social Security numbers, birth dates and addresses. Attackers exploited a known flaw in the Apache Struts web framework (CVE-2017-5638) that Equifax had not patched, and they stayed inside the network for 76 days before being detected. The case highlights failures in vulnerability management, governance, monitoring and data protection. It led to a settlement of at least $575 million, executive departures and a lasting loss of public trust. It remains one of the clearest real-world examples of how delayed patching and weak oversight can turn one unpatched system into a company-wide crisis.

## Key timeline

| Date (2017) | Event |
|---|---|
| March 7 | Apache Struts flaw CVE-2017-5638 is disclosed and a patch is released |
| March 9 | Equifax's internal security team circulates the alert, but the vulnerable system is not patched |
| May 13 | Attackers first gain access through the unpatched web application |
| July 29 | Equifax notices suspicious traffic after fixing its inspection tool |
| July 30 | The attacker's access is blocked |
| September 7 | Equifax publicly announces the breach |

---

## Case study analysis

### 1. Root causes
1. **Failure to patch a known vulnerability.** A fix for CVE-2017-5638 had been available for roughly two months. Equifax received alerts but never patched the affected internet-facing system, and its vulnerability scan did not detect the exposure.
2. **Weak ownership and communication.** The patch alert did not reach the people responsible for the vulnerable system, and there was no clear accountability or reliable asset inventory to make sure critical patches were applied.

### 2. Actions taken
1. **Incident response and containment.** Once the suspicious activity was found, the security team blocked the traffic, took the affected application offline and brought in an outside cybersecurity firm and law enforcement to investigate.
2. **Disclosure and remediation.** Equifax notified regulators and the public and offered affected people identity protection and credit monitoring. A later settlement also required it to build a comprehensive information security program.

### 3. Effectiveness and timeliness
- **Incident response (effective but late).** Blocking the attacker the day after discovery worked. However, the attackers had already been inside for 76 days. The monitoring tool that should have exposed the data theft had an expired certificate and could not inspect encrypted traffic, so detection happened by chance, not by design.
- **Disclosure (slow and uneven).** The public announcement came about six weeks after discovery. The consumer response was criticized for confusing messaging and website problems, and credit monitoring did not fully address the long-term identity theft risk of leaked Social Security numbers.

### 4. Successes, gaps and failures
- **Success:** After detection, Equifax contained the attack quickly, cooperated with regulators and law enforcement, and later invested heavily in security improvements.
- **Gap:** Weak patch management, sensitive data stored without adequate protection (including some unencrypted data and credentials left in accessible locations), and poor network segmentation that let attackers move between systems.
- **Failure:** Not detecting the intrusion for 76 days because the inspection tool was not working.

### 5. Impact on the organization
1. **Financial and regulatory (short and long term):** A settlement of at least $575 million with the FTC, CFPB and states, plus legal, investigation and remediation costs, and the departure of senior executives including the CEO, CIO and CISO.
2. **Reputational and strategic:** A severe loss of consumer and partner trust, closer regulatory scrutiny and a lasting association with one of the largest breaches in history, affecting the company's core business of handling sensitive data.

### 6. Lessons learned
1. **Patching needs ownership, tracking and verification.** Knowing about a vulnerability is not enough. Organizations need a complete asset inventory, clear responsibility for each system and scans that confirm the patch was applied.
2. **Defense in depth and working monitoring matter.** Encryption, segmentation and least-privilege access limit the damage once attackers get in, and detection tools must be maintained (for example, certificates renewed) or they give a false sense of security.

### 7. Recommendations for future actions
1. **Do:** Implement automated patch and vulnerability management with a maintained asset inventory, fixed deadlines for critical CVEs and follow-up scans.
   **Avoid:** Relying on emailed alerts and manual processes for critical fixes.
2. **Do:** Adopt a zero-trust architecture with network segmentation, encryption of sensitive data, strict access control and regular health checks on monitoring tools.
   **Avoid:** Flat networks and implicit trust of internal systems.

### 8. Conclusion
The Equifax breach shows that a single unpatched system, combined with weak governance and broken monitoring, can cause catastrophic harm at massive scale. The pattern is common across major breaches: the root cause is often a known, fixable weakness rather than a sophisticated attack. For organizations that hold sensitive data, strong architecture, proactive policies, accountable patching and real-time monitoring are essential, and regulators now expect them.

---

## References
1. U.S. House of Representatives, Committee on Oversight and Government Reform. (2018, December). *The Equifax Data Breach: Majority Staff Report.*
2. Federal Trade Commission. (2019, July 22). *Equifax to Pay $575 Million as Part of Settlement with FTC, CFPB, and States Related to 2017 Data Breach.*

---

## What I learned
- How one known, unpatched vulnerability can lead to a major breach
- Why detection depends on tools being maintained, not just installed
- How to connect technical failures to business, legal and reputational impact
- How to turn lessons learned into clear, actionable recommendations

*This project provided by IBM. This analysis is my own work and wording, based on public sources.*
