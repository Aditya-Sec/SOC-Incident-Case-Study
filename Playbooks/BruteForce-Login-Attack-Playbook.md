# 🔐 Playbook: Brute Force Login Attack

## 🎯 Objective:
To detect and respond to brute force login attempts against internal or public-facing systems.

---

## 🛠 Tools Involved:
- Kibana
- Sumo Logic
- AWS CloudTrail
- Cloudflare (or firewall logs)
- Endpoint protection (e.g., Symantec)

---

## 📈 Detection:

### ✅ Indicators:
- Repeated failed login attempts from same IP
- High volume of 401/403 HTTP responses
- Unusual login behavior from geo-locations

### 🧪 Detection Sources:
- Sumo Logic: failed login logs
- Cloudflare: rate-limiting triggers
- AWS CloudTrail: `ConsoleLogin` events
- Endpoint logs: multiple password failures

---

## 🧭 Investigation Steps:

1. **Verify alert accuracy**
   - Confirm brute force pattern (e.g., >20 failed attempts in 5 mins)
   - Check if IP is internal or external

2. **Identify target**
   - Which user accounts or systems were targeted?
   - Did any login succeed?

3. **Geo-location & Reputation check**
   - Use IP reputation tools (e.g., AbuseIPDB)

4. **Correlate with other activity**
   - Check CloudTrail or SIEM for lateral movement attempts

---

## ✅ Response Actions:

- Block attacking IP(s) via firewall or Cloudflare
- Force password reset for targeted accounts
- Enable/verify MFA on affected accounts
- Add custom rule to monitor for future attempts

---

## 📚 Preventive Measures:

- Configure rate-limiting (WAF/Cloudflare)
- Enforce strong password policies
- Enable login anomaly detection alerts
- Enable account lockout thresholds

---

## 📌 Documentation:

- Attach alert logs and investigation notes
- Update incident tracker and threat intel DB
