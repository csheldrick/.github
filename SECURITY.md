# Security Policy

## Supported Versions

We provide security updates for the following versions:

| Version / Branch | Supported          |
|------------------|--------------------|
| `main`           | :white_check_mark: |
| Older branches   | :x:                |

---

## Reporting a Vulnerability

**Please do not report security vulnerabilities through public GitHub issues.**

If you discover a security vulnerability, please report it responsibly using one of the following methods:

1. **GitHub Private Security Advisory (preferred):** Navigate to the **Security** tab of this repository and select **"Report a vulnerability"** to open a private advisory.
2. **Email:** Contact the repository maintainers directly via the email listed in their GitHub profile.

### What to Include

When reporting a vulnerability, please provide:

- A clear description of the vulnerability and its potential impact.
- Step-by-step instructions to reproduce the issue.
- Any proof-of-concept code, screenshots, or logs (if applicable).
- The affected version(s) or branch(es).
- Your suggested fix or mitigation (optional but appreciated).

---

## Vulnerability Severity

We triage reported vulnerabilities using the following severity levels:

| Severity | Description |
|----------|-------------|
| **Critical** | Allows remote code execution, full system compromise, or data exfiltration without authentication. |
| **High** | Allows significant data exposure, privilege escalation, or service disruption. |
| **Medium** | Requires specific conditions or partial access to exploit; limited impact. |
| **Low** | Minor issues with negligible security impact. |

---

## Response Timeline

We are committed to responding to security reports in a timely manner:

| Action | Target Timeframe |
|--------|-----------------|
| Acknowledge receipt | Within **48 hours** |
| Initial triage and severity assessment | Within **5 business days** |
| Remediation or mitigation plan | Within **30 days** (Critical/High); **90 days** (Medium/Low) |
| Public disclosure | Coordinated with reporter after fix is released |

---

## Security Best Practices for Contributors

All contributors are expected to follow these practices to keep the project secure:

- **Never commit secrets or credentials** (API keys, tokens, passwords) to the repository. Use environment variables or secrets management tools.
- **Avoid introducing vulnerable dependencies.** Run `npm audit` / `pip audit` / equivalent before submitting a PR.
- **Validate and sanitize all user inputs** to prevent injection attacks.
- **Follow the principle of least privilege** — request only the permissions your code needs.
- **Keep dependencies up to date** and address known CVEs promptly.
- **Review Dependabot or Renovate alerts** and address them as part of regular maintenance.

---

## Scope

This security policy applies to:

- All code in this repository.
- Configuration files and workflows (e.g., GitHub Actions).
- Documentation that may contain sensitive operational details.

It does **not** apply to:

- Third-party services or dependencies (report those directly to the respective projects).
- Issues in forked repositories not contributed back to this project.
