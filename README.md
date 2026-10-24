# Handle Verification Protocol

This is the working area for the individual Internet-Draft, "Handle Verification Protocol" (HVP).

* [Editor's Copy](https://samuelgoto.github.io/handle-verification/draft-goto-handle-verification.html)
* [Datatracker Page](https://datatracker.ietf.org/doc/draft-goto-handle-verification)

## Abstract

This document defines the Handle Verification Protocol (HVP), which enables web applications to verify that a user controls a handle without the user typing it and without revealing the application to the user's provider. HVP covers domain handles, such as `@alice.example` (used by the AT Protocol and proposed for ActivityPub), and username handles, such as `@alice@social.example` (used by ActivityPub). Username handles are resolved through WebFinger. Domain handles are resolved to a DID, or, as proposed for ActivityPub, a username handle, through ecosystem-neutral `_handle` and `/.well-known/handle` records that remain compatible with the AT Protocol. In both cases the user explicitly authorizes an issuer, and the browser obtains a signed Handle Verification Token from it and presents it to a verifier. HVP applies the Email Verification Protocol (EVP) to handles.

## Related Work

* [Email Verification Protocol](https://github.com/dickhardt/email-verification) — HVP reuses EVP's token request, key binding, and token formats. Email addresses are verified with EVP, not HVP.
* [IdP Registration API (W3C FedID CG)](https://github.com/w3c-fedid/idp-registration) — a browser API that discovers a user's handles and their providers. It relates to HVP the way the [Email Verification API (WICG)](https://github.com/WICG/email-verification-protocol) relates to EVP.
* [Handles Task Force proposal (W3C SWICG)](https://lists.w3.org/Archives/Public/public-swicg/2026Aug/0015.html) — a proposal to add domain handles to ActivityPub, which HVP aims to reconcile with.

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
