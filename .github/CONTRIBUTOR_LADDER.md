# Contributor Ladder

Everyone is welcome to contribute to Privateer through discussion, issues, and pull requests.

The following roles define additional responsibilities and privileges a community member may receive. Moving up the ladder is meant to be achievable, not bureaucratic.

All governance decisions follow the processes defined in the [governance] document.


## All New & Established Contributors

Anyone participating in a Privateer discussion, issue, or contribution is expected to follow the [OpenSSF Code of Conduct].

New contributors should be welcomed by existing members, helped with the PR workflow, and directed to relevant documentation and communication channels.

### Definition of Contributions

Contributions are meaningful engagements that advance the goals of the project. These include, but are not limited to:

- Submission of pull requests that are subsequently merged.
- Participation in discussions on issues, pull requests, or community channels.
- Contribution to design proposals or reviews.
- Development or maintenance of a plugin.
- Documentation improvements.
- Helping others in discussions.
- Event planning or managing community tools and resources.

## Member

A Member is an active community member who has made repeated, meaningful contributions to the project over time.

**Defined by:** GitHub `privateerproj` Organization Membership.

### Requirements

- Enabled two-factor authentication on their GitHub account.
- Have made multiple [contributions] to the project, enough to demonstrate an ongoing commitment.
- Sponsored by one (1) existing Approver or Maintainer.

### Process

1. A sponsor opens a GitHub issue in the [`privateerproj/.github`](https://github.com/privateerproj/.github) repository (or the relevant repository, if `.github` does not yet exist) requesting the contributor be added to the `privateerproj` GitHub Organization.
   - The issue should summarize the contributor's contributions to date.
2. Any Maintainer adds the new Member to the organization.

### Responsibilities & Privileges

- Can have issues and PRs assigned to them.
- Can be invited to review PRs.

## Approver

**Defined by:** [CODEOWNERS] entry for specific files or directories (e.g. `plugins/<plugin-name>/`) and GitHub `approvers` Team.

An Approver reviews and approves contributions from other members within a specific scope — commonly a single plugin, or a defined area of `privateer` or `privateer-sdk`. Approval is focused on holistic acceptance of a contribution, including backward/forward compatibility with the core CLI and SDK contract, adherence to conventions, and interactions with other parts of the system.

### Requirements

- Active [Member] for at least three (3) months.
- History of quality reviews and contributions within a specific scope.

Community members who meet the above requirements may become Approver candidates through:

- Nomination by an existing Approver or Maintainer.
- Self-nomination.

### Process

1. The nominator opens a pull request to add the candidate to the relevant [CODEOWNERS] file.
   - The PR must remain open for seven (7) days to gather feedback, or until all existing Approvers for that scope have responded, whichever is first.
2. Any current Approver or Maintainer may request changes or object to the nomination.
3. Once approved, the PR is merged and the candidate is added to the `approvers` GitHub Team.

### Responsibilities & Privileges

- Review and approve PRs within their designated scope.
- Ensure contributions meet the project's conventions and quality standards, including the [Guiding Governance Principles].
- Adhere to the general responsibilities of a [Member].

## Maintainer

A Maintainer has organization-wide oversight, maintains the `privateer` CLI and `privateer-sdk`, and holds a binding vote on project [governance] decisions.

**Defined by:** [MAINTAINERS.md] entry and GitHub `core-maintainers` Team.

### Requirements

Community members may become Maintainer candidates through:

- Nomination by an existing Maintainer.
- Self-nomination after actively contributing to Privateer monthly for six months or more.

Candidates must be an active [Approver] with sustained cross-project contributions. Roles are not mutually exclusive; a [Community Manager] may also hold [Approver] status and progress to Maintainer.

### Process

Nominations are submitted via pull request to update Privateer's [MAINTAINERS.md]. After validation, [maintainer consensus] is sought. Upon consensus, the PR is merged and the new Maintainer is added to the `core-maintainers` GitHub Team.

### Responsibilities & Privileges

Maintainers guide the project's technical direction and make decisions through [maintainer consensus]. Maintainers must uphold the [Guiding Governance Principles] and ensure all proposals align with them.

- Maintainers can review, approve, and merge pull requests.
- Maintainers have access to repository management settings.
- Maintainers have binding votes in [maintainer consensus] decisions.
- Maintainers can sponsor new Members, nominate new Approvers, and nominate new Maintainers and Community Managers.

### Continued Maintainer Status

Maintainer status requires regular activity and adherence to the [OpenSSF Code of Conduct].

### Emeritus Maintainers

Emeritus maintainers are listed in Privateer's [EMERITUS.md](./EMERITUS.md).
A maintainer may be given Emeritus status after six months of inactivity (e.g., no pull request or issue interactions) or may self-assign Emeritus status via pull request.
A maintainer may return from Emeritus status through [maintainer consensus] and a pull request.

## Organization Admin

Organization Admins hold administrative rights over the entire `privateerproj` GitHub Organization — billing, repository creation/deletion, org-wide security settings, and team membership management. This is an infrastructure/operations responsibility, not a separate rung of technical authority: Organization Admins are expected to also be active Maintainers, and admin rights do not grant extra weight in [maintainer consensus] decisions.

**Defined by:** GitHub `admins` Team.

### Process

Because this role carries organization-wide administrative access, new Organization Admins are added only by existing Admins, and only from within the active Maintainer body. Additions and removals should be logged (e.g. via issue or PR referencing this document) for transparency, even though GitHub team membership itself is managed outside of version control.

## Community Manager

A Community Manager is a lateral role focused on community engagement, outreach, moderation, and documentation maintenance. It is not part of the technical contributor ladder.

**Defined by:** [MAINTAINERS.md] entry.

### Requirements

Community members may become Community Managers through:

- Nomination by an existing Maintainer.
- Self-nomination after actively contributing to Privateer in areas such as moderation, event organization, content creation, or user support.

### Process

Nominations are submitted via pull request to update Privateer's [MAINTAINERS.md] under `Community Managers`. After validation, there must be **unanimous approval** from all active Maintainers. Upon consensus, the PR is merged to confirm the new Community Manager.

Removal of a Community Manager requires [maintainer consensus] on a corresponding pull request.

### Responsibilities & Privileges

Community Managers manage community engagement and outreach without maintainer responsibilities.

- Community Managers receive access to Privateer community tools (GitHub Pages, social media accounts, etc.).
- Maintain and improve project documentation (website, guides, onboarding materials).
- The nature of the role is neutral facilitator; thus, they **do not** have a binding vote in [maintainer consensus].

## GitHub Team Mapping

The following table maps contributor ladder roles to GitHub Teams and their repository permission levels.

| GitHub Team | Role | Permission | Scope |
|:---|:---|:---|:---|
| `approvers` | [Approver] | Write | Specific repositories/plugins (review scope defined by [CODEOWNERS]) |
| `core-maintainers` | [Maintainer] | Maintain/Admin | All fully open-source repositories |
| `admins` | Organization Admin | Owner | Entire `privateerproj` GitHub Organization |

[Members][Member] receive Read access as the organization-level base permission. No dedicated team is required.

Community Manager currently has no dedicated GitHub Team — it is tracked solely via a [MAINTAINERS.md] entry until the community grows enough to warrant one.

Team membership changes follow the processes defined for each role above.

## Inactive Members

Maintaining a healthy community requires encouraging active participation. It is natural for people's focus to shift over time, and no one is expected to contribute forever.

An inactive member is anyone holding a role above with **zero** qualifying [contributions] in the preceding six (6) months. Inactive members may:

- Self-assign **Emeritus** status via pull request at any time.
- Be moved to Emeritus after six months of inactivity by any Maintainer via pull request.

Emeritus members are listed in [EMERITUS.md](./EMERITUS.md). An Emeritus member may return to active status through [maintainer consensus] and a pull request.

## Revisions to the Contributor Ladder

Changes to this document require approval from at least 66% of active Maintainers, as defined in the [governance] document.

## Acknowledgements

This contributor ladder was adapted from [Gemara's contributor ladder](https://github.com/gemaraproj/.github/blob/main/CONTRIBUTOR_LADDER.md), which was itself inspired by the FINOS Common Cloud Controls [member roles](https://github.com/finos/common-cloud-controls/blob/main/docs/governance/member-roles.md).

[governance]: ./GOVERNANCE.md
[MAINTAINERS.md]: ./MAINTAINERS.md
[CODEOWNERS]: https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners
[OpenSSF Code of Conduct]: https://openssf.org/community/code-of-conduct/
[maintainer consensus]: ./GOVERNANCE.md#maintainer-consensus
[Guiding Governance Principles]: ./GOVERNANCE.md#guiding-governance-principles
[contributions]: #definition-of-contributions
[Member]: #member
[Approver]: #approver
[Maintainer]: #maintainer
[Community Manager]: #community-manager
