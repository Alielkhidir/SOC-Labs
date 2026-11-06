# Cybersecurity Windows & Linux Admin Labs

Final project from the IBM Cybersecurity Analyst course (Coursera). I played a junior analyst at a fictional company, "Cyber Secure Inc.", working through six support tickets: three on Windows Server and three on Linux.

## Skills demonstrated
- User and group management (Windows Server, Linux)
- Endpoint protection: Windows Defender updates and scans
- Host firewall configuration (inbound rules)
- Linux command line: `adduser`, `mkdir`, `touch`, `ls`, `apt`, log review
- System patching and update verification

## Tools & environments
Windows Server (Computer Management, Windows Security, Windows Defender Firewall with Advanced Security) · Ubuntu Linux terminal (Skills Network Cloud IDE)

---

## Part 1: Windows tasks

### Ticket 1: Create a user and a group
Created a local user account (`PinkPanther`) with a strong password in Computer Management, then created a group named `Accounting`.
<br><br><br><br><br>
*The new `PinkPanther` account listed under Local Users and Groups > Users.*
![New user](https://github.com/Alielkhidir/SOC-Labs/blob/main/cybersecurity-windows-linux-admin-labs/Screenshots/1.PNG)
<br><br>
*The new `Accounting` group listed under Local Users and Groups > Groups.*
![Accounting group](https://github.com/Alielkhidir/SOC-Labs/blob/main/cybersecurity-windows-linux-admin-labs/Screenshots/2.PNG)
<br><br>
### Ticket 2: Virus & threat protection
Checked for updates in Windows Update / Windows Security, then ran a Quick Scan to confirm the system was protected.
<br><br><br><br><br>
*Windows Update showing pending updates (including the Malicious Software Removal Tool) and the time of the last check.*
![Update check](https://github.com/Alielkhidir/SOC-Labs/blob/main/cybersecurity-windows-linux-admin-labs/Screenshots/3.PNG)
<br><br>
*Quick Scan completed on 8/7/2025: 0 threats found, 27,264 files scanned.*
![Quick scan](https://github.com/Alielkhidir/SOC-Labs/blob/main/cybersecurity-windows-linux-admin-labs/Screenshots/4.PNG)
<br><br>
### Ticket 3: Firewall rule
In Windows Defender Firewall with Advanced Security, I created an inbound rule named **Port 80 Permitted** that allows TCP port 80 on the Domain, Private and Public profiles.
<br><br><br><br><br>
*"Port 80 Permitted" at the top of the Inbound Rules list: enabled, profile All, action Allow.*
![Firewall rule](https://github.com/Alielkhidir/SOC-Labs/blob/main/cybersecurity-windows-linux-admin-labs/Screenshots/5.PNG)
<br><br>

---

## Part 2: Linux tasks

### Ticket 4: Create a user
Used `sudo adduser` to create a user, then verified it with `cat /etc/passwd | grep pinkpanther`.

![Linux user](https://github.com/Alielkhidir/SOC-Labs/blob/main/cybersecurity-windows-linux-admin-labs/Screenshots/6.PNG)
*The account already existed from earlier in the session (hence the "already exists" message); the `/etc/passwd` entry confirms UID 1001, its home directory and its `/bin/bash` shell.*

### Ticket 5: Files and folders
Created the `accounting` and `payroll` directories with `mkdir`, then created a `best practices` file inside `accounting` with `touch`.

![Folders](https://github.com/Alielkhidir/SOC-Labs/blob/main/cybersecurity-windows-linux-admin-labs/Screenshots/7.PNG)
*`mkdir accounting payroll` followed by `ls -l` confirming both folders.*

![File](https://github.com/Alielkhidir/SOC-Labs/blob/main/cybersecurity-windows-linux-admin-labs/Screenshots/8.PNG)
*`ls -l accounting` showing the new `best practices` file.*

### Ticket 6: System updates
Ran `sudo apt update` and `sudo apt upgrade`, then reviewed recent package activity with `less /var/log/dpkg.log`.

![Update log](https://github.com/Alielkhidir/SOC-Labs/blob/main/cybersecurity-windows-linux-admin-labs/Screenshots/9.PNG)
*The dpkg log showing packages being installed, unpacked and configured (e.g. `base-passwd`, `base-files`, `dpkg`).*

---

## What I learned
- Managing local identities and groups on both Windows and Linux
- Why up-to-date endpoint protection and a scoped firewall rule matter
- How to verify changes (via `/etc/passwd`, `ls -l`, and update logs) instead of assuming they worked

*Lab provided by IBM via Coursera. This README describes my own work and results.*
