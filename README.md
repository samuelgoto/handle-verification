# Handle Verification Protocol

This is the working area for the individual Internet-Draft, "Handle Verification Protocol" (HVP).

* [Editor's Copy](https://samuelgoto.github.io/handle-verification/draft-goto-handle-verification.html)
* [Datatracker Page](https://datatracker.ietf.org/doc/draft-goto-handle-verification)

## Abstract

This document defines the Handle Verification Protocol (HVP), which enables web applications to verify that a user controls an AT Protocol handle, such as `@alice.example`, without the user typing it and without revealing the application to the user's provider. It defines the syntax of handles, how a handle is resolved to its DID, its DID document, and the issuers authorized to vouch for it, and how a browser obtains a signed Handle Verification Token from such an issuer and presents it to a verifier. HVP applies the Email Verification Protocol (EVP) to AT Protocol handles; other ecosystems, such as ActivityPub, IndieAuth, and Linked Web Storage, are expected to be addressed by separate protocols that reuse the same EVP-based framework.

## Related Work

* [Email Verification Protocol](https://github.com/dickhardt/email-verification) — HVP reuses EVP's token request, key binding, and token formats. Email addresses are verified with EVP, not HVP.
* [IdP Registration API (W3C FedID CG)](https://github.com/w3c-fedid/idp-registration) — a browser API that discovers a user's handles and their providers. It relates to HVP the way the [Email Verification API (WICG)](https://github.com/WICG/email-verification-protocol) relates to EVP.

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
