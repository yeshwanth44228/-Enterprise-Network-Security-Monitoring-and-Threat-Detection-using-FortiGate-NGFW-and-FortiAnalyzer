# Detection Use Cases

This document defines practical detection use cases for a FortiGate and FortiAnalyzer monitoring environment.

## Use Case 1: Network Port Scan

**Goal:** Detect reconnaissance activity where a host probes multiple ports or services.

**Relevant logs:**

- FortiGate traffic logs
- FortiGate IPS logs
- FortiAnalyzer event logs

**Indicators:**

- One source IP attempts connections to many destination ports.
- Multiple denied or reset sessions occur in a short period.
- Traffic targets administrative ports such as SSH, HTTPS management, FTP, SIP, or database services.
- IPS signatures related to scanning or reconnaissance are triggered.

**Investigation steps:**

1. Identify the source IP, destination IP, and time window.
2. Check whether the source belongs to an authorized vulnerability scanner.
3. Review the destination asset and exposed services.
4. Search for other events from the same source.
5. Determine whether the scan was internal, external, or lateral.

**Response actions:**

- If authorized, document the scan window and scanner owner.
- If unauthorized, block the source IP or isolate the endpoint.
- Review firewall exposure for the scanned services.
- Create or tune an event handler for repeated scanning behavior.

## Use Case 2: Web Filtering Policy Violation

**Goal:** Detect and document access attempts to blocked web categories.

**Relevant logs:**

- Web filter logs
- Traffic logs
- FortiAnalyzer reports

**Indicators:**

- Action is blocked by the web filter profile.
- Category matches a restricted class such as social networking, gambling, proxy avoidance, or malware.
- Same user or endpoint repeatedly attempts access.

**Investigation steps:**

1. Identify the user, source IP, URL, category, and policy.
2. Confirm whether the block is expected under acceptable-use policy.
3. Check for repeated attempts or access through alternate domains.
4. Review whether the endpoint attempted proxy or anonymizer services.

**Response actions:**

- Notify the user or asset owner if repeated violations occur.
- Keep the category blocked if aligned with policy.
- Add URL exceptions only when approved by business owners.
- Include recurring violations in weekly reports.

## Use Case 3: IPS Signature Match

**Goal:** Identify exploit attempts, suspicious payloads, or known attack patterns.

**Relevant logs:**

- IPS logs
- Traffic logs
- FortiAnalyzer incident views

**Indicators:**

- IPS event severity is high or critical.
- Action is blocked, reset, or monitored.
- Signature relates to exploit, malware, command execution, or vulnerability scanning.

**Investigation steps:**

1. Review signature name, severity, CVE mapping if available, and action.
2. Identify source, destination, service, and direction.
3. Check whether the target system is vulnerable.
4. Search for repeated attempts from the same source or against the same asset.

**Response actions:**

- Block or quarantine malicious sources.
- Patch the targeted system if vulnerable.
- Increase logging or enable blocking for confirmed high-confidence signatures.
- Escalate high and critical events to incident response.

## Use Case 4: Repeated Denied Traffic

**Goal:** Detect repeated blocked attempts that may indicate probing or misconfiguration.

**Relevant logs:**

- Deny traffic logs
- Local-in policy logs
- FortiAnalyzer reports

**Indicators:**

- High number of denied attempts from one source.
- Attempts target sensitive services or management interfaces.
- Activity occurs outside normal business hours.

**Investigation steps:**

1. Group denied traffic by source, destination, service, and policy.
2. Confirm whether the source is expected to access the destination.
3. Review whether the blocked service should be exposed.
4. Check for related IPS or threat events.

**Response actions:**

- Create a more specific block rule if needed.
- Restrict management services to trusted networks.
- Contact the owner of misconfigured internal systems.
- Escalate suspicious external activity.

## Use Case 5: Security Reporting and Trend Review

**Goal:** Use reports to identify recurring risk patterns.

**Relevant logs:**

- Traffic logs
- Web filter logs
- IPS logs
- System event logs

**Metrics to track:**

- Top blocked categories.
- Top IPS signatures.
- Top denied sources.
- Top destination services.
- Policy hit counts.
- Event volume by severity.

**Response actions:**

- Tune noisy policies or signatures.
- Harden frequently targeted services.
- Update acceptable-use policy exceptions.
- Brief management on recurring security trends.
