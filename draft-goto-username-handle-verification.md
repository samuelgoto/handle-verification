%%%
title = "Username Handles"
abbrev = "Username Handles"
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

<reference anchor="URL-HANDLES" target="https://samuelgoto.github.io/handle-verification/draft-goto-url-handle-verification.html">
  <front>
    <title>URL Handles</title>
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

<reference anchor="CID-1.0" target="https://www.w3.org/TR/cid-1.0/">
  <front>
    <title>Controlled Identifiers v1.0</title>
    <author>
      <organization>W3C</organization>
    </author>
    <date year="2025" month="May"/>
  </front>
  <refcontent>W3C Recommendation</refcontent>
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

<reference anchor="INDIEAUTH" target="https://indieauth.spec.indieweb.org/">
  <front>
    <title>IndieAuth</title>
    <author initials="A." surname="Parecki" fullname="Aaron Parecki">
      <organization/>
    </author>
    <date year="2024"/>
  </front>
  <refcontent>IndieWeb Living Standard</refcontent>
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

This document defines *username handles*, a handle type of the Handle Verification Protocol ([@!HVP]) that builds on URL handles ([@!URL-HANDLES]), such as `@alice@social.example`, which ActivityPub implementations use to identify users. A username handle is mapped with WebFinger, in a way that is backwards compatible with how ActivityPub implementations resolve handles today, to the URL of the user's account, which is then resolved as a URL handle ([@!URL-HANDLES]) to a unique user identifier and to the issuer that the user has authorized to vouch for it. The browser then obtains a Handle Verification Token (HVT) from that issuer, and presents it to a verifier, as for any handle type of HVP.

This document also defines how a domain handle, such as `@alice.example`, can name a username handle or a URL handle rather than a DID, so that the domain handles being proposed for ActivityPub can be verified through the account's username handle or the URL of its actor.

.# Discussion Venues

*Note: This section is to be removed before publishing as an RFC.*

Source for this draft and an issue tracker can be found at https://github.com/samuelgoto/handle-verification.

{mainmatter}

# Introduction

The Handle Verification Protocol ([@!HVP]) lets a browser obtain a signed Handle Verification Token (HVT) attesting that the user controls a handle, and present it to a verifier, without the user typing the handle and without revealing the verifier to the issuer. HVP is extensible to several handle types, and defines one, domain handles, such as `@alice.example`, which are resolved to a DID, whose DID document names the issuer that the user has authorized.

ActivityPub ([@?ACTIVITYPUB]) has no concept of a handle itself, but its implementations identify users with handles of the form `@alice@social.example`, which they resolve to the URL of an ActivityPub actor with WebFinger ([@!RFC7033]) and the `acct` URI scheme ([@!RFC7565]) ([@?MASTODON-WEBFINGER]). This document calls these *username handles*. Their accounts do not have DIDs, and asking every user to publish DNS records would not be practical, so the resolution of domain handles does not apply to them.

[@!URL-HANDLES] defines another handle type, URL handles, for users who are identified by an `https` URL, such as an ActivityPub actor, and resolves such a URL to a unique user identifier and an authorized issuer by fetching it.

This document defines a third handle type, username handles, on top of URL handles. It maps a username handle to the URL of its account with WebFinger, which every such server already implements, and resolves that URL as described in [@!URL-HANDLES]. The only thing that this document adds to resolution is the WebFinger mapping, and a check that the account agrees to the handle. Nothing in it is specific to ActivityPub: the account URL is the `self` link of the WebFinger resource descriptor, which can refer to an ActivityPub actor, a Solid WebID, or any other identity document. Everything after resolution, that is, the issuer metadata, the HVT request, the HVT, its key binding, and the verification of the HVT+KB, is that of HVP. A verifier that implements all three handle types accepts domain handles, URL handles, and username handles alike.

This document also lets a domain handle name a username handle or a URL handle, with a `me=` key in HVP's handle records ((#domain-handles)), so that a user of an ActivityPub server, or of any server that identifies its accounts by URL, can use a domain handle such as `@alice.example`, as proposed by the SWICG Handles Task Force ([@?HANDLES-TF]).

# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 [@!RFC2119] [@!RFC8174] when, and only when, they appear in all capitals, as shown here.

This document uses the terms domain handle, DID, issuer, issuer identifier, authorized issuer, Handle Verification Token (HVT), HVT+KB, and verifier as defined in [@!HVP], the terms URL handle and identity document as defined in [@!URL-HANDLES], and the following terms:

Username handle:
: A handle that consists of a user name and a DNS name, such as `alice@social.example`, displayed as `@alice@social.example`. See (#username-handles).

Unique user identifier:
: As in [@!HVP], an identifier of the user's account that resolution produces, and that the HVT carries in its `sub` claim. For a username handle, it is the unique user identifier of the URL handle that the `self` link of its WebFinger resource descriptor refers to ([@!URL-HANDLES]), which for an ActivityPub account is the URL of its actor. Unlike a handle, it identifies one account, but it changes when the account moves to another server.

# Protocol Flow {#protocol-flow}

The protocol flow is the flow of [@!HVP], with the following particulars:

- The handle is a username handle ((#username-handles)), or a domain handle that names a username handle or a URL handle ((#domain-handles)).
- The browser and the verifier resolve the handle as described in (#resolve-user): with WebFinger, and then as a URL handle ([@!URL-HANDLES]).
- The `sub` of the HVT request and of the HVT is the unique user identifier, an `https` URL, while the `handle` remains the username handle ((#issuance)).

```
Step                       Verifier     Browser              Issuer
                               |            |                    |
Handle Discovery               |      [obtain handle from user]  |
                               |            |                    |
Session Binding                |--- nonce ->|                    |
                               |            |                    |
Handle Resolution              |   [WebFinger, then GET account  |
                               |    URL: identifier, issuer]     |
                               |            |                    |
HVT Request                    |            |-- POST /issuance ->|
                               |            |   (handle, sub)    |
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

*Resolution* takes a normalized username handle and produces the user's unique user identifier and the authorized issuer for the handle. It maps the handle to the URL of the user's account with WebFinger ([@!RFC7033]), in a way that is backwards compatible with how ActivityPub implementations already resolve handles to accounts ([@?MASTODON-WEBFINGER]), resolves that URL as a URL handle ([@!URL-HANDLES]), and checks that the account agrees to the handle. Both the browser and the verifier perform resolution, for the same reasons as in [@!HVP], and the rules that [@!HVP] applies to every resolution step (on HTTP requests, redirects, limits, and caching) apply here too.

Given a normalized username handle *handle*, whose `acct` URI is `acct:` followed by *handle*:

1. **WebFinger.** `GET https://` *domain* `/.well-known/webfinger?resource=` followed by the percent-encoded `acct` URI, where *domain* is the domain of the handle, with an `Accept` header of `application/jrd+json`. The response MUST have a 2xx status code and contain a JSON Resource Descriptor ([@!RFC7033]).

2. **Subject.** The `subject` of the resource descriptor, converted to ASCII lowercase, MUST be identical to the `acct` URI. Otherwise fail. A resource descriptor whose `subject` names a different account only redirects discovery to that account, and does not make *handle* one of its handles.

3. **Account URL.** The account URL is the `href` of the first link whose `rel` is `self` and whose `href` is an `https` URL, whatever its `type`. If there is none, or it is not a URL handle once normalized ([@!URL-HANDLES]), fail. For an ActivityPub account, this is the URI of its actor.

4. **URL handle resolution.** Resolve the account URL as a URL handle ([@!URL-HANDLES]). If resolution fails, fail. Otherwise, the unique user identifier and the authorized issuer are those that it produces: the account's identity document names the issuer, with the `HandleVerification` service of its controlled identifier document ([@!HVP]) or a `handle-verification` link.

5. **Back-link.** Check that the server that hosts the account agrees that the account has the handle ((#same-origin)):
   - If the origin of the unique user identifier is identical to the authorized issuer, the check succeeds without any further request: the issuer is the server that hosts the account.
   - Otherwise, `GET https://` *host* `/.well-known/webfinger?resource=` followed by the percent-encoded unique user identifier, where *host* is the host of the unique user identifier, with an `Accept` header of `application/jrd+json`; a WebFinger resource can be any URI ([@!RFC7033]). The response MUST have a 2xx status code and contain a JSON Resource Descriptor; the `acct` URI of the handle MUST be identical, after conversion to ASCII lowercase, to its `subject` or to one of its `aliases`; and it MUST have a `self` link whose `href` is identical to the unique user identifier. Otherwise fail.

If any step fails, resolution fails. Unlike a URL handle that the user typed, the username handle is not replaced by the unique user identifier: it remains the handle, in the HVT request and in the HVT.

The WebFinger request of step 5 costs one request, and uses only WebFinger, so it does not depend on the protocol of the account. Some ActivityPub implementations, such as Mastodon, already answer such requests for the URLs of their accounts, with the account's canonical handle as the `subject`, including in split domain configurations. A verifier MAY also perform it when the origins are identical.

The resource descriptor is served by the handle's domain, but the account and the issuer can be on another host. This lets a domain use handles for accounts that are hosted elsewhere. For example, a domain `example.com` whose website is hosted separately can run an ActivityPub server at `social.example.com`, and give its users handles such as `@alice@example.com` (a "split domain" configuration); or a website can be bridged into ActivityPub by a service that hosts its actor. See (#examples).

For example, a username handle `@alice@example.com` on a split domain could resolve as follows:

```
GET https://example.com/.well-known/webfinger
      ?resource=acct%3Aalice%40example.com
  -> subject: acct:alice@example.com              (subject ok)
     self:    https://social.example.com/users/alice
GET https://social.example.com/users/alice      (URL handle)
  -> { "id": "https://social.example.com/users/alice",
       "service": [{ "id": "#handle_verification",
                     "type": "HandleVerification",
                     "serviceEndpoint":
                       "https://social.example.com" }], ... }
User identifier:    https://social.example.com/users/alice
Issuer:             https://social.example.com    (same origin)
```

> Open Issue: Some ActivityPub servers, such as Mastodon servers with "authorized fetch" enabled, serve actors only to requests that are signed by another server's actor, and respond to the unsigned requests of resolution with a 401 (Unauthorized) response. Their WebFinger responses remain public, so step 3 succeeds, but step 4 fails, as it does for URL handles of such servers ([@!URL-HANDLES]). Such servers would need to serve their actors, or at least the `handle-verification` link of their responses, to unsigned requests. This needs to be discussed with Mastodon as an implementation detail.

# Domain Handles That Name Other Handles {#domain-handles}

Adding domain handles to ActivityPub is ongoing work, proposed by the SWICG Handles Task Force ([@?HANDLES-TF]). This section extends the resolution of domain handles of [@!HVP] so that a domain handle can name a username handle ((#username-handles)) or a URL handle ([@!URL-HANDLES]), rather than a DID, so that such handles can be verified as they are adopted, without the account adopting any new identifier.

[@!HVP] maps a domain handle to a DID with a `TXT` record at `_handle.` followed by the handle, whose value starts with `did=`, and with the `did` member of the well-known document `/.well-known/handle`, and ignores records and members with other keys. This document defines another key for each:

- **DNS `TXT` record.** A record at `_handle.` followed by the handle, whose value starts with `me=`, names a handle, in the remainder of the value.
- **Well-known document.** The `me` member of the well-known document, if present, names a handle.

The named handle is either a username handle, written with its leading `@`, such as `@alice@social.example`, or a URL handle, such as `https://social.example/users/alice`. The resolving party parses it as a username handle ((#parsing)) if it starts with `@`, and as a URL handle ([@!URL-HANDLES]) if it starts with `https://`; if it is neither, fail. A resolving party that implements this document applies the rules of step 1 of the resolution of [@!HVP] to these keys as well: if the two lookups name different handles, compared in normalized form, or one names a DID and the other a handle, resolution fails; and a handle that names a handle with either lookup names something, so the resolving party does not fall back to the AT Protocol names.

Given a domain handle *handle* that names another handle *named*:

1. **Resolution.** Resolve *named*, as described in (#resolve-user) if it is a username handle, or in [@!URL-HANDLES] if it is a URL handle. If resolution fails, fail. Otherwise, the unique user identifier and the authorized issuer are those that it produces.
2. **Back-link.** The identity document of the account ([@!URL-HANDLES]) MUST claim *handle* back, with `at://` followed by *handle*, compared after conversion to ASCII lowercase. A controlled identifier document claims it in its `alsoKnownAs` member ([@!CID-1.0]), read as described in [@!HVP], whose value is a JSON array of strings; ActivityPub actors and DID documents ([@?DID-CORE]) use the same member, with the same meaning. As [@!CID-1.0] advises, the two identifiers are treated as referring to the same account only because each refers to the other: the domain handle names the account, and the account's document lists the domain handle. An HTML identity document claims it with a link whose relation type is `me`, in a `Link` header field ([@!RFC8288]) or in a `<link>` element, as IndieWeb websites link to their other identities ([@?INDIEAUTH]). Otherwise fail. This check ensures that an account cannot be claimed by a domain handle that it did not agree to. The `at` URI form ([@?ATPROTO-URI]) is the form in which [@!HVP] writes domain handles of every ecosystem.

The named handle cannot itself be a domain handle, so resolution does not recurse. No DID is involved. The `handle` of the HVT request and of the HVT is the domain handle.

For example, a user whose account is `@alice@social.example`, at `https://social.example/users/alice`, and who wants to use the domain handle `@alice.example`, publishes a `TXT` record `_handle.alice.example` with the value `me=@alice@social.example`, or `me=https://social.example/users/alice`, or the well-known document:

```http
GET /.well-known/handle HTTP/1.1
Host: alice.example

HTTP/1.1 200 OK
Content-Type: application/json

{"me": "@alice@social.example"}
```

Their server also lists `at://alice.example` in the `alsoKnownAs` of the account's actor.

A resolving party that implements [@!HVP] but not this document ignores the `me=` record and the `me` member, so the handle fails to resolve for it, unless it also has AT Protocol records.

> Open Issue: ActivityPub implementations, such as Mastodon, use `alsoKnownAs` to list the other actors of an account, for example when it moves to another server, and might not expect it to contain `at` URIs. Whether `alsoKnownAs` is the right property for the back-link needs to be discussed with them.

> Open Issue: Whether an ActivityPub account should also be able to resolve its domain handle to a DID, for example to have an identity that survives a move to another server, or to let one DID document, and so one domain handle, serve both the AT Protocol and ActivityPub. ActivityPub implementations do not identify accounts by DIDs today, so a verifier that receives a DID would not necessarily know how to find, or interact with, the ActivityPub account that it belongs to; the DID document could name the actor in its `alsoKnownAs`, with a check that the actor refers back to the DID ([@?FEP-C390]).

# Issuance and Verification {#issuance}

Issuance and verification are those of [@!HVP], for which a username handle is a handle of the username handle type, with the syntax and normalization of (#username-handles) and the resolution of (#resolve-user). Its unique user identifier is an `https` URL, which is carried in the `sub` member of the HVT request and the `sub` claim of the HVT, while the `handle` remains the username handle: unlike a URL handle, a username handle is not replaced by its unique user identifier.

This document also extends the domain handle type of [@!HVP]: a domain handle that names another handle ((#domain-handles)) has the unique user identifier of that handle, an `https` URL, rather than a DID, and its `handle` remains the domain handle.

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
 "sub":"https://social.example/users/alice"}
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

As for every handle type, a verifier recognizes a username handle by the form of its `handle` claim ([@!HVP]).

# Privacy Considerations

The privacy considerations of [@!HVP] apply. In particular, the issuer does not learn which verifier the user signs in to, and handles and unique user identifiers are public identifiers.

Resolution of a username handle is specific to one user, as resolution of a domain handle is: the WebFinger request names the user. When the browser resolves a username handle, the WebFinger server of the handle's domain, the server that hosts the account, from which step 4 of (#resolve-user) fetches the identity document, and, when the back-link request of step 5 is made, the WebFinger server of the account's host can observe that the user's device is resolving that handle, but not which verifier is involved, because the requests carry no credentials or referrer. When the verifier resolves it, these servers see the verifier's network address, as described in [@!HVP]. For username handles, the WebFinger server is usually the user's issuer, which can therefore often correlate the HVTs it issues with the resolutions that follow. The mitigations described in [@!HVP], such as caching and resolving through a shared intermediary, apply.

# Security Considerations

The security considerations of [@!HVP] apply, with the following additions.

## Unique User Identifiers of Username Handles {#same-origin}

The WebFinger response of a username handle is controlled by the owner of the handle's domain, and names the account. The issuer is named by the account's identity document, which is controlled by the server that hosts the account ([@!URL-HANDLES]), so a malicious domain cannot choose the issuer of another user's account. But without a further check, it could give another user's account a handle that the account did not agree to:

```
acct:x@evil.example -> self: https://social.example/users/bob
```

Bob's issuer would then be the authorized issuer for `x@evil.example`, and a verifier would accept an HVT from it that says that Bob controls `x@evil.example`. For domain handles, the back-link checks of [@!HVP] and of (#domain-handles) prevent the equivalent problem, in which a domain handle claims another user's DID, username handle, or URL handle. For username handles, step 5 of (#resolve-user) prevents it, in one of two ways:

- If the unique user identifier is on the origin of the authorized issuer, the issuer is the server that hosts the account, and a server that issues an HVT for one of its accounts has authenticated that account's user, and checked that the user controls the handle ((#issuance)). A domain can at most give its own handles to accounts on that server, which the server can refuse.
- Otherwise, the back-link check of step 5 of (#resolve-user) requires the server that hosts the account to agree that it has the handle. Bob's account does not claim `x@evil.example`, so resolution fails.

## Domain Control Is Handle Control

Whoever controls the domain of a username handle controls its WebFinger responses, and therefore which account each username handle refers to, within the limits of step 5 of (#resolve-user): a handle can name an account on another server only if that account agrees ((#same-origin)). When a domain changes hands, its username handles change hands too.

## Handle Reassignment

As in [@!HVP], verifiers SHOULD identify accounts by the unique user identifier in the `sub` claim rather than by the `handle` claim. The unique user identifier of a username handle is the URL of the account on its server, which survives changes of handle that keep the account on the same server, but changes when the account moves to another server.

# IANA Considerations

This document has no IANA actions.

# Design Rationale

## Why a Separate Document?

Domain handles and username handles are resolved differently, because each already has a resolution mechanism that is deployed: domain handles are mapped to a DID through DNS or a well-known URL, as in the AT Protocol, and username handles are mapped to an account through WebFinger, as in ActivityPub implementations. The two mechanisms are at different stages of maturity and involve different communities, so they are specified separately, while sharing issuance and verification, which do not depend on how the handle was resolved.

## Why WebFinger?

Every ActivityPub server that supports username handles already implements WebFinger, so supporting username handles requires updating server software, not asking each user to publish DNS records. WebFinger maps the handle to the URL of the account, which [@!URL-HANDLES] already knows how to resolve to a unique user identifier and an explicitly authorized issuer, so issuance and verification are the same for every form of handle.

This document could instead treat the handle's domain as the issuer, as [@?EVP] treats the email domain, and skip WebFinger. But in ActivityPub the server that hosts an account is not always at the handle's domain: in a split domain configuration, the handles are at `example.com` and the server at `social.example.com`, and a bridging service can host actors for handles at many domains ((#examples)). WebFinger is what tells the two apart, per user, at the cost of one request.

## Why Build on URL Handles?

A username handle is an alias of an account that already has a URL, and a server that hosts accounts at URLs, such as an ActivityPub server, describes each account in the identity document at its URL. Naming the issuer in that document, rather than in the WebFinger response, means that the issuer is named in one place, which serves the account whether it is reached through its username handle or through its URL, and that the issuer is named by the server that hosts the account rather than by the handle's domain ((#same-origin)). It also keeps this document independent of ActivityPub: it relies only on WebFinger and on [@!URL-HANDLES]. The cost is one more request, to fetch the identity document.

## Why the Same-Origin Shortcut? {#why-same-origin}

A username handle's WebFinger response is controlled by the handle's domain, which is not necessarily the server that hosts the account it names ((#same-origin)). Resolution checks the account back with a WebFinger request for its unique user identifier (step 5 of (#resolve-user)), at the cost of one request. ActivityPub implementations perform an equivalent check by fetching the actor and reading its `webfinger` property or performing a reverse WebFinger lookup ([@?MASTODON-WEBFINGER], [@?FEP-2C59]), which is specific to ActivityPub.

In the common case, the issuer is the server that hosts the account, and the unique user identifier is on its origin. The issuer then authenticates the account's user itself, which gives the same protection for the purposes of HVP, so the back-link request is skipped. This covers split domains and bridges ((#examples)).

The back-link request is still needed for issuers on another origin (for example, Threads ([@?THREADS]) gives its users handles such as `@zuck@threads.net`, whose actors are at `https://threads.net/ap/users/...`, while its website, where users sign in, has moved to `https://www.threads.com`; ActivityPub accounts cannot change their URLs without breaking federation, so the natural issuer is on a different site from the accounts it vouches for).

> Open Issue: At the time of writing, Threads does not answer WebFinger requests for the URLs of its accounts, which the back-link request requires when the issuer is on another origin, and the reference cited for its move to `threads.com` is its home page rather than an announcement. How Threads, and other services whose accounts are on a different site from where their users sign in, would deploy username handles needs to be investigated, and the reference replaced.

## Why Let Domain Handles Name Other Handles?

A domain handle of an ActivityPub account needs a stable identifier for the account, a document that claims the handle back, and a place to name the issuer. The identity document of the account provides all three, so the domain handle can resolve to it without the account adopting any new identifier, such as a DID ((#domain-handles)).

A single `me=` key names either a username handle or a URL handle, rather than a key for each, because the value already says which it is, and because both resolve to the same thing, an identity document. Users who know their username handle, as most ActivityPub users do, can name it, and users who know the URL of their account, such as Solid users, or whose server has no username handles, can name that.

# Implementation Status

*Note: This section is to be removed before publishing as an RFC.*

There are no implementations of this document yet.

# Document History

*Note: This section is to be removed before publishing as an RFC.*

- draft-goto-username-handle-verification-00
  - Initial draft, covering username handles, previously part of [@!HVP].

{backmatter}

# Examples {#examples}

This appendix shows the resolution of handles. The username handle examples are real handles at the time of writing. None of their accounts names an issuer yet, so each shows what would be added to its identity document to opt in. The domain handle examples are hypothetical. The values will change over time.

## Domain Handle That Names a Username Handle

```
Handle:        @alice.example
DNS TXT _handle.alice.example
  -> "me=@alice@social.example"
Names:         @alice@social.example
GET https://social.example/.well-known/webfinger
      ?resource=acct%3Aalice%40social.example
  subject: acct:alice@social.example            (subject ok)
  self:    https://social.example/users/alice
GET https://social.example/users/alice          (URL handle)
  id:                 https://social.example/users/alice
  HandleVerification: https://social.example   (service)
  alsoKnownAs:        ["at://alice.example"]    (back-link ok)
Identifier:    https://social.example/users/alice
Issuer:        https://social.example           (same origin)
```

## Domain Handle That Names a URL Handle

```
Handle:        @alice.example
DNS TXT _handle.alice.example
  -> "me=https://social.example/users/alice"
Names:         https://social.example/users/alice
GET https://social.example/users/alice          (URL handle)
  id:                 https://social.example/users/alice
  HandleVerification: https://social.example   (service)
  alsoKnownAs:        ["at://alice.example"]    (back-link ok)
Identifier:    https://social.example/users/alice
Issuer:        https://social.example
```

## Username Handle on a Split Domain

The handle is at the owner's website, and the ActivityPub server is on a subdomain.

```
Handle:        @simon@simonwillison.net
GET https://simonwillison.net/.well-known/webfinger
      ?resource=acct%3Asimon%40simonwillison.net
  subject: acct:simon@simonwillison.net         (subject ok)
  self:    https://fedi.simonwillison.net/users/simon
GET https://fedi.simonwillison.net/users/simon  (URL handle)
  id:      https://fedi.simonwillison.net/users/simon
Identifier:    https://fedi.simonwillison.net/users/simon
To opt in, add to the actor:
  "service": [{ "id": "#handle_verification",
                "type": "HandleVerification",
                "serviceEndpoint": "https://fedi.simonwillison.net" }]
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
GET https://fed.brid.gy/snarfed.org             (URL handle)
  id:      https://fed.brid.gy/snarfed.org
Identifier:    https://fed.brid.gy/snarfed.org
To opt in, add to the actor:
  "service": [{ "id": "#handle_verification",
                "type": "HandleVerification",
                "serviceEndpoint": "https://fed.brid.gy" }]
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
GET https://threads.net/ap/users/17841401746480004/  (URL handle)
Identifier:    https://threads.net/ap/users/17841401746480004/
To opt in, add to the actor:
  "service": [{ "id": "#handle_verification",
                "type": "HandleVerification",
                "serviceEndpoint": "https://www.threads.com" }]
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

This document builds on the Handle Verification Protocol and URL handles, on the Handles Task Force proposal by Anuj Ahooja and Emelia Smith, on FEP-c390 by silverpill, and on the WebFinger conventions of ActivityPub implementations.
