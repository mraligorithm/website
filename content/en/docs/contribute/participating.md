---
title: Participating in SIG Docs
content_template: templates/concept
---

{{% capture overview %}}

SIG Docs is one of the
[special interest groups](https://github.com/kubernetes/community/blob/master/sig-list.md)
within the Kubernetes project, focused on writing, updating, and maintaining
the documentation for Kubernetes as a whole. See
[SIG Docs from the community github repo](https://github.com/kubernetes/community/tree/master/sig-docs)
for more information about the SIG.

SIG Docs welcomes content and reviews from all contributors. Anyone can open a
pull request (PR), and anyone is welcome to file issues about content or comment
on pull requests in progress.

Within SIG Docs, you may also become a [member](#members),
[reviewer](#reviewers), or [approver](#approvers). These roles require greater
access and entail certain responsibilities for approving and committing changes.
See [community-membership](https://github.com/kubernetes/community/blob/master/community-membership.md)
for more information on how membership works within the Kubernetes community.
The rest of this document outlines some unique ways these roles function within
SIG Docs, which is responsible for maintaining one of the most public-facing
aspects of Kubernetes -- the Kubernetes website and documentation.

{{% /capture %}}

{{% capture body %}}

## Roles and responsibilities

When a pull request is merged to the branch used to publish content (currently
`master`), that content is published and available to the world. To ensure that
the quality of our published content is high, we limit merging pull requests to
SIG Docs approvers. Here's how it works.

- When a pull request has both the `lgtm` and `approve` labels and has no `hold`
  labels, the pull request merges automatically. 
- Kubernetes organization members and SIG Docs approvers can add comments to
  prevent automatic merging of a given pull request (by adding a `/hold` comment
  or withholding a `/lgtm` comment).
- Any Kubernetes member can add the `lgtm` label, by adding a `/lgtm` comment.
- Only an approver who is a member of SIG Docs can cause a pull request to merge
  by adding an `/approve` comment. Some approvers also perform additional
  specific roles, such as [PR Wrangler](#pr-wrangler) or
  [SIG Docs chairperson](#sig-docs-chairperson).

For more information about expectations and differences between the roles of
Kubernetes organization member and SIG Docs approvers, see
[Types of contributor](/docs/contribute#types-of-contributor). The following
sections cover more details about these roles and how they work within
SIG Docs.

### Anyone

Anyone can file an issue against any part of Kubernetes, including documentation.

Anyone who has signed the CLA can submit a pull request. If you cannot sign the
CLA, the Kubernetes project cannot accept your contribution.

### Members

Any member of the [Kubernetes organization](https://github.com/kubernetes) can
review a pull request, and SIG Docs team members frequently request reviews from
members of other SIGs for technical accuracy.
SIG Docs also welcomes reviews and feedback regardless of a person's membership
status in the Kubernetes organization. You can indicate your approval by adding
a comment of `/lgtm` to a pull request. If you are not a member of the
Kubernetes organization, your `/lgtm` has no effect on automated systems.

Any member of the Kubernetes organization can add a `/hold` comment to prevent
the pull request from being merged. Any member can also remove a `/hold` comment
to cause a PR to be merged if it already has both `/lgtm` and `/approve` applied
by appropriate people.

### Reviewers

Reviewers are members of the
[@kubernetes/sig-docs-pr-reviews](https://github.com/orgs/kubernetes/teams/sig-docs-pr-reviews)
Github group. See [Teams and groups within SIG Docs](#teams-and-groups-within-sig-docs).

Reviewers review documentation pull requests and provide feedback on proposed
changes.

Automation assigns reviewers to pull requests, and contributors can request a
review from a specific reviewer with a comment on the pull request: `/assign
[@_github_handle]`. To indicate that a pull request is technically accurate and
requires no further changes, a reviewer adds a `/lgtm` comment to the pull
request.

If the assigned reviewer has not yet reviewed the content, another reviewer can
step in. In addition, you can assign technical reviewers and wait for them to
provide `/lgtm`.

For a trivial change or one that needs no technical review, the SIG Docs
[approver](#approvers) can provide the `/lgtm` as well.

A `/approve` comment from a reviewer is ignored by automation.

For more about how to become a SIG Docs reviewer and the responsibilities and
time commitment involved, see
[Becoming a reviewer or approver](#becoming-an-approver-or-reviewer).

### Approvers

Approvers are members of the
[@kubernetes/sig-docs-maintainers](https://github.com/orgs/kubernetes/teams/sig-docs-maintainers)
Github group. See [Teams and groups within SIG Docs](#teams-and-groups-within-sig-docs).

Approvers have the ability to merge a PR, and thus, to publish content on the
Kubernetes website. To approve a PR, an approver leaves an `/approve` comment on
the PR. If someone who is not an approver leaves the approval comment,
automation ignores it.

If the PR already has a `/lgtm`, or if the approver also comments with `/lgtm`,
the PR merges automatically. A SIG Docs approver should only leave a `/lgtm` on
a change that doesn't need additional technical review.

For more about how to become a SIG Docs approver and the responsibilities and
time commitment involved, see
[Becoming a reviewer or approver](#becoming-an-approver-or-reviewer).

#### PR Wrangler

SIG Docs approvers are added to the
[PR Wrangler rotation scheduler](https://github.com/kubernetes/website/wiki/PR-Wranglers)
for weekly rotations. All SIG Docs approvers are expected to take part in this
rotation. See
[Be the PR Wrangler for a week](/docs/contribute/advanced#be-the-pr-wrangler-for-a-week)
for more details.

#### SIG Docs chairperson

Each SIG, including SIG Docs, selects one or more SIG members to act as
chairpersons. These are points of contact between SIG Docs and other parts of
the Kubernetes organization. They require extensive knowledge of the structure
of the Kubernetes project as a whole and how SIG Docs works within it. See
[Leadership](https://github.com/kubernetes/community/tree/master/sig-docs#leadership)
for the current list of chairpersons.



## SIG Docs teams and automation

Automation in SIG Docs relies on two different mechanisms for automation:
Github groups and OWNERS files.

### Github groups

The SIG Docs group defines two teams on Github:

 - [@kubernetes/sig-docs-maintainers](https://github.com/orgs/kubernetes/teams/sig-docs-maintainers)
 - [@kubernetes/sig-docs-pr-reviews](https://github.com/orgs/kubernetes/teams/sig-docs-pr-reviews)

Each can be referenced with their `@name` in Github comments to communicate with
everyone in that group.

These teams overlap, but do not exactly match, the groups used by the automation
tooling. For assignment of issues, pull requests, and to support PR approvals,
the automation uses information from OWNERS files.

### OWNERS files and front-matter

The Kubernetes project uses an automation tool called prow for automation
related to Github issues and pull requests. The
[Kubernetes website repository](https://github.com/kubernetes/website) uses
two [prow plugins](https://github.com/kubernetes/test-infra/blob/master/prow/plugins.yaml#L210):

- blunderbuss
- approve

These two plugins use the
[OWNERS](https://github.com/kubernetes/website/blob/master/OWNERS) and
[OWNERS_ALIASES](https://github.com/kubernetes/website/blob/master/OWNERS_ALIASES)
files in the top level of the `kubernetes/website` Github repository to control
how prow works within the repository.

An OWNERS file contains a list of people who are SIG Docs reviewers and
approvers. OWNERS files can also exist in subdirectories, and can override who
can act as a reviewer or approver of files in that subdirectory and its
descendents. For more information about OWNERS files in general, see
[OWNERS](https://github.com/kubernetes/community/blob/master/contributors/guide/owners.md).

In addition, an individual Markdown file can list reviewers and approvers in its
front-matter, either by listing individual Github usernames or Github groups.

The combination of OWNERS files and front-matter in Markdown files determines
the advice PR owners get from automated systems about who to ask for technical
and editorial review of their PR.

## Become a reviewer or approver

To volunteer as a reviewer or approver, make sure you
[meet the general requirements](https://github.com/kubernetes/community/blob/master/community-membership.md#membership)
and the [requirements for SIG Docs](#become-a-reviewer-or-approver). Your
SIG Docs sponsor adds you to the appropriate Github groups and OWNERS files
after your status as a reviewer or approver is approved by the SIG.

| Role                   | SIG Docs prerequisites                            | Responsibilities                                          |
|------------------------|---------------------------------------------------|-----------------------------------------------------------|
| [Member](#members)     | Sign the CLA                                      | Follow the [Code of Conduct](/community/#code-of-conduct) |
| [Reviewer](#reviewers) | Regularly participate in weekly SIG Docs meetings | Review PRs auto-assigned by blunderbuss within 1 week     |
| [Approver](#approvers) | <ul><li>Contribute regularly as a reviewer for at least 3 months</li><li>Understand SIG Docs workflows and tooling</li></ul> | <ul><li>Respond to PR comments/requests for review from other maintainers within 1 week</li><li>Serve periodically as the PR Wrangler for SIG Docs</li></ul> |


{{% /capture %}}

{{% capture whatsnext %}}

For more information about contributing to the Kubernetes documentation, see:

- [Start contributing](/docs/contribute/start/)
- [Documentation style](/docs/contribute/style/)

{{% /capture %}}


