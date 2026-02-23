# 🛡️ Room: Defensive Security Intro
**Platform:** TryHackMe
**Date:** Feb 2026
**Topic:** Security Operations Center (SOC) & Incident Response

## 🚀 Objective
I transitioned from an offensive mindset (Red Team) to a defensive mindset which is the (Blue Team). The goal of this lab was to utilize a simulated Security Information and Event Management (SIEM) dashboard to detect, analyze, and mitigate an active Web Discovery Attack against a financial institution's web application.

## 💻 The Incident
- **Alert Triggered:** Web Discovery Attack (Directory Enumeration).
- **Attacker Behavior:** An adversary was utilizing automated scanning tools to brute-force hidden administrative endpoints on the web server. 
- **Indicator of Compromise (IOC):** Malicious traffic originating from IP `32.122.195.63`.

## 🛠️ Incident Response & Mitigation Actions
To properly secure the application, I implemented a "Defense in Depth" strategy rather than relying on a single security control:

1. **Immediate Triage (IP Blocking):** - I configured the perimeter firewall to drop all inbound traffic from the offending source IP address (`32.122.195.63`) for 72 hours. This neutralized the immediate threat.

2. **Traffic Shaping (Rate Limiting):**
   - Because attackers frequently cycle through proxy or VPN IP addresses, IP blocking is insufficient!. I implemented Rate Limiting on the admin endpoints, restricting traffic to `50 requests per 60 seconds`.
   - **Result:** This allows legitimate human traffic to pass smoothly while effectively breaking the functionality of high-speed automated brute-forcing tools like DirBuster or ffuf.

3. **Proactive Defense (WAF Configuration):**
   - Finally, I updated the Web Application Firewall (WAF) ruleset to permanently block "suspicious enumeration attempts." 
   - **Result:** The WAF will now inspect HTTP requests for known automated scanner signatures, providing long-term protection against similar attack vectors regardless of the source IP.

## 🔑 Key Takeaway for Interviews
Effective defensive security requires a layered approach (Defense in Depth). Stopping an attack isn't just about banning an IP address; it requires implementing structural limits (like rate limiting) and behavioral analysis (WAF rules) to protect the network from future iterations of the same attack.
