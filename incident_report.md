# Security Incident Report - yummyrecipesforme.com

## Section 1: Identified Network Protocols
**DNS (Domain Name System)** and **HTTP (Hypertext Transfer Protocol)** were exploited during this incident.

### Evidence from tcpdump logs:
- **DNS Queries:**  
  `14:18:32.195571 IP your.machine.52444 > dns.google.domain: 35084 A? yummyrecipesforme.com. (24)`  
  `14:20:32.195571 IP your.machine.52444 > dns.google.domain: 21899 A? greatrecipesforme.com. (24)`

- **HTTP Connections:**  
  `14:19:36.786501 IP your.machine.36886 > yummyrecipesforme.com.http: Flags [S]...`  
  `14:25:29.576493 IP your.machine.56378 > greatrecipesforme.com.http: Flags [S]...`

## Section 2: Incident Documentation
**Date:** September 10, 2025  
**Affected System:** yummyrecipesforme.com web server

### Summary:
A former employee executed a brute force attack against the administrative account, exploiting a default password. The attacker inserted malicious JavaScript code into the website's source, forcing visitors to download a file disguised as a "browser update." After execution, users were redirected to `greatrecipesforme.com` (IP: `192.0.2.17`), which hosted malware.

### Evidence Sources:
- tcpdump traffic logs showing DNS/HTTP redirection
- Source code analysis confirming malicious JavaScript
- Customer reports to helpdesk
- Failed login attempts to admin panel

### Impact:
- Users exposed to malware
- Brand reputation damage
- Potential financial losses

## Section 3: Security Recommendation
**Implement Two-Factor Authentication (2FA)** for all administrative accounts.

### Rationale:
2FA requires a second authentication factor (e.g., mobile app code) beyond passwords, preventing unauthorized access even if credentials are obtained through brute force attacks. This aligns with NIST guidelines and industry best practices.

### Additional Measures:
- Eliminate default passwords
- Implement account lockouts after multiple failed login attempts
- Regular audit of administrative accounts
