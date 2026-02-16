# HTTP Credential Exposure Analysis (Wireshark)

## Overview

This case study demonstrates how sensitive user information can be
exposed on the network when web applications transmit data over
unencrypted HTTP.

Using Wireshark, live network traffic was captured and analyzed to
observe HTTP POST requests carrying credentials and personally
identifiable information (PII) in plaintext.

All analysis was conducted in a controlled lab environment for
educational and defensive security purposes only.

---

## Environment

- Network monitoring performed on a local interface
- Traffic captured using Wireshark
- Web application communicating over HTTP (port 80)
- No TLS/HTTPS encryption enabled

---

## Observations

During packet inspection, multiple HTTP POST requests were identified
containing form-submitted data.

The captured traffic revealed:

- Usernames transmitted in plaintext
- Password values visible in HTTP payloads
- Additional sensitive fields such as email addresses and phone numbers
- No encryption or transport-layer protection

Because HTTP does not provide confidentiality, any party with network
visibility could intercept and read this information.

---

## Security Impact

The exposure of credentials and PII over plaintext HTTP introduces
severe security risks, including:

- Credential theft via packet sniffing
- Account compromise and unauthorized access
- Privacy violations and potential data leakage
- Non-compliance with basic security and data protection standards

Attackers do not require exploitation tools in this scenario; passive
network monitoring alone is sufficient.

---

## Defensive Perspective

From a defensive and SOC standpoint, this issue highlights:

- The importance of enforcing HTTPS across all authentication endpoints
- The need for network monitoring to detect insecure protocols
- Risks introduced by legacy or misconfigured web services
- The value of traffic inspection in identifying policy violations

---

## Recommendations

- Enforce HTTPS using TLS for all web traffic
- Redirect all HTTP requests to HTTPS
- Implement HSTS to prevent protocol downgrade
- Monitor network traffic for unencrypted credential transmission
- Conduct regular security assessments of web applications

---

## Conclusion

This analysis demonstrates how insecure transport protocols can expose
sensitive data without active exploitation.

Proper encryption, monitoring, and secure configuration are critical to
reducing the risk of credential compromise in modern environments.

