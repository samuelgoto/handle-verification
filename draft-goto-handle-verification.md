%%%
title = "Handle Verification Protocol"
abbrev = "HVP"
ipr = "trust200902"
area = "Security"
workgroup = "TBD"
keyword = ["handle", "verification", "identity", "authentication", "atproto", "activitypub", "did"]

[seriesInfo]
status = "standard"
name = "Internet-Draft"
value = "draft-goto-handle-verification-latest"
stream = "IETF"

date = 2026-10-23T00:00:00Z

[[author]]
initials = "S."
surname = "Goto"
fullname = "Sam Goto"
organization = "Google"
  [author.address]
  email = "goto@google.com"

%%%

<reference anchor="EVP" target="https://datatracker.ietf.org/doc/draft-hardt-email-verification/">
  <front>
    <title>Email Verification Protocol</title>
    <author initials="D." surname="Hardt" fullname="Dick Hardt">
      <organization>Hellō</organization>
    </author>
    <author initials="S." surname="Goto" fullname="Sam Goto">
      <organization>Google</organization>
    </author>
    <date year="2026"/>
  </front>
  <seriesInfo name="Internet-Draft" value="draft-hardt-email-verification-latest"/>
</reference>

<reference anchor="IDP-REGISTRATION" target="https://w3c-fedid.github.io/idp-registration/">
  <front>
    <title>IdP Registration API</title>
    <author>
      <organization>W3C Federated Identity Community Group</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

<reference anchor="EMAIL-VERIFICATION-API" target="https://github.com/WICG/email-verification-protocol">
  <front>
    <title>Email Verification API</title>
    <author>
      <organization>W3C Web Incubator Community Group</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

<reference anchor="FEDCM" target="https://w3c-fedid.github.io/FedCM/">
  <front>
    <title>Federated Credential Management API</title>
    <author>
      <organization>W3C Federated Identity Working Group</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

<reference anchor="ATPROTO" target="https://atproto.com/specs/atp">
  <front>
    <title>AT Protocol</title>
    <author>
      <organization>Bluesky Social PBC</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

<reference anchor="ATPROTO-HANDLE" target="https://atproto.com/specs/handle">
  <front>
    <title>AT Protocol: Handle</title>
    <author>
      <organization>Bluesky Social PBC</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

<reference anchor="ATPROTO-URI" target="https://atproto.com/specs/at-uri-scheme">
  <front>
    <title>AT Protocol: AT URI Scheme</title>
    <author>
      <organization>Bluesky Social PBC</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

<reference anchor="ATPROTO-DID" target="https://atproto.com/specs/did">
  <front>
    <title>AT Protocol: DID</title>
    <author>
      <organization>Bluesky Social PBC</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

<reference anchor="ATPROTO-OAUTH" target="https://atproto.com/specs/oauth">
  <front>
    <title>AT Protocol: OAuth</title>
    <author>
      <organization>Bluesky Social PBC</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

<reference anchor="ACTIVITYPUB" target="https://www.w3.org/TR/activitypub/">
  <front>
    <title>ActivityPub</title>
    <author>
      <organization>W3C</organization>
    </author>
    <date year="2018" month="January"/>
  </front>
  <refcontent>W3C Recommendation</refcontent>
</reference>

<reference anchor="HANDLES-TF" target="https://lists.w3.org/Archives/Public/public-swicg/2026Aug/0015.html">
  <front>
    <title>Proposal to Create Handles Task Force</title>
    <author initials="A." surname="Ahooja" fullname="Anuj Ahooja">
      <organization/>
    </author>
    <author initials="E." surname="Smith" fullname="Emelia Smith">
      <organization/>
    </author>
    <date year="2026" month="August"/>
  </front>
  <refcontent>W3C Social Web Incubator Community Group</refcontent>
</reference>

<reference anchor="URL-HVP" target="https://samuelgoto.github.io/handle-verification/draft-goto-url-handle-verification.html">
  <front>
    <title>URL Handle Verification Protocol</title>
    <author initials="S." surname="Goto" fullname="Sam Goto">
      <organization>Google</organization>
    </author>
    <author fullname="@bumblefudge.com">
      <organization/>
    </author>
    <date year="2026"/>
  </front>
  <seriesInfo name="Internet-Draft" value="draft-goto-url-handle-verification-latest"/>
</reference>

<reference anchor="UHVP" target="https://samuelgoto.github.io/handle-verification/draft-goto-username-handle-verification.html">
  <front>
    <title>Username Handle Verification Protocol</title>
    <author initials="S." surname="Goto" fullname="Sam Goto">
      <organization>Google</organization>
    </author>
    <date year="2026"/>
  </front>
  <seriesInfo name="Internet-Draft" value="draft-goto-username-handle-verification-latest"/>
</reference>

<reference anchor="WHATWG.HTML" target="https://html.spec.whatwg.org/multipage/">
  <front>
    <title>HTML Standard</title>
    <author>
      <organization>WHATWG</organization>
    </author>
    <date year="2026"/>
  </front>
  <refcontent>Living Standard</refcontent>
</reference>

<reference anchor="DID-PLC" target="https://web.plc.directory/spec/v0.1/did-plc">
  <front>
    <title>DID PLC Method</title>
    <author>
      <organization>Bluesky Social PBC</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

<reference anchor="DID-WEB" target="https://w3c-ccg.github.io/did-method-web/">
  <front>
    <title>did:web Method Specification</title>
    <author>
      <organization>W3C Credentials Community Group</organization>
    </author>
    <date year="2024"/>
  </front>
</reference>

<reference anchor="DID-CORE" target="https://www.w3.org/TR/did-1.0/">
  <front>
    <title>Decentralized Identifiers (DIDs) v1.0</title>
    <author>
      <organization>W3C</organization>
    </author>
    <date year="2022" month="July"/>
  </front>
  <refcontent>W3C Recommendation</refcontent>
</reference>

.# Abstract

This document defines the Handle Verification Protocol (HVP), the HTTP-level protocol by which a browser obtains a signed Handle Verification Token (HVT) from an issuer attesting that the user controls a *handle*, and presents it to a verifier. This document covers *domain handles*, such as `@alice.example`, which are used by the AT Protocol and are being proposed for ActivityPub, and is designed to be extended to other forms of handle, such as the username handles of ActivityPub implementations. HVP uses the same three-party model as the Email Verification Protocol ([@!EVP]), in which the browser intermediates between the verifier and the issuer and hides the verifier's identity from the issuer.

This document defines the syntax of domain handles, their resolution, through a DID document, to a unique user identifier and to the issuer authorized to vouch for them, in a way that is backwards compatible with the AT Protocol, the HVT request, the HVT, and the verification of the HVT and its key binding (HVT+KB). The browser API, that is, how the user selects a handle and how the HVT+KB is delivered to the verifier, is defined separately, for example by the W3C IdP Registration API ([@?IDP-REGISTRATION]).

.# Discussion Venues

*Note: This section is to be removed before publishing as an RFC.*

Source for this draft and an issue tracker can be found at https://github.com/samuelgoto/handle-verification.

{mainmatter}

# Introduction

Social networks built on open protocols let any server host a user's account, and let users bring their own domain name as their identity. The AT Protocol ([@?ATPROTO]) identifies every user with a *handle* that is a DNS name, such as `@alice.example`, which resolves to a stable decentralized identifier (DID). ActivityPub ([@?ACTIVITYPUB]) implementations identify users with handles of the form `@alice@social.example`, and the W3C Social Web Incubator Community Group is considering adding domain handles, such as `@alice.example`, as an alternative ([@?HANDLES-TF]). The result is an open federation: a website that wants to accept these users cannot know their providers in advance.

Email shows that an open federation can still be verified. A verifier accepts an email address at any mail domain without a prior relationship with the domain, and the Email Verification Protocol ([@!EVP]) lets the verifier check such an address with a signed token. HVP applies that model to domain handles, in a way that does not depend on which ecosystem the user's account belongs to.

## The Problem

A website that wants to let users sign in with a handle today has to integrate with each ecosystem separately. For the AT Protocol, it uses AT Protocol OAuth ([@?ATPROTO-OAUTH]): it presents a text field for the user to type their handle, resolves the handle to a DID and PDS, discovers the PDS's authorization server, and redirects the user to it. ActivityPub has no common sign-in protocol, so websites typically use the OAuth API of each server implementation. In both cases:

- the user has to know and type their handle, which experience with OpenID 2.0 suggests many users do not;
- the website is identified to the user's authorization server, which learns every site the user signs in to;
- the browser, which often already knows the user's handles, has no role in the flow, unlike in [@!EVP] and the Email Verification API ([@?EMAIL-VERIFICATION-API]), which let the browser integrate verification into autofill and form submission, into a JavaScript API, or into FedCM ([@?FEDCM]); and
- each authorization server and each website implements the protocol independently, and nothing between them checks the result. An authorization server learns whether it interoperates with a website only by testing against that website, so interoperability across many authorization servers and many websites rests on conformance testing and certification rather than on the protocol itself.

## Solution

HVP separates the problem into three parts:

1. **Syntax** ((#handles)): what a domain handle is, and how it is written and normalized.
2. **Resolution** ((#resolution)): how a domain handle is resolved to a DID, checked against the handle, and turned into the issuer that the user has authorized to vouch for it, in a way that is backwards compatible with the AT Protocol ((#atproto-compat)).
3. **Issuance and verification**: how a browser obtains a Handle Verification Token (HVT) from the authorized issuer, and how a verifier verifies it. This part reuses the token request, key binding, and token format of EVP.

Nothing in issuance or verification depends on the ecosystem that the account belongs to. A verifier that implements HVP accepts domain handles of every ecosystem.

HVP keeps the privacy properties of EVP: the browser intermediates between the verifier and the issuer, so the issuer does not learn which verifier the user is signing in to.

## Scope

This document covers domain handles, which consist of a DNS name alone. Two companion documents extend it: [@?URL-HVP] covers URL handles, that is, users identified by an `https` URL, such as a Solid WebID, an ActivityPub actor, or an IndieAuth personal website, and [@?UHVP] builds on it to cover username handles, which combine a user name and a domain, such as `@alice@social.example`, by mapping them to the URL of their account with WebFinger. Both reuse the issuance and verification defined here. HVP is designed so that other forms of handle can be added in this way, with a resolution of their own, without changing issuance or verification. Email addresses are out of scope: they are verified with [@!EVP].

HVP provides verified identification, for example to sign a user in: it tells the verifier that the user controls a handle, and which unique user identifier that handle resolves to. It does not provide authorization: an HVT grants no access to the user's account, and cannot be used to read or publish content or to act on the user's behalf. A verifier that needs such access continues to use the ecosystem's authorization protocol, such as AT Protocol OAuth ([@?ATPROTO-OAUTH]), and can use HVP and that protocol together, for example by signing the user in with HVP and requesting authorization later, only when it needs it. See (#why-not-oauth).

## Relationship to EVP

HVP reuses the mechanics of [@!EVP] (the token request, key binding, and token format) with the substitutions described in this document. A browser API can offer both, using EVP for email addresses and HVP for handles.

## Relationship to the Browser API

This document specifies the IETF protocol aspects of handle verification: the HTTP-level interactions between the browser, the issuer, and the verifier, and the lookups needed to resolve a handle. How the browser learns about the user's handles, how the user selects one, and how the browser communicates with the verifier are defined separately. The W3C IdP Registration API ([@?IDP-REGISTRATION]), an extension of FedCM ([@?FEDCM]), is one such API. See (#idp-registration).

# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 [@!RFC2119] [@!RFC8174] when, and only when, they appear in all capitals, as shown here.

This document uses the following terms:

Handle:
: A human-readable identifier of a user, displayed with a leading `@`. In this document, a handle is a domain handle. A handle is not necessarily permanent: a user can change it. See (#handles).

Domain handle:
: A handle that consists of a DNS name, such as `alice.example`, displayed as `@alice.example`.

Unique user identifier:
: An identifier of the user's account that resolution produces, and that the HVT carries in its `sub` claim. In this document, it is the DID that the handle resolves to. Unlike a handle, which can change hands and point to different accounts over time, it identifies one account.

DID:
: A decentralized identifier ([@?DID-CORE]) that identifies a user's account more permanently than its handle, such as `did:plc:bftbdgcbe4zclvpkboe4hleq` or `did:web:alice.example`. A handle resolves to a DID.

DID document:
: The document that a DID resolves to. It lists the handle that the account claims, the account's services, and, for HVP, its authorized issuer.

Authorized issuer:
: The issuer identifier that resolution yields for a handle: the one that its DID document names with its `HandleIssuer` service ((#handle-issuer)). Only the authorized issuer can issue an HVT that a verifier accepts for that handle. A handle has at most one authorized issuer.

Issuer:
: A service that verifies the user controls a handle and issues HVTs for it, typically the server that hosts the user's account, such as an AT Protocol personal data server (PDS) or an ActivityPub server. An issuer is identified by an issuer identifier ((#issuer-identifier)).

Handle Verification Token (HVT):
: A JWT ([@!RFC7519]) issued by an issuer that contains a handle, the unique user identifier it resolves to, and the browser's public key. See (#hvt).

HVT+KB:
: An HVT combined with a Key Binding JWT that binds it to a verifier and a session. See (#kb).

Verifier:
: The party, typically a website, to which the browser presents an HVT+KB, and which verifies it to learn that the user controls a handle. It corresponds to the relying party (RP) of [@!EVP] and of federated sign-in protocols.

# Protocol Flow {#protocol-flow}

The protocol involves three parties: the verifier, the browser, and the issuer. The following diagram shows the protocol flow:

```
Step                       Verifier     Browser              Issuer
                               |            |                    |
3.1 Handle Discovery           |      [obtain handle from user]  |
                               |            |                    |
3.2 Session Binding            |--- nonce ->|                    |
                               |            |                    |
3.3 Handle Resolution          |   [resolve handle: subject      |
                               |    identifier, issuer]          |
                               |            |                    |
3.4 HVT Request                |            |-- POST /issuance ->|
                               |            |   (handle, did)    |
                               |            |                    |
3.5 HVT Issuance               |            |<------- HVT -------|
                               |            |                    |
3.6 KB Creation                |        [create KB-JWT]          |
                               |            |                    |
3.7 HVT+KB Presentation        |<-- HVT+KB -|                    |
                               |            |                    |
3.8 HVT+KB Verification [resolve handle;    |                    |
                         verify HVT+KB]     |                    |
```

The flow is the same as the flow of [@!EVP], with two differences: the browser and the verifier *resolve* the handle ((#resolution)) where EVP looks up a DNS delegation record, and the token is an HVT rather than an EVT.

## Handle Discovery {#handle-discovery}

How the browser assembles candidate handles, from its own store, from accounts that an issuer pushes or the browser pulls, or from the user typing one, is defined by the browser API ([@?IDP-REGISTRATION]) and is out of scope for this document. When the browser starts from text that the user typed, it parses it as described in (#parsing).

## Session Binding {#session-binding}

As in [@!EVP]: the verifier generates a cryptographically random nonce with at least 128 bits of entropy and binds it to a session it has with the browser. How the verifier provides the nonce to the browser is defined by the browser API.

## Handle Resolution {#flow-resolution}

The browser resolves the handle as described in (#resolution). Resolution produces the unique user identifier and the authorized issuer. The browser fetches the issuer's metadata ((#issuer-metadata)). From this point onward, the handle and the unique user identifier are never altered: they are sent byte-for-byte in the HVT request, and returned byte-for-byte in the `handle` and `sub` claims.

## HVT Request {#token-request}

The browser sends an HVT request to the issuer's `issuance_endpoint`. The request is the token request of [@!EVP], with the substitutions listed in (#token-request-details).

## HVT Issuance {#hvt-issuance}

The issuer verifies the request, checks that the browser's cookies represent a signed-in user who controls the handle, and returns an HVT ((#hvt)) as the value of `issuance_token` in an `application/json` response, as in [@!EVP].

## KB Creation {#kb-creation}

The browser verifies the HVT ((#hvt-verification)), additionally confirming that the `handle` and `sub` claims are byte-for-byte identical to the handle and unique user identifier it requested and that the `cnf.jwk` claim matches the public key it generated. It then creates a KB-JWT and combines it with the HVT as described in (#kb).

## HVT+KB Presentation {#token-presentation}

The browser provides the HVT+KB to the verifier. This mechanism is defined by the browser API.

## HVT+KB Verification {#token-verification}

The verifier verifies the HVT+KB as described in (#verification). The verifier resolves the handle itself, and does not rely on the browser's resolution. If verification succeeds, the verifier has verified that the user controls the handle in the `handle` claim, and has learned the user's unique user identifier in the `sub` claim.

# Handles {#handles}

A *domain handle* is a DNS name, such as `alice.example`. Domain handles are the handles of the AT Protocol ([@?ATPROTO-HANDLE]), and the domain-based handles proposed for ActivityPub ([@?HANDLES-TF]). In DID documents, a domain handle is written as an `at` URI ([@?ATPROTO-URI]), `at://` followed by the handle, such as `at://alice.example`, as in the AT Protocol. This document uses that form for domain handles of every ecosystem.

A handle is displayed with a leading `@`, as in `@alice.example`, and is carried in the protocol without it.

## Domain Handle Syntax {#handle-syntax}

A domain handle MUST satisfy the following rules, which are a synthesis of the hostname rules of [@!RFC1035], [@?RFC3696] and [@!RFC3986]:

- The handle contains only ASCII characters, and is at most 253 characters long.
- The handle consists of at least two labels separated by ASCII periods (`.`). It has no leading or trailing period.
- Each label is between 1 and 63 characters long, and contains only ASCII letters, digits, and hyphens (`-`). A label does not start or end with a hyphen.
- The last label (the top-level domain) does not start with a digit. As a consequence, IP addresses are not handles.

Internationalized domain names are written in their A-label form ([@!RFC5890]), for example `xn--ls8h.example`.

In ABNF ([@!RFC5234]), before normalization:

```abnf
handle    = 1*( label "." ) tld-label
label     = alnum [ *61( alnum / "-" ) alnum ]
tld-label = ALPHA [ *61( alnum / "-" ) alnum ]
alnum     = ALPHA / DIGIT
```

with the additional constraint that the whole `handle` is at most 253 characters long. A reference regular expression is:

```
^([a-zA-Z0-9]([a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?\.)+
[a-zA-Z]([a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?$
```

(The regular expression is shown on two lines for display; it is a single expression.)

The following top-level domains are syntactically valid in a handle, but a handle whose domain ends in one of them MUST fail resolution: `.alt`, `.arpa`, `.example`, `.internal`, `.invalid`, `.local`, `.localhost`, and `.onion`. The `.test` top-level domain MAY be used in development, and MUST fail resolution in production deployments. (The examples in this document use `.example` and so would fail resolution.)

> Open Issue: How internationalized handles are displayed, and how homoglyph attacks are mitigated, in coordination with the internationalization work of [@?HANDLES-TF].

## Normalization {#normalization}

Handles are case-insensitive. The *normalized* form of a handle is the handle converted to ASCII lowercase. Every handle in this protocol (in the `handle` claim, and in comparisons) is in normalized form, and every comparison of handles is a byte-for-byte comparison of normalized handles.

## Parsing User Input {#parsing}

To parse a handle that a user typed:

1. Strip leading and trailing ASCII whitespace.
2. If the input starts with `at://`, remove it, or else if it starts with `@`, remove it.
3. If the input then ends with a single `/`, remove it.
4. Normalize the rest ((#normalization)), and check that it satisfies (#handle-syntax).

If any step fails, the input is not a handle.

| Input | Handle |
|-------|--------|
| `@Alice.Example`, `alice.example`, `at://alice.example` | `alice.example` |
| `alice@mail.example`, `@alice@social.example` | not a domain handle |
| `https://alice.example/` | not a domain handle (URL handle, see [@?URL-HVP]) |
| `@192.0.2.1`, `@com` | not a handle |

An input that contains `@` after its leading `@` is not a domain handle: `alice@mail.example` is an email address, which a browser API can verify with [@!EVP], and `@alice@social.example` is a username handle, which a browser API can verify with [@?UHVP].

# Handle Resolution {#resolution}

*Resolution* takes a normalized handle and produces:

- the user's *unique user identifier*, which is the subject of the HVT; and
- the *authorized issuer* for the handle.

A domain handle is resolved through a DID ((#resolution-steps)). Resolution checks that the handle and the DID refer to each other, so that a handle cannot claim an account that does not agree to it, and finds the issuer that the user has explicitly authorized.

Both the browser and the verifier perform resolution. The browser does it to find an issuer to ask for an HVT; the verifier does it to check that the HVT was issued by an issuer that is authorized for the handle ((#verification)).

The following rules apply to every resolution step:

- DNS queries use the resolving party's DNS resolver. DNSSEC is not required, but see (#dns-security).
- HTTP requests use the `https` scheme, MUST NOT include credentials (cookies or HTTP authentication), and SHOULD NOT include a `Referer` header. When the browser makes them, they SHOULD be made from an opaque origin, so that the servers involved do not learn which verifier the user is visiting.
- Redirects are followed only to `https` URLs, and at most 5 times for a single request.
- Responses are subject to reasonable limits on size and time, and resolving parties take the precautions of (#ssrf).

## Domain Handles {#resolution-steps}

A domain handle resolves to a DID ([@?DID-CORE]), which is its unique user identifier, and whose DID document claims the handle back and names the authorized issuer. This generalizes the handle resolution of the AT Protocol ([@?ATPROTO-HANDLE], [@?ATPROTO-DID]): it uses ecosystem-neutral names for the records that map a handle to its DID, also accepts the names of the AT Protocol ((#atproto-compat)), and adds the extraction of the authorized issuer.

Given a normalized domain handle *handle*:

1. **Handle to DID.** Perform the following lookups. A DID MUST use the `plc` method ([@?DID-PLC]) or the `web` method ([@?DID-WEB]); otherwise fail. If both lookups yield a DID, and the DIDs differ, fail. If either lookup yields a DID, it is the handle's DID. If neither yields anything, the resolving party MUST fall back to the lookups of existing AT Protocol handles ((#atproto-compat)), but only if both lookups established that the handle names nothing: that is, if the DNS query returned no `TXT` record whose value starts with a recognized key, or no record at all, and the well-known request returned a 404 (Not Found) or 410 (Gone) response, or a document with no recognized member. If either lookup failed in any other way, for example because of a DNS server failure, a timeout, or a server error, fail. A resolving party MAY perform the lookups of (#atproto-compat) in parallel with these, to avoid adding a round trip, and use their results only when it falls back. A handle near the 253-character limit cannot use the DNS lookups, because the prefix would push the query name over the limit; the well-known lookups work for such handles.
   - **DNS `TXT` record.** Query `TXT` records at the name `_handle.` *handle*. A record whose value starts with `did=` names a DID, in the remainder of the value. Records whose value starts with anything else are ignored. This method aligns with [@?RFC1464].
   - **Well-known document.** `GET https://` *handle* `/.well-known/handle`. A 2xx response with the `application/json` media type is a JSON object whose `did` member, if present, names a DID. Other members are ignored.

2. **DID to DID document.** Resolve the DID to its DID document ([@?DID-CORE]), whose `id` member MUST be identical to the DID:
   - For `did:plc`, `GET` the DID from a PLC directory, by default `https://plc.directory/` followed by the DID.
   - For `did:web`, `GET https://` *domain* `/.well-known/did.json`, where *domain* is the method-specific identifier ([@?DID-WEB]), such as `alice.example` for `did:web:alice.example`. A `did:web` DID with a path is not supported, as in the AT Protocol ([@?ATPROTO-DID]).

3. **Back-link.** Find the first element of the DID document's `alsoKnownAs` array that is `at://` followed by a string that satisfies (#handle-syntax). After normalization, that string MUST be identical to *handle*. Otherwise fail. This check ensures that a DID document cannot be claimed by a handle that it did not agree to.

4. **Issuer.** The authorized issuer is the `serviceEndpoint` of the DID document's `HandleIssuer` service ((#handle-issuer)). If there is none, fail.

If any step fails, resolution fails. The unique user identifier is the DID.

For example, the handle `@samuelgoto.bsky.social` resolves as follows at the time of writing, through the AT Protocol names ((#atproto-compat)), since it publishes none of the new ones:

```
GET https://samuelgoto.bsky.social/.well-known/atproto-did
  -> did:plc:bftbdgcbe4zclvpkboe4hleq
GET https://plc.directory/did:plc:bftbdgcbe4zclvpkboe4hleq
  -> alsoKnownAs: ["at://samuelgoto.bsky.social"]
```

so its unique user identifier is the DID `did:plc:bftbdgcbe4zclvpkboe4hleq`. Its DID document has no `HandleIssuer` service yet, so it has no authorized issuer. See (#examples).

Because records and members with other keys are ignored, other kinds of records can be added later without affecting resolving parties that do not support them. For example, [@?UHVP] defines the `webfinger=` key and the `webfinger` member, which let a domain handle name a username handle instead of a DID.

> Open Issue: Other kinds of records could be added later with keys of their own: for example, `domain=` for another domain handle, resolved recursively and failing when a loop is detected, or `email=` for an email address verified with [@!EVP]. A handle could also be allowed to name several identifiers, any one of which proves it; this would require a rule for which unique user identifier an HVT for the handle carries, because each resolves to a different one, and a verifier identifies accounts by it.

> Open Issue: The SWICG Handles Task Force proposes `/.well-known/activitypub-actor`, a JSON document that refers to an ActivityPub actor, to resolve domain handles in ActivityPub ([@?HANDLES-TF]). This document proposes `/.well-known/handle` and `_handle`, which refer to a DID instead, so that the same names serve every ecosystem. The two need to be reconciled.

### The HandleIssuer Service {#handle-issuer}

A DID document names the issuer authorized to vouch for its handle with a service ([@?DID-CORE]) whose `id` is `#handle_issuer`, whose `type` is `HandleIssuer`, and whose `serviceEndpoint` is an issuer identifier ((#issuer-identifier)):

```json
{ "id": "#handle_issuer", "type": "HandleIssuer",
  "serviceEndpoint": "https://issuer.example" }
```

The service is identified by its `id`, which can also be written as the DID followed by `#handle_issuer`, in the same way that the AT Protocol identifies the account's PDS by the `id` `#atproto_pds` ([@?ATPROTO-DID]). Service `id`s are unique within a DID document ([@?DID-CORE]), and in `did:plc` services are stored as a map keyed by `id` ([@?DID-PLC]), so a DID document names at most one issuer.

If the DID document has no service whose `id` is `#handle_issuer`, or that service's `type` is not `HandleIssuer`, or its `serviceEndpoint` is not an issuer identifier, that is, not an `https` origin with no path, query, or fragment, the handle has no authorized issuer, and HVP cannot be used with it.

Because a handle has a single authorized issuer, a change of issuer takes effect at once: as soon as the DID document names a new issuer, HVTs from the previous one no longer verify. This is the same as when a user moves their account to another server.

Authorization is always explicit: resolution does not infer an issuer from the account's existing services, such as its AT Protocol PDS (the `#atproto_pds` service), the PDS's authorization server, or its ActivityPub server. An issuer has to deploy HVP anyway, and requiring the DID document to name it means that a server does not become able to vouch for a handle in a new way, to verifiers it may never have dealt with, without the account's owner opting in. See (#why-opt-in).

A user who moves their account to another server, and whose issuer is that server, updates their `HandleIssuer` service as part of the move.

> Open Issue: The name of the DID service type, and whether it should be registered in the W3C DID Extensions registry.

> Open Issue: Whether a server that the DID document already names, such as the PDS named by the `#atproto_pds` service, should be an authorized issuer by default, which would let HVP work with existing accounts without changing their DID documents, at the cost of the explicit opt-in.

### Backwards Compatibility with the AT Protocol {#atproto-compat}

The AT Protocol maps a handle to a DID with a `TXT` record at `_atproto.` followed by the handle, and with the well-known URL `/.well-known/atproto-did` ([@?ATPROTO-HANDLE]). These names are specific to the AT Protocol. This document defines ecosystem-neutral names, `_handle` and `/.well-known/handle`, which take precedence, and falls back to the AT Protocol names when a handle does not publish the new ones, so that every existing AT Protocol handle keeps working.

When step 1 of resolution ((#resolution-steps)) falls back, the resolving party performs the following lookups, each of which yields the handle's DID:

- **AT Protocol DNS `TXT` record.** Query `TXT` records at the name `_atproto.` *handle*. Ignore records whose value does not start with `did=`. The DID is the remainder of the value.
- **AT Protocol well-known URL.** `GET https://` *handle* `/.well-known/atproto-did`. A 2xx response with the `text/plain` media type contains the DID, with leading and trailing whitespace removed.

If both lookups yield a DID, and the DIDs differ, resolution fails, in the same way that an AT Protocol handle with conflicting `_atproto` records fails today. If neither yields a DID, resolution fails.

As a consequence:

- A handle that is published with the AT Protocol names only, as every AT Protocol handle is today, resolves for every resolving party, without any change.
- A handle that is published with the new names resolves to what they name, whatever the AT Protocol names say. This lets the owner of a handle point it elsewhere, for example to a different DID, without first removing its AT Protocol records.
- Operators of handle domains MAY publish both. AT Protocol software that does not yet support the new names reads only the AT Protocol names, so operators that want the handle to resolve the same way in both SHOULD keep them consistent.

> Open Issue: Whether, and when, the AT Protocol adopts the new names, and whether resolving parties can eventually stop querying the AT Protocol names. This needs coordination with the AT Protocol community and the IETF ATP working group.

## Caching {#caching}

A resolving party MAY cache the results of resolution, subject to DNS time-to-live values and HTTP caching rules. A verifier SHOULD NOT cache resolution results for longer than a few minutes when verifying an HVT+KB, because a user who moves their handle to another issuer, or who loses control of it, expects the change to take effect promptly.

# Issuers {#issuers}

## Issuer Identifier {#issuer-identifier}

An issuer identifier is an HTTPS origin: the string `https://` followed by a host, with no port, path, or trailing slash, for example `https://issuer.example`. This is the same form as the issuer identifier of [@!EVP], and for the same reasons: it names the same thing as the `iss` claim of OpenID Connect and the issuer of [@!RFC8414], and it can be compared byte-for-byte.

Every use of the issuer identity in this document (the authorized issuer that resolution yields, the `iss` claim of the HVT, the `issuer` member of the metadata, and the base of the well-known URL) is this origin. Comparisons are byte-for-byte; no scheme defaulting, port normalization, or trailing-slash tolerance is applied.

## Issuer Metadata {#issuer-metadata}

An issuer serves its metadata at `$ISSUER/.well-known/handle-verification`, where `$ISSUER` is its issuer identifier. For `https://issuer.example`, this is `https://issuer.example/.well-known/handle-verification`.

The metadata document is a JSON object with the following members:

- `issuer` (REQUIRED): The issuer identifier. It MUST be identical to the issuer identifier that the document was fetched under, and a party that fetches the document MUST reject it if it is not (as in Section 3.3 of [@!RFC8414]).
- `issuance_endpoint` (REQUIRED): The URL that the browser sends HVT requests to. It MUST be an `https` URL that is same site ([@!WHATWG.HTML]) with the issuer identifier, so that the HVT request carries the cookies of the issuer's site; a party that fetches the metadata MUST reject it otherwise.
- `jwks_uri` (REQUIRED): The URL of the issuer's JSON Web Key Set ([@!RFC7517]), used to verify HVTs.
- `signing_alg_values_supported` (OPTIONAL): As defined by [@!EVP].
- `federations` (OPTIONAL): An array of `https` URLs, each of which identifies a federation that the accounts of the issuer belong to, such as `https://atproto.com`. HVP does not interpret these URLs, and verification does not depend on them. A browser API uses them to offer a verifier only the handles whose issuers belong to the federations that the verifier asks for ((#idp-registration)).

Example:

```json
{
  "issuer": "https://issuer.example",
  "issuance_endpoint": "https://issuer.example/hvp/issuance",
  "jwks_uri": "https://issuer.example/hvp/jwks",
  "signing_alg_values_supported": ["Ed25519", "ES256"],
  "federations": ["https://atproto.com"]
}
```

An issuer that also acts as an EVP issuer serves its EVP metadata and its HVP metadata at their respective well-known paths. It MAY use the same keys for both.

> Open Issue: Whether requiring the `issuance_endpoint` to be same site with the issuer identifier is appropriate, and whether [@!EVP] has, or should have, the same requirement, so that HVP does not diverge from it.

## HVT Request {#token-request-details}

The HVT request is the token request of [@!EVP], including its use of HTTP Message Signatures ([@!RFC9421]) and the `hwk` key scheme, with the following substitutions:

- The browser performs (#resolution), not EVP's issuer discovery, to obtain the issuer and its metadata, and sends the request to the `issuance_endpoint` of the HVP metadata.
- The request body is a JSON object with the following members:
  - `handle` (REQUIRED): The handle that the user selected, in normalized form ((#normalization)).
  - `did` (REQUIRED): The DID that the handle resolves to, byte-for-byte as resolution produced it.
- The `Sec-Fetch-Dest` header has the value `handle-verification`.

Example:

```http
POST /hvp/issuance HTTP/1.1
Host: accounts.issuer.example
Cookie: session=...
Content-Type: application/json
Sec-Fetch-Dest: handle-verification
Content-Digest: \
    sha-256=:...:
Signature-Input: sig=("@method" "@authority" "@path" \
    "content-digest" "signature-key");created=1792620000
Signature: sig=:MEQCIHd8Y8qYKm5e3dV8y....:
Signature-Key: sig=hwk;kty="OKP";crv="Ed25519"; \
    x="JrQLj5P_89iXES9-vFgrIy29clF9CC_oPPsw3c5D0bs";alg="Ed25519"

{"handle":"samuelgoto.bsky.social",
 "did":"did:plc:bftbdgcbe4zclvpkboe4hleq"}
```

On receipt of an HVT request, the issuer:

1. Verifies the request headers, the HTTP Message Signature, and the `Content-Digest`, as in the request verification of [@!EVP], with `handle-verification` in place of `email-verification` as the expected `Sec-Fetch-Dest`.
2. Verifies that `handle` satisfies (#handle-syntax) and is in normalized form, and that `did` is a syntactically valid `did:plc` or `did:web` DID. If it does not, the issuer returns an `invalid_request` error ((#errors)).
3. Checks that the cookies represent a signed-in user who controls `handle`, and whose account is the `did`. If they do not, the issuer returns an `authentication_required` error.
4. SHOULD resolve `handle` ((#resolution)) and check that it is the authorized issuer and that resolution yields the `did`. An HVT from an issuer that is not authorized is rejected by the verifier anyway, so this check is not needed for security, but it avoids issuing HVTs that will fail.
5. Creates an HVT ((#hvt-creation)) and returns it as the value of `issuance_token` in an `application/json` response, as in [@!EVP].

### Error Responses {#errors}

The issuer returns the error responses of [@!EVP] (`invalid_request`, `invalid_signature`, `authentication_required`, and server errors), with the `handle` member in place of the `email` member.

# Handle Verification Token (HVT) {#hvt}

The Handle Verification Token (HVT) is a JWT ([@!RFC7519]) issued by an issuer. It contains a handle, the unique user identifier that the handle resolves to, and the browser's public key.

## HVT Structure {#hvt-structure}

### Header

- `alg` (REQUIRED): The signing algorithm, with the same requirements as the `alg` of the EVT in [@!EVP]: a fully-specified identifier, and not `none`, a symmetric MAC algorithm, or the polymorphic `EdDSA`.
- `kid` (REQUIRED): The identifier of the signing key in the issuer's JWKS.
- `typ` (REQUIRED): `hvt+jwt`.

### Payload

- `iss` (REQUIRED): The issuer identifier ((#issuer-identifier)).
- `iat` (REQUIRED): The time the HVT was issued.
- `cnf` (REQUIRED): A confirmation claim ([@!RFC7800]) containing the browser's public key as a `jwk`, reproduced from the `Signature-Key` header of the HVT request with the same members, including its `alg`.
- `handle` (REQUIRED): The handle that the user controls, byte-for-byte as it appeared in the HVT request.
- `sub` (REQUIRED): The unique user identifier that the handle resolves to ((#resolution)), byte-for-byte as it appeared in the `did` member of the HVT request.

Example:

```json
{
  "iss": "https://bsky.social",
  "iat": 1792620000,
  "cnf": {
    "jwk": {
      "kty": "OKP",
      "crv": "Ed25519",
      "x": "JrQLj5P_89iXES9-vFgrIy29clF9CC_oPPsw3c5D0bs",
      "alg": "Ed25519"
    }
  },
  "handle": "samuelgoto.bsky.social",
  "sub": "did:plc:bftbdgcbe4zclvpkboe4hleq"
}
```

### Format

As with the EVT, the HVT has a `~` appended to it for compatibility with SD-JWT with Key Binding ([@!I-D.ietf-oauth-selective-disclosure-jwt]).

## HVT Creation {#hvt-creation}

After verifying the request and authenticating the user, the issuer:

1. Constructs the header with `alg`, `kid`, and `typ`.
2. Constructs the payload with `iss`, `iat`, `cnf` (containing the public key from the `Signature-Key` header, including its `alg` member), `handle`, and `sub`.
3. Signs the JWT with the private key identified by `kid`.
4. Appends `~` to the signed JWT.

## HVT Verification {#hvt-verification}

Both the browser and the verifier verify the HVT:

1. Parse the HVT into its header, payload, and signature.
2. Verify that `typ` is `hvt+jwt`, and validate `alg` and `kid` as for the EVT in [@!EVP].
3. Extract the `iss`, `iat`, `cnf`, `handle`, and `sub` claims. Verify that `handle` satisfies (#handle-syntax) and is in normalized form.
4. Resolve `handle` ((#resolution)), and verify that:
   - the unique user identifier that resolution produces is byte-for-byte identical to `sub`; and
   - `iss` is byte-for-byte identical to the authorized issuer.
5. Fetch the issuer metadata from `iss` ((#issuer-metadata)).
6. Fetch the issuer's public keys from its `jwks_uri`, and verify the HVT's signature with the key identified by `kid`.
7. Verify that `iat` is within an acceptable time window.

The browser additionally verifies that `handle` and `sub` are byte-for-byte identical to the handle and unique user identifier it requested, and that `cnf.jwk` matches the public key it generated. The browser MAY reuse the results of the resolution it performed before the HVT request for step 4.

# Key Binding (HVT+KB) {#kb}

Key binding is the key binding of [@!EVP], with the HVT in place of the EVT. The browser creates a KB-JWT whose `aud` is the verifier's origin, whose `nonce` is the verifier's session nonce, and whose `sd_hash` is the hash of the HVT (including its trailing `~`), and signs it with its private key. The HVT+KB is:

```
<HVT>~<KB-JWT>
```

The HVT+KB is compatible with SD-JWT with Key Binding ([@!I-D.ietf-oauth-selective-disclosure-jwt]), in the same way as the EVT+KB.

# HVT+KB Verification {#verification}

The verifier receives the HVT+KB, and verifies it by:

1. Verifying the KB-JWT as in [@!EVP], with the HVT in place of the EVT: its `alg` matches the `alg` of the HVT's `cnf.jwk`, its `aud` is the verifier's origin, its `nonce` is the session's nonce, its `iat` is recent, and its `sd_hash` is the hash of the HVT.
2. Verifying the HVT as described in (#hvt-verification), including resolving the handle itself.
3. Verifying the KB-JWT's signature with the public key in the HVT's `cnf.jwk`.

If all verification steps pass, the verifier has verified that the user controls the handle in the `handle` claim. The verifier SHOULD identify the user's account by the unique user identifier in the `sub` claim, and treat the `handle` as a mutable attribute of the account ((#reassignment)).

The verifier MUST perform its own resolution in step 2, and MUST NOT rely on resolution results provided by the browser. The verifier's resolution is what establishes that the issuer is authorized for the handle.

# Privacy Considerations

## Three-Party Model

As in [@!EVP], the browser intermediates between the verifier and the issuer. The issuer learns which handle the user is verifying, but not which verifier the user is signing in to, and the verifier learns the handle only after the user has chosen to share it.

## Handles Are Public Identifiers

Handles and unique user identifiers are public by design: they are meant to be shared, are the same at every site, and are linked to the user's public activity in the AT Protocol or ActivityPub. A verifier that receives a handle can correlate the user with other verifiers that receive the same handle, and with the user's public activity under that handle. HVP does not change this, and offers no equivalent of the private email addresses of [@!EVP]. Browser APIs that use HVP should make clear to the user that the verifier will learn their handle and DID.

## Resolution Traffic

Resolution consists of DNS queries and unauthenticated HTTPS requests. Unlike the lookup of [@!EVP], which queries only the email domain and is shared by every user of that domain, every resolution step of HVP is specific to one user: the DNS name queried is the handle itself, and the DID document is the user's. Any party that observes a resolution therefore learns which user is being resolved, and when.

When the browser resolves a handle, the DNS resolver and the servers involved (the handle's host, the host of a `did:web` DID document, and the PLC directory for `did:plc`) can observe that the user's device is resolving that handle, but not which verifier is involved, because the requests carry no credentials or referrer.

When the verifier resolves a handle to verify an HVT+KB, the requests carry nothing that names the verifier either, but they are sent by the verifier itself. The servers involved see the verifier's network address, which they can often attribute to the verifier, for example through reverse DNS or the verifier's hosting provider, or by signing in to a suspected verifier themselves and observing which address resolves their handle. Combined with the per-user nature of resolution, this can let them learn that a particular user signed in to the verifier at that time. When the handle's host or the host of the DID document is also the user's issuer, as is common for handles under a server's domain, the issuer can correlate the HVTs it issues with the resolutions that follow, which weakens the property, described above, that the issuer does not learn which verifier the user signs in to. A verifier that goes on to interact with the user's account in the AT Protocol or ActivityPub reveals this anyway.

Verifiers can reduce this exposure by:

- caching resolution results within the limits of (#caching), which helps for returning users but not for first sign-ins;
- resolving through an intermediary shared by many verifiers, such as a resolution service reached over Oblivious HTTP ([@?RFC9458]), so that the servers involved do not see the verifier's network address; and
- for `did:plc` DIDs, maintaining a local copy of the PLC directory, as described below.

A browser or verifier can remove the PLC directory from per-sign-in traffic entirely by maintaining a local copy of the directory, ingested through its bulk export endpoint and kept current through its streaming endpoint ([@?DID-PLC]), and verifying each operation's signatures as it is ingested. Resolving a `did:plc` DID then consults the local copy and sends no request that reveals which DID is being resolved. This has limits:

- It applies only to the DID-to-DID-document step. The handle-to-DID step still queries DNS records and well-known URLs of the handle's host, which observe the resolution as described above.
- It does not change the trust placed in the PLC directory ((#plc-trust)): the local copy contains only what the directory chose to publish, in the order it chose.
- It requires storing and continuously ingesting every operation for every DID, which is a significant cost, particularly for browsers on constrained devices and for small verifiers.

# Security Considerations

## Resolution Is Not Authentication

Resolution establishes which issuer is authorized for a handle. It does not establish that the user controls the handle: that is established by the issuer's signature on an HVT, which the issuer produces only after authenticating the user. An attacker who manipulates the browser's resolution can cause the browser to send the user's handle to an issuer of the attacker's choosing, but cannot produce an HVT that the verifier accepts, because the verifier resolves the handle itself.

## DNS Spoofing {#dns-security}

Resolution of domain handles relies on DNS `TXT` records, which are not authenticated unless DNSSEC is used. As in [@!EVP], spoofing the browser's DNS resolution discloses the handle to the attacker but yields no HVT that the verifier will accept, while spoofing the verifier's DNS resolution lets the attacker choose the DID, and therefore the authorized issuer. Verifiers SHOULD use a DNSSEC-validating resolver, and operators of handle domains SHOULD sign their zones. The other resolution steps rely on HTTPS and the Web PKI.

## Domain Control Is Handle Control

Every handle rests on control of a DNS name: whoever controls the handle's domain controls its `_handle` and `_atproto` records and its well-known URLs, and therefore which DID the handle resolves to. For a `did:web` DID on the handle's domain, the same party also controls the DID document, and therefore the authorized issuer. This is by design: it is what lets users bring their own domain. It also means that when a domain changes hands, for example when it expires and is registered by someone else, its handle changes hands too. The back-link check means the new owner cannot claim the previous owner's DID, but can point the handle at a DID of their own.

## Conflicting Records

A domain handle can be mapped to a DID by up to four records ((#resolution-steps)): two with the new names, and two with the AT Protocol names, which are used only as a fallback ((#atproto-compat)). Resolution is designed so that the browser and the verifier cannot reach different results for the same handle, and so that an attacker who can block or delay some lookups cannot choose between them:

- Two records with the same names that name different DIDs cause resolution to fail, rather than letting the result depend on which record a resolving party happened to read.
- The AT Protocol names are used only when the new names have positively established that the handle names nothing. If a lookup with the new names fails for any other reason, resolution fails, rather than falling back. Otherwise, an attacker who can make that lookup fail, for one party but not the other, could make the two parties resolve the handle through different records.

An attacker who can block lookups can still cause resolution to fail, but cannot cause it to succeed with a different result. Only the owner of the handle's domain can create records that disagree.

## Handle Reassignment {#reassignment}

Handles can be reassigned: a domain can expire and be re-registered, and a hosting provider can let a new account take a handle that a deleted account used. Verifiers SHOULD identify accounts by the unique user identifier in the `sub` claim rather than by the `handle` claim. A DID survives changes of handle, so a verifier that keys accounts on it is not affected when a handle moves to another account.

## Trust in the PLC Directory {#plc-trust}

For `did:plc` DIDs, resolution trusts the PLC directory to return the current DID document, and therefore the current authorized issuer.

Operations in the PLC directory are signed by the account's rotation keys, and the DID is derived from the hash of the signed genesis operation, so the operation log is self-certifying: a resolving party can fetch the log and verify it instead of trusting the directory's rendering of the DID document. Doing so prevents the directory from forging operations, and therefore from naming an issuer that the account's rotation keys did not authorize.

Verifying the log does not remove all trust in the directory. As the "PLC Server Trust Model" section of [@?DID-PLC] states, some trust in the directory is required, and its attacks are limited to:

- **Denial of service:** rejecting valid operations, or refusing to serve some information about the DID. For HVP, this includes withholding an operation that changes or removes the `HandleIssuer` service, so that a resolving party keeps accepting HVTs from an issuer that the user no longer authorizes, or withholding an operation that adds one, so that a newly authorized issuer is rejected.
- **Misordering:** in the event of a fork in the DID document's history, serving the "wrong" fork. For HVP, this determines which `HandleIssuer` service is in effect.

Neither the browser nor the verifier can detect these attacks. Operations are submitted only to the PLC directory, and are not published anywhere else that a resolving party could observe independently: mirrors and replicas obtain their operations from the directory, and the timestamps that the directory assigns to operations, on which the resolution of forks depends, are not signed. Both the browser and the verifier therefore place this trust in the PLC directory, and HVP inherits it for every handle that resolves to a `did:plc` DID. Handles that resolve to a `did:web` DID instead rely on the security of the DID's domain, as described in (#dns-security).

## Server-Side Request Forgery {#ssrf}

Resolution makes a verifier fetch URLs derived from user-controlled input. Verifiers MUST resolve only `https` URLs, MUST NOT fetch URLs whose host resolves to a loopback, link-local, or private IP address, and SHOULD apply limits on redirects, response size, and time.

## Token Confusion

The `typ` of the HVT (`hvt+jwt`) is distinct from that of the EVT (`evt+jwt`), so an HVT cannot be presented as an EVT or the other way around.

# IANA Considerations

## Well-Known URIs

This document registers the following well-known URIs in the "Well-Known URIs" registry ([@!RFC8615]):

- URI suffix: `handle`
  - Change controller: IETF
  - Reference: (#resolution-steps) of this document
  - Status: permanent

- URI suffix: `handle-verification`
  - Change controller: IETF
  - Reference: (#issuer-metadata) of this document
  - Status: permanent

- URI suffix: `atproto-did`
  - Change controller: IETF
  - Reference: (#atproto-compat) of this document
  - Status: permanent
  - Related information: Originally defined by the AT Protocol ([@?ATPROTO-HANDLE]).

## Underscored and Globally Scoped DNS Node Names

This document registers the following entries in the "Underscored and Globally Scoped DNS Node Names" registry ([@!RFC8552]):

- RR Type: `TXT`
  - `_NODE NAME`: `_handle`
  - Reference: (#resolution-steps) of this document

- RR Type: `TXT`
  - `_NODE NAME`: `_atproto`
  - Reference: (#atproto-compat) of this document

> Open Issue: The `atproto-did` well-known URI and the `_atproto` DNS node name are defined by the AT Protocol. Whether this document or a document of the IETF ATP working group should register them needs coordination with that working group.

## JSON Web Token Claims

This document registers the following claim in the "JSON Web Token Claims" registry ([@!RFC7519]):

- Claim Name: `handle`
- Claim Description: A handle that the subject controls
- Change Controller: IETF
- Specification Document(s): (#hvt) of this document

## Media Types

This document registers the `application/hvt+jwt` media type in the "Media Types" registry ([@!RFC6838]), for the `typ` header of the HVT.

> Open Issue: Complete the media type registration template.


# Design Rationale

## Why Resolve Domain Handles to a DID? {#why-did}

HVP needs three things from the target of a domain handle: a stable identifier for the account, a document that claims the handle back, and a place to name the issuer. A DID provides all three, through its DID document, in a form that is not specific to any ecosystem, and the AT Protocol already resolves domain handles to DIDs.

The record names the kind of value in its key, `did=` as in the AT Protocol, so that resolution does not have to infer it, and holds a single value rather than a list. Values of other kinds, such as username handles ([@?UHVP]), domain handles, or email addresses, can be added later with keys of their own, which resolving parties that do not support them ignore.

Only `did:plc` and `did:web` are supported, because they are the methods that the AT Protocol uses. Other methods can be added if an ecosystem needs them. A `did:key` DID is not sufficient on its own: its DID document is derived from the key, and so has no `alsoKnownAs` to claim the handle back and no services to name the issuer.

## Why New Names for the Handle Records? {#why-names}

The AT Protocol's `_atproto` record and `/.well-known/atproto-did` URL are specific to one ecosystem, and an ActivityPub account that published them would appear to be an AT Protocol account. Neutral names let any ecosystem use the same records. The names do not mention DIDs, so that they can refer to other kinds of identifiers later, and the well-known document is JSON, so that it can carry more information later. Resolving parties fall back to the AT Protocol names when the new ones are absent ((#atproto-compat)), so that every existing AT Protocol handle keeps working, and the new names take precedence when present, so that a handle can move to the new names at its own pace.

## Why Not OAuth? {#why-not-oauth}

AT Protocol OAuth ([@?ATPROTO-OAUTH]) and the OAuth APIs of ActivityPub servers let a verifier sign a user in, and grant it access to the user's account. But they ask the verifier to present a text field for the user to type a handle, and they reveal the verifier to the user's authorization server. HVP lets the browser offer the user's handles without the user typing them, and keeps the verifier hidden from the issuer. A verifier that needs access to the user's account, and not only proof that the user controls a handle, still uses OAuth.

HVP also changes how interoperability is achieved. In OAuth, the authorization server's response goes to the client, and nothing in between checks it: whether an authorization server interoperates with a given client is discovered by testing that pair, and ecosystems with many of each rely on conformance test suites and certification programs. In HVP, the browser verifies every HVT ((#hvt-verification)) with the same checks that a verifier performs, before any verifier receives it, and does not deliver an HVT that fails. An issuer that develops against a browser therefore has an independent verifier in its development loop, and an HVT that the browser accepts is accepted by any verifier that implements (#verification), unless the handle's resolution changes in between. Each issuer and each verifier needs to interoperate only with the browser's verification, rather than each issuer with each verifier.

## Why Generalize EVP?

EVP already solves the same problem for email addresses, with a three-party model, proof of possession of a browser key, and a token format compatible with SD-JWT. Reusing it lets verifiers and issuers share code and keys between the two, and keeps the privacy properties. An alternative would be to profile OpenID Connect, but OpenID Connect's redirect-based flow reveals the verifier to the provider.

## Why Does the Verifier Resolve the Handle?

The verifier cannot trust the browser's resolution, which could be manipulated, and it cannot trust the issuer to say which handles it is authorized for. Resolving the handle itself is how the verifier checks that the issuer is authorized, in the same way that the verifier looks up the DNS delegation in [@!EVP].

## Why Require an Explicit HandleIssuer Service? {#why-opt-in}

An account already says who hosts it: an AT Protocol account names its PDS, whose authorization server authenticates it, and an ActivityPub account is hosted by the server of its actor. HVP could infer its issuer from them. It does not, for two reasons. First, there is little to gain: an issuer has to deploy HVP's issuance endpoint and metadata anyway, and a server can add a `HandleIssuer` service to the DID documents of its accounts at the same time. Second, an HVT is a new kind of statement, presented to verifiers through the browser, and a user who authorized a server to host their account, or to sign them in with OAuth, has not necessarily authorized it to make that statement. An explicit service makes the user's opt-in visible in their DID document.

An explicit service also lets a user choose an issuer that is not the server that hosts their account, and gives both ecosystems the same way to name it.

## Why Define Handle Resolution Here?

Handle resolution is useful outside any one ecosystem. Defining it here, in a form that is shared by the AT Protocol and ActivityPub, makes HVP implementable from this document alone, by verifiers that implement neither protocol.

## Why Are Email Addresses Out of Scope?

Email addresses already have a protocol of their own, [@!EVP], which is further along, has implementations, and has requirements specific to email, such as private email addresses. A browser API can use EVP for email addresses and HVP for handles side by side; an email address is never parsed as a domain handle ((#parsing)).

# Implementation Status

*Note: This section is to be removed before publishing as an RFC.*

There are no implementations of this document yet. Prototypes of the related IdP Registration API ([@?IDP-REGISTRATION]) exist in Chrome behind a flag.

# Document History

*Note: This section is to be removed before publishing as an RFC.*

- draft-goto-handle-verification-00
  - Initial draft, covering domain handles in the AT Protocol and ActivityPub. URL handles and username handles are covered by companion documents, [@?URL-HVP] and [@?UHVP].

{backmatter}

# Examples {#examples}

This appendix shows the resolution of handles. The examples are real handles at the time of writing, which publish only the AT Protocol names, and so resolve through the fallback of (#atproto-compat). Neither publishes a `HandleIssuer` service yet, so each shows what would be added to opt in. The values will change over time.

## AT Protocol Handle on a Self-Hosted PDS

```
Handle:        @sgo.to
DNS TXT _atproto.sgo.to -> "did=did:plc:thaoj4hhvraos7y6v3yog7re"
DID document (plc.directory):
  alsoKnownAs: ["at://sgo.to"]                  (back-link ok)
DID:           did:plc:thaoj4hhvraos7y6v3yog7re
To opt in, add to the DID document's services:
  { "id": "#handle_issuer", "type": "HandleIssuer",
    "serviceEndpoint": "https://pds.sgo.to" }
Issuer:        https://pds.sgo.to
```

## AT Protocol Handle on a Hosted PDS

```
Handle:        @samuelgoto.bsky.social
GET https://samuelgoto.bsky.social/.well-known/atproto-did
  -> did:plc:bftbdgcbe4zclvpkboe4hleq
DID document (plc.directory):
  alsoKnownAs: ["at://samuelgoto.bsky.social"]  (back-link ok)
DID:           did:plc:bftbdgcbe4zclvpkboe4hleq
To opt in, add to the DID document's services:
  { "id": "#handle_issuer", "type": "HandleIssuer",
    "serviceEndpoint": "https://bsky.social" }
Issuer:        https://bsky.social
```

# Relationship to IdP Registration {#idp-registration}

*This section is non-normative.*

The W3C IdP Registration API ([@?IDP-REGISTRATION]) extends FedCM ([@?FEDCM]) so that a verifier can request any issuer in an open federation, and the browser keeps a registry of the user's handles. It relates to HVP the way the Email Verification API ([@?EMAIL-VERIFICATION-API]) relates to EVP: the browser API decides which handles to offer, lets the user register and select them, and delivers the HVT+KB to the verifier, while HVP defines what a handle is, how it is resolved, and how the HVT is issued and the HVT+KB is verified. In particular:

- The IdP Registration API parses and resolves handles as described in (#handles) and (#resolution), and treats the authorized issuer of a handle as its identity provider.
- It fetches the issuer metadata ((#issuer-metadata)) of the authorized issuer, and reads the `accounts_endpoint` and `login_url` that the browser needs to show the user's accounts and let the user sign in from FedCM's well-known file, `/.well-known/web-identity`, on the issuer's site.
- A verifier asks for handles by federation, such as `https://atproto.com`. The browser offers the handles whose issuers list that federation in the `federations` member of their issuer metadata.
- When the user selects an account, the browser obtains an HVT from the issuer with an HVT request ((#token-request-details)), rather than with FedCM's identity assertion endpoint, which would reveal the verifier to the issuer, creates the KB-JWT ((#kb)), and delivers the HVT+KB to the verifier, which verifies it as described in (#verification).

# Acknowledgments

This document builds on the Email Verification Protocol by Dick Hardt and Sam Goto, on the AT Protocol handle, DID, and AT URI specifications by Bluesky, and on the Handles Task Force proposal by Anuj Ahooja and Emelia Smith.
