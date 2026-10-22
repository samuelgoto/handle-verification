# Domain Handle Verification Protocol

This is the working area for the individual Internet-Draft, "Domain Handle Verification Protocol" (DHVP).

* [Editor's Copy](https://samuelgoto.github.io/handle-verification/draft-goto-handle-verification.html)
* [Datatracker Page](https://datatracker.ietf.org/doc/draft-goto-handle-verification)

## Abstract

This document defines the Domain Handle Verification Protocol (DHVP), which enables web applications to verify that a user controls a domain handle, such as `@alice.example`, without the user typing it and without revealing the application to the user's provider. Domain handles are used by the AT Protocol and are being proposed for ActivityPub; DHVP covers both interchangeably. It defines the syntax of domain handles, how a handle is resolved to its DID, its DID document, and the issuer authorized to vouch for it (through ecosystem-neutral `_handle` and `/.well-known/handle` records, while remaining compatible with the AT Protocol's `_atproto` and `/.well-known/atproto-did`), and how a browser obtains a signed Handle Verification Token from that issuer and presents it to a verifier. DHVP applies the Email Verification Protocol (EVP) to domain handles.

## Related Work

* [Email Verification Protocol](https://github.com/dickhardt/email-verification) — DHVP reuses EVP's token request, key binding, and token formats. Email addresses are verified with EVP, not DHVP.
* [IdP Registration API (W3C FedID CG)](https://github.com/w3c-fedid/idp-registration) — a browser API that discovers a user's handles and their providers. It relates to DHVP the way the [Email Verification API (WICG)](https://github.com/WICG/email-verification-protocol) relates to EVP.
* [Handles Task Force proposal (W3C SWICG)](https://lists.w3.org/Archives/Public/public-swicg/2026Aug/0015.html) — a proposal to add domain handles to ActivityPub, which DHVP aims to reconcile with.

## Discussion

Discussion of this draft takes place in the [issue tracker](https://github.com/samuelgoto/handle-verification/issues).

## Command Line Usage

Formatted text and HTML versions of the draft can be built using `make`.

```sh
$ make
```

Command line usage requires that you have the necessary software installed. See [the instructions](https://github.com/martinthomson/i-d-template/blob/main/doc/SETUP.md).

## Authors

- Sam Goto (Google)
