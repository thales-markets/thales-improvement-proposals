---
id: tip-1
title: TIP-1:TIP Purpose and Guidelines
status: Draft
author: [Farmwell](https://github.com/farmwell)
description: TIP-1:TIP Purpose and Guidelines
discussions-to: https://discord.com/invite/cFGv5zyVEj 
hide_title: false
sidebar_label: TIP-1
---

## What is a TIP?

TIP stands for Thales Improvement Proposal, it has been adapted from the EIP (Ethereum Improvement Proposal) and SIP (Synthetix Improvement Proposal) stndards. The purpose of this process is to ensure changes to Thales are transparent and well governed.

An TIP is a design document providing information to the Thales community about a proposed change to the system. The author is responsible for building consensus within the community and documenting dissenting opinions.

## TIP Rationale

We intend TIPs to be the primary mechanisms for proposing new features, collecting community input on an issue, and for documenting the design decisions for changes to Thales. TIPs will describe standards, protocol specifications, and contract standards. 

A single TIP is highly recommended to contain a single key proposal or new idea. The more focused the TIP, the more successful it is likely to be.

A TIP must meet certain minimum criteria. It must be a clear and complete description of the proposed enhancement. The enhancement must represent a net improvement.

## TIP Work Flow

Parties involved in the process are the *author*, the [*TIP editors*](#TIP-editors), the [Thales Core Contributors] and the Thales community.

:warning: Before you begin, vet your idea, this will save you time. Ask the Thales community first if an idea is original to avoid wasting time on something that will be rejected based on prior research (searching the Internet does not always do the trick). It also helps to make sure the idea is applicable to the entire community and not just the author. Just because an idea sounds good to the author does not mean it will have the intend effect. The appropriate public forum to gauge interest around your TIP or is [the Thales Discord](https://discord.gg/hUt94jD7MY).

Your role as the champion of a TIP is to write the TIP using the style and format described below, shepherd the discussions in the appropriate forums, and build community consensus around the idea. Following is the process that a successful TIP will move along:

Each status change is requested by the TIP author and reviewed by the TIP editors. Use a pull request to update the status. Please include a link to where people should continue discussing your TIP. The TIP editors will process these requests as per the conditions below.

* **Draft** -- This TIP is work-in-progress and being reviewed by a Spartan Council member with the champion.
* **Vote Pending** -- This TIP is scheduled for vote on the Thales Snapshot space.
* **Approved** -- This TIP has passed community governance and is now being prioritised for development.
* **Implemented** -- This TIP has been implemented and deployed to mainnet.
* **Rejected** -- This TIP has failed to reach community consensus.

## What belongs in a successful TIP?

Each TIP should have the following parts:

- Preamble - Headers containing metadata about the TIP, including the TIP number, a short descriptive title (limited to a maximum of 44 characters), and the author details.
- Simple Summary - “If you can’t explain it simply, you don’t understand it well enough.” Provide a simplified and layman-accessible explanation of the TIP.
- Abstract - a short (~200 word) description of the technical issue being addressed.
- Motivation (*optional) - The motivation is critical for TIPs that want to change Thales. It should clearly explain why the existing specification is inadequate to address the problem that the TIP solves. TIP submissions without sufficient motivation may be rejected outright.
- Specification - The technical specification should describe the syntax and semantics of any new feature.
- Rationale - The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.
- Test Cases - Test cases may be added during the implementation phase but are required before implementation.
- Copyright Waiver - All TIPs must be in the public domain. See the bottom of this TIP for an example copyright waiver.

## TIP Formats and Templates

TIPs should be written in [markdown] format.
Image files should be included in a subdirectory of the `assets` folder for that TIP as follows: `assets/TIP-X` (for TIP **X**). When linking to an image in the TIP, use relative links such as `../assets/TIP-X/image.png`.

## TIP Header 

Each TIP document must begin with the following markdown header fields completed, preceded and followed by three hyphens (`---`). 

`- id`: A unique document id. If this field is not present, the document's id will default to its file name (without the extension).

`- title`: The title of your document. If this field is not present, the document's title will default to its id.

`- status`: Draft | Vote Pending | Approved | Implemented | Rejected

`- author`: [a list of the author's or authors' name(s) and/or username(s), or name(s) and email(s)]

`- description`: Short description of TIP 

`- discussions-to`: [URL pointing to the officiali discussion thread]

`- created`: date created on

`- updated`: comma seperated list of dates

`- hide_title`: Whether to hide the title at the top of the doc. (True/False)

`- sidebar_label`: The text shown in the document sidebar and in the next/previous button for this document. If this field is not present, the document's `sidebar_label` will default to its title.

Headers requiring dates will always do so in the format of ISO 8601 (yyyy-mm-dd).

#### `author` header

The `author` header optionally lists the names, email addresses or usernames of the authors/owners of the TIP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the author header value must be:

> [Random J. User] (address@dom.ain)

or

> [Random J. User] (https://github.com/RandomJUser)

if the email address or GitHub username is included. The actual header values should not have a space between the username and parenthetical email or github reference. 

If the email address is not given the author header value must be:

> Random J. User

#### `discussions-to` header

While an TIP is in **Draft** status, a `discussions-to` header will indicate the URL where the TIP is being discussed.

#### `created` header

The `created` header records the date that the TIP was assigned a number. Both headers should be in yyyy-mm-dd format, e.g. 2001-08-14.

#### `updated` header

The `updated` header records the date(s) when the TIP was updated with "substantial" changes. This header is only valid for TIPs of Draft and Active status.

#### `requires` header

TIPs may have a `requires` header, indicating the TIP numbers that this TIP depends on.

## Auxiliary Files

TIPs may include auxiliary files such as diagrams. Such files must be named TIP-XXXX-Y.ext, where “XXXX” is the TIP number, “Y” is a serial number (starting at 1), and “ext” is replaced by the actual file extension (e.g. “png”).

## TIP Editors

The current TIP editors are
  
` * Danijel (@dgornjakovic)`

` * Gorshtak (@Gorshtak)`

` * Vpoklopic (@vpoklopic)`



## TIP Editor Responsibilities

For each new TIP that comes in, an editor does the following:

- Read the TIP to check if it is ready, sound, and complete. The ideas must make technical sense, even if they don't seem likely to get to final status.
- The title should accurately describe the content.
- Check the TIP for language (spelling, grammar, sentence structure, etc.), markup (Github flavored Markdown), code style

If the TIP isn't ready, the editor will send it back to the author for revision, along with specific instructions.

Once the TIP is ready for the repository, the TIP editor will:

- Assign an TIP number (generally the PR number or, if preferred by the author, the Issue # if there was discussion in the Issues section of this repository about this TIP)

- Merge the corresponding pull request

- Send a message back to the TIP author with the next step.

Many TIPs are written and maintained by developers with write access to the Thales codebase. The TIP editors monitor TIP changes, and correct any structure, grammar, spelling, or markup mistakes we see.

The editors don't pass judgment on TIPs. We merely do the administrative & editorial part.

## History

The TIP document was derived heavily from the EIP Ethereum Improvement Proposal and Synthetix Improvement Proposal documents in many places text was simply copied and modified. Any comments about the TIP document should be directed to the TIP editors. The history of the EIP is quoted below from the EIP document  for context:

*"This document (EIP) was derived heavily from [Bitcoin's BIP-0001](https://github.com/bitcoin/bips) written by Amir Taaki which in turn was derived from [Python's PEP-0001](https://www.python.org/dev/peps/). In many places text was simply copied and modified. Although the PEP-0001 text was written by Barry Warsaw, Jeremy Hylton, and David Goodger, they are not responsible for its use..."*

July 10, 2021: TIP 1 has been drafted and submitted as a PR.


See [the revision history for further details](https://github.com/Thales-Markets/).

### Bibliography

1. [Thales Discord](https://discord.com/invite/cFGv5zyVEj)
2. [pull request](https://github.com/Thales-Markets/TIPs/pulls) 
3. [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
4. [Synthetix's TIP-01](https://TIPs.synthetix.io/TIPs/TIP-1)
5. [Bitcoin's BIP-0001](https://github.com/bitcoin/bips)
6. [Python's PEP-0001](https://www.python.org/dev/peps/)


## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
