# -FUTURE_CS_03
# API Security Risk Analysis: ReqRes Demo API

**Future Interns | Cyber Security Task 3 (2026)**

A read-only API security risk analysis of the public ReqRes demo API (`https://reqres.in`), written as a professional consultant-style report. The goal is to identify common API security risks, explain them in simple business language and recommend clear remediation steps, without exploiting or attacking anything.

## Repository Contents

```
API-Security-Risk-Analysis/
├── API_Security_Risk_Analysis_Report.docx   # Full report (editable)
├── API_Security_Risk_Analysis_Report.pdf    # Full report (PDF)
├── README.md
└── screenshots/
    ├── 01_GET_users_list_page2.png          # GET /api/users?page=2
    ├── 02_POST_login.png                    # POST /api/login
    └── 03_GET_single_user_id2.png           # GET /api/users/2
```

## Scope

**In scope**
- Public demo API: ReqRes (`https://reqres.in`), built for testing and learning
- Read-only requests: `GET /api/users?page=2`, `GET /api/users/2` and the safe demo `POST /api/login` preset
- Inspection of authentication, headers, status codes, latency, response size and response body

**Out of scope / not performed**
- Exploitation or bypass attempts
- Flooding, load or denial-of-service testing
- Any testing of private or production APIs

## Tools Used

| Tool | Purpose |
|------|---------|
| Postman | Sending requests with a free ReqRes API key and inspecting responses |
| ReqRes Request Builder / Response Viewer | Demo presets, request and response inspection |
| Microsoft Word / PDF | Report writing and delivery |

## Methodology

1. **Select API:** chose the ReqRes demo API as a safe, legal target.
2. **Review documentation:** studied the available presets and endpoints.
3. **Test endpoints:** obtained a free ReqRes API key, ran three representative requests in Postman with the key in the `x-api-key` header, and captured screenshots.
4. **Inspect:** reviewed authentication (`x-api-key`, login token), headers and response data.
5. **Identify risks:** mapped observations to the OWASP API Security Top 10 (2023).
6. **Classify severity:** rated each finding Low / Medium / High.
7. **Recommend and document:** wrote business impact and remediation for each finding.

## Endpoints Tested

| # | Method | Endpoint | Status | Latency | Size |
|---|--------|----------|--------|---------|------|
| 1 | GET | `/api/users?page=2` | 200 | 504 ms | 1.5 KB |
| 2 | POST | `/api/login` | 200 | 505 ms | 436 B |
| 3 | GET | `/api/users/2` | 200 | 249 ms | 777 B |

## Summary of Findings

| ID | Finding | Severity | OWASP API 2023 |
|----|---------|----------|----------------|
| F-01 | Sequential object IDs and no visible object-level authorization | **High** | API1: BOLA |
| F-02 | Excessive data exposure (PII in user objects) | **Medium** | API3: BOPLA |
| F-03 | Shared static API key as the sole authentication mechanism | **Medium** | API2: Broken Authentication |
| F-04 | Minimal / weak token design in the login response | **Medium** | API2: Broken Authentication |
| F-05 | No rate limiting evidenced on any endpoint | **Medium** | API4: Unrestricted Resource Consumption |
| F-06 | Unnecessary metadata and third-party links in responses | **Low** | API8: Security Misconfiguration |
| F-07 | Client-controlled query parameters, validation not evidenced | **Low** | API8: Security Misconfiguration |

Severity reflects what the same pattern would mean in a production SaaS product. ReqRes is a demo service that intentionally returns fictional data.

## Ethics Statement

All testing was performed on a public demo API intended for learning, using low-volume, read-only requests. No exploitation, authentication bypass, brute-forcing or denial-of-service activity was carried out. Findings describe risk, they do not demonstrate exploitation.

## References

- [OWASP API Security Top 10](https://github.com/OWASP/API-Security)
- [API Security Checklist](https://github.com/shieldfy/API-Security-Checklist)
- [Public APIs collection](https://github.com/public-apis/public-apis)
- [ReqRes](https://reqres.in)



