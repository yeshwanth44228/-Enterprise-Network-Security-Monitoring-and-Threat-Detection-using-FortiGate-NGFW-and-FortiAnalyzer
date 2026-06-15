# Incident Response Playbook

This playbook describes how to respond to security events detected by FortiGate and investigated in FortiAnalyzer.

## Severity Levels

| Severity | Description | Example |
| --- | --- | --- |
| Critical | Confirmed or highly likely compromise | Exploit attempt against vulnerable public service |
| High | Strong attack indicator requiring immediate review | Repeated port scan or high-severity IPS hit |
| Medium | Suspicious or policy-violating behavior | Blocked restricted category or repeated denies |
| Low | Informational event requiring trend review | Single denied packet or expected web block |

## Triage Workflow

1. Open the FortiAnalyzer event or log entry.
2. Record event time, source IP, destination IP, user, policy, action, and severity.
3. Determine whether the action was allowed, denied, blocked, reset, or monitored.
4. Search for related logs in a 15- to 30-minute window around the event.
5. Decide whether the activity is authorized, misconfigured, suspicious, or malicious.

## Containment Actions

| Scenario | Containment |
| --- | --- |
| Unauthorized scanner | Block source IP, isolate endpoint, notify asset owner |
| High-severity IPS event | Block source, review target vulnerability, preserve logs |
| Repeated web policy violation | Notify user/manager, review user activity, keep category blocked |
| External probing | Restrict exposed services, apply geo/IP block if appropriate |
| Internal lateral movement | Isolate source endpoint and start endpoint investigation |

## Investigation Checklist

- Source IP and hostname identified.
- Destination IP and asset owner identified.
- User identity confirmed if authentication logs are available.
- Related traffic logs reviewed.
- Related IPS or web filter logs reviewed.
- Firewall policy matched by the event identified.
- Business justification checked.
- Action taken and evidence documented.

## Evidence to Preserve

- FortiAnalyzer log export or screenshot.
- Firewall policy name and ID.
- IPS signature name and severity, if applicable.
- URL/category and web filter action, if applicable.
- Source and destination details.
- Timeline of related events.
- Final response decision.

## Closure Criteria

An event can be closed when:

- The activity has been confirmed as authorized, benign, contained, or remediated.
- Required firewall or IPS policy changes are complete.
- Asset owner notification is complete if needed.
- Evidence is attached to the incident record.
- Detection tuning recommendations are documented.

## Post-Incident Improvements

- Add a FortiAnalyzer event handler for repeated patterns.
- Create a scheduled report for recurring events.
- Tune IPS action from monitor to block for confirmed malicious signatures.
- Update firewall policy comments and object names.
- Add user awareness or policy communication for repeated web violations.
