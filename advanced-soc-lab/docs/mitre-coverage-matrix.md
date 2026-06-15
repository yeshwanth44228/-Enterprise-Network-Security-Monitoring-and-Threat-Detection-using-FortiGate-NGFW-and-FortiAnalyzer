# MITRE ATT&CK Coverage Matrix

Use this table in the final report to show detection engineering coverage.

| Detection | ATT&CK Tactic | Technique | Log Source | KQL File | Validation Evidence |
| --- | --- | --- | --- | --- | --- |
| Brute-force login attempts | Credential Access | T1110 - Brute Force | Windows Security Events | `01-brute-force-logon.kql` | Screenshot pending |
| Suspicious PowerShell execution | Execution | T1059.001 - PowerShell | Windows Process Creation / Sysmon | `02-suspicious-powershell.kql` | Screenshot pending |
| Port scanning / service discovery | Discovery | T1046 - Network Service Discovery | FortiGate CEF / Sysmon Network | `03-fortigate-port-scan.kql` | Screenshot pending |
| Privilege escalation indicators | Privilege Escalation | T1068 - Exploitation for Privilege Escalation / T1078 - Valid Accounts | Windows Security Events | `04-privilege-escalation.kql` | Screenshot pending |
| RDP lateral movement | Lateral Movement | T1021.001 - Remote Desktop Protocol | Windows Security Events | `05-rdp-lateral-movement.kql` | Screenshot pending |

## Detection Quality Checklist

- [ ] Detection has a clear threat objective.
- [ ] Detection has a defined log source.
- [ ] Detection maps to at least one MITRE ATT&CK technique.
- [ ] Detection has tested KQL.
- [ ] Detection has a screenshot of query output.
- [ ] Detection has a screenshot of Sentinel incident creation.
- [ ] Detection includes response steps.
- [ ] False-positive tuning notes are documented.

## False Positive Notes

Use this section during testing.

| Detection | Possible False Positive | Tuning Idea |
| --- | --- | --- |
| Brute force | User mistypes password repeatedly | Exclude helpdesk reset windows or known test accounts |
| Suspicious PowerShell | Admin scripts | Allow known script paths or admin automation accounts |
| Port scan | Authorized vulnerability scanner | Allow scanner IPs during approved scan windows |
| Privilege escalation | Approved admin change | Exclude change-management windows |
| RDP lateral movement | Normal admin access | Allow known jump boxes and admin accounts |
