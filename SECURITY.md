# Security reporting

## Report privately

Do not publish exploit details, credentials, complete PAR URLs, customer data, or private tenancy information in issues or pull requests.

If the affected repository offers **Security → Advisories → Report a vulnerability**, use that private reporting channel. Availability depends on repository settings; this document does not enable it. Include the affected revision, impact, prerequisites, sanitized reproduction steps, and a proposed mitigation if known.

If private reporting is unavailable, contact a known repository maintainer or organization owner through an established private channel. If you have no private contact, open an issue asking only for a private security contact; include no vulnerability details. For Oracle product vulnerabilities, use [Oracle's official reporting process](https://www.oracle.com/security-alerts/reportingvulnerabilities.html).

If a credential is exposed, have its owner revoke or rotate it promptly. Deleting the visible text is not a substitute for revocation. Keep remediation details private until maintainers agree on disclosure.

## Support expectations

These projects are incubating. Maintainers prioritize fixes on the current default branch; no support window or response SLA is promised for older revisions. Skill and template checks do not certify generated applications, IAM policies, or live OCI deployments. Each adopter must review and test its generated application and dependencies.
