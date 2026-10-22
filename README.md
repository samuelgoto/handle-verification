# Handle Verification Protocol

This is the working area for the individual Internet-Draft, "Handle Verification Protocol" (HVP).

* [Editor's Copy](https://samuelgoto.github.io/handle-verification/draft-goto-handle-verification.html)
* [Datatracker Page](https://datatracker.ietf.org/doc/draft-goto-handle-verification)

## Abstract

This document defines the Handle Verification Protocol (HVP), which enables web applications to verify that a user controls a handle — such as an AT Protocol handle (`@alice.example`), an ActivityPub address (`@alice@social.example`), or a URL identity used by IndieAuth and Linked Web Storage (`https://alice.example/`) — without integrating with each protocol separately. It defines the notation of handles, how a handle is resolved to a machine-readable identity document and to the issuers authorized to vouch for it, and how a browser obtains a signed Handle Verification Token from such an issuer and presents it to a verifier. HVP generalizes the Email Verification Protocol (EVP) to handles; email addresses remain out of scope and are verified with EVP, which can be used alongside HVP.

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
