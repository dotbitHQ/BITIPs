---
dbip: 1
title: DBIP Purpose and Guidelines
status: Active
author: Jeff Jing <jeff@did.id>
created: 2022-04-25
updated: 2022-04-25
---

## What is an DBIP?

DBIP stands for **.bit Improvement Proposal**. An DBIP is a design document providing information to the .bit community or describing a new feature for .bit or its processes or environment. The DBIP should provide a concise technical specification of the feature and a rationale for the feature. The DBIP author is responsible for building consensus within the community and documenting dissenting opinions.

## DBIP Rationale

We intend DBIPs to be the primary mechanisms for proposing new features, for collecting community technical input on an issue, and for documenting the design decisions that have gone into .bit. Because the DBIPs are maintained as text files in a versioned repository, their revision history is the historical record of the feature proposal.

## DBIP Formats and Templates

DBIPs should be written in [markdown] format.
Image files should be included in a subdirectory of the `assets` folder for that DBIP as follows: `assets/dbip-N` (where **N** is to be replaced with the DBIP number). When linking to an image in the DBIP, use relative links such as `./assets/dbip-1/image.png`.

## DBIP Header Preamble

Each DBIP must begin with an [RFC 822](https://www.ietf.org/rfc/rfc822.txt) style header preamble, preceded and followed by three hyphens (`---`). This header is also termed ["front matter" by Jekyll](https://jekyllrb.com/docs/front-matter/). The headers must appear in the following order. Headers marked with "*" are optional and are described below. All other headers are required.

` dbip:` <DBIP number> (this is determined by the DBIP editor)

` title:` <DBIP title>

` author:` <a list of the author's or authors' name(s) and/or username(s), or name(s) and email(s). Details are below.>

` * discussions-to:` \<an url pointing to the official discussion thread\>

` status:` <Draft | Last Call | Accepted | Active | Abandoned | Rejected | Superseded>

`* review-period-end:` <date review period ends>

` * category:` <Core | Networking | Interface>

` created:` <date created on>

` * updated:` <comma separated list of dates>

` * requires:` <DBIP number(s)>

` * replaces:` <DBIP number(s)>

` * superseded-by:` <DBIP number(s)>

Headers that permit lists must separate elements with commas.

Headers requiring dates will always do so in the format of ISO 8601 (yyyy-mm-dd).

#### `author` header

The `author` header optionally lists the names, email addresses or usernames of the authors/owners of the DBIP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the author header value must be:

> Random J. User &lt;address@dom.ain&gt;

or

> Random J. User (@username)

if the email address or GitHub username is included, and

> Random J. User

if the email address is not given.

#### `resolution` header

#### `discussions-to` header

While a DBIP is a draft, a `discussions-to` header will indicate the mailing list or URL where the DBIP is being discussed.

As a single exception, `discussions-to` cannot point to GitHub pull requests.

#### `created` header

The `created` header records the date that the DBIP was assigned a number. Both headers should be in yyyy-mm-dd format, e.g. 2001-08-14.

#### `updated` header

The `updated` header records the date(s) when the DBIP was updated with "substantial" changes. This header is only valid for DBIPs of Draft and Active status.

#### `requires` header

DBIPs may have a `requires` header, indicating the DBIP numbers that this DBIP depends on.

#### `superseded-by` and `replaces` headers

DBIPs may also have a `superseded-by` header indicating that an DBIP has been rendered obsolete by a later document; the value is the number of the DBIP that replaces the current document. The newer DBIP must have a `replaces` header containing the number of the DBIP that it rendered obsolete.

## Auxiliary Files

DBIPs may include auxiliary files such as diagrams. Such files must be named DBIP-XXXX-Y.ext, where “XXXX” is the DBIP number, “Y” is a serial number (starting at 1), and “ext” is replaced by the actual file extension (e.g. “png”).

## Transferring DBIP Ownership

It occasionally becomes necessary to transfer ownership of DBIPs to a new champion. In general, we'd like to retain the original author as a co-author of the transferred DBIP, but that's really up to the original author. A good reason to transfer ownership is because the original author no longer has the time or interest in updating it or following through with the DBIP process, or has fallen off the face of the 'net (i.e. is unreachable or isn't responding to email). A bad reason to transfer ownership is because you don't agree with the direction of the DBIP. We try to build consensus around an DBIP, but if that's not possible, you can always submit a competing DBIP.

If you are interested in assuming ownership of an DBIP, send a message asking to take over, addressed to both the original author and the DBIP editor. If the original author doesn't respond to email in a timely manner, the DBIP editor will make a unilateral decision (it's not like such decisions can't be reversed :)).

## DBIP Editors

The current DBIP editors are

` * jeff <jeff@did.id>`

## DBIP Editor Responsibilities

For each new DBIP that comes in, an editor does the following:

- Read the DBIP to check if it is ready: sound and complete. The ideas must make technical sense, even if they don't seem likely to get to final status.
- The title should accurately describe the content.
- Check the DBIP for language (spelling, grammar, sentence structure, etc.), markup (Github flavored Markdown), code style

If the DBIP isn't ready, the editor will send it back to the author for revision, with specific instructions.

Once the DBIP is ready for the repository, the DBIP editor will:

- Assign an DBIP number (generally the PR number or, if preferred by the author, the Issue # if there was discussion in the Issues section of this repository about this DBIP)

- Merge the corresponding pull request

- Send a message back to the DBIP author with the next step.

The editors don't pass judgment on DBIPs. We merely do the administrative & editorial part.

## History

This document was derived heavily from [CAIP's CAIP-0001] by ligi, which in turn was derived from [Bitcoin's BIP-0001] written by Amir Taaki, which eventually was derived from [Python's PEP-0001]. In many places text was simply copied and modified. Although the PEP-0001 text was written by Barry Warsaw, Jeremy Hylton, and David Goodger, they are not responsible for its use in the Ethereum Improvement Process, and should not be bothered with technical questions specific to DBIPs. Please direct all comments to the DBIP editors.

### Bibliography

[markdown]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
[CAIP's CAIP-0001]: https://github.com/ChainAgnostic/CAIPs
[Bitcoin's BIP-0001]: https://github.com/bitcoin/bips
[Python's PEP-0001]: https://www.python.org/dev/peps

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).