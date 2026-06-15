# Incident Response Playbook

This playbook supports the detections in the MITRE ATT&CK-based SOC lab.

## Triage Workflow

1. Open the Microsoft Sentinel incident.
2. Confirm severity, title, entities, and alert time.
3. Identify affected user, host, source IP, destination IP, and process details.
4. Review the KQL query result that triggered the incident.
5. Search for related events in a 30-minute window before and after the alert.
6. Map the event to the MITRE ATT&CK tactic and technique.
7. Decide whether the event is benign, suspicious, or confirmed malicious.
8. Document evidence and response actions.

## Detection Response Matrix

| Detection | Immediate Action | Investigation Questions | Containment |
| --- | --- | --- | --- |
| Brute force | Check failed and successful logons | Did the same source later succeed? Is the account sensitive? | Reset password, block IP, require MFA |
| Suspicious PowerShell | Review command line and parent process | Was this admin automation or unknown execution? | Isolate host, collect script, block IOC |
| Port scan | Confirm source and scan scope | Is the source an approved scanner? What ports were targeted? | Block source, restrict exposed services |
| Privilege escalation | Review group/user changes | Who made the change? Was it approved? | Remove unauthorized access, disable account |
| RDP lateral movement | Review source, target, and account | Is this normal admin movement? Any unusual time/location? | Disable account, isolate host, review sessions |

## Evidence Checklist

- [ ] Alert screenshot.
- [ ] Incident screenshot.
- [ ] KQL result screenshot.
- [ ] Source and destination entities.
- [ ] User or account details.
- [ ] MITRE ATT&CK mapping.
- [ ] Containment decision.
- [ ] Final status and closure notes.

## Closure Template

```text
Incident:
Detection:
Severity:
MITRE Technique:
Source:
Destination:
User/Account:
Summary:
Evidence Reviewed:
Action Taken:
False Positive or True Positive:
Closure Reason:
```
