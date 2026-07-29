# Ledger-API
# Security Gate Fail Policies

| Security Gate | Tool | Policy | Action |
|--------------|------|--------|--------|
| Secret Scan | Gitleaks | Hard Block | Pipeline fails if secrets are detected. |
| Static Analysis | Semgrep | Hard Block | Pipeline fails for High/Critical findings. |
| Dependency Scan | Trivy | Hard Block | Pipeline fails on Critical/High vulnerabilities. |
| Container Image Scan | Trivy | Hard Block | Pipeline fails if Critical/High vulnerabilities exist. |
| Image Signing | Cosign | Hard Block | Pipeline fails if signing fails. |
| Provenance Attestation | Cosign | Hard Block | Pipeline fails if attestation generation fails. |
| SARIF Upload | GitHub Code Scanning | Warning | Failure to upload does not stop the build. |

## Handling CVEs Without Available Fixes

When Trivy reports a vulnerability without an available fix:

- Document the CVE.
- Assess exploitability.
- Apply compensating controls where possible.
- Monitor vendor releases.
- Upgrade once a fixed package becomes available.
