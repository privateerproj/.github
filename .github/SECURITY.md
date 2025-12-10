# Security Policy for Privateer

Version: **v0.2 (2025-12-09)**

## Preface

Privateer currently only supports non-production use cases, but the Privateer Project team places high value on security considerations and welcomes input.

The project uses a weekly run of the [OSPS Baseline Scanner](https://github.com/marketplace/actions/open-source-project-security-baseline-scanner)
to ensure conformance with Level 1 of the [Open Source Project Security Baseline](https://baseline.openssf.org).

## Supported Versions

We do not extend assurances or updates for any versions prior to the latest minor version. We will add security updates as semver "patch" releases only for the highest minor version. 

For example, updates will be added to `v1.3` only until `v1.4` is released. If a security update was added in `v1.3.1`,
then `v1.4.0` is released, any defects found will be fixed in `v1.4.1` and there will not be a `v1.3.2`.

In the event that a new major version is released, we will revisit this documentation to update accordingly.

## Report a Vulnerability

If you find a security-related bug in Privateer, we kindly ask you for 
responsible disclosure to give us appropriate time to recieve, analyze and
develop a fix to mitigate the found security vulnerability.

- [Submit Vulnerability Report for Privateer Core](https://github.com/privateerproj/privateer/security)
- [Submit Vulnerability Report for Privateer SDK](https://github.com/privateerproj/privateer-sdk/security)

## Review Known Vulnerabilities

We will publish security advisories using the GitHub Security Advisories feature for each
repository to keep our community well-informed, and will credit the reporter (if desired).

- [View Advisories for Privateer Core](https://github.com/privateerproj/privateer/security/advisories)
- [View Advisories for Privateer SDK](https://github.com/privateerproj/privateer-sdk/security/advisories)

We will do our best to react quickly on your inquiry, and to coordinate a fix
and disclosure with you. Sometimes, it might take a little longer for us to
react (e.g. out of office conditions), so please bear with us in these cases.
