# 🧾 Incident Report: Brute Force Login Attempt

## 📅 Date of Incident:
March 15, 2025

## 🚨 Alert Details:
- **Alert Type:** Multiple Failed Login Attempts
- **Severity:** High
- **Source:** Sumo Logic SIEM
- **Detection Tool:** Cloudflare WAF, Sumo Logic
- **Rule Triggered:** BruteForceLoginDetectionRule
- **Affected Asset:** VPN Gateway (vpn-secure01.internal.local)

---

## 👀 Alert Summary:
- **IP Address Involved:** `185.92.26.45`
- **Target Account:** `user_demo@example.com`
- **Attempt Count:** 102 failed attempts in 4 minutes
- **Geo-location of IP:** Moscow, Russia
- **Initial Detection:** Cloudflare rate-limiting
- **Correlated Alert:** AWS GuardDuty – suspicious login

---

## 🔎 Investigation Steps:

1. **Log Review via Sumo Logic**  
   Identified a pattern of repeated login attempts from a single IP targeting the VPN gateway.

2. **Geo-lookup & Threat Intel**  
   IP `185.92.26.45` marked as malicious on AbuseIPDB.

3. **Account Review**  
   `user_demo@example.com` did **not** log in successfully. No other suspicious behavior tied to the account.

4. **System Health Check**  
   No changes, failed authentication only, no system compromise.

---

## 🛡️ Mitigation Actions:

- 🚫 Blocked IP `185.92.26.45` via Cloudflare & firewall ACL
- 🔐 Forced password reset for `user_demo@example.com`
- 🔄 Enabled stricter rate limits on VPN login interface
- ✅ Verified MFA enabled for all remote users

---

## 📈 Timeline:

| Time (IST)       | Event                                    |
|------------------|-------------------------------------------|
| 09:01 AM         | Alert triggered in Cloudflare             |
| 09:03 AM         | Correlated in Sumo Logic                  |
| 09:06 AM         | Threat Intel Lookup – IP flagged          |
| 09:15 AM         | IP blocked on Cloudflare & firewall       |
| 09:30 AM         | Account reviewed & password reset issued  |

---

## 💡 Lessons Learned:

- 🚀 Add alert enrichment with GeoIP tagging for faster triage
- 🔐 Increase lockout policy for high-value systems
- 📊 Setup dashboard panel for brute force attempts by country

---

## 🧠 Analyst Notes:

This case involved early detection from Cloudflare and showed the value of layered security (WAF + SIEM + Threat Intel). Incident resolved within 30 minutes with no breach.

---

## 🔗 Related Playbooks:
- [🔐 BruteForce Login Playbook](Playbooks/BruteForce-Login-Attack-Playbook.md)
