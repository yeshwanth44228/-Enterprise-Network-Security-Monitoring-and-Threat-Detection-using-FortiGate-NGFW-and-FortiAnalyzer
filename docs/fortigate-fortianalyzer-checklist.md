# FortiGate and FortiAnalyzer Checklist

Use this checklist to validate the project configuration and to guide future deployment work.

## FortiGate Firewall Policy

- [ ] Firewall policies use clear names and comments.
- [ ] Source and destination interfaces are correct.
- [ ] Source and destination objects are specific.
- [ ] Services are limited to business requirements.
- [ ] NAT is enabled only where required.
- [ ] Logging is enabled for security-relevant policies.
- [ ] IPS profile is attached to inspected traffic.
- [ ] Web filter profile is attached to user internet traffic.
- [ ] Policy order has been reviewed.

## Intrusion Prevention

- [ ] IPS profile is enabled.
- [ ] Critical and high-severity signatures are reviewed.
- [ ] Initial false-positive tuning is complete.
- [ ] FortiGuard updates are enabled.
- [ ] IPS logs are forwarded to FortiAnalyzer.
- [ ] Blocking mode is enabled for validated high-confidence signatures.

## Web Filtering

- [ ] Web filter profile is enabled.
- [ ] Restricted categories are set to block.
- [ ] Business-required exceptions are documented.
- [ ] Block page is displayed to users.
- [ ] Web filter logs are visible in FortiAnalyzer.
- [ ] Repeated violations are included in reports.

## FortiAnalyzer Logging

- [ ] FortiGate is registered with FortiAnalyzer.
- [ ] Log forwarding is enabled.
- [ ] Traffic logs are received.
- [ ] Security logs are received.
- [ ] Time synchronization is correct on all devices.
- [ ] Device names and administrative domains are organized.
- [ ] Log retention settings match policy requirements.

## Monitoring and Reporting

- [ ] SOC/dashboard widgets are reviewed.
- [ ] Log search works for source IP, destination IP, service, and policy.
- [ ] Daily security event report is configured.
- [ ] Weekly web usage report is configured.
- [ ] IPS event report is configured.
- [ ] Report recipients and schedule are documented.
- [ ] Event handler requirements are identified.

## Validation Tests

- [ ] Controlled Nmap scan generates observable logs.
- [ ] Blocked social networking access displays FortiGuard block page.
- [ ] Denied traffic is visible in log search.
- [ ] IPS activity is visible in FortiAnalyzer.
- [ ] Report definitions are available.
