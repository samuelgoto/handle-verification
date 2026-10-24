%%%
title = "Username Handle Verification Protocol"
abbrev = "UHVP"
ipr = "trust200902"
area = "Security"
workgroup = "TBD"
keyword = ["handle", "verification", "identity", "authentication", "activitypub", "webfinger"]

[seriesInfo]
status = "standard"
name = "Internet-Draft"
value = "draft-goto-username-handle-verification-latest"
stream = "IETF"

date = 2026-10-24T00:00:00Z

[[author]]
initials = "S."
surname = "Goto"
fullname = "Sam Goto"
organization = "Google"
  [author.address]
  email = "goto@google.com"

%%%

<reference anchor="HVP" target="https://samuelgoto.github.io/handle-verification/draft-goto-handle-verification.html">
  <front>
    <title>Handle Verification Protocol</title>
    <author initials="S." surname="Goto" fullname="Sam Goto">
      <organization>Google</organization>
    </author>
    <date year="2026"/>
  </front>
  <seriesInfo name="Internet-Draft" value="draft-goto-handle-verification-latest"/>
</reference>

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

<reference anchor="ATPROTO-URI" target="https://atproto.com/specs/at-uri-scheme">
  <front>
    <title>AT Protocol: AT URI Scheme</title>
    <author>
      <organization>Bluesky Social PBC</organization>
    </author>
    <date year="2026"/>
  </front>
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

<reference anchor="FEP-C390" target="https://codeberg.org/fediverse/fep/src/branch/main/fep/c390/fep-c390.md">
  <front>
    <title>FEP-c390: Identity Proofs</title>
    <author>
      <organization>Fediverse Enhancement Proposals</organization>
    </author>
    <date year="2025"/>
  </front>
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

<reference anchor="MASTODON-WEBFINGER" target="https://docs.joinmastodon.org/spec/webfinger/">
  <front>
    <title>WebFinger</title>
    <author>
      <organization>Mastodon</organization>
    </author>
    <date year="2026"/>
  </front>
  <refcontent>Mastodon documentation</refcontent>
</reference>

<reference anchor="THREADS" target="https://www.threads.com/">
  <front>
    <title>Threads</title>
    <author>
      <organization>Meta Platforms, Inc.</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

.# Abstract

This document defines the Username Handle Verification Protocol (UHVP), which extends the Handle Verification Protocol ([@!HVP]) to *username handles*, such as `@alice@social.example`, which ActivityPub implementations use to identify users. A username handle is resolved with WebFinger, in a way that is backwards compatible with how ActivityPub implementations resolve handles today, to a unique user identifier and to the issuer that the user has authorized to vouch for it. The browser then obtains a Handle Verification Token (HVT) from that issuer, and presents it to a verifier, exactly as for a domain handle in HVP.

This document also defines how a domain handle, such as `@alice.example`, can name a username handle rather than a DID, so that the domain handles being proposed for ActivityPub can be verified through the account's username handle.

.# Discussion Venues

*Note: This section is to be removed before publishing as an RFC.*

Source for this draft and an issue tracker can be found at https://github.com/samuelgoto/handle-verification.

{mainmatter}

# Introduction

The Handle Verification Protocol ([@!HVP]) lets a browser obtain a signed Handle Verification Token (HVT) attesting that the user controls a domain handle, such as `@alice.example`, and present it to a verifier, without the user typing the handle and without revealing the verifier to the issuer. A domain handle is resolved to a DID, whose DID document names the issuer that the user has authorized.

ActivityPub ([@?ACTIVITYPUB]) has no concept of a handle itself, but its implementations identify users with handles of the form `@alice@social.example`, which they resolve to the URL of an ActivityPub actor with WebFinger ([@!RFC7033]) and the `acct` URI scheme ([@!RFC7565]) ([@?MASTODON-WEBFINGER]). This document calls these *username handles*. Their accounts do not have DIDs, and asking every user to publish DNS records would not be practical, so HVP's resolution does not apply to them.

This document extends HVP to username handles. It replaces HVP's resolution with a resolution through WebFinger, which every such server already implements, and which names the authorized issuer with a new `handle-issuer` link. Everything after resolution, that is, the issuer metadata, the HVT request, the HVT, its key binding, and the verification of the HVT+KB, is that of HVP, with the unique user identifier carried in a `url` member rather than a `did` member. A verifier that implements both documents accepts domain handles and username handles alike.

This document also lets a domain handle name a username handle, with a `webfinger=` key in HVP's handle records ((#activitypub)), so that a user of an ActivityPub server can use a domain handle such as `@alice.example`, as proposed by the SWICG Handles Task Force ([@?HANDLES-TF]).

# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 [@!RFC2119] [@!RFC8174] when, and only when, they appear in all capitals, as shown here.

This document uses the terms domain handle, DID, issuer, issuer identifier, authorized issuer, Handle Verification Token (HVT), HVT+KB, and verifier as defined in [@!HVP], and the following terms:

Username handle:
: A handle that consists of a user name and a DNS name, such as `alice@social.example`, displayed as `@alice@social.example`. See (#username-handles).

Unique user identifier:
: As in [@!HVP], an identifier of the user's account that resolution produces, and that the HVT carries in its `sub` claim. For a username handle, it is the `self` link of its WebFinger resource descriptor, which for an ActivityPub account is the URL of its actor. Unlike a handle, it identifies one account, but it changes when the account moves to another server.

# Protocol Flow {#protocol-flow}

The protocol flow is the flow of [@!HVP], with the following differences:

- The handle is a username handle ((#username-handles)), or a domain handle that names one ((#activitypub)).
- The browser and the verifier resolve the handle as described in (#resolve-user), rather than through a DID.
- The HVT request carries the unique user identifier in its `url` member, and the `sub` claim of the HVT is that URL ((#issuance)).

```
Step                       Verifier     Browser              Issuer
                               |            |                    |
Handle Discovery               |      [obtain handle from user]  |
                               |            |                    |
Session Binding                |--- nonce ->|                    |
                               |            |                    |
Handle Resolution              |   [WebFinger: unique user       |
                               |    identifier, issuer]          |
                               |            |                    |
HVT Request                    |            |-- POST /issuance ->|
                               |            |   (handle, url)    |
                               |            |                    |
HVT Issuance                   |            |<------- HVT -------|
                               |            |                    |
KB Creation                    |        [create KB-JWT]          |
                               |            |                    |
HVT+KB Presentation            |<-- HVT+KB -|                    |
                               |            |                    |
HVT+KB Verification [WebFinger;             |                    |
                     verify HVT+KB]         |                    |
```

# Username Handles {#username-handles}

A username handle is a user name and a DNS name separated by `@`, such as `alice@social.example`. It corresponds to the `acct` URI ([@!RFC7565]) `acct:alice@social.example`, which is resolved with WebFinger ([@!RFC7033]). A username handle is displayed with a leading `@`, as in `@alice@social.example`, and is carried in the protocol without it.

## Syntax {#username-handle-syntax}

A username handle consists of a user name, `@`, and a domain that satisfies the domain handle syntax of [@!HVP]. The user name is the `userpart` of an `acct` URI ([@!RFC7565]), and so does not contain `@`:

```abnf
user-handle = userpart "@" handle
userpart    = unreserved / sub-delims
              0*( unreserved / pct-encoded / sub-delims )
```

where `unreserved`, `pct-encoded`, and `sub-delims` are defined by [@!RFC3986], and `handle` is the domain handle syntax of [@!HVP]. The `acct` URI of a username handle is `acct:` followed by the handle.

## Normalization {#normalization}

Username handles are case-insensitive. The *normalized* form of a username handle is the handle converted to ASCII lowercase. Every username handle in this protocol (in the `handle` claim, and in comparisons) is in normalized form, and every comparison of handles is a byte-for-byte comparison of normalized handles.

> Open Issue: [@!RFC7565] does not require the `userpart` of an `acct` URI to be case-insensitive, although ActivityPub implementations generally treat it so. Whether lowercasing the whole handle is appropriate, or whether the `userpart` should be compared case-sensitively, needs to be investigated.

## Parsing User Input {#parsing}

To parse a username handle that a user typed:

1. Strip leading and trailing ASCII whitespace.
2. If the input starts with `@` and contains a second `@`, it is a username handle: remove the leading `@`, normalize the rest ((#normalization)), and check that it satisfies (#username-handle-syntax).
3. Otherwise, it is not a username handle; it can still be a domain handle, parsed as described in [@!HVP].

If any step fails, the input is not a username handle.

| Input | Handle |
|-------|--------|
| `@Alice@Social.Example` | `alice@social.example` (username handle) |
| `@alice.example` | not a username handle (domain handle, see [@!HVP]) |
| `alice@mail.example` | not a handle |

A username handle is always typed with its leading `@`, which distinguishes it from an email address: `alice@mail.example` is an email address, which a browser API can verify with [@?EVP], and `@alice@mail.example` is a username handle.

# Handle Resolution {#resolve-user}

*Resolution* takes a normalized username handle and produces the user's unique user identifier and the authorized issuer for the handle. It checks that the handle and the unique user identifier refer to each other, so that a handle cannot claim an account that does not agree to it, and finds the issuer that the user has explicitly authorized. Both the browser and the verifier perform resolution, for the same reasons as in [@!HVP], and the rules that [@!HVP] applies to every resolution step (on HTTP requests, redirects, limits, and caching) apply here too.

A username handle is resolved with WebFinger ([@!RFC7033]), in a way that is backwards compatible with how ActivityPub implementations already resolve handles to accounts ([@?MASTODON-WEBFINGER]). Given a normalized username handle *handle*, whose `acct` URI is `acct:` followed by *handle*:

1. **WebFinger.** `GET https://` *domain* `/.well-known/webfinger?resource=` followed by the percent-encoded `acct` URI, where *domain* is the domain of the handle, with an `Accept` header of `application/jrd+json`. The response MUST have a 2xx status code and contain a JSON Resource Descriptor ([@!RFC7033]).

2. **Subject.** The `subject` of the resource descriptor, converted to ASCII lowercase, MUST be identical to the `acct` URI. Otherwise fail. A resource descriptor whose `subject` names a different account only redirects discovery to that account, and does not make *handle* one of its handles.

3. **Unique user identifier.** The unique user identifier is the `href` of the first link whose `rel` is `self` and whose `href` is an `https` URL. If there is none, fail. For an ActivityPub account, this is the URI of its actor.

4. **Issuer.** The authorized issuer is the `href` of the link whose `rel` is `handle-issuer` ((#handle-issuer-link)). If there is none, or more than one, fail.

5. **Back-link.** Check that the server that hosts the account that the unique user identifier refers to agrees that the account has the handle ((#same-origin)). This check ensures that a username handle cannot claim an account that did not agree to it:
   - If the origin of the unique user identifier is identical to the authorized issuer, the check succeeds without any further request: the issuer is the server that hosts the account.
   - Otherwise, `GET https://` *host* `/.well-known/webfinger?resource=` followed by the percent-encoded unique user identifier, where *host* is the host of the unique user identifier, with an `Accept` header of `application/jrd+json`; a WebFinger resource can be any URI ([@!RFC7033]). The response MUST have a 2xx status code and contain a JSON Resource Descriptor; the `acct` URI of the handle MUST be identical, after conversion to ASCII lowercase, to its `subject` or to one of its `aliases`; and it MUST have a `self` link whose `href` is identical to the unique user identifier. Otherwise fail.

If any step fails, resolution fails.

The WebFinger request of step 5 costs one request, and uses only WebFinger, so it does not depend on the protocol of the account. Some ActivityPub implementations, such as Mastodon, already answer such requests for the URLs of their accounts, with the account's canonical handle as the `subject`, including in split domain configurations. A verifier MAY also perform it when the origins are identical.

The resource descriptor is served by the handle's domain, but the unique user identifier and the issuer can be on another host. This lets a domain use handles for accounts that are hosted elsewhere. For example, a domain `example.com` whose website is hosted separately can run an ActivityPub server at `social.example.com`, and give its users handles such as `@alice@example.com` (a "split domain" configuration); or a website can be bridged into ActivityPub by a service that hosts its actor. See (#examples).

For example, a username handle `@alice@example.com` on a split domain could resolve as follows:

```
GET https://example.com/.well-known/webfinger
      ?resource=acct%3Aalice%40example.com
  -> subject: acct:alice@example.com              (subject ok)
     self:    https://social.example.com/users/alice
     handle-issuer: https://social.example.com
User identifier:    https://social.example.com/users/alice
Issuer:             https://social.example.com    (same origin)
```

## The handle-issuer Link Relation {#handle-issuer-link}

A WebFinger resource descriptor names the issuer authorized to vouch for its handle with a link ([@!RFC7033]) whose `rel` is `handle-issuer` and whose `href` is an issuer identifier ([@!HVP]):

```json
{ "rel": "handle-issuer", "href": "https://social.example" }
```

A resource descriptor names at most one issuer. If it has no `handle-issuer` link, or its `href` is not an issuer identifier, the handle has no authorized issuer, and UHVP cannot be used with it. The issuer is usually the server that hosts the account, in which case the back-link request is skipped ((#resolve-user)), but it can be another origin, for example when a server's website and sign-in have moved to a new domain while its accounts keep their original URLs.

As with the `HandleIssuer` service of [@!HVP], authorization is explicit: resolution does not infer an issuer from the `self` link or from any other link, for the same reasons.

# Domain Handles That Name Username Handles {#activitypub}

Adding domain handles to ActivityPub is ongoing work, proposed by the SWICG Handles Task Force ([@?HANDLES-TF]). This section extends the resolution of domain handles of [@!HVP] so that a domain handle can name a username handle, rather than a DID, so that such handles can be verified as they are adopted, without the account adopting any new identifier.

[@!HVP] maps a domain handle to a DID with a `TXT` record at `_handle.` followed by the handle, whose value starts with `did=`, and with the `did` member of the well-known document `/.well-known/handle`, and ignores records and members with other keys. This document defines another key for each:

- **DNS `TXT` record.** A record at `_handle.` followed by the handle, whose value starts with `webfinger=`, names a username handle, in the remainder of the value.
- **Well-known document.** The `webfinger` member of the well-known document, if present, names a username handle.

The username handle MUST be written with its leading `@`, and satisfy (#username-handle-syntax) once the `@` is removed; otherwise fail. A resolving party that implements this document applies the rules of step 1 of the resolution of [@!HVP] to these keys as well: if the two lookups name different username handles, compared in normalized form ((#normalization)), or one names a DID and the other a username handle, resolution fails; and a handle that names a username handle with either lookup names something, so the resolving party does not fall back to the AT Protocol names.

Given a domain handle *handle* that names a username handle, resolve the username handle as described in (#resolve-user), with one additional check:

- **Back-link.** The `aliases` array of the WebFinger resource descriptor of the username handle ([@!RFC7033]) MUST contain `at://` followed by *handle*, compared after conversion to ASCII lowercase. Otherwise fail. This check ensures that a username handle cannot be claimed by a domain handle that it did not agree to. The `at` URI form ([@?ATPROTO-URI]) is the form in which [@!HVP] writes domain handles of every ecosystem.

The unique user identifier and the authorized issuer are those of the username handle. No DID is involved. The `handle` of the HVT request and of the HVT is the domain handle.

For example, a user whose account is `@alice@social.example`, and who wants to use the domain handle `@alice.example`, publishes a `TXT` record `_handle.alice.example` with the value `webfinger=@alice@social.example`, or the well-known document:

```http
GET /.well-known/handle HTTP/1.1
Host: alice.example

HTTP/1.1 200 OK
Content-Type: application/json

{"webfinger": "@alice@social.example"}
```

Their server also lists `at://alice.example` in the `aliases` of the account's WebFinger resource descriptor, next to its `handle-issuer` link.

A resolving party that implements [@!HVP] but not this document ignores the `webfinger=` record and the `webfinger` member, so the handle fails to resolve for it, unless it also has AT Protocol records.

> Open Issue: Whether an ActivityPub account should also be able to resolve its domain handle to a DID, for example to have an identity that survives a move to another server, or to let one DID document, and so one domain handle, serve both the AT Protocol and ActivityPub. ActivityPub implementations do not identify accounts by DIDs today, so a verifier that receives a DID would not necessarily know how to find, or interact with, the ActivityPub account that it belongs to; the DID document could name the actor in its `alsoKnownAs`, with a check that the actor refers back to the DID ([@?FEP-C390]).

# Issuance and Verification {#issuance}

Issuance and verification are those of [@!HVP]: the issuer metadata, the HVT request, its error responses, the HVT, the key binding, and the verification of the HVT+KB, with the following substitutions:

- Wherever [@!HVP] resolves a handle, the resolving party resolves a username handle as described in (#resolve-user), and a domain handle as described in [@!HVP] as extended by (#activitypub).
- The body of the HVT request carries the unique user identifier in a `url` member, in place of the `did` member:
  - `handle` (REQUIRED): The handle that the user selected, in normalized form: a username handle ((#normalization)), or a domain handle that names one ((#activitypub)).
  - `url` (REQUIRED): The unique user identifier that the handle resolves to, byte-for-byte as resolution produced it.
- On receipt of an HVT request, the issuer verifies that the body has exactly one of `did` and `url`, that `handle` satisfies (#username-handle-syntax) or the domain handle syntax of [@!HVP] and is in normalized form, and that a `url` is an `https` URL; otherwise it returns an `invalid_request` error. It then checks that the cookies represent a signed-in user who controls `handle`, and whose account is the `url`.
- The `sub` claim of the HVT is the unique user identifier, byte-for-byte as it appeared in the `url` member of the HVT request.
- When verifying an HVT, the browser and the verifier accept a `handle` claim that satisfies (#username-handle-syntax), and resolve it as described in (#resolve-user).

Example:

```http
POST /hvp/issuance HTTP/1.1
Host: social.example
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

{"handle":"alice@social.example",
 "url":"https://social.example/users/alice"}
```

and the payload of the resulting HVT:

```json
{
  "iss": "https://social.example",
  "iat": 1792620000,
  "cnf": {
    "jwk": {
      "kty": "OKP",
      "crv": "Ed25519",
      "x": "JrQLj5P_89iXES9-vFgrIy29clF9CC_oPPsw3c5D0bs",
      "alg": "Ed25519"
    }
  },
  "handle": "alice@social.example",
  "sub": "https://social.example/users/alice"
}
```

A verifier distinguishes the unique user identifiers of the two documents by their form: a DID starts with `did:`, and the `self` link of a username handle with `https:`.

# Privacy Considerations

The privacy considerations of [@!HVP] apply. In particular, the issuer does not learn which verifier the user signs in to, and handles and unique user identifiers are public identifiers.

Resolution of a username handle is specific to one user, as resolution of a domain handle is: the WebFinger request names the user. When the browser resolves a username handle, the WebFinger server of the handle's domain and, when the back-link request of step 5 of (#resolve-user) is made, the server that hosts the account can observe that the user's device is resolving that handle, but not which verifier is involved, because the requests carry no credentials or referrer. When the verifier resolves it, these servers see the verifier's network address, as described in [@!HVP]. For username handles, the WebFinger server is usually the user's issuer, which can therefore often correlate the HVTs it issues with the resolutions that follow. The mitigations described in [@!HVP], such as caching and resolving through a shared intermediary, apply.

# Security Considerations

The security considerations of [@!HVP] apply, with the following additions.

## Unique User Identifiers of Username Handles {#same-origin}

The WebFinger response of a username handle is controlled by the owner of the handle's domain, and names both the unique user identifier and the issuer. Without a further check, a malicious domain could name another user's account as the unique user identifier, and an issuer of its own choosing:

```
acct:x@evil.example -> self:          https://social.example/users/bob
                       handle-issuer: https://evil.example
```

Its issuer could then issue an HVT whose `sub` is Bob's account, and a verifier that identifies accounts by `sub` would sign the attacker in as Bob. For domain handles, the back-link checks of [@!HVP] and of (#activitypub) prevent the equivalent attack, in which a domain handle claims another user's DID or username handle. For username handles, step 5 of (#resolve-user) prevents it, in one of two ways:

- If the unique user identifier is on the origin of the authorized issuer, the issuer is the server that hosts the account, and a server that issues an HVT for one of its accounts has authenticated that account's user ((#issuance)). A domain can at most give its own handles to accounts on that server.
- Otherwise, the back-link check of step 5 of (#resolve-user) requires the server that hosts the account to agree that it has the handle. Bob's account does not claim `x@evil.example`, so resolution fails.

## Domain Control Is Handle Control

Whoever controls the domain of a username handle controls its WebFinger responses, and therefore which account and which issuer each username handle refers to, within the limits of step 5 of (#resolve-user): a handle can name an account on another server only if that account agrees ((#same-origin)). When a domain changes hands, its username handles change hands too.

## Handle Reassignment

As in [@!HVP], verifiers SHOULD identify accounts by the unique user identifier in the `sub` claim rather than by the `handle` claim. The unique user identifier of a username handle is the URL of the account on its server, which survives changes of handle that keep the account on the same server, but changes when the account moves to another server.

# IANA Considerations

## Link Relation Types

This document registers the following link relation type in the "Link Relation Types" registry ([@!RFC8288]):

- Relation Name: `handle-issuer`
- Description: Refers to the issuer that the context authorizes to issue Handle Verification Tokens for its handle.
- Reference: (#handle-issuer-link) of this document

# Design Rationale

## Why a Separate Document?

Domain handles and username handles are resolved differently, because each already has a resolution mechanism that is deployed: domain handles are mapped to a DID through DNS or a well-known URL, as in the AT Protocol, and username handles are mapped to an account through WebFinger, as in ActivityPub implementations. The two mechanisms are at different stages of maturity and involve different communities, so they are specified separately, while sharing issuance and verification, which do not depend on how the handle was resolved.

## Why WebFinger?

Every ActivityPub server that supports username handles already implements WebFinger, so supporting UHVP requires updating server software, not asking each user to publish DNS records. WebFinger produces the same things as the resolution of [@!HVP], a unique user identifier and an explicitly authorized issuer, so issuance and verification are the same for both.

UHVP could instead treat the handle's domain as the issuer, as [@?EVP] treats the email domain, and skip WebFinger. But in ActivityPub the server that hosts an account is not always at the handle's domain: in a split domain configuration, the handles are at `example.com` and the server at `social.example.com`, and a bridging service can host actors for handles at many domains ((#examples)). WebFinger is what tells the two apart, per user, at the cost of one request.

## Why the Same-Origin Shortcut? {#why-same-origin}

A username handle's WebFinger response is controlled by the handle's domain, which is not necessarily the server that hosts the account it names ((#same-origin)). UHVP checks the account back with a WebFinger request for its unique user identifier (step 5 of (#resolve-user)), at the cost of one request. ActivityPub implementations perform an equivalent check by fetching the actor and reading its `webfinger` property or performing a reverse WebFinger lookup ([@?MASTODON-WEBFINGER], [@?FEP-2C59]), which is specific to ActivityPub.

In the common case, the issuer is the server that hosts the account, and the unique user identifier is on its origin. The issuer then authenticates the account's user itself, which gives the same protection for the purposes of UHVP, so the back-link request is skipped. This covers split domains and bridges ((#examples)).

The back-link request is still needed for issuers on another origin (for example, Threads ([@?THREADS]) gives its users handles such as `@zuck@threads.net`, whose actors are at `https://threads.net/ap/users/...`, while its website, where users sign in, has moved to `https://www.threads.com`; ActivityPub accounts cannot change their URLs without breaking federation, so the natural issuer is on a different site from the accounts it vouches for).

> Open Issue: At the time of writing, Threads does not answer WebFinger requests for the URLs of its accounts, which the back-link request requires when the issuer is on another origin, and the reference cited for its move to `threads.com` is its home page rather than an announcement. How Threads, and other services whose accounts are on a different site from where their users sign in, would deploy UHVP needs to be investigated, and the reference replaced.

## Why Alias Domain Handles to Username Handles?

A domain handle of an ActivityPub account needs a stable identifier for the account, a document that claims the handle back, and a place to name the issuer. A username handle provides all three through its WebFinger resource descriptor, so the domain handle can resolve to it without the account adopting any new identifier, such as a DID ((#activitypub)).

# Implementation Status

*Note: This section is to be removed before publishing as an RFC.*

There are no implementations of this document yet.

# Document History

*Note: This section is to be removed before publishing as an RFC.*

- draft-goto-username-handle-verification-00
  - Initial draft, covering username handles, previously part of [@!HVP].

{backmatter}

# Examples {#examples}

This appendix shows the resolution of handles. The username handle examples are real handles at the time of writing. None of them publishes a `handle-issuer` link yet, so each shows what would be added to opt in. The domain handle example is hypothetical. The values will change over time.

## Domain Handle That Names a Username Handle

```
Handle:        @alice.example
DNS TXT _handle.alice.example
  -> "webfinger=@alice@social.example"
Names:         @alice@social.example
GET https://social.example/.well-known/webfinger
      ?resource=acct%3Aalice%40social.example
  subject: acct:alice@social.example            (subject ok)
  aliases: ["at://alice.example"]               (back-link ok)
  self:    https://social.example/users/alice
  handle-issuer: https://social.example
Identifier:    https://social.example/users/alice
Issuer:        https://social.example           (same origin)
```

## Username Handle on a Split Domain

The handle is at the owner's website, and the ActivityPub server is on a subdomain.

```
Handle:        @simon@simonwillison.net
GET https://simonwillison.net/.well-known/webfinger
      ?resource=acct%3Asimon%40simonwillison.net
  subject: acct:simon@simonwillison.net         (subject ok)
  self:    https://fedi.simonwillison.net/users/simon
Identifier:    https://fedi.simonwillison.net/users/simon
To opt in, add to the resource descriptor's links:
  { "rel": "handle-issuer",
    "href": "https://fedi.simonwillison.net" }
Issuer:        https://fedi.simonwillison.net   (same origin)
```

## Username Handle Hosted by a Bridge

The handle is at a website, and its actor is hosted by a service that bridges the website into ActivityPub.

```
Handle:        @snarfed.org@snarfed.org
GET https://snarfed.org/.well-known/webfinger
      ?resource=acct%3Asnarfed.org%40snarfed.org
  subject: acct:snarfed.org@snarfed.org         (subject ok)
  self:    https://fed.brid.gy/snarfed.org
Identifier:    https://fed.brid.gy/snarfed.org
To opt in, add to the resource descriptor's links:
  { "rel": "handle-issuer", "href": "https://fed.brid.gy" }
Issuer:        https://fed.brid.gy              (same origin)
```

## Username Handle Whose Issuer Is on Another Origin

The handle and the actor are on the service's original domain, and its website, where users sign in, has moved to another domain. The back-link request is required.

```
Handle:        @zuck@threads.net
GET https://threads.net/.well-known/webfinger
      ?resource=acct%3Azuck%40threads.net
  subject: acct:zuck@threads.net                (subject ok)
  self:    https://threads.net/ap/users/17841401746480004/
Identifier:    https://threads.net/ap/users/17841401746480004/
To opt in, add to the resource descriptor's links:
  { "rel": "handle-issuer", "href": "https://www.threads.com" }
Issuer:        https://www.threads.com          (other origin)
Back-link:     WebFinger at threads.net for the resource
               https://threads.net/ap/users/17841401746480004/
               must name acct:zuck@threads.net
```

## Discovery Alias That Is Not a Handle

A domain can serve a WebFinger response that redirects discovery to an account elsewhere. Its `subject` names that account, so the input is not a handle of the account ((#resolve-user)), and resolution fails.

```
Input:         @scott@hanselman.com
GET https://hanselman.com/.well-known/webfinger
      ?resource=acct%3Ascott%40hanselman.com
  subject: acct:shanselman@hachyderm.io         (subject mismatch)
Result:        not a handle; @shanselman@hachyderm.io is
```

# Acknowledgments

This document builds on the Handle Verification Protocol, on the Handles Task Force proposal by Anuj Ahooja and Emelia Smith, on FEP-c390 by silverpill, and on the WebFinger conventions of ActivityPub implementations.
