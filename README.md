# Handle Verification Protocol

This is the working area for the individual Internet-Drafts that let web applications verify that a user controls a handle, without the user typing it and without revealing the application to the user's provider. All apply the Email Verification Protocol (EVP) to handles: the user explicitly authorizes an issuer, and the browser obtains a signed Handle Verification Token (HVT) from it and presents it to a verifier.

## Handle Verification Protocol (HVP)

* [Editor's Copy](https://samuelgoto.github.io/handle-verification/draft-goto-handle-verification.html)
* [Datatracker Page](https://datatracker.ietf.org/doc/draft-goto-handle-verification)

Covers domain handles, and is designed to be extended to other forms of handle. Domain handles are handles such as `@alice.example` (used by the AT Protocol and proposed for ActivityPub), which are resolved to a DID through ecosystem-neutral `_handle` and `/.well-known/handle` records that remain compatible with the AT Protocol, and the DID document names the authorized issuer. HVP also defines the issuer metadata, the HVT request, the HVT, and the verification of the HVT and its key binding (HVT+KB).

## URL Handle Verification Protocol (URL-HVP)

* [Editor's Copy](https://samuelgoto.github.io/handle-verification/draft-goto-url-handle-verification.html)
* [Datatracker Page](https://datatracker.ietf.org/doc/draft-goto-url-handle-verification)

Extends HVP to URL handles: users identified by an `https` URL, such as a Solid WebID, an ActivityPub actor, or an IndieAuth website. The URL is fetched with content negotiation, and its identity document names the authorized issuer with a `handleIssuer` property or a `handle-issuer` link, without anything specific to an ecosystem. Issuance and verification are those of HVP.

## Username Handle Verification Protocol (UHVP)

* [Editor's Copy](https://samuelgoto.github.io/handle-verification/draft-goto-username-handle-verification.html)
* [Datatracker Page](https://datatracker.ietf.org/doc/draft-goto-username-handle-verification)

Builds on URL-HVP to cover username handles, such as `@alice@social.example` (used by ActivityPub implementations), which are mapped through WebFinger to the URL of their account, which is then resolved as a URL handle. It also lets a domain handle name a username handle, with a `webfinger=` record. Issuance and verification are those of HVP.

## Related Work

* [Email Verification Protocol](https://github.com/dickhardt/email-verification) — the drafts reuse EVP's token request, key binding, and token formats. Email addresses are verified with EVP.
* [IdP Registration API (W3C FedID CG)](https://github.com/w3c-fedid/idp-registration) — a browser API that discovers a user's handles and their providers. It relates to HVP the way the [Email Verification API (WICG)](https://github.com/WICG/email-verification-protocol) relates to EVP.
* [Handles Task Force proposal (W3C SWICG)](https://lists.w3.org/Archives/Public/public-swicg/2026Aug/0015.html) — a proposal to add domain handles to ActivityPub, which the drafts aim to reconcile with.

## Discussion

Discussion of these drafts takes place in the [issue tracker](https://github.com/samuelgoto/handle-verification/issues).

## Command Line Usage

Formatted text and HTML versions of the drafts can be built using `make`.

```sh
$ make
```

Command line usage requires that you have the necessary software installed. See [the instructions](https://github.com/martinthomson/i-d-template/blob/main/doc/SETUP.md).

## Authors

- Sam Goto (Google)
