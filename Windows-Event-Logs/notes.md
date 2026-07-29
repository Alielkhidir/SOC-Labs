# Windows Event Logs Notes

## Important Event IDs

### Authentication

| Event ID | Description |
|----------|-------------|
| 4624 | Successful Logon |
| 4625 | Failed Logon |
| 4634 | Logoff |
| 4648 | Logon using explicit credentials |

---

## Investigation Notes

### Questions to Answer

- Who logged in?
- From where?
- When did it happen?
- Was it expected behavior?

---

## Useful Commands

```powershell
Get-WinEvent -LogName Security
```

---

## Tools

- Windows Event Viewer
- PowerShell
- Sysmon
- SIEM platforms

---

## MITRE ATT&CK

- T1078 - Valid Accounts
- T1110 - Brute Force
