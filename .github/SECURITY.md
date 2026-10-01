# Security Policy for Privateer

Version: **v0.3 (2026-10-01)**

## Preface

Privateer currently only supports non-production use cases, but the Privateer Project team places high value on security considerations and welcomes input.

The project uses a weekly run of the [OSPS Baseline Scanner](https://github.com/revanite-io/osps-baseline-action)
to ensure conformance with Level 1 of the [Open Source Project Security Baseline](https://baseline.openssf.org).

## Supported Versions

We do not extend assurances or updates for any versions prior to the latest minor version. We will add security updates as semver "patch" releases only for the highest minor version.

For example, updates will be added to `v1.3` only until `v1.4` is released. If a security update was added in `v1.3.1`,
then `v1.4.0` is released, any defects found will be fixed in `v1.4.1` and there will not be a `v1.3.2`.

In the event that a new major version is released, we will revisit this documentation to update accordingly.

## Report a Vulnerability

If you find a security-related bug in Privateer, we kindly ask you for
responsible disclosure to give us appropriate time to receive, analyze and
develop a fix to mitigate the found security vulnerability.

- [Submit Vulnerability Report for Privateer Core](https://github.com/privateerproj/pvtr/security)
- [Submit Vulnerability Report for Privateer SDK](https://github.com/privateerproj/privateer-sdk/security)

## Review Known Vulnerabilities

We will publish security advisories using the GitHub Security Advisories feature for each
repository to keep our community well-informed, and will credit the reporter (if desired).

- [View Advisories for Privateer Core](https://github.com/privateerproj/pvtr/security/advisories)
- [View Advisories for Privateer SDK](https://github.com/privateerproj/privateer-sdk/security/advisories)

We will do our best to react quickly on your inquiry, and to coordinate a fix
and disclosure with you. Sometimes, it might take a little longer for us to
react (e.g. out of office conditions), so please bear with us in these cases.

## Security Contact

Jason Meridth ([@jmeridth](https://github.com/jmeridth)) is the security contact
for Privateer Core and the Privateer SDK.

Please do not email security reports. Submit them through GitHub private
vulnerability reporting using the links in
[Report a Vulnerability](#report-a-vulnerability).

## Secure Development

Both [Privateer Core](https://github.com/privateerproj/pvtr) and the
[Privateer SDK](https://github.com/privateerproj/privateer-sdk) follow these
practices:

- A ruleset on `main` blocks deletion and force pushes.
- Every change to `main` goes through a pull request with at least one approval,
  a code owner review, and resolved review threads.
- Pull requests must pass required status checks before merge, including CI and
  pull request title validation.
- GitHub Actions workflows pin every third-party action and reusable workflow to
  a full commit SHA.
- Every workflow job that runs its own steps starts with
  `step-security/harden-runner` in audit mode.
- Dependabot opens weekly update pull requests for Go modules and GitHub Actions.
- A weekly [OSPS Baseline](https://baseline.openssf.org) scan runs and uploads
  its results to code scanning.
- Each repository publishes a threat assessment in Gemara threat catalog format
  (see [Risk Handling](#risk-handling)).

Where the repositories differ:

- **Privateer Core** requires integration tests and Go and Markdown linting.
  The SDK requires a Go lint check.
- **Privateer Core** also uses Dependabot for Docker images.
- **The SDK** dismisses stale approvals when new commits are pushed.
  Privateer Core does not.
- **The SDK** requires sign-off on commits made through the GitHub web interface.
  Neither repository enforces Developer Certificate of Origin (DCO) sign-off on
  pull request commits.

## Risk Handling

Maintainers triage every vulnerability report in a private GitHub security
advisory on the affected repository. Discussion stays private until the
advisory is published.

The maintainers record known threats and mitigations in each repository's threat
assessment:

- [Privateer Core threat assessment](https://github.com/privateerproj/pvtr/blob/main/.github/threat-assessment.yaml)
- [Privateer SDK threat assessment](https://github.com/privateerproj/privateer-sdk/blob/main/.github/threat-assessment.yaml)

## Vulnerability Process

When we receive a report, the maintainers:

1. Acknowledge the report in the private security advisory.
2. Triage it to confirm the issue and assess its severity.
3. Develop the fix in the advisory's temporary private fork.
4. Release the fix as a patch on the latest minor version (see
   [Supported Versions](#supported-versions)).
5. Publish the security advisory with a CVE.
6. Credit the reporter, if they want credit.

We handle reports on a best-effort basis and do not promise a response or fix
timeframe.

## End of Life

Only the latest minor release receives security fixes, as described in
[Supported Versions](#supported-versions). When a new minor release ships, the
previous one reaches end of life.

If a repository is archived, its README will say so, and it will receive no
further fixes.
