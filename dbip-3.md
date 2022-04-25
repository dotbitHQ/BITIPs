---
dbip: 3
title: Avatar Data Value Definition
author: Jeff Jing <jeff@did.id>
discussions-to: <URL>
status: Draft
created: 2022-04-25
updated: 2022-04-25
requires 2
---

<!--You can leave these HTML comments in your merged EIP and delete the visible duplicate text guides, they will not appear and may be helpful to refer to if you edit it again. This is the suggested template for new EIPs. Note that an EIP number will be assigned by an editor. When opening a pull request to submit your EIP, please use an abbreviated title in the filename, `eip-draft_title_abbrev.md`. The title should be 44 characters or fewer.-->
## Abstract
<!--A short (~200 word) description of the technical issue being addressed.-->
This DBIP defines a process for retrieving avatar URIs from .bit account, several URI schemes for the .bit 'profile.avatar' text field, and how they should be interpreted by clients wishing to display a user's avatar image.

## Motivation
<!--The motivation is critical for DBIP. It should clearly explain why the state of the art is inadequate to address the problem that the DBIP solves. DBIP submissions without sufficient motivation may be rejected outright.-->
Avatar is a very important symbol of a person, and applications integrating .bit have the need for display users' avatar from .bit. As many apps started specifying avatar profile image as well as let users pick NFT as pfp (profile image), it became obvious to store such information within .bit so that the avatar information can be shared across different applications.

## Specification
<!--The technical specification should describe the standard in detail. The specification should be detailed enough to allow competing, interoperable implementations. -->

### Retrieving the avatar URI

The process for retrieving the avatar URI depends on whether the client has an .bit account to start with.

To determine the avatar URI for an .bit account, the client MUST look up `profile.avatar` field of the specific .bit account to retrieve the avatar URI for the account.

The client MUST treat the absence of `profile.avatar` field and an empty string retrieved identically, as a failure to find a valid avatar URI.

### General Format

The 'avatar' text field MUST be formatted as a URI. Clients MUST ignore URI types they do not recognise, treating them the same as if no value was set for the field.

### Image Types

Clients MUST support images with mime types of `image/jpeg`, `image/png`, and `image/svg+xml`. Clients MAY support additional image types.

### URI Types

All clients SHOULD support the URI schemes defined below. They MAY implement additional schemes not defined in this specification.

**`https`**

If a https URI is provided, it MUST resolve to an avatar image directly. https URLs MUST NOT resolve to HTML pages, metadata, or other content containing the avatar image.

**`ipfs`**

If an [ipfs URI](https://docs.ipfs.io/how-to/address-ipfs-on-web/#native-urls) is provided, it MUST resolve to an avatar image directly. Clients without built-in IPFS support MAY rewrite the URI to a https URL referencing an IPFS gateway as described in [this document](https://docs.ipfs.io/how-to/address-ipfs-on-web/) before resolving it as a https URL.

**`data`**

If a [data URL](https://datatracker.ietf.org/doc/html/rfc2397) is provided, it MUST resolve to an avatar image directly.

**NFTs**

A reference to an NFT may be used as an avatar URI, following the standards defined in [CAIP-22](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-22.md) and [CAIP-29](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-29.md).

Clients MUST support at least ERC721 and ERC1155 type NFTs, and MAY support additional types of NFT.

To resolve an NFT URI, a client follows this process:

1. Retrieve the metadata URI for the token specified in the `avatar` field URI.
2. Resolve the metadata URI, fetching the ERC721 or ERC1155 metadata.
3. Extract the image URL specified in the NFT metadata.
4. Resolve the image URL and use it as the avatar.

Clients MUST support at least `https` and `ipfs` URIs for resolving the metadata URI and the avatar image, and MAY support additional schemes. Clients MAY implement `ifps` scheme support by rewriting the URI to an HTTPS URL referencing an IPFS gateway as described above.

Clients SHOULD additionally take the following verification steps:

1. Get the `owner` field of the .bit account and check if the `owner` and the NFT are on the same chain.
2. Verify that the address from step 1 is an owner of the NFT specified in the URI. If it is not, the client MUST treat the URI as invalid and behave in the same manner as they would if no avatar URI was specified.

Clients MAY support NFT URIs by rewriting them to `https` URIs for a service that provides NFT avatar image resolution support.

## Rationale
<!--The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.-->
The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.-->

## Examples
<!--Please add test cases here if applicable.-->
Please add test cases here if applicable.
```text
eip155:1/erc721:0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d/0 # BAYC token 0
ipfs://QmRRPWG96cmgTn2qSzjwr2qvfNEuhunv6FNeMFGa9bx6mQ # IPFS hash for BAYC token 0 image
https://ipfs.io/ipfs/QmRRPWG96cmgTn2qSzjwr2qvfNEuhunv6FNeMFGa9bx6mQ # HTTPS URL to IPFS gateway for BAYC token 0 image
```

## Backwards Compatibility
<!--All CAIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The DBIP must explain how the author proposes to deal with these incompatibilities. DBIP submissions without a sufficient backwards compatibility treatise may be rejected outright.-->
Not applicable.

## Links
<!--Links to external resources that help understanding the DBIP better. This can e.g. be links to existing implementations.-->
[ENSIP-12](https://docs.ens.domains/ens-improvement-proposals/ensip-12-avatar-text-records)

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).