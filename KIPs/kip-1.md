---
kip: 1
title: KIP Purpose and Guidelines
author: Bitkub Chain (@bitkubchain), et al.
status: Draft
type: Meta
created: 2024-07-19
---

## Abstract

KIP stands for KUB Improvement Proposal. A KIP is a design document providing information to the Bitkub Chain community, or describing a new feature for Bitkub Chain or its processes or environment. The KIP should provide a concise technical specification of the feature and a rationale for the feature.

## KIP Rationale

We intend KIPs to be the primary mechanisms for proposing new features, collecting community technical input on an issue, and documenting the design decisions that have gone into Bitkub Chain. The KIP author is responsible for building consensus within the community and documenting dissenting opinions.

Because the KIPs are maintained as text files in a versioned repository, their revision history is the historical record of the feature proposal.

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

## KIP Work Flow

### Shepherding a KIP

Parties involved in the process are you, the champion or *KIP author*, the *KIP editors*, and the *Bitkub Chain Core Developers*.

Before you begin writing a formal KIP, you should vet your idea. Ask the Bitkub Chain community first if an idea is original to avoid wasting time on something that will be rejected based on prior research. It is thus recommended to open a discussion thread on [Bitkub Chain Discord Forum](https://discord.gg/U5wKGZhEmA) to do this.

Once the idea has been vetted, your next responsibility will be to present (through a KIP) the idea to the reviewers and all interested parties, and invite editors, developers, and the community to give feedback on the aforementioned channels. You should try and gauge whether the interest in your KIP is commensurate with both the work involved in implementing it and how many parties will have to conform to it. For example, the work required for implementing a Core KIP will be much greater than for an KAP and the KIP will need sufficient interest from the Bitkub Chain client teams. Negative community feedback will be taken into consideration and may prevent your KIP from moving past the Draft stage.

### KIP Process

The following is the standardization process for all KIPs in all tracks:

![KIP Status Diagram](KIPs/assets/kip-1/KIP_Process.png)

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

## What belongs in a successful KIP?

Each KIP should have the following parts:

- Preamble - RFC 822 style headers containing metadata about the KIP, including the KIP number, a short descriptive title (limited to a maximum of 44 characters), and the author details. Irrespective of the category and the title should not include KIP number.
- Abstract - Abstract is a multi-sentence (short paragraph) technical summary. This should be a very terse and human-readable version of the specification section. Someone should be able to read only the abstract to get the gist of what this specification does.
- Motivation *(optional)* - A motivation section is critical for KIPs that want to change the Bitkub Chain protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the KIP solves. This section may be omitted if the motivation is evident.
- Specification - The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Bitkub Chain platforms.
- Rationale - The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale should discuss important objections or concerns raised during discussion around the KIP.
- Backwards Compatibility *(optional)* - All KIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their consequences. The KIP must explain how the author proposes to deal with these incompatibilities. This section may be omitted if the proposal does not introduce any backwards incompatibilities, but this section must be included if backward incompatibilities exist.
- Test Cases *(optional)* - Test cases for an implementation are mandatory for KIPs that are affecting consensus changes. This section may be omitted for non-Core proposals.
- Reference Implementation *(optional)* - An optional section that contains a reference/example implementation that people can use to assist in understanding or implementing this specification. This section may be omitted for all KIPs.
- Security Considerations - All KIPs must contain a section that discusses the security implications/considerations relevant to the proposed change. Include information that might be important for security discussions, surfaces risks and can be used throughout the life-cycle of the proposal. E.g. include security-relevant design decisions, concerns, important discussions, implementation-specific guidance and pitfalls, an outline of threats and risks and how they are being addressed. KIP submissions missing the "Security Considerations" section will be rejected. A KIP cannot proceed to status "Final" without a Security Considerations discussion deemed sufficient by the reviewers.
- Copyright Waiver - All KIPs must be in the public domain. The copyright waiver MUST link to the license file.

## KIP Formats and Templates

KIPs should be written in [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) format. There is a [template](kip-template.md) to follow.

## KIP Header Preamble

Each KIP must begin with an [RFC 822](https://www.ietf.org/rfc/rfc822.txt) style header preamble, preceded and followed by three hyphens (`---`). This header is also termed ["front matter" by Jekyll](https://jekyllrb.com/docs/front-matter/). The headers must appear in the following order.

`kip`: *KIP number*

`title`: *The KIP title is a few words, not a complete sentence*

`author`: *The list of the author's or authors' name(s) and/or username(s), or name(s) and email(s). Details are below.*

`discussions-to`: *The url pointing to the official discussion thread*

`status`: *Draft, Review, Last Call, Final, Stagnant, Withdrawn, Living*

`last-call-deadline`: *The date last call period ends on* (Optional field, only needed when status is `Last Call`)

`type`: *One of `Standards Track`, `Meta`, or `Informational`*

`category`: *One of `Core`, `Interface`, or `KAP`* (Optional field, only needed for `Standards Track` KIPs)

`created`: *Date the KIP was created on*

`requires`: *KIP number(s)* (Optional field)

`withdrawal-reason`: *A sentence explaining why the KIP was withdrawn.* (Optional field, only needed when status is `Withdrawn`)

Headers that permit lists must separate elements with commas.

Headers requiring dates will always do so in the format of ISO 8601 (yyyy-mm-dd).

### `author` header

The `author` header lists the names, email addresses or usernames of the authors/owners of the KIP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the `author` header value must be:

> Random J. User &lt;address@dom.ain&gt;

or

> Random J. User (@username)

or

> Random J. User (@username) &lt;address@dom.ain&gt;

if the email address and/or GitHub username is included, and

> Random J. User

if neither the email address nor the GitHub username are given.

At least one author must use a GitHub username, in order to get notified on change requests and have the capability to approve or reject them.

### `discussions-to` header

While an KIP is a draft, a `discussions-to` header will indicate the URL where the KIP is being discussed.

The preferred discussion URL is a topic on [Bitkub Chain Discord Forum](https://discord.gg/U5wKGZhEmA). The URL cannot point to Github pull requests, any URL which is ephemeral, and any URL which can get locked over time (i.e. Reddit topics).

### `type` header

The `type` header specifies the type of KIP: Standards Track, Meta, or Informational. If the track is Standards please include the subcategory (core, interface, or KAP).

### `category` header

The `category` header specifies the KIP’s category. This is required for standards-track KIPs only.

### `created` header

The `created` header records the date that the KIP was assigned a number. Both headers should be in yyyy-mm-dd format, e.g. 2001-08-14.

### `requires` header

KIPs may have a `requires` header, indicating the KIP numbers that this KIP depends on. If such a dependency exists, this field is required.

A `requires` dependency is created when the current KIP cannot be understood or implemented without a concept or technical element from another KIP. Merely mentioning another KIP does not necessarily create such a dependency.

## Auxiliary Files

Images, diagrams and auxiliary files should be included in a subdirectory of the `assets` folder for that KIP as follows: `assets/kip-N` (where **N** is to be replaced with the KIP number). When linking to an image in the KIP, use relative links such as `../assets/kip-1/image.png`.

## Transferring KIP Ownership

It occasionally becomes necessary to transfer ownership of KIPs to a new champion. In general, we'd like to retain the original author as a co-author of the transferred KIP, but that's really up to the original author. A good reason to transfer ownership is because the original author no longer has the time or interest in updating it or following through with the KIP process, or has fallen off the face of the 'net (i.e. is unreachable or isn't responding to email). A bad reason to transfer ownership is because you don't agree with the direction of the KIP. We try to build consensus around an KIP, but if that's not possible, you can always submit a competing KIP.

## KIP Editors

The current KIP editors are

- Bitkub Chain (@bitkubchain)

## KIP Editor Responsibilities

For each new KIP that comes in, an editor does the following:

- Read the KIP to check if it is ready: sound and complete. The ideas must make technical sense, even if they don't seem likely to get to final status.
- The title should accurately describe the content.
- Check the KIP for language (spelling, grammar, sentence structure, etc.), markup (GitHub flavored Markdown), code style

If the KIP isn't ready, the editor will send it back to the author for revision, with specific instructions.

Once the KIP is ready for the repository, the KIP editor will:

- Assign an KIP number (generally incremental; editors can reassign if number sniping is suspected)
- Merge the corresponding pull request
- Send a message back to the KIP author with the next step.

Many KIPs are written and maintained by developers with write access to the Bitkub Chain codebase. The KIP editors monitor KIP changes, and correct any structure, grammar, spelling, or markup mistakes we see.

The editors don't pass judgment on KIPs. We merely do the administrative & editorial part.

## Style Guide

### Titles

The `title` field in the preamble:

- Should not include the word "standard" or any variation thereof; and
- Should not include the KIP's number.

### Descriptions

The `description` field in the preamble:

- Should not include the word "standard" or any variation thereof; and
- Should not include the KIP's number.

### KIP numbers

When referring to an KIP with a `category` of `KAP`, it must be written in the hyphenated form `KAP-X` where `X` is that KIP's assigned number. When referring to KIPs with any other `category`, it must be written in the hyphenated form `KIP-X` where `X` is that KIP's assigned number.

### RFC 2119 and RFC 8174

KIPs are encouraged to follow [RFC 2119](https://www.ietf.org/rfc/rfc2119.html) and [RFC 8174](https://www.ietf.org/rfc/rfc8174.html) for terminology and to insert the following at the beginning of the Specification section:

> The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119 and RFC 8174.

## History

This document was heavily derived from the [Ethereum EIP-1](https://github.com/ethereum/EIPs/) written by Hudson Jameson and Martin Becze which in turn was derived from [Bitcoin's BIP-0001](https://github.com/bitcoin/bips) written by Amir Taaki which in turn was derived from [Python's PEP-0001](https://peps.python.org/). In many places text was simply copied and modified. Although the PEP-0001 text was written by Barry Warsaw, Jeremy Hylton, and David Goodger, they are not responsible for its use in the KUB Improvement Proposal, and should not be bothered with technical questions specific to Bitkub Chain or the KIP. Please direct all comments to the KIP editors.

## Copyright

Copyright and related rights waived via [CC0](LICENSE).