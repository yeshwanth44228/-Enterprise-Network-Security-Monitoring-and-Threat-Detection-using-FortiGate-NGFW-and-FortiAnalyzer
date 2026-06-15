# Implementation Guide

This guide explains how to build the MITRE ATT&CK-based SOC detection engineering lab.

## Phase 1: Create Azure Monitoring Workspace

1. Sign in to the Azure portal.
2. Create or use an existing Resource Group.
3. Create a Log Analytics Workspace.
4. Enable Microsoft Sentinel on that workspace.
5. Set cost controls by keeping test scope small and shutting down virtual machines after testing.

Evidence to capture:

- Log Analytics workspace overview.
- Microsoft Sentinel overview page.
- Resource group showing the lab resources.

## Phase 2: Create Test Machines

Create at least one Windows VM and one attacker/test machine.

Recommended lab systems:

| System | Purpose |
| --- | --- |
| Windows VM | Victim endpoint and Windows event source |
| Ubuntu/Kali VM | Controlled scan and test activity |
| FortiGate/FortiAnalyzer lab | Network security telemetry and firewall evidence |

Evidence to capture:

- Windows VM overview.
- Test VM overview.
- Network layout or diagram.

## Phase 3: Enable Windows Log Collection

Connect Windows Security Events to Microsoft Sentinel.

Important event IDs:

| Event ID | Meaning |
| --- | --- |
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4672 | Special privileges assigned |
| 4688 | Process creation |
| 4720 | User account created |
| 4732 | User added to local group |

For process command-line visibility, enable process creation auditing and command-line logging on the Windows VM.

Evidence to capture:

- Data connector page.
- Logs showing `SecurityEvent` data.
- Example query result for Event ID 4625.

## Phase 4: Add FortiGate or FortiAnalyzer Telemetry

Use one of these paths:

| Option | Description |
| --- | --- |
| Full integration | Forward FortiGate logs to Sentinel using Syslog/CEF |
| Existing lab evidence | Use the FortiGate/FortiAnalyzer screenshots from the previous project |
| Hybrid evidence | Use existing screenshots now and add live Sentinel ingestion later |

Recommended Sentinel table for FortiGate CEF logs:

```text
CommonSecurityLog
```

Evidence to capture:

- FortiGate log forwarding settings.
- FortiAnalyzer dashboard.
- Sentinel query showing Fortinet logs, if live ingestion is configured.

## Phase 5: Generate Controlled Test Activity

Perform safe tests only in the lab.

| Scenario | Test Action | Expected Detection |
| --- | --- | --- |
| Brute force | Multiple failed login attempts | Brute-force KQL rule |
| Suspicious PowerShell | Run encoded or download-style PowerShell command in a safe test | Suspicious PowerShell rule |
| Port scan | Run Nmap against a lab host | Port scan KQL rule |
| Privilege escalation | Create user or add user to Administrators group | Privilege escalation rule |
| Lateral movement | RDP login from test VM | RDP lateral movement rule |

Evidence to capture:

- Test command or activity.
- Log result in Sentinel.
- Analytics rule alert.
- Incident page.

## Phase 6: Create Analytics Rules

Use the KQL files in `detections/kql`.

For each detection:

1. Open Microsoft Sentinel.
2. Go to Analytics.
3. Create scheduled query rule.
4. Paste the relevant KQL.
5. Set entity mappings.
6. Set severity.
7. Enable incident creation.
8. Run the query and validate output.

Recommended severity:

| Detection | Severity |
| --- | --- |
| Brute force | Medium |
| Suspicious PowerShell | High |
| Port scan | Medium |
| Privilege escalation | High |
| RDP lateral movement | Medium or High |

## Phase 7: Build SOAR Enrichment Playbook

Create a Logic Apps playbook that enriches incident IP addresses.

Suggested workflow:

```text
Microsoft Sentinel incident created
-> Extract IP entity
-> Send IP to reputation service
-> Add enrichment result as incident comment
-> Assign owner or update severity
```

Evidence to capture:

- Logic App designer.
- Trigger configuration.
- HTTP action.
- Incident comment showing enrichment result.

## Phase 8: Create Dashboard and Final Report

Create a Sentinel workbook or dashboard showing:

- Alerts by severity.
- Top source IPs.
- Top users.
- Top MITRE tactics.
- Incident status.
- Detection coverage.

Complete the final report using `docs/report-template.md`.
