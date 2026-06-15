# FortiGate Baseline Configuration Notes

These notes summarize the FortiGate configuration logic used in the project. Values such as interface names, object names, and IP addresses should be adapted to the actual deployment.

## Policy Design

Recommended policy structure:

| Policy | Source | Destination | Service | Security Profiles | Logging |
| --- | --- | --- | --- | --- | --- |
| User internet access | User LAN | Internet | HTTP/HTTPS/DNS/NTP as needed | IPS, Web Filter | All sessions or security events |
| Internal service access | User LAN | Internal servers | Required application ports | IPS | Security events |
| Default deny | Any | Any | Any | None | Denied traffic |

## Security Profile Placement

Apply profiles where traffic must be inspected:

- IPS profile on internet-bound and server-bound traffic.
- Web filter profile on user internet access.
- Antivirus and application control may be added as future enhancements.
- SSL inspection may be added in a scoped deployment after certificate and privacy review.

## Logging Guidance

Enable logging for:

- Allowed traffic that carries user activity.
- Denied traffic that may indicate probing.
- IPS events.
- Web filtering events.
- Administrative and system events.

## FortiAnalyzer Integration

FortiGate should forward logs to FortiAnalyzer so analysts can investigate events centrally. Confirm:

- FortiAnalyzer IP address is reachable from FortiGate.
- FortiGate is authorized or registered on FortiAnalyzer.
- Traffic, web filter, and IPS logs are arriving.
- Device time is synchronized.

## Example Policy Logic

This is a conceptual policy model, not a copy-paste configuration:

```text
Policy Name: User-to-Internet-Secure
Incoming Interface: LAN
Outgoing Interface: WAN
Source: Internal_Users
Destination: all
Service: HTTP, HTTPS, DNS, NTP
Action: Accept
NAT: Enabled
Security Profiles: IPS_Profile, Web_Filter_Profile
Log: Enabled
```

## Hardening Recommendations

- Restrict administrative access to trusted management networks.
- Disable unused administrative services.
- Use strong administrator authentication and role-based access.
- Keep FortiGuard services and firmware updated.
- Review policy hit counts and remove unused rules.
- Back up configuration after major changes.
- Document each rule with owner, purpose, and review date.
