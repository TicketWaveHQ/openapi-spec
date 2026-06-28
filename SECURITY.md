# Security Policy

## Reporting a vulnerability

If you believe you have found a security vulnerability in the TicketWave API surface described by this spec, or in any TicketWave-operated service, please **do not** open a public GitHub issue.

Instead, report it privately to:

**[security@ticketwavehq.com](mailto:security@ticketwavehq.com)**

Please include, where possible:

- A description of the issue and its impact.
- Steps to reproduce (request payloads, headers, expected vs actual response).
- Whether the issue has been disclosed elsewhere.
- Your name / handle for credit, if you would like to be acknowledged.

We aim to acknowledge new reports within **3 business days** and to provide a remediation timeline within **10 business days** of acknowledgement. Critical-severity issues are triaged immediately.

## Scope

In scope:

- The endpoints documented in [`openapi.yaml`](./openapi.yaml).
- Authentication, authorisation, tenant-isolation, and rate-limiting behaviour described in the spec.
- The signing and verification of webhook payloads referenced in this spec.

Out of scope (report to the project that owns them instead):

- Vulnerabilities in third-party SDK generators (OpenAPI Generator, Stainless, Redocly).
- Issues in client code generated *from* this spec by third parties.
- Spam, social engineering, or denial-of-service attempts against TicketWave staff.

## Safe-harbour

Good-faith research that follows this policy will not be pursued under the Computer Misuse Act 1990 or equivalent legislation. Please do not access, modify, or exfiltrate data belonging to anyone other than yourself, and stop and notify us if you encounter such data during testing.
