# Presentation Outline

## Slide 1: Title

**Enterprise Network Security Monitoring and Threat Detection using FortiGate NGFW and FortiAnalyzer**

Presenter name, institution/organization, and date.

## Slide 2: Problem Statement

Enterprise networks need centralized visibility to detect scans, policy violations, and suspicious traffic. Without log centralization, security teams may miss early attack indicators.

## Slide 3: Project Objectives

- Configure FortiGate firewall policies.
- Enable IPS and web filtering.
- Forward logs to FortiAnalyzer.
- Validate detection with test traffic.
- Generate dashboards and reports.

## Slide 4: Lab Architecture

Show the monitoring flow:

Client endpoint -> FortiGate NGFW -> Internet/Internal Services -> FortiAnalyzer -> Dashboards/Reports.

## Slide 5: Firewall Policy

Use screenshots:

- `01-firewall-policy-overview.png`
- `02-firewall-policy-details.png`

Explain how the firewall policy controls and logs traffic.

## Slide 6: IPS Configuration

Use screenshots:

- `03-ips-sensor-list.png`
- `04-ips-sensor-configuration.png`

Explain how IPS signatures support threat detection.

## Slide 7: FortiAnalyzer Integration

Use screenshots:

- `05-fortianalyzer-log-settings.png`
- `06-fortianalyzer-dashboard.png`

Explain centralized logging and dashboard visibility.

## Slide 8: Detection Test - Nmap Scan

Use screenshot:

- `07-nmap-port-scan-detection.png`

Explain why port scanning is a reconnaissance indicator.

## Slide 9: Web Filtering Control

Use screenshots:

- `08-web-filter-profile.png`
- `09-social-networking-block-rule.png`
- `10-facebook-access-blocked.png`

Explain acceptable-use enforcement and policy validation.

## Slide 10: Reporting

Use screenshot:

- `11-report-definitions.png`

Explain scheduled reports for operations, compliance, and management review.

## Slide 11: Results

- Firewall policies configured.
- IPS profile prepared.
- FortiAnalyzer logging enabled.
- Dashboard visibility confirmed.
- Nmap scan test performed.
- Social networking access blocked.
- Reports prepared.

## Slide 12: Future Scope

- Event handlers and email alerts.
- Ticketing integration.
- SSL inspection for selected traffic.
- Additional threat scenarios.
- Compliance report mapping.

## Slide 13: Conclusion

FortiGate and FortiAnalyzer provide a practical enterprise monitoring foundation by combining prevention, detection, investigation, and reporting.
