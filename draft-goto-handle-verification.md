%%%
title = "Handle Verification Protocol"
abbrev = "HVP"
ipr = "trust200902"
area = "Security"
workgroup = "TBD"
keyword = ["handle", "verification", "identity", "authentication", "atproto", "activitypub", "indieauth", "webid"]

[seriesInfo]
status = "standard"
name = "Internet-Draft"
value = "draft-goto-handle-verification-latest"
stream = "IETF"

date = 2026-10-21T00:00:00Z

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

<reference anchor="FEDCM" target="https://w3c-fedid.github.io/FedCM/">
  <front>
    <title>Federated Credential Management API</title>
    <author>
      <organization>W3C Federated Identity Working Group</organization>
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

<reference anchor="FEP-2C59" target="https://codeberg.org/fediverse/fep/src/branch/main/fep/2c59/fep-2c59.md">
  <front>
    <title>FEP-2c59: Discovery of a Webfinger address from an ActivityPub actor</title>
    <author>
      <organization>Fediverse Enhancement Proposals</organization>
    </author>
    <date year="2024"/>
  </front>
</reference>

<reference anchor="INDIEAUTH" target="https://indieauth.spec.indieweb.org/">
  <front>
    <title>IndieAuth</title>
    <author initials="A." surname="Parecki" fullname="Aaron Parecki">
      <organization/>
    </author>
    <date year="2024"/>
  </front>
  <refcontent>Living Standard</refcontent>
</reference>

<reference anchor="WEBID" target="https://www.w3.org/2005/Incubator/webid/spec/identity/">
  <front>
    <title>WebID 1.0</title>
    <author>
      <organization>W3C WebID Community Group</organization>
    </author>
    <date year="2014" month="March"/>
  </front>
</reference>

<reference anchor="LWS" target="https://www.w3.org/groups/wg/lws/">
  <front>
    <title>Linked Web Storage</title>
    <author>
      <organization>W3C Linked Web Storage Working Group</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

<reference anchor="WHATWG.URL" target="https://url.spec.whatwg.org/">
  <front>
    <title>URL Standard</title>
    <author>
      <organization>WHATWG</organization>
    </author>
    <date year="2026"/>
  </front>
  <refcontent>Living Standard</refcontent>
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

<reference anchor="PSL" target="https://publicsuffix.org/">
  <front>
    <title>Public Suffix List</title>
    <author>
      <organization>Mozilla Foundation</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

.# Abstract

This document defines the Handle Verification Protocol (HVP), the HTTP-level protocol by which a browser obtains a signed token from an issuer attesting that the user controls a *handle*, and presents it to a verifier. A handle is a human-readable identifier at an open-ended set of providers, written with a leading `@` and carried as an `at://` URI: an AT Protocol handle such as `@alice.example`, an ActivityPub address such as `@alice@social.example`, or a URL identity as used by IndieAuth and Linked Web Storage, such as `@alice.example/profile/card#me`. HVP uses the same three-party model as the Email Verification Protocol (EVP), in which the browser intermediates between the verifier and the issuer and hides the verifier's identity from the issuer.

This document defines the notation of handles and the `at` URI scheme that carries them, the resolution of a handle to a machine-readable identity document and to the issuers authorized to vouch for it, the token issuance request, the Handle Verification Token (HVT), and token verification. Email addresses are out of scope: they are verified with EVP, which can be used alongside HVP. The browser API, that is, how the user selects a handle and how the token is delivered to the verifier, is defined separately, for example by the W3C IdP Registration API ([@?IDP-REGISTRATION]).

.# Discussion Venues

*Note: This section is to be removed before publishing as an RFC.*

Source for this draft and an issue tracker can be found at https://github.com/samuelgoto/handle-verification.

{mainmatter}

# Introduction

Web applications let users sign in with an account they already have elsewhere. With federated sign-in, the application lists the identity providers it accepts, integrates with each of them, and shows each as a button. This works for a handful of large providers. It does not work for the long tail: users whose identity lives on their own domain, on one of thousands of ActivityPub servers, on a self-hosted AT Protocol personal data server, or in a Solid pod.

Email shows that an open federation is possible. A verifier accepts an email address at any mail domain without a prior relationship with the domain, and the Email Verification Protocol ([@!EVP]) lets the verifier check such an address with a signed token. HVP extends that model to the other kinds of human-readable identifiers that users already have, which this document calls *handles*.

## The Open Federation Problem

Several open protocols identify users with a handle and let any server act as the user's provider:

- The AT Protocol ([@?ATPROTO-HANDLE]) identifies users with a DNS name, such as `@alice.example`.
- ActivityPub ([@?ACTIVITYPUB]) servers identify users with an address, such as `@alice@social.example`, that is resolved with WebFinger ([@!RFC7033]).
- IndieAuth ([@?INDIEAUTH]) identifies users with a URL, such as `https://alice.example/`.
- Solid and Linked Web Storage ([@?LWS]) identify users with a WebID ([@?WEBID]), a URL such as `https://alice.example/profile/card#me`.

A verifier that wants to accept all of these users today has to implement each protocol's discovery and sign-in flow, and has to present a text field asking the user to type an identifier. Experience with OpenID 2.0 suggests that most users do not know what to type into such a field.

## Protocol Fragmentation

Each of these protocols has its own way to go from a handle to a machine-readable description of the user, and its own way to prove that a sign-in really is from the user who owns the handle:

- AT Protocol resolves the handle to a DID through a DNS `TXT` record or a well-known URL, and checks that the DID document claims the handle back.
- ActivityPub resolves the address through WebFinger to an actor document, and checks that the actor's server agrees with the address.
- IndieAuth fetches the URL, discovers an authorization server from the page, and checks that the authorization server returns the same URL.
- Solid fetches the WebID's RDF profile and checks that the OpenID provider that signed the user in is listed in that profile.

The checks are similar in spirit but different in every detail, and none of them is shared by more than one protocol.

## Solution

HVP separates the problem into three parts:

1. **Notation** ((#handles)): how handles are written (as `@` followed by a host, a user and host, or a host and path), and the `at://` *handle URI* that carries each of them.
2. **Resolution** ((#resolution)): how a handle URI is resolved to a machine-readable identity document, checked against the handle, and turned into a stable subject identifier and the set of issuers that the user has authorized to vouch for it. Resolution depends on the shape of the handle URI and on what its host publishes, and reuses each protocol's existing discovery mechanisms.
3. **Issuance and verification**: how a browser obtains a Handle Verification Token (HVT) from an authorized issuer, and how a verifier verifies it. This part is the same for every handle, and reuses the token request, key binding, and token format of EVP.

A verifier that implements HVP verifies one token format with one algorithm, whatever protocol the user's handle belongs to. Only resolution is type-specific. It consists of unauthenticated lookups (DNS queries and HTTPS `GET` requests) that each protocol already uses, plus a single `handle-issuer` link that the user adds to their identity document to opt in to an issuer.

HVP keeps the privacy properties of EVP: the browser intermediates between the verifier and the issuer, so the issuer does not learn which verifier the user is signing in to.

## Relationship to EVP

HVP reuses the mechanics of [@!EVP] (the token request, key binding, and token format) with the substitutions described in this document. Email addresses are not handles in the sense of this document: they are verified with [@!EVP], and a browser API can offer both, using EVP for email addresses and HVP for handles.

## Relationship to the Browser API

This document specifies the IETF protocol aspects of handle verification: the HTTP-level interactions between the browser, the issuer, and the verifier, and the lookups needed to resolve a handle. How the browser learns about the user's handles, how the user selects one, and how the browser communicates with the verifier are defined separately. The W3C IdP Registration API ([@?IDP-REGISTRATION]), an extension of FedCM ([@?FEDCM]), is one such API. See (#idp-registration).

# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 [@!RFC2119] [@!RFC8174] when, and only when, they appear in all capitals, as shown here.

This document uses the following terms:

Handle:
: A human-readable string that identifies a user at a provider, written as `@` followed by a handle reference, such as `@alice.example`, `@alice@social.example`, or `@alice.example/profile/card#me`. A handle is not necessarily permanent: a user can change it, or move it to another provider.

Handle URI:
: The canonical form of a handle as an `at` URI, such as `at://alice.example`, `at://alice@social.example`, or `at://alice.example/profile/card#me`. Every comparison of handles in this document is a byte-for-byte comparison of handle URIs. See (#handle-uris).

Shape:
: Whether a handle URI consists of a host, a user and a host, or a URL (a host with a path, query, or fragment). The shape determines how a handle is resolved.

Identity document:
: The machine-readable document that a handle resolves to: a DID document, a WebFinger resource descriptor and ActivityPub actor, an HTML profile page, or an RDF profile document, depending on the handle and what its host publishes.

Subject identifier:
: A stable identifier for the user that resolution obtains from the identity document: a DID, an ActivityPub actor ID, or a canonical profile URL. Unlike the handle, it is expected not to change when the user changes handle.

Back-link:
: The part of the identity document that refers back to the handle, which resolution checks so that a document cannot be claimed by a handle it did not agree to.

Authorized issuers:
: The set of issuer identifiers that the identity document names with the `handle-issuer` link relation ((#handle-issuer)). Only an authorized issuer can issue an HVT that a verifier accepts for that handle.

Issuer:
: A service that verifies the user controls a handle and issues HVTs for it. An issuer is identified by an issuer identifier ((#issuer-identifier)).

Handle Verification Token (HVT):
: A JWT ([@!RFC7519]) issued by an issuer that contains a handle URI, a subject identifier, and the browser's public key. See (#hvt).

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
3.3 Handle Resolution          |   [resolve handle: identity     |
                               |    document, subject, issuers]  |
                               |            |                    |
3.4 Token Request              |            |-- POST /issuance ->|
                               |            |   (handle, ...)    |
                               |            |                    |
3.5 HVT Issuance               |            |<------- HVT -------|
                               |            |                    |
3.6 KB Creation                |        [create KB-JWT]          |
                               |            |                    |
3.7 Token Presentation         |<-- HVT+KB -|                    |
                               |            |                    |
3.8 Token Verification  [resolve handle;    |                    |
                         verify HVT+KB]     |                    |
```

The flow is the same as the flow of [@!EVP], with two differences: the browser and the verifier *resolve* the handle ((#resolution)) where EVP looks up a DNS delegation record, and the token is an HVT rather than an EVT.

## Handle Discovery {#handle-discovery}

How the browser assembles candidate handles, from its own store, from accounts that an issuer pushes or the browser pulls, or from the user typing one, is defined by the browser API ([@?IDP-REGISTRATION]) and is out of scope for this document. When the browser starts from text that the user typed, it parses it as described in (#notation).

## Session Binding {#session-binding}

As in [@!EVP]: the verifier generates a cryptographically random nonce with at least 128 bits of entropy and binds it to a session it has with the browser. How the verifier provides the nonce to the browser is defined by the browser API.

## Handle Resolution {#flow-resolution}

The browser resolves the handle as described in (#resolution). Resolution produces the canonical handle URI, the subject identifier, and the set of authorized issuers. The browser selects one authorized issuer, and fetches its metadata ((#issuer-metadata)). If the handle has more than one authorized issuer, which one the browser selects is up to the browser API. From this point onward, the handle URI is never altered: it is sent byte-for-byte in the token request, and returned byte-for-byte in the `handle` claim.

## Token Request {#token-request}

The browser sends a token request to the issuer's `issuance_endpoint`. The request is the token request of [@!EVP], with the substitutions listed in (#token-request-details).

## HVT Issuance {#hvt-issuance}

The issuer verifies the request, checks that the browser's cookies represent a signed-in user who controls the handle, and returns an HVT ((#hvt)) as the value of `issuance_token` in an `application/json` response, as in [@!EVP].

## KB Creation {#kb-creation}

The browser verifies the HVT ((#hvt-verification)), additionally confirming that the `handle` claim is byte-for-byte identical to the handle URI it requested and that the `cnf.jwk` claim matches the public key it generated. It then creates a KB-JWT and combines it with the HVT as described in (#kb).

## Token Presentation {#token-presentation}

The browser provides the HVT+KB to the verifier. This mechanism is defined by the browser API.

## Token Verification {#token-verification}

The verifier verifies the HVT+KB as described in (#verification). The verifier resolves the handle itself, and does not rely on the browser's resolution. If verification succeeds, the verifier has verified that the user controls the handle in the `handle` claim, and has learned the user's subject identifier in the `sub` claim.

# Handles {#handles}

A handle is written as `@` followed by a *handle reference*, and is carried in the protocol as an `at` URI: `at://` followed by the same handle reference. The two are spellings of the same identifier: `@` is how a handle is displayed and typed, and `at://` is how it is carried in tokens and compared.

| Written | Handle URI | Shape |
|---------|------------|-------|
| `@alice.example` | `at://alice.example` | host |
| `@alice@social.example` | `at://alice@social.example` | user |
| `@alice.example/profile/card#me` | `at://alice.example/profile/card#me` | URL |

The *shape* of a handle URI determines how it is resolved: a host handle as an AT Protocol handle, or else as a URL ((#resolve-host)); a user handle with WebFinger and ActivityPub ((#resolve-acct)); and a URL handle by fetching it ((#resolve-url)). Which protocol a handle belongs to is not part of its notation: it is determined by what the handle's host publishes.

## Handle Hosts {#handle-host}

Every handle contains a DNS name, called the handle's *host*. A handle host MUST satisfy the following rules. They are the rules for AT Protocol handles ([@?ATPROTO-HANDLE]), which are themselves a synthesis of the hostname rules of [@!RFC1035], [@?RFC3696] and [@!RFC3986], and they apply here to every handle:

- The host contains only ASCII characters, and is at most 253 characters long.
- The host consists of at least two labels separated by ASCII periods (`.`). It has no leading or trailing period.
- Each label is between 1 and 63 characters long, and contains only ASCII letters, digits, and hyphens (`-`). A label does not start or end with a hyphen.
- The last label (the top-level domain) does not start with a digit. As a consequence, IP addresses are not hosts.
- Hosts are case-insensitive, and are normalized to lowercase.

Internationalized domain names are written in their A-label form ([@!RFC5890]), for example `xn--ls8h.example`.

In ABNF ([@!RFC5234]), before normalization:

```abnf
handle-host = 1*( label "." ) tld-label
label       = alnum [ *61( alnum / "-" ) alnum ]
tld-label   = ALPHA [ *61( alnum / "-" ) alnum ]
alnum       = ALPHA / DIGIT
```

with the additional constraint that the whole `handle-host` is at most 253 characters long. A reference regular expression is:

```
^([a-zA-Z0-9]([a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?\.)+
[a-zA-Z]([a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?$
```

(The regular expression is shown on two lines for display; it is a single expression.)

The following top-level domains are syntactically valid in a handle host, but a handle whose host ends in one of them MUST fail resolution: `.alt`, `.arpa`, `.example`, `.internal`, `.invalid`, `.local`, `.localhost`, and `.onion`. The `.test` top-level domain MAY be used in development, and MUST fail resolution in production deployments. (The examples in this document use `.example` and so would fail resolution.)

## The at URI Scheme {#at-uri-scheme}

The `at` URI scheme originates in the AT Protocol ([@?ATPROTO-URI]), where `at://alice.example` identifies the account whose handle is `alice.example`, and `at://alice.example/` followed by a collection and a record key identifies a record in that account's repository. This document defines the scheme so that it can be referenced independently of the AT Protocol, and generalizes it so that the same `at://` form, read as "@", identifies accounts in other protocols too.

```abnf
at-uri       = "at://" at-authority [ path-abempty ]
               [ "?" query ] [ "#" fragment ]
at-authority = [ at-user "@" ] handle-host / did
at-user      = 1*( unreserved / pct-encoded / sub-delims )
did          = "did:" method-name ":" method-specific-id
```

where `unreserved`, `pct-encoded`, `sub-delims`, `path-abempty`, `query`, and `fragment` are defined by [@!RFC3986], and `did`, `method-name`, and `method-specific-id` by [@?DID-CORE]. The host is normalized to lowercase; the user part and a DID are case-sensitive.

An `at` URI whose authority is a host, optionally with a user part, can be a handle URI ((#handle-uris)). An `at` URI whose authority is a DID is used by the AT Protocol to refer to an account or record by its DID, and is not a handle URI.

> Note: A DID contains colons, so an `at` URI whose authority is a DID does not follow the generic authority syntax of [@!RFC3986], which reads a colon in the authority as the start of a port. Generic URI parsers MUST NOT be used to extract the authority of an `at` URI. Handle URIs never have a DID authority, and do follow the generic syntax.

> Open Issue: In the AT Protocol, `at://alice.example/app.bsky.feed.post/3k2a` is a record in the repository of `@alice.example`, while in this document an `at` URI with a path is a URL handle ((#handle-uris)), which would refer to `https://alice.example/app.bsky.feed.post/3k2a`. The two uses can be told apart by context (an identifier of a user, as opposed to a reference to a record), but not by syntax. This, and the broadening of the scheme beyond the AT Protocol, needs coordination with the authors of the AT Protocol and the IETF ATP working group.

## Handle URIs {#handle-uris}

A handle URI is an `at` URI in one of three shapes:

```abnf
handle-uri = "at://" handle-ref
handle-ref = host-ref / user-ref / url-ref
host-ref   = handle-host
user-ref   = at-user "@" handle-host
url-ref    = handle-host path-abempty [ "?" query ] [ "#" fragment ]
```

where a `url-ref` has a path other than the empty path and `/`, a query, or a fragment.

Host:
: A host on its own, as in `at://alice.example`. This is the handle URI of an AT Protocol handle ([@?ATPROTO-HANDLE]), and also of a URL identity at the root of a host, such as an IndieAuth profile `https://alice.example/` ([@?INDIEAUTH]). Which one it is depends on what the host publishes ((#resolve-host)).

User:
: A user part and a host, as in `at://alice@social.example`. This identifies an account at a server that is discovered with WebFinger ([@!RFC7033]), as used by ActivityPub ([@?ACTIVITYPUB]). Its *acct URI* is `acct:` followed by the handle reference, here `acct:alice@social.example` ([@!RFC7565]). A user handle URI has no path, query, or fragment.

URL:
: A host followed by a path, query, or fragment, as in `at://alice.example/profile/card#me`. This identifies a URL identity, such as a WebID ([@?WEBID]) used by Solid and Linked Web Storage ([@?LWS]), or an IndieAuth profile URL that is not at the root of its host.

The *https URL* of a host or URL handle URI is `https://` followed by its handle reference, with a path of `/` added if it has no path. For example, the https URL of `at://alice.example` is `https://alice.example/`, and that of `at://alice.example/profile/card#me` is `https://alice.example/profile/card#me`.

A handle URI is always in canonical form:

- The host is lowercase.
- The handle reference of a URL handle URI is the result of running the URL parser of [@!WHATWG.URL] on its https URL, running the URL serializer on the result, and removing the leading `https://`. The URL MUST NOT contain a username, password, or port.
- A path of exactly `/` with no query or fragment is removed, so that `at://alice.example/` is the host handle URI `at://alice.example`. A path of `/` followed by a query or fragment is kept, so `at://alice.example/#me` is a URL handle URI.
- The user part is not normalized. Resolution replaces it with the canonical form that the account's server reports ((#resolve-acct)).

## Notation {#notation}

A handle is displayed as `@` followed by its handle reference: `@alice.example`, `@alice@social.example`, `@alice.example/profile/card#me`.

When a user types a handle, they type either this notation or the handle URI. Input that starts with neither `@` nor `at://` is not a handle. In particular, `alice@mail.example` without a leading `@` is not a handle (it is an email address, which a browser API can verify with [@!EVP]), and an `https` URL is not a handle.

To parse user input:

1. Strip leading and trailing ASCII whitespace.
2. If the input starts with `at://`, remove it. Otherwise, if it starts with `@`, remove it. Otherwise, fail.
3. Split the rest at the first `/`, `?`, or `#` into an authority and a remainder (which may be empty).
4. If the authority contains `@`, the user part is what precedes the last `@`, and the host is what follows it. The user part MUST be a valid `at-user`, and the remainder MUST be empty. Otherwise, the host is the whole authority.
5. Normalize the host to lowercase. It MUST be a handle host ((#handle-host)).
6. Construct the handle URI and bring it to canonical form ((#handle-uris)).

If any step fails, the input is not a handle.

| Input | Handle URI |
|-------|------------|
| `@Alice.Example`, `at://alice.example/` | `at://alice.example` |
| `@alice@Social.Example` | `at://alice@social.example` |
| `@alice.example/profile/card#me` | `at://alice.example/profile/card#me` |
| `@alice.example/#me` | `at://alice.example/#me` |
| `alice@mail.example`, `https://alice.example/` | not a handle |
| `@192.0.2.1`, `@com`, `@alice.example:8080` | not a handle |

> Open Issue: Requiring `@` or `at://` is a change for IndieAuth and Solid users, who are used to typing an `https` URL. A browser API could offer to convert a typed `https` URL into the corresponding handle, but that would reintroduce the ambiguity that the `@` requirement removes.

# Handle Resolution {#resolution}

*Resolution* takes a handle URI and produces:

- the *canonical handle URI*, which is the input handle URI or a canonical form of it that resolution discovers;
- the *identity document* that describes the user;
- the *subject identifier* of the user; and
- the set of *authorized issuers* for the handle.

The shape of the handle URI determines how it is resolved:

- A host handle URI is resolved as described in (#resolve-host): as an AT Protocol handle if its host publishes a DID, and as a URL otherwise.
- A user handle URI is resolved with WebFinger, as described in (#resolve-acct).
- A URL handle URI is resolved by fetching its https URL, as described in (#resolve-url).

Each of these follows the same structure:

1. **Locate:** use the handle URI to locate and fetch the identity document.
2. **Back-link:** check that the identity document refers back to the handle, so that a document cannot be claimed by a handle that it did not agree to.
3. **Subject:** extract the subject identifier from the identity document.
4. **Issuers:** extract the authorized issuers from the identity document: the targets of its `handle-issuer` links ((#handle-issuer)). If there are none, resolution fails.

If any step fails, resolution fails.

Both the browser and the verifier perform resolution. The browser does it to find an issuer to ask for a token; the verifier does it to check that the token was issued by an issuer that is authorized for the handle ((#verification)).

The following rules apply to every resolution step:

- DNS queries use the resolving party's DNS resolver. DNSSEC is not required, but see (#dns-security).
- HTTP requests use the `https` scheme, MUST NOT include credentials (cookies or HTTP authentication), and SHOULD NOT include a `Referer` header. When the browser makes them, they SHOULD be made from an opaque origin, so that the servers involved do not learn which verifier the user is visiting.
- Redirects are followed only to `https` URLs, and at most 5 times for a single request.
- Responses are subject to reasonable limits on size and time, and resolving parties take the precautions of (#ssrf).

## The handle-issuer Link Relation {#handle-issuer}

An identity document names the issuers authorized to vouch for its handle with the `handle-issuer` link relation ([@!RFC8288]). The link context is the user that the identity document describes, and the link target is the issuer identifier ((#issuer-identifier)) of an issuer that the user authorizes to issue HVTs for the handle.

A link relation can be expressed in each of the formats that identity documents use, so a single relation serves every handle:

- In a WebFinger resource descriptor ([@!RFC7033]):

  ```json
  { "rel": "handle-issuer", "href": "https://issuer.example" }
  ```

- In an HTTP response header ([@!RFC8288]):

  ```
  Link: <https://issuer.example>; rel="handle-issuer"
  ```

- In an HTML document ([@!WHATWG.HTML]):

  ```html
  <link rel="handle-issuer" href="https://issuer.example">
  ```

- In an RDF document, using the link relation's URI form, `http://www.iana.org/assignments/relation/handle-issuer`:

  ```
  <#me> <http://www.iana.org/assignments/relation/handle-issuer>
        <https://issuer.example> .
  ```

- In a DID document, which has services rather than links, as a service whose `type` is `HandleIssuer` and whose `serviceEndpoint` is the issuer identifier:

  ```json
  { "id": "#handle_issuer", "type": "HandleIssuer",
    "serviceEndpoint": "https://issuer.example" }
  ```

A link target that is not an issuer identifier, that is, not an `https` origin with no path, query, or fragment, is ignored. The valid `handle-issuer` links of an identity document are its authorized issuers. An identity document without any has no authorized issuers, and HVP cannot be used with its handle.

Authorization is always explicit: resolution does not infer an issuer from a protocol's existing sign-in mechanisms, such as the authorization server of an AT Protocol personal data server, the server of an ActivityPub actor, an IndieAuth authorization server, or the OpenID providers listed in a WebID. An issuer has to deploy HVP anyway, and requiring the identity document to name it means that a server does not become able to vouch for a handle in a new way, to verifiers it may never have dealt with, without the handle's owner opting in. See (#why-opt-in).

> Open Issue: The name of the link relation and of the DID service type, and whether the DID service type should be registered in the W3C DID Extensions registry.

## Host Handles {#resolve-host}

A host handle URI `at://` *host* is either an AT Protocol handle or a URL identity at the root of *host*. The host's DNS records and well-known URLs decide which:

1. Perform step 1 of (#resolve-at), "Handle to DID".
2. If it yields a DID, resolve the handle as an AT Protocol handle, as described in (#resolve-at). If any later step fails, resolution fails; it does not fall back to step 3.
3. If neither method of step 1 yields a DID, because there is no `TXT` record whose value starts with `did=` and the well-known URL returns a 404 (Not Found) or 410 (Gone) response, resolve the handle as a URL, as described in (#resolve-url).
4. If step 1 fails in any other way, for example because a DNS query fails or the well-known URL returns a server error, resolution fails.

Resolution does not fall back to the URL when the AT Protocol lookup fails for transient reasons, so that the browser and the verifier reach the same result, and so that an attacker who can block a lookup cannot change how a handle resolves. See (#downgrade).

## AT Protocol Handles {#resolve-at}

The resolution of AT Protocol handles follows the AT Protocol ([@?ATPROTO-HANDLE], [@?ATPROTO-DID]), which this section restates so that it can be used independently of that protocol. Given a host handle URI `at://` *host*:

1. **Handle to DID.** Obtain the DID for *host* with either of the following methods. A resolving party MUST support both. If the DNS method yields a DID, the HTTPS method is not used.
   - **DNS `TXT` method.** Query `TXT` records at the name `_atproto.` *host*. Ignore records whose value does not start with `did=`. The DID is the remainder of the value. If there is more than one such record and they contain different DIDs, fail. This method aligns with [@?RFC1464].
   - **HTTPS well-known method.** `GET https://` *host* `/.well-known/atproto-did`. The response MUST have a 2xx status code and the `text/plain` media type. The DID is the response body, with leading and trailing whitespace removed.

   The DID MUST use the `plc` method ([@?DID-PLC]) or the `web` method ([@?DID-WEB]); otherwise fail.

   Note that a host near the 253-character limit cannot use the DNS method, because the `_atproto.` prefix would push the query name over the limit. The HTTPS method works for such hosts.

2. **DID to DID document.** Resolve the DID to its DID document ([@?DID-CORE]):
   - For `did:plc`, `GET` the DID from a PLC directory, by default `https://plc.directory/` followed by the DID.
   - For `did:web`, `GET https://` *domain* `/.well-known/did.json`, where *domain* is the method-specific identifier. A `did:web` DID with a path is not supported.

   The `id` member of the DID document MUST be identical to the DID.

3. **Back-link.** Find the first element of the DID document's `alsoKnownAs` array that is a syntactically valid host handle URI ((#handle-uris)). After normalization to lowercase, it MUST be identical to the handle URI. Otherwise fail.

4. **Subject.** The subject identifier is the DID.

5. **Issuers.** The authorized issuers are the `serviceEndpoint` values of the DID document's `HandleIssuer` services ((#handle-issuer)).

The identity document is the DID document.

For example, the handle `@samuelgoto.bsky.social` resolves as follows at the time of writing:

```
GET https://samuelgoto.bsky.social/.well-known/atproto-did
  -> did:plc:bftbdgcbe4zclvpkboe4hleq
GET https://plc.directory/did:plc:bftbdgcbe4zclvpkboe4hleq
  -> alsoKnownAs: ["at://samuelgoto.bsky.social"]
```

so its subject identifier is `did:plc:bftbdgcbe4zclvpkboe4hleq`. Its DID document has no `HandleIssuer` service yet, so it has no authorized issuers. If its PDS operator deployed an HVP issuer at `https://bsky.social`, the DID document would add:

```json
{ "id": "#handle_issuer", "type": "HandleIssuer",
  "serviceEndpoint": "https://bsky.social" }
```

## User Handles {#resolve-acct}

Given a user handle URI `at://` *user* `@` *host*, whose acct URI is `acct:` *user* `@` *host*:

1. **WebFinger.** `GET https://` *host* `/.well-known/webfinger?resource=` followed by the percent-encoded acct URI, with an `Accept` header of `application/jrd+json` ([@!RFC7033]).

2. **Canonical handle URI.** The `subject` of the resource descriptor MUST be an `acct` URI that is identical to the acct URI when both are converted to ASCII lowercase. The canonical handle URI is `at://` followed by the `subject` without its leading `acct:`.

3. **Actor.** Find the first link whose `rel` is `self` and whose `type` is `application/activity+json`, or `application/ld+json` with the profile `https://www.w3.org/ns/activitystreams`. Its `href` is the actor URL. `GET` the actor URL with an `Accept` header of `application/activity+json`. The `id` of the actor document MUST be identical to the actor URL.

4. **Back-link.** The actor's server must agree that the actor has this handle. This is the case if either:
   - the actor document has a `webfinger` property ([@?FEP-2C59]) that, with `at://` prepended, is identical to the canonical handle URI; or
   - a WebFinger request to the host of the actor URL, for the resource `acct:` followed by the actor's `preferredUsername`, `@`, and the host of the actor URL, returns a resource descriptor whose `subject` is the acct URI of the canonical handle URI and whose `self` link is the actor URL. If this is the same request as in step 1, it is not repeated.

   Otherwise fail.

5. **Subject.** The subject identifier is the actor's `id`.

6. **Issuers.** The authorized issuers are the targets of the `handle-issuer` links of the resource descriptor of step 1.

The identity document is the resource descriptor together with the actor document.

The resource descriptor is served by the handle's host, so a domain can delegate its handles to a server on another domain (the "split domain" configuration) by serving resource descriptors that point to actors on that server. The back-link check ensures that the server agrees. The `handle-issuer` links are also taken from the resource descriptor served by the handle's host, so the owner of the handle's domain decides which issuers can vouch for it.

> Open Issue: Whether the `handle-issuer` links should instead, or also, be taken from the actor document, which is controlled by the actor's server rather than by the handle's host.

## URL Handles {#resolve-url}

Given a URL handle URI, or a host handle URI whose host publishes no DID ((#resolve-host)):

1. **Fetch.** `GET` the handle URI's https URL without its fragment, with the `Accept` header `text/turtle, application/ld+json;q=0.9, text/html;q=0.8`. Follow redirects:
   - after a permanent redirect (status code 301 or 308), the canonical handle URI becomes the handle URI whose https URL is the redirect target, with the original fragment. If the redirect target has a username, password, or port, or its host is not a handle host, fail;
   - after any other redirect (for example 302, 303 or 307), the canonical handle URI is unchanged. In particular, a 303 response that refers to a document describing the WebID ([@?WEBID]) does not change the WebID.

2. **Profile.** The media type of the final response selects how the document is processed:
   - `text/turtle` or `application/ld+json`: an RDF profile, as used by Solid and Linked Web Storage ((#resolve-rdf)).
   - `text/html`: an HTML profile, as used by IndieAuth ((#resolve-html)).
   - Any other media type: fail.

The *profile URL* is the https URL of the canonical handle URI. It is the URL that the identity document describes, and it is the subject identifier. The identity document is the fetched document.

### RDF Profiles {#resolve-rdf}

The document is parsed as RDF using its base URL, the URL that it was fetched from.

1. **Back-link.** The document MUST contain at least one statement whose subject is the profile URL. This is how a WebID profile document states that it describes the WebID ([@?WEBID]).

2. **Issuers.** The authorized issuers are the objects of the statements whose subject is the profile URL and whose predicate is `http://www.iana.org/assignments/relation/handle-issuer`.

> Open Issue: The Linked Web Storage working group is defining authentication suites ([@?LWS]), including one based on OpenID Connect and one based on self-signed controlled identifiers. This section should align with how LWS identity documents name their issuers once that work stabilizes.

### HTML Profiles {#resolve-html}

The document is processed using the discovery rules of IndieAuth ([@?INDIEAUTH]): links are taken from the HTTP `Link` headers ([@!RFC8288]) of the final response and from the `link` elements of the HTML document, and links from `Link` headers take precedence.

1. **Back-link.** No separate back-link is checked. The document *is* the user's profile, so the links that it publishes are statements by the user. See (#shared-hosts).

2. **Issuers.** The authorized issuers are the targets of the `handle-issuer` links.

> Open Issue: Issuer identifiers are origins, as in [@!EVP]. IndieAuth and OpenID Connect both allow issuers whose identifier has a path, which cannot be named with `handle-issuer` as currently defined.

## Caching {#caching}

A resolving party MAY cache the results of resolution, subject to DNS time-to-live values and HTTP caching rules. A verifier SHOULD NOT cache resolution results for longer than a few minutes when verifying a token, because a user who moves their handle to another issuer, or who loses control of it, expects the change to take effect promptly.

# Issuers {#issuers}

## Issuer Identifier {#issuer-identifier}

An issuer identifier is an HTTPS origin: the string `https://` followed by a host, with no port, path, or trailing slash, for example `https://issuer.example`. This is the same form as the issuer identifier of [@!EVP], and for the same reasons: it names the same thing as the `iss` claim of OpenID Connect and the issuer of [@!RFC8414], and it can be compared byte-for-byte.

Every use of the issuer identity in this document (the authorized issuers that resolution yields, the `iss` claim of the HVT, the `issuer` member of the metadata, and the base of the well-known URL) is this origin. Comparisons are byte-for-byte; no scheme defaulting, port normalization, or trailing-slash tolerance is applied.

## Issuer Metadata {#issuer-metadata}

An issuer serves its metadata at `$ISSUER/.well-known/handle-verification`, where `$ISSUER` is its issuer identifier. For `https://issuer.example`, this is `https://issuer.example/.well-known/handle-verification`.

The metadata document is a JSON object with the following members:

- `issuer` (REQUIRED): The issuer identifier. It MUST be identical to the issuer identifier that the document was fetched under, and a party that fetches the document MUST reject it if it is not (as in Section 3.3 of [@!RFC8414]).
- `issuance_endpoint` (REQUIRED): The URL that the browser sends token requests to.
- `jwks_uri` (REQUIRED): The URL of the issuer's JSON Web Key Set ([@!RFC7517]), used to verify HVTs.
- `signing_alg_values_supported` (OPTIONAL): As defined by [@!EVP].

Example:

```json
{
  "issuer": "https://issuer.example",
  "issuance_endpoint": "https://issuer.example/hvp/issuance",
  "jwks_uri": "https://issuer.example/hvp/jwks",
  "signing_alg_values_supported": ["Ed25519", "ES256"]
}
```

An issuer that also acts as an EVP issuer serves its EVP metadata and its HVP metadata at their respective well-known paths. It MAY use the same keys for both.

> Open Issue: How the HVP metadata relates to the FedCM configuration file ([@?FEDCM]).

# Token Request Details {#token-request-details}

The token request is the token request of [@!EVP], including its use of HTTP Message Signatures ([@!RFC9421]) and the `hwk` key scheme, with the following substitutions:

- The browser performs (#resolution), not EVP's issuer discovery, to obtain the issuer and its metadata, and sends the request to the `issuance_endpoint` of the HVP metadata.
- The request body is a JSON object with the following member:
  - `handle` (REQUIRED): The canonical handle URI, byte-for-byte as resolution produced it.
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

{"handle":"at://samuelgoto.bsky.social"}
```

On receipt of a token request, the issuer:

1. Verifies the request headers, the HTTP Message Signature, and the `Content-Digest`, as in the request verification of [@!EVP], with `handle-verification` in place of `email-verification` as the expected `Sec-Fetch-Dest`.
2. Verifies that `handle` is a handle URI in canonical form ((#handle-uris)). If it is not, the issuer returns an `invalid_request` error ((#errors)).
3. Checks that the cookies represent a signed-in user who controls the handle. If they do not, the issuer returns an `authentication_required` error.
4. SHOULD resolve the handle ((#resolution)) and check that it is one of the authorized issuers and that the subject identifier is the user's. An HVT from an issuer that is not authorized is rejected by the verifier anyway, so this check is not needed for security, but it avoids issuing tokens that will fail.
5. Creates an HVT ((#hvt-creation)) and returns it as the value of `issuance_token` in an `application/json` response, as in [@!EVP].

# Handle Verification Token (HVT) {#hvt}

The Handle Verification Token (HVT) is a JWT ([@!RFC7519]) issued by an issuer. It contains a handle URI, the user's subject identifier, and the browser's public key.

## HVT Structure {#hvt-structure}

### Header

- `alg` (REQUIRED): The signing algorithm, with the same requirements as the `alg` of the EVT in [@!EVP]: a fully-specified identifier, and not `none`, a symmetric MAC algorithm, or the polymorphic `EdDSA`.
- `kid` (REQUIRED): The identifier of the signing key in the issuer's JWKS.
- `typ` (REQUIRED): `hvt+jwt`.

### Payload

- `iss` (REQUIRED): The issuer identifier ((#issuer-identifier)).
- `iat` (REQUIRED): The time the HVT was issued.
- `cnf` (REQUIRED): A confirmation claim ([@!RFC7800]) containing the browser's public key as a `jwk`, reproduced from the `Signature-Key` header of the token request with the same members, including its `alg`.
- `handle` (REQUIRED): The handle URI, byte-for-byte as it appeared in the token request.
- `sub` (REQUIRED): The subject identifier that resolution of the handle yields ((#resolution)): a DID for an AT Protocol handle, an actor ID for a user handle, or the profile URL for a handle resolved as a URL.

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
  "handle": "at://samuelgoto.bsky.social",
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
3. Extract the `iss`, `iat`, `cnf`, `handle`, and `sub` claims. Verify that `handle` is a handle URI in canonical form.
4. Resolve `handle` ((#resolution)), and verify that:
   - the canonical handle URI that resolution produces is byte-for-byte identical to `handle`;
   - the subject identifier that resolution produces is byte-for-byte identical to `sub`; and
   - `iss` is byte-for-byte identical to one of the authorized issuers.
5. Fetch the issuer metadata from `iss` ((#issuer-metadata)).
6. Fetch the issuer's public keys from its `jwks_uri`, and verify the HVT's signature with the key identified by `kid`.
7. Verify that `iat` is within an acceptable time window.

The browser additionally verifies that `handle` is byte-for-byte identical to the handle URI it requested, and that `cnf.jwk` matches the public key it generated. The browser MAY reuse the results of the resolution it performed before the token request for step 4.

# Key Binding (HVT+KB) {#kb}

Key binding is the key binding of [@!EVP], with the HVT in place of the EVT. The browser creates a KB-JWT whose `aud` is the verifier's origin, whose `nonce` is the verifier's session nonce, and whose `sd_hash` is the hash of the HVT (including its trailing `~`), and signs it with its private key. The HVT+KB is:

```
<HVT>~<KB-JWT>
```

The HVT+KB is compatible with SD-JWT with Key Binding ([@!I-D.ietf-oauth-selective-disclosure-jwt]), in the same way as the EVT+KB.

# Token Verification Details {#verification}

The verifier receives the HVT+KB, and verifies it by:

1. Verifying the KB-JWT as in [@!EVP], with the HVT in place of the EVT: its `alg` matches the `alg` of the HVT's `cnf.jwk`, its `aud` is the verifier's origin, its `nonce` is the session's nonce, its `iat` is recent, and its `sd_hash` is the hash of the HVT.
2. Verifying the HVT as described in (#hvt-verification), including resolving the handle itself.
3. Verifying the KB-JWT's signature with the public key in the HVT's `cnf.jwk`.

If all verification steps pass, the verifier has verified that the user controls the handle in the `handle` claim. The verifier SHOULD identify the user's account by the `sub` claim, and treat the `handle` as a mutable attribute of the account ((#reassignment)).

The verifier MUST perform its own resolution in step 2, and MUST NOT rely on resolution results provided by the browser. The verifier's resolution is what establishes that the issuer is authorized for the handle.

# Error Responses {#errors}

The issuer returns the error responses of [@!EVP] (`invalid_request`, `invalid_signature`, `authentication_required`, and server errors), with the `handle` member in place of the `email` member.


# Privacy Considerations

## Three-Party Model

As in [@!EVP], the browser intermediates between the verifier and the issuer. The issuer learns which handle the user is verifying, but not which verifier the user is signing in to, and the verifier learns the handle only after the user has chosen to share it.

## Handles Are Public Identifiers

Handles are public by design: an AT Protocol handle, an ActivityPub address, or a profile URL is meant to be shared and is the same at every site. A verifier that receives a handle can correlate the user with other verifiers that receive the same handle, and with the user's public activity under that handle. HVP does not change this, and offers no equivalent of the private email addresses of [@!EVP]. Browser APIs that use HVP should make clear to the user that the verifier will learn their handle.

## Resolution Traffic

Resolution consists of DNS queries and unauthenticated HTTPS requests. When the browser resolves a handle, the DNS resolver and the servers involved (the handle's host, a PLC directory, the user's personal data server, the user's profile host) can observe that someone is resolving that handle, but not which verifier is involved, because the requests carry no credentials or referrer.

When the verifier resolves a handle to verify a token, the same servers can observe that the verifier is checking the handle at that time. This is a difference from [@!EVP], where the verifier's lookup is a DNS query for the email domain only. The servers learn that the user signed in to the verifier, which is often information they would learn anyway once the verifier interacts with the user's account in that protocol. verifiers can reduce this by caching resolution results within the limits of (#caching).

# Security Considerations

## Resolution Is Not Authentication

Resolution establishes which issuers are authorized for a handle. It does not establish that the user controls the handle: that is established by the issuer's signature on an HVT, which the issuer produces only after authenticating the user. An attacker who manipulates the browser's resolution can cause the browser to send the user's handle to an issuer of the attacker's choosing, but cannot produce an HVT that the verifier accepts, because the verifier resolves the handle itself.

## DNS Spoofing {#dns-security}

Resolution of host handles relies on DNS `TXT` records, which are not authenticated unless DNSSEC is used. As in [@!EVP], spoofing the browser's DNS resolution discloses the handle to the attacker but yields no token the verifier will accept, while spoofing the verifier's DNS resolution lets the attacker choose the DID, and therefore the authorized issuers. verifiers SHOULD use a DNSSEC-validating resolver, and operators of handle domains SHOULD sign their zones. The other resolution steps rely on HTTPS and the Web PKI.

## Domain Control Is Handle Control

Every handle ultimately rests on control of a DNS name: whoever controls the handle's host controls its DNS records, its well-known URLs, its WebFinger responses, and its profile documents, and therefore its authorized issuers. This is by design: it is what lets users bring their own domain. It also means that when a domain changes hands, for example when it expires and is registered by someone else, its handles change hands too.

## Handle Reassignment {#reassignment}

Handles can be reassigned: a domain can expire and be re-registered, and a server can let a new account take a user name that a deleted account used. verifiers SHOULD identify accounts by the `sub` claim rather than the `handle` claim. For AT Protocol handles the subject identifier is a DID, which survives changes of handle and of server. For user and URL handles the subject identifier is itself a URL on the handle's domain, which gives weaker protection against reassignment.

## Shared Hosts {#shared-hosts}

For URL handles, whoever can publish a document at a URL controls the identity at that URL. Hosts that serve content from several users on one domain MUST NOT let a user publish `Link` headers, `link` elements, or RDF statements that name issuers for URLs belonging to other users. Hosts that give each user their own subdomain should be listed on the Public Suffix List ([@?PSL]) so that other mechanisms treat them as separate sites.

Resolving parties SHOULD take `link` elements only from the `head` of an HTML document, so that links injected into user-generated content in the `body` of a page are not treated as statements by the profile's owner.

## Multiple Authorized Issuers

A handle can have more than one authorized issuer, when its identity document has more than one `handle-issuer` link. Any of them can issue an HVT that the verifier accepts, so the security of the handle is the security of the weakest of them. This is the user's choice.

## Trust in the PLC Directory

For `did:plc` DIDs, resolution trusts the PLC directory to return the current DID document. Operations in the PLC directory are signed by the account's rotation keys, and a resolving party can verify the operation log instead of trusting the directory's response.

## Server-Side Request Forgery {#ssrf}

Resolution makes a verifier fetch URLs derived from user-controlled input. verifiers MUST resolve only `https` URLs, MUST NOT fetch URLs whose host resolves to a loopback, link-local, or private IP address, and SHOULD apply limits on redirects, response size, and time.

## Token Confusion

The `typ` of the HVT (`hvt+jwt`) is distinct from that of the EVT (`evt+jwt`), so an HVT cannot be presented as an EVT or the other way around. Each handle URI has exactly one resolution, determined by its shape and by what its host publishes, so the verifier and the browser cannot disagree on which identity document, subject, and issuers a token refers to.

## Downgrade Between AT Protocol and URL Resolution {#downgrade}

A host handle resolves as an AT Protocol handle when its host publishes a DID, and as a URL otherwise ((#resolve-host)). If transient failures of the AT Protocol lookup caused a fallback to URL resolution, an attacker who can block DNS queries or HTTPS requests could make a host handle resolve to a different identity document, with different issuers. Resolution therefore falls back only when the host positively indicates that it publishes no DID.

# IANA Considerations

## Well-Known URIs

This document registers the following well-known URIs in the "Well-Known URIs" registry ([@!RFC8615]):

- URI suffix: `handle-verification`
  - Change controller: IETF
  - Reference: (#issuer-metadata) of this document
  - Status: permanent

- URI suffix: `atproto-did`
  - Change controller: IETF
  - Reference: (#resolve-at) of this document
  - Status: permanent
  - Related information: Originally defined by the AT Protocol ([@?ATPROTO-HANDLE]).

## Underscored and Globally Scoped DNS Node Names

This document registers the following entry in the "Underscored and Globally Scoped DNS Node Names" registry ([@!RFC8552]):

- RR Type: `TXT`
- `_NODE NAME`: `_atproto`
- Reference: (#resolve-at) of this document

## Link Relation Types

This document registers the following link relation type in the "Link Relation Types" registry ([@!RFC8288]):

- Relation Name: `handle-issuer`
- Description: Refers to an issuer that the context authorizes to issue Handle Verification Tokens for its handle.
- Reference: (#handle-issuer) of this document

## URI Schemes

This document registers the following URI scheme in the "Uniform Resource Identifier (URI) Schemes" registry ([@!RFC7595]):

- Scheme name: `at`
- Status: provisional
- Applications/protocols that use this scheme name: AT Protocol; Handle Verification Protocol (as handle URIs, including for ActivityPub, IndieAuth, and Linked Web Storage identities)
- Contact: Sam Goto (goto@google.com)
- Change controller: IETF
- Reference: (#at-uri-scheme) of this document, and [@?ATPROTO-URI]

## JSON Web Token Claims

This document registers the following claim in the "JSON Web Token Claims" registry ([@!RFC7519]):

- Claim Name: `handle`
- Claim Description: A handle URI that the subject controls
- Change Controller: IETF
- Specification Document(s): (#hvt) of this document

## Media Types

This document registers the `application/hvt+jwt` media type in the "Media Types" registry ([@!RFC6838]), for the `typ` header of the HVT.

> Open Issue: Complete the media type registration template.


# Design Rationale

## Why Not Each Protocol's Own Sign-In?

AT Protocol, IndieAuth, and Solid each have an OAuth-based sign-in flow, and a verifier can implement all of them. But each requires a separate integration, each asks the verifier to present a text field for the user to type a handle, and in each the provider learns which verifier the user is signing in to. HVP gives verifiers a single integration, lets the browser offer the user's handles without the user typing them, and keeps the verifier hidden from the issuer. It reuses each protocol's resolution, which is the part that is already widely deployed.

## Why Generalize EVP?

EVP already solves the same problem for email addresses, with a three-party model, proof of possession of a browser key, and a token format compatible with SD-JWT. Generalizing it lets verifiers and issuers share code and keys between the two, and keeps the privacy properties. An alternative would be to profile OpenID Connect, but OpenID Connect's redirect-based flow reveals the verifier to the provider.

## Why a Single at URI Form?

Users should only have to learn one thing: a handle starts with `@`. The `@` notation is already how AT Protocol and ActivityPub handles are written, and requiring it for URL identities too removes every ambiguity of parsing: `alice@mail.example` is an email address and `@alice@mail.example` is a handle; `alice.example` is not a handle and `@alice.example` is. Carrying every handle as an `at://` URI, the URI spelling of `@`, gives tokens one handle format that can be compared byte-for-byte.

Which protocol a handle belongs to is then decided by the owner of its host, through what the host publishes, and not by how the handle is written. The cost is that IndieAuth and Solid users type `@alice.example` where they used to type `https://alice.example/`, and that the `at` scheme is broadened beyond the AT Protocol ((#at-uri-scheme)).

## Why Does the Verifier Resolve the Handle?

The verifier cannot trust the browser's resolution, which could be manipulated, and it cannot trust the issuer to say which handles it is authorized for. Resolving the handle itself is how the verifier checks that the issuer is authorized, in the same way that the verifier looks up the DNS delegation in [@!EVP].

## Why Require an Explicit handle-issuer Link? {#why-opt-in}

Each protocol already says who can authenticate its users: the PDS's authorization server, the IndieAuth metadata, the WebID's OpenID providers. HVP could infer its issuers from them. It does not, for two reasons. First, there is nothing to gain: an issuer has to deploy HVP's issuance endpoint and metadata anyway, and can add a `handle-issuer` link to the identity documents it serves at the same time. Second, an HVT is a new kind of statement, presented to verifiers through the browser, and a user who authorized a server to sign them in to one protocol has not necessarily authorized it to make that statement. An explicit link makes the user's opt-in visible in their identity document.

A single link relation, which works in every format that identity documents use, also lets a user choose an issuer that is not their protocol's sign-in server, without waiting for each protocol to define a way to do it.

## Why Define AT Protocol Handles and the at Scheme Here?

AT Protocol handles are DNS names with a resolution method that is useful outside the AT Protocol. Defining them, their resolution, and the `at` URI scheme in an IETF document makes them available to other protocols, lets the `at` scheme serve as the URI form of handles in general, and lets the AT Protocol reference this document rather than the other way around.

## Why Are Email Addresses Out of Scope?

Email addresses already have a protocol of their own, [@!EVP], which is further along, has implementations, and has requirements specific to email, such as private email addresses. A browser API can use EVP for email addresses and HVP for handles side by side. Covering email here as well would create two definitions that could diverge.

# Implementation Status

*Note: This section is to be removed before publishing as an RFC.*

There are no implementations of this document yet. Prototypes of the related IdP Registration API ([@?IDP-REGISTRATION]) exist in Chrome behind a flag, together with prototype identity providers and verifiers from the IndieWeb and Solid communities.

# Document History

*Note: This section is to be removed before publishing as an RFC.*

- draft-goto-handle-verification-00
  - Initial draft.

{backmatter}

# Examples {#examples}

This appendix shows the resolution of real handles at the time of writing. None of them publishes a `handle-issuer` link yet, so each example shows the link that would be added to opt in to a hypothetical issuer. The values will change over time.

## AT Protocol Handle on a Self-Hosted PDS

```
Handle:        @sgo.to
Handle URI:    at://sgo.to
DNS TXT _atproto.sgo.to -> "did=did:plc:thaoj4hhvraos7y6v3yog7re"
DID document (plc.directory):
  alsoKnownAs: ["at://sgo.to"]                  (back-link ok)
Subject:       did:plc:thaoj4hhvraos7y6v3yog7re
To opt in, add to the DID document's services:
  { "id": "#handle_issuer", "type": "HandleIssuer",
    "serviceEndpoint": "https://pds.sgo.to" }
Issuers:       https://pds.sgo.to
```

## AT Protocol Handle on a Hosted PDS

```
Handle:        @samuelgoto.bsky.social
Handle URI:    at://samuelgoto.bsky.social
GET https://samuelgoto.bsky.social/.well-known/atproto-did
  -> did:plc:bftbdgcbe4zclvpkboe4hleq
DID document (plc.directory):
  alsoKnownAs: ["at://samuelgoto.bsky.social"]  (back-link ok)
Subject:       did:plc:bftbdgcbe4zclvpkboe4hleq
To opt in, add to the DID document's services:
  { "id": "#handle_issuer", "type": "HandleIssuer",
    "serviceEndpoint": "https://bsky.social" }
Issuers:       https://bsky.social
```

## ActivityPub Address

```
Handle:        @goto@w3c.social
Handle URI:    at://goto@w3c.social
GET https://w3c.social/.well-known/webfinger
    ?resource=acct%3Agoto%40w3c.social
  subject: acct:goto@w3c.social
  self:    https://w3c.social/users/goto
GET https://w3c.social/users/goto
  id:          https://w3c.social/users/goto
  webfinger:   goto@w3c.social                 (back-link ok)
Subject:       https://w3c.social/users/goto
To opt in, add to the WebFinger resource descriptor's links:
  { "rel": "handle-issuer", "href": "https://w3c.social" }
Issuers:       https://w3c.social
```

## URL Handle with an HTML Profile (IndieAuth)

```
Handle:        @aaronparecki.com
Handle URI:    at://aaronparecki.com
DNS TXT _atproto.aaronparecki.com -> (none)
GET https://aaronparecki.com/.well-known/atproto-did -> 404
  (no DID: resolve as a URL)
GET https://aaronparecki.com/  (text/html)
Subject:       https://aaronparecki.com/
To opt in, add a response header:
  Link: <https://aaronparecki.com>; rel="handle-issuer"
Issuers:       https://aaronparecki.com
```

## URL Handle with an RDF Profile (Solid)

```
Handle:        @timbl.solidcommunity.net/profile/card#me
Handle URI:    at://timbl.solidcommunity.net/profile/card#me
GET https://timbl.solidcommunity.net/profile/card  (text/turtle)
  (back-link ok: the document describes <#me>)
Subject:       https://timbl.solidcommunity.net/profile/card#me
To opt in, add the statement:
  <#me> <http://www.iana.org/assignments/relation/handle-issuer>
        <https://solidcommunity.net> .
Issuers:       https://solidcommunity.net
```

# Relationship to IdP Registration {#idp-registration}

*This section is non-normative.*

The W3C IdP Registration API ([@?IDP-REGISTRATION]) extends FedCM ([@?FEDCM]) so that a verifier can request any identity provider in an open federation, and the browser keeps a registry of the user's handles. It relates to HVP the way the W3C Email Verification API relates to EVP:

- The browser API decides which handles to offer, lets the user register and select them, and delivers the token to the verifier. HVP defines what a handle is, how it is resolved, and how the token is issued and verified.
- The IdP Registration API currently parses handles and resolves them to an identity provider through its own DNS record. It could instead use the notation and resolution of this document, so that the identity provider of a handle is one of its authorized issuers.
- A verifier request for a "federation" in that API could correspond to HVP, and the token that the verifier receives could be an HVT+KB.

# Acknowledgments

This document builds on the Email Verification Protocol by Dick Hardt and Sam Goto, on the AT Protocol handle and AT URI specifications by Bluesky, and on IndieAuth, WebFinger, ActivityPub, WebID, and Solid.
