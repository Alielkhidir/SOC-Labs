<a href="https://github.com/Alielkhidir/SOC-Labs"><img src="../badges/back-to-soc-labs.png" alt="Back to SOC Labs" height="30"></a>

# Network Design & Firewall Security Lab

Planned a network for a fictional company, "TechSafe, Ltd.", then analyzed web traffic and enforced security policy with host firewall rules. The lab is part of the IBM Cybersecurity Analyst program, and this page describes my own work and results.

| | |
|---|---|
| **Level** | Beginner |
| **Date** | Aug 2025 |
| **Source** | IBM Cybersecurity Analyst Professional Certificate |
| **Environment** | Windows 10 |
| **Tools** | Wireshark, Windows Defender Firewall with Advanced Security, Command Prompt (FTP client), network diagramming |

## IBM Badge Earned

<table>
  <tr>
    <td width="150" align="center">
      <a href="https://www.credly.com/badges/366f3efe-ab08-4266-8f07-946e59dec8e8"><img src="../badge/ibm-network-security.png" alt="IBM badge: Network Security & Database Vulnerabilities" width="130"></a>
    </td>
    <td>
      <b>Network Security & Database Vulnerabilities</b><br>
      Issued by IBM through Coursera on 23 Aug 2025. This lab was part of the coursework for earning this badge.<br><br>
      <a href="https://www.credly.com/badges/366f3efe-ab08-4266-8f07-946e59dec8e8">Verify on Credly →</a>
    </td>
  </tr>
</table>

## Results at a Glance

| # | Task | Outcome | How I verified it |
|---|---|---|---|
| 1 | Network design | One router and one switch connected to three VLAN subnets (Administration, Sales, IT) | Network diagram |
| 2 | Subnetting | Three /26 blocks, 62 usable hosts each | Subnet table |
| 3 | HTTPS traffic analysis | Isolated TLS traffic to Google services in Wireshark | Display filter and packet details |
| 4 | Block outbound FTP | Rule "FTP block" created | Connection worked before the rule and failed after |
| 5 | Block outbound HTTP | Rule blocking TCP port 80 created | `httpforever.com` loaded before the rule and failed after |

## Skills Demonstrated

- Network design with VLAN-based subnets (router, switch, three departments)
- IPv4 subnetting with CIDR and subnet masks
- Packet capture and display filtering with Wireshark
- Outbound firewall rules in Windows Defender Firewall with Advanced Security
- Testing and verifying security controls (test before, apply, test after)

---

## Task 1: Network Design with Subnets

Designed a network with one router, one switch, and three subnets (Administration, Sales, IT). The router connects to the switch over an 802.1Q trunk, and each department sits in its own VLAN so traffic is segmented.

**Why it matters:** Segmentation limits how far an attacker can move. If one department is compromised, the other VLANs are not automatically exposed.

<img src="screenshots/1.PNG" alt="Network diagram with router, switch and three subnets" width="700">

*Router and switch connected to the Administration, Sales, and IT subnets.*

## Task 2: Subnet Addresses and Masks

Each department was given a /26 block (64 addresses, 62 usable hosts). The addresses come from the 198.51.100.0 range, which is reserved for documentation and examples.

| Subnet | Network address | Mask | Usable host range | Broadcast |
|---|---|---|---|---|
| Administration | 198.51.100.0/26 | 255.255.255.192 | .1 – .62 | 198.51.100.63 |
| Sales | 198.51.100.64/26 | 255.255.255.192 | .65 – .126 | 198.51.100.127 |
| IT | 198.51.100.128/26 | 255.255.255.192 | .129 – .190 | 198.51.100.191 |

<img src="screenshots/2.PNG" alt="Subnet plan table" width="700">

*Subnet plan generated for later reference.*

## Task 3: HTTPS Traffic Analysis with Wireshark

Captured traffic on my Wi-Fi interface and used the display filter `tcp.port==443 and tcp contains "google"` to isolate HTTPS (TLS) packets to Google services, then inspected the packet details and bytes. The server name is visible in the TLS handshake even though the payload is encrypted.

**Why it matters:** Even when traffic is encrypted, metadata such as the server name and destination still show who a host is talking to. That is often enough to spot suspicious connections.

<img src="screenshots/3.PNG" alt="Wireshark with filtered HTTPS packets and details expanded" width="700">

*Filtered HTTPS packets with frame, Ethernet, IP, and TCP details expanded.*

## Task 4: Firewall Rules in Windows Defender Firewall

For each protocol I followed the same method: confirm it works, create the rule, then confirm it is blocked.

**Why it matters:** Testing before and after proves the rule is what changed the result. Blocking FTP also stops a protocol that sends credentials in plain text, and blocking HTTP pushes users toward HTTPS.

### 4.1 Block FTP

Confirmed the baseline by reaching the public test server `ftp.dlptest.com`, created an outbound rule named **FTP block**, then tested again.

<img src="screenshots/5.PNG" alt="FTP block rule in Outbound Rules" width="700">

*The "FTP block" rule in Outbound Rules: enabled, action Block.*

<table>
  <tr>
    <td align="center"><img src="screenshots/4.PNG" alt="FTP connection established before the rule" width="400"><br><i>Before: connection established and FTP login prompt displayed.</i></td>
    <td align="center"><img src="screenshots/6.PNG" alt="FTP connection failing after the rule" width="400"><br><i>After: the connection to ftp.dlptest.com fails.</i></td>
  </tr>
</table>

### 4.2 Block HTTP

Confirmed that `http://httpforever.com` loaded, created an outbound rule blocking TCP port 80, then tested again.

<img src="screenshots/8.PNG" alt="Outbound rule blocking TCP port 80" width="700">

*Outbound rule blocking TCP port 80.*

<table>
  <tr>
    <td align="center"><img src="screenshots/7.PNG" alt="httpforever.com loading before the rule" width="400"><br><i>Before: the site loads normally.</i></td>
    <td align="center"><img src="screenshots/9.PNG" alt="httpforever.com unreachable after the rule" width="400"><br><i>After: the site can no longer be reached.</i></td>
  </tr>
</table>

---

## The SOC Perspective

I did not collect these logs in this lab. This table is what an analyst would look for when working with the same kinds of activity, and it is what I plan to practice next.

| Activity in this lab | Where it shows up |
|---|---|
| Firewall rule created | Windows Security log, Event ID 4946 (needs the audit policy enabled) |
| Outbound connection blocked by the firewall | Windows Security log, Event ID 5157 (needs "Filtering Platform" auditing enabled) |
| Encrypted web traffic | Network captures and logs: destination, server name, and volume |
| Plain-text protocols (FTP, HTTP) | Network captures: credentials and content visible to anyone capturing |
| Segmented VLANs | Firewall and flow logs show traffic crossing between departments |

## Limits of This Lab

- The rules protect one Windows host only. In a real network, the same policy would also be enforced on the perimeter or an internal firewall.
- Blocking a protocol by port is a basic control. Traffic can use other ports, so monitoring still matters.

## What I Learned

- How VLANs and subnets segment departments, and how to size /26 blocks
- How to read encrypted traffic metadata in Wireshark with display filters
- How to enforce and verify security policy with firewall rules: test before, apply, test after

## Next Steps

- Find the matching firewall events in Event Viewer after creating a rule
- Capture a plain-text protocol in Wireshark and compare it with the same traffic over TLS
- Search firewall logs in Splunk, as part of the planned SOC Operations labs

*Lab provided by IBM. This page describes my own work and results.*
