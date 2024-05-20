# KUB Improvement Proposals (KIPs)

KUB Improvement Proposals (KIPs) describe standards for the Bitkub Chain platform, including core protocol specifications, SDK, and contract standards. A KIP is a design document providing information to the Bitkub Chain community, or describing a new feature for Bitkub Chain or its processes or environment. The KIP should provide a concise technical specification of the feature and a rationale for the feature.

The goal of the KIP project is to standardize and provide high-quality documentation for Bitkub Chain itself and conventions built upon it. This repository tracks past and ongoing improvements to Bitkub Chain in the form of KUB Improvement Proposals (KIPs). [KIP-1](KIPs/kip-1.md) governs how KIPs are published.

## KIP Types

There are three types of KIP:

- A **Standards Track KIP** describes any change that affects most or all Bitkub Chain implementations, such as a change to the network protocol, a change in block or transaction validity rules, proposed application standards/conventions, or any change or addition that affects the interoperability of applications using Bitkub Chain. Standards Track KIPs consist of three parts—a design document, an implementation, and (if warranted) an update to the formal specification. Furthermore, Standards Track KIPs can be broken down into the following categories:
  - **Core**: improvements requiring a consensus fork, as well as changes that are not necessarily consensus critical but may be relevant to “core dev” discussions.
  - **Interface**: includes improvements around language-level standards like method names and contract ABIs.
  - **KAP**: application-level standards and protocols, including contract standards such as token standards, name registries, URI schemes, library/package formats, and wallet formats.

- A **Meta KIP** describes a process surrounding Bitkub Chain or proposes a change to (or an event in) a process. Process KIPs are like Standards Track KIPs but apply to areas other than the Bitkub Chain protocol itself. They may propose an implementation, but not to Bitkub Chain's codebase; unlike Informational KIPs, they are more than recommendations, and users are typically not free to ignore them. Examples include procedures, guidelines, changes to the decision-making process, and changes to the tools or environment used in Bitkub Chain development. Any meta-KIP is also considered a Process KIP.

- An **Informational KIP** describes a Bitkub Chain design issue, or provides general guidelines or information to the Bitkub Chain community, but does not propose a new feature. Informational KIPs do not necessarily represent Bitkub Chain community consensus or a recommendation, so users and implementers are free to ignore Informational KIPs or follow their advice.

It is highly recommended that a single KIP contain a single key proposal or new idea. The more focused the KIP, the more successful it tends to be. A change to one client doesn't require a KIP; a change that affects multiple clients or defines a standard for multiple apps to use does.

A KIP must meet certain minimum criteria. It must be a clear and complete description of the proposed enhancement. The enhancement must represent a net improvement. The proposed implementation, if applicable, must be solid and must not complicate the protocol unduly.

### KIP Process

**Before you write a KIP, ideas MUST be thoroughly discussed on [Bitkub Chain Discord Forum](https://discord.gg/U5wKGZhEmA). Once consensus is reached, thoroughly read and review [KIP-1](KIPs/kip-1.md), which describes the KIP process.**

The following is the standardization process for all KIPs in all tracks:

**Idea** - An idea that is pre-draft. This is not tracked within the KIP Repository.

**Draft** - The first formally tracked stage of a KIP in development. A KIP is merged by a KIP Editor into the KIP repository when properly formatted.

**Review** - A KIP Author marks a KIP as ready for and requesting Peer Review.

**Last Call** - This is the final review window for a KIP before moving to `Final`. A KIP editor will assign `Last Call` status and set a review end date (`last-call-deadline`), typically 14 days later.

If this period results in necessary normative changes it will revert the KIP to `Review`.

**Final** - This KIP represents the final standard. A Final KIP exists in a state of finality and should only be updated to correct errata and add non-normative clarifications.

A PR moving an KIP from Last Call to Final SHOULD contain no changes other than the status update. Any content or editorial proposed change SHOULD be separate from this status-updating PR and committed prior to it.

**Stagnant** - Any KIP in `Draft` or `Review` or `Last Call` if inactive for a period of 6 months or greater is moved to `Stagnant`. A KIP may be resurrected from this state by Authors or KIP Editors through moving it back to `Draft` or its earlier status. If not resurrected, a proposal may stay forever in this status.

**Withdrawn** - The KIP Author(s) have withdrawn the proposed KIP. This state has finality and can no longer be resurrected using this KIP number. If the idea is pursued at a later date it is considered a new proposal.

**Living** - A special status for KIPs that are designed to be continually updated and not reach a state of finality. This includes most notably KIP-1.

## Submitting KIPs

Before you initiate a pull request, please read the [KIP-1 process document](KIPs/kip-1.md). If your proposal is discussing a new contract standard, make sure you submit it under the [KUB Application Protocols (KAPs)]() repo. Draft all proposals following the template below and submit them to the KIPs repository via a PR (pull request).

## KIP Template

Please see [kip-template.md](kip-template.md) for a template.

#### Preferred Citation Format
Consider any document not published by the KIPs repository as a working paper. Additionally, consider published KIPs with a status of "draft", "review", or "last call" to be incomplete drafts, and note that their specification is likely to be subject to change.
