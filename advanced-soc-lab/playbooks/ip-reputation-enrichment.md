# SOAR Playbook: IP Reputation Enrichment

This playbook design enriches Microsoft Sentinel incidents with IP reputation context.

## Objective

When a Sentinel incident is created, automatically extract IP entities, check reputation, and add the result to the incident as a comment.

## Suggested Workflow

```text
Microsoft Sentinel incident trigger
-> Get incident entities
-> Filter IP entities
-> Query reputation API
-> Parse score/result
-> Add comment to incident
-> Optionally update severity or assign owner
```

## Recommended Services

| Service | Purpose |
| --- | --- |
| Microsoft Sentinel incident trigger | Starts the playbook |
| Logic Apps HTTP action | Calls the reputation service |
| AbuseIPDB or VirusTotal | Enriches IP address context |
| Sentinel comment action | Writes enrichment result into incident |

## Incident Comment Template

```text
IP Reputation Enrichment

Source IP: <ip-address>
Provider: <provider-name>
Reputation Score: <score>
Country: <country>
Abuse Confidence: <score>
Recommendation: Review source activity and block if unauthorized.
```

## Screenshot Evidence

Capture:

- Logic App overview.
- Sentinel incident trigger.
- IP entity extraction step.
- HTTP reputation lookup step.
- Incident comment with enrichment result.

## Resume Value

This playbook shows SOAR knowledge, alert enrichment, automation, and practical Tier-1 SOC response workflow design.
