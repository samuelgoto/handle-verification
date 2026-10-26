%%%
title = "URL Handles"
abbrev = "URL Handles"
ipr = "trust200902"
area = "Security"
workgroup = "TBD"
keyword = ["handle", "verification", "identity", "authentication", "url", "webid", "actor"]

[seriesInfo]
status = "standard"
name = "Internet-Draft"
value = "draft-goto-url-handle-verification-latest"
stream = "IETF"

date = 2026-10-24T00:00:00Z

[[author]]
initials = "S."
surname = "Goto"
fullname = "Sam Goto"
organization = "Google"
  [author.address]
  email = "goto@google.com"

[[author]]
fullname = "@bumblefudge.com"

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

<reference anchor="USERNAME-HANDLES" target="https://samuelgoto.github.io/handle-verification/draft-goto-username-handle-verification.html">
  <front>
    <title>Username Handles</title>
    <author initials="S." surname="Goto" fullname="Sam Goto">
      <organization>Google</organization>
    </author>
    <date year="2026"/>
  </front>
  <seriesInfo name="Internet-Draft" value="draft-goto-username-handle-verification-latest"/>
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

<reference anchor="WEBID" target="https://www.w3.org/2005/Incubator/webid/spec/identity/">
  <front>
    <title>WebID 1.0</title>
    <author>
      <organization>W3C WebID Incubator Group</organization>
    </author>
    <date year="2014" month="March"/>
  </front>
</reference>

<reference anchor="SOLID-WEBID-PROFILE" target="https://solid.github.io/webid-profile/">
  <front>
    <title>Solid WebID Profile</title>
    <author>
      <organization>W3C Solid Community Group</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

<reference anchor="SOLID-PROTOCOL" target="https://solidproject.org/TR/protocol">
  <front>
    <title>Solid Protocol</title>
    <author>
      <organization>W3C Solid Community Group</organization>
    </author>
    <date year="2026"/>
  </front>
</reference>

<reference anchor="SOLID-OIDC" target="https://solidproject.org/TR/oidc">
  <front>
    <title>Solid-OIDC</title>
    <author>
      <organization>W3C Solid Community Group</organization>
    </author>
    <date year="2026"/>
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
  <refcontent>IndieWeb Living Standard</refcontent>
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

<reference anchor="LWS-AUTHN-OPENID" target="https://w3c.github.io/lws-protocol/lws10-authn-openid/">
  <front>
    <title>Linked Web Storage: OpenID Connect Authentication Suite</title>
    <author>
      <organization>W3C Linked Web Storage Working Group</organization>
    </author>
    <date year="2026"/>
  </front>
  <refcontent>Editor's Draft</refcontent>
</reference>

<reference anchor="JSON-LD11" target="https://www.w3.org/TR/json-ld11/">
  <front>
    <title>JSON-LD 1.1</title>
    <author>
      <organization>W3C</organization>
    </author>
    <date year="2020" month="July"/>
  </front>
  <refcontent>W3C Recommendation</refcontent>
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

.# Abstract

This document defines *URL handles*, a handle type of the Handle Verification Protocol ([@!HVP]), for users who are identified by an `https` URL, such as a Solid WebID, an ActivityPub actor, or the URL of an IndieAuth personal website. A URL handle is resolved by fetching it as a controlled identifier document ([@!CID-1.0]), which gives the canonical identifier of the account and names the issuer that the user has authorized to vouch for it with the `HandleVerification` service of HVP, the same service that domain handles use, or by fetching it as an HTML page that names the issuer with a `handle-verification` link. The browser then obtains a Handle Verification Token (HVT) from that issuer, and presents it to a verifier, as for any handle type of HVP. The resolution is not specific to any ecosystem.

.# Discussion Venues

*Note: This section is to be removed before publishing as an RFC.*

Source for this draft and an issue tracker can be found at https://github.com/samuelgoto/handle-verification.

{mainmatter}

# Introduction

The Handle Verification Protocol ([@!HVP]) lets a browser obtain a signed Handle Verification Token (HVT) attesting that the user controls a handle, and present it to a verifier, without the user typing the handle and without revealing the verifier to the issuer. HVP is extensible to several handle types, and defines one, domain handles, such as `@alice.example`. This document defines another handle type, URL handles, and [@?USERNAME-HANDLES] builds on this document to define username handles, such as `@alice@social.example`, by mapping them to the URL of their account with WebFinger.

Several ecosystems identify users with an `https` URL instead:

- Solid identifies users with a WebID ([@?WEBID]), such as Tim Berners-Lee's `https://timbl.solidcommunity.net/profile/card#me`, whose profile document describes the user ([@?SOLID-WEBID-PROFILE]).
- ActivityPub ([@?ACTIVITYPUB]) identifies actors with the URL of their actor object, such as `https://bumblefudge.com/`, which serves Bumblefudge's actor. Handles of the form `@alice@social.example` are a convention of some implementations, and are covered by [@?USERNAME-HANDLES]; the actor URL is the identifier that ActivityPub itself defines.
- IndieAuth ([@?INDIEAUTH]) identifies users with the URL of their personal website, such as Aaron Parecki's `https://aaronparecki.com/`.

In each, fetching the URL returns a document about the user. Controlled Identifiers ([@!CID-1.0]) defines a JSON format for such documents, which generalizes DID documents to any URL, and which the Linked Web Storage protocol, the successor of Solid, uses to identify its users ([@?LWS-AUTHN-OPENID]). This document calls such a URL a *URL handle*, and defines URL handles as a handle type of HVP, whose resolution fetches the URL as a controlled identifier document, checks that its `id` is the URL, and reads the issuer that the user has authorized from its `HandleVerification` service ([@!HVP]), the same service that the DID documents of domain handles use. A website that serves HTML, such as an IndieAuth website, can name its issuer with a `handle-verification` link instead. Everything after resolution, that is, the issuer metadata, the HVT request, the HVT, its key binding, and the verification of the HVT+KB, is that of HVP.

The resolution does not depend on the ecosystem: it requests a controlled identifier document, or generic JSON-LD, and reads it as plain JSON, with the same algorithm, whether it is served by a Linked Web Storage server, an ActivityPub server, or any other server, and reads the same link from any HTML page.

# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 [@!RFC2119] [@!RFC8174] when, and only when, they appear in all capitals, as shown here.

This document uses the terms issuer, issuer identifier, authorized issuer, Handle Verification Token (HVT), HVT+KB, and verifier as defined in [@!HVP], and the following terms:

URL handle:
: A handle that is an `https` URL, such as `https://alice.solidcommunity.net/profile/card` or `https://social.example/users/alice`. Unlike domain handles and username handles, it is displayed as is, without a leading `@`. See (#url-handles).

Controlled identifier document:
: As in [@!HVP], a JSON document that describes the subject of an identifier ([@!CID-1.0]).

Identity document:
: The document that is served at a URL handle, which describes the user: a controlled identifier document, or an HTML page. See (#resolution).

Unique user identifier:
: As in [@!HVP], an identifier of the user's account that resolution produces, and that the HVT carries in its `sub` claim. For a URL handle, it is the canonical URL of the account, as named by its identity document. Resolution replaces the URL handle with it ((#why-canonical)).

# Protocol Flow {#protocol-flow}

The protocol flow is the flow of [@!HVP], with the following particulars:

- The handle is a URL handle ((#url-handles)).
- The browser and the verifier resolve the handle as described in (#resolution), by fetching it, rather than through a DID.
- The `handle` and `sub` of the HVT request and of the HVT are both the unique user identifier ((#issuance)).

```
Step                       Verifier     Browser              Issuer
                               |            |                    |
Handle Discovery               |      [obtain URL from user]     |
                               |            |                    |
Session Binding                |--- nonce ->|                    |
                               |            |                    |
Handle Resolution              |   [GET URL: unique user         |
                               |    identifier, issuer]          |
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
HVT+KB Verification [GET URL;               |                    |
                     verify HVT+KB]         |                    |
```

# URL Handles {#url-handles}

## Syntax {#url-handle-syntax}

A URL handle is an absolute URL ([@!WHATWG.URL]) that satisfies the following rules:

- Its scheme is `https`.
- It has no username or password.
- Its host is a domain that satisfies the domain handle syntax of [@!HVP], and does not end in one of the top-level domains that [@!HVP] excludes from resolution. As a consequence, IP addresses are not URL handles.
- It has no fragment.

A URL handle can have a path and a query. Because the `id` of a controlled identifier document is the URL from which it is fetched ([@!CID-1.0]), a URL handle identifies the user by the URL of their identity document, rather than by a fragment within it: for example, the URL handle of a Solid user whose WebID ([@?WEBID]) is `https://alice.solidcommunity.net/profile/card#me` is `https://alice.solidcommunity.net/profile/card`.

## Normalization {#normalization}

The *normalized* form of a URL handle is the result of parsing it and serializing it with the URL parser and serializer of [@!WHATWG.URL], which, among other things, converts the scheme and host to lowercase, removes the default port, and adds a `/` path to a URL that has none. Every URL handle and unique user identifier in this protocol is in normalized form, and every comparison of them is a byte-for-byte comparison of normalized forms.

## Parsing User Input {#parsing}

To parse a URL handle that a user typed:

1. Strip leading and trailing ASCII whitespace.
2. If the input does not start with `https://`, compared ASCII case-insensitively, it is not a URL handle; it can still be a domain handle, parsed as described in [@!HVP], or a username handle, parsed as described in [@?USERNAME-HANDLES].
3. Remove the fragment, if any, so that a user can type a WebID, normalize the input ((#normalization)), and check that it satisfies (#url-handle-syntax).

If any step fails, the input is not a URL handle.

| Input | Handle |
|-------|--------|
| `https://Social.Example/users/alice` | `https://social.example/users/alice` |
| `https://alice.example` | `https://alice.example/` |
| `https://alice.solidcommunity.net/profile/card#me` | `https://alice.solidcommunity.net/profile/card` |
| `alice.example`, `@alice.example` | not a URL handle (domain handle, see [@!HVP]) |
| `http://alice.example/`, `https://192.0.2.1/` | not a handle |

A URL handle is always typed with its scheme, which distinguishes it from a domain handle: `alice.example` is a domain handle, and `https://alice.example/` is a URL handle. The two are resolved differently, and need not refer to the same account.

# Handle Resolution {#resolution}

*Resolution* takes a normalized URL handle and produces the user's unique user identifier and the authorized issuer for the handle. Both the browser and the verifier perform resolution, for the same reasons as in [@!HVP], and the rules that [@!HVP] applies to every resolution step (on HTTP requests, redirects, limits, and caching) apply here too.

Given a normalized URL handle *handle*:

1. **Fetch.** `GET` *handle* with the following `Accept` header ([@!RFC9110]). The response MUST have a 2xx status code. The *final URL* is the URL of the response, after any redirects.

    ```
    Accept: application/cid,
            application/ld+json;q=0.9,
            text/html;q=0.5
    ```

2. **Parse.** If the media type of the response is `application/cid`, `application/json`, `application/ld+json`, or another media type with the `+json` structured syntax suffix ([@!RFC6839]), such as `application/activity+json`, read it as a controlled identifier document, as described in [@!HVP]; if it is not one, fail. If the media type is `text/html`, parse it as HTML ([@!WHATWG.HTML]). Otherwise fail.

3. **Unique user identifier.** For a controlled identifier document, the unique user identifier is its `id`, normalized ((#normalization)); if it does not satisfy (#url-handle-syntax), fail. For an HTML document, it is the final URL.

4. **Identity document.** If the unique user identifier is identical to the final URL, the response of step 1 is the identity document, whose `id` is the URL from which it was fetched, as [@!CID-1.0] requires. Otherwise, the document names an account at another URL: `GET` the unique user identifier, as in step 1, and parse it, as in step 2. The final URL of this response MUST be same origin with the unique user identifier, the response MUST be a controlled identifier document, and its `id` MUST be identical to the unique user identifier. Otherwise fail. This response is the identity document. This step is not repeated: an identity document that names yet another account fails.

5. **Issuer.** Collect the issuer identifiers that the identity document names: from its `Link` header fields ([@!RFC8288]) whose relation type is `handle-verification` ((#handle-verification-link)); for a controlled identifier document, from its `HandleVerification` service ([@!HVP]); and for an HTML document, from its `<link>` elements whose relation type is `handle-verification` ((#handle-verification-link)). If there are none, or they are not all identical, or they are not an issuer identifier ([@!HVP]), fail. Otherwise, it is the authorized issuer.

If any step fails, resolution fails.

Resolution replaces the URL handle with the unique user identifier: from this point on, the unique user identifier is the handle, in the HVT request, in the HVT, and in what the browser displays. In most cases, the two are identical; they differ when the URL that the user typed serves a document about an account at another URL, or redirects to it. See (#why-canonical).

A document is read as a controlled identifier document if it is a JSON object with an `id` member, whatever its media type: an ActivityPub actor, for example, is one, and can name its issuer by adding the `HandleVerification` service to its `service` member, which [@!CID-1.0] defines. The `service` member is unrelated to the `Service` actor type of ActivityStreams, and to the `endpoints` member of ActivityPub ([@?ACTIVITYPUB]). For example, an ActivityPub actor resolves as follows:

```
GET https://social.example/users/alice
Accept: application/cid, application/ld+json;q=0.9, ...
  -> Content-Type: application/activity+json
     { "@context": ["https://www.w3.org/ns/activitystreams",
                    "https://www.w3.org/ns/cid/v1"],
       "id": "https://social.example/users/alice",
       "type": "Person",
       "service": [{ "id": "#handle_verification",
                     "type": "HandleVerification",
                     "serviceEndpoint": "https://social.example" }],
       ... }
User identifier: https://social.example/users/alice
Issuer:          https://social.example
```

> Open Issue: Some ActivityPub servers serve actors only for the media types of ActivityPub ([@?ACTIVITYPUB]), and not for `application/ld+json` without a profile, so that resolution does not reach their actors. Such servers would need to serve their actors for `application/cid` or `application/ld+json`.

> Open Issue: Some ActivityPub servers, such as Mastodon servers with "authorized fetch" enabled, serve actors only to requests that are signed with the key of another server's actor, and respond to the unsigned requests of resolution with a 401 (Unauthorized) response, so that resolution of their actors fails. Resolving parties cannot sign their requests, because they have no actor, and because a signature would identify them. Such servers would need to serve their actors, or at least the `handle-verification` link of their responses ((#handle-verification-link)), to unsigned requests. This needs to be discussed with Mastodon as an implementation detail.

> Open Issue: Solid servers serve JSON-LD in expanded form, which has no `id` member, and so is not read as a controlled identifier document. Such servers would need to serve the profile documents of their users as controlled identifier documents, as the Linked Web Storage protocol does ([@?LWS-AUTHN-OPENID]).

## The handle-verification Link {#handle-verification-link}

An identity document can also name the issuer authorized to vouch for its handle with a link whose relation type is `handle-verification` ((#iana)), whose target is an issuer identifier, and whose context is the identity document: in a `Link` header field ([@!RFC8288]) of the response, with any media type, or, in an HTML document, in a `<link>` element ([@!WHATWG.HTML]), whose `href` is resolved against the document's base URL:

```http
HTTP/1.1 200 OK
Content-Type: text/html
Link: <https://issuer.example>; rel="handle-verification"

<!doctype html>
<link rel="handle-verification" href="https://issuer.example">
```

This is how IndieAuth websites already name their authorization endpoints ([@?INDIEAUTH]), and it lets a website that cannot vary its responses by media type, such as a static website, use its URL as a URL handle by serving HTML.

# Issuance and Verification {#issuance}

Issuance and verification are those of [@!HVP], for which a URL handle is a handle of the URL handle type, with the syntax and normalization of (#url-handles) and the resolution of (#resolution). Its unique user identifier is an `https` URL.

Because resolution replaces a URL handle with its unique user identifier, the `handle` and `sub` members of the HVT request, and the `handle` and `sub` claims of the HVT, are all the unique user identifier. An issuer MUST return an `invalid_request` error for an HVT request for a URL handle whose `handle` and `sub` differ, and a browser or verifier MUST reject an HVT for a URL handle whose `handle` and `sub` claims differ.

For example, the payload of an HVT for an ActivityPub actor is:

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
  "handle": "https://social.example/users/alice",
  "sub": "https://social.example/users/alice"
}
```

As for every handle type, a verifier recognizes a URL handle by the form of its `handle` claim ([@!HVP]).

# Privacy Considerations

The privacy considerations of [@!HVP] apply. In particular, the issuer does not learn which verifier the user signs in to, and handles and unique user identifiers are public identifiers.

Resolution of a URL handle is specific to one user: it fetches the user's identity document. When the browser resolves a URL handle, the server that hosts it, and, when step 4 of (#resolution) fetches another URL, the server that hosts that URL, can observe that the user's device is resolving that handle, but not which verifier is involved, because the requests carry no credentials or referrer. When the verifier resolves it, these servers see the verifier's network address, as described in [@!HVP]. The server that hosts an identity document is usually the user's issuer, which can therefore often correlate the HVTs it issues with the resolutions that follow. The mitigations described in [@!HVP], such as caching and resolving through a shared intermediary, apply.

Identity documents can contain more information about the user than their handle, such as their name, picture, or contacts. Resolving parties read only the properties and links that this document defines, but the user's choice to use a URL handle shares the whole identity document with the verifier.

# Security Considerations

The security considerations of [@!HVP] apply, with the following additions.

## Documents That Name Other Accounts {#other-accounts}

An identity document is controlled by the server that hosts its URL, and names both the unique user identifier and the issuer. A document at one URL could name another user's account as its `id`, and an issuer of its own choosing:

```
https://evil.example/
  -> id:                 https://social.example/users/bob
     HandleVerification: https://evil.example
```

Step 4 of (#resolution) prevents this: when the `id` of a document is not its own URL, resolution fetches the `id`, and reads the issuer from the document that the server that hosts the account serves, rather than from the document that named it. Bob's actor names his own issuer, or none, so the issuer of `evil.example` is never authorized for Bob's account. The URL that the user typed is replaced by Bob's account ((#why-canonical)), and so `evil.example` cannot give Bob a handle that Bob did not agree to.

For the same reason, step 4 requires the final URL of the second fetch to be same origin with the account, so that a server cannot redirect the request for the account to a document of its own.

## Host Control Is Handle Control

Whoever controls the server that hosts a URL handle controls its identity document, and therefore which issuer it names. On a server that hosts many users, such as a Solid server or an ActivityPub server, that is the server's operator, who can also name an issuer for any of its accounts. This is the same trust that users of such servers already place in them. A server that lets users publish documents of their own at URLs on its origin, or lets them control the `<head>` of HTML pages, lets them name issuers for those URLs.

## Handle Reassignment

As in [@!HVP], verifiers SHOULD identify accounts by the unique user identifier in the `sub` claim. For a URL handle, the unique user identifier is the URL of the account, which changes when the account moves to another server, and which a server can reassign to a new account after deleting the previous one. Servers SHOULD NOT reassign the URLs of deleted accounts.

## Content Negotiation

A server can serve different documents at the same URL depending on the `Accept` header. Resolving parties send the same `Accept` header ((#resolution)), so that the browser and the verifier read the same document, and a server that serves an identity document only for some media types, and HTML for others, names its issuer in each.

# IANA Considerations {#iana}

## Link Relation Types

This document registers the following link relation type in the "Link Relation Types" registry ([@!RFC8288]):

- Relation Name: `handle-verification`
- Description: Refers to the issuer that the context authorizes to issue Handle Verification Tokens for its handle.
- Reference: (#handle-verification-link) of this document

# Design Rationale

## Why the HandleVerification Service? {#why-new-term}

A Solid WebID profile names the OpenID Connect issuers that can authenticate the user with `solid:oidcIssuer` ([@?SOLID-OIDC]), and a Linked Web Storage controlled identifier document names them with a service of type `https://www.w3.org/ns/lws#OpenIdProvider` ([@?LWS-AUTHN-OPENID]). But an HVT is not an OpenID Connect token: OpenID Connect is a two-party protocol, in which the issuer issues tokens to the relying party, and learns who it is, while HVP is a three-party protocol, in which the browser obtains the token and hides the verifier from the issuer. A user who authorized an issuer to sign them in with OpenID Connect has not necessarily authorized it to make statements that the browser presents to verifiers that the issuer does not know. A profile can also list several OpenID Connect issuers, while a handle has a single authorized issuer in HVP. The `HandleVerification` service makes the user's opt-in explicit, and is the same service, defined once by [@!HVP], that the DID documents of domain handles use.

## Why Content Negotiation?

ActivityPub servers serve actors through content negotiation ([@?ACTIVITYPUB]), and Solid servers serve every RDF document as Turtle or JSON-LD through content negotiation ([@?SOLID-PROTOCOL]), so that the same URL can serve both a page for people and a document for machines. Requiring them to serve identity documents at another URL, such as a well-known URL, would require changes to every server, and would not fit identifiers that are not at the root of a domain. Websites that cannot vary their responses by media type can name their issuer in HTML instead ((#handle-verification-link)).

The `Accept` header requests a controlled identifier document first, and generic JSON-LD next, which ActivityPub servers such as Mastodon already serve their actors for, so that it does not name the media types of any ecosystem. It does not request `application/json`, for which some servers serve HTML.

## Why Replace the Handle With the Canonical Identifier? {#why-canonical}

A URL that the user types can serve a document about an account at another URL, or redirect to it, for example when a personal website serves the actor of an account whose identifier is at a longer URL on the same server. Resolution then has two URLs: the one that the user typed, and the one that identifies the account. Verifying the typed URL as a handle of the account would require the account to agree to it, with a back-link from the account's identity document to the typed URL. This document instead replaces the typed URL with the account's identifier, which needs no back-link, because the server that hosts the account names the issuer itself. Typed URLs that the account agrees to could be supported later.

> Open Issue: Whether to let an identity document keep the URL that the user typed as its handle, when the document lists it, for example in its `alsoKnownAs` or `url` property.

## Why Controlled Identifier Documents?

A URL handle needs, from the document at its URL, a canonical identifier for the account and a place to name the issuer. Controlled identifier documents ([@!CID-1.0]) provide both, with the `id` member and its canonical URL rule, and with services, in a JSON format that is not specific to any ecosystem, that generalizes the DID documents that domain handles already use, and that the Linked Web Storage protocol uses to identify its users ([@?LWS-AUTHN-OPENID]). Using them lets URL handles and domain handles name their issuer with the same `HandleVerification` service ([@!HVP]).

Resolving parties read controlled identifier documents as plain JSON, without JSON-LD processing ([@?JSON-LD11]), which would fetch remote contexts, adding requests, latency, and attack surface to resolution, and which is a large dependency for a browser and for verifiers. Controlled identifier documents can be processed as plain JSON ([@!CID-1.0]), and so can the actors of ActivityPub ([@?ACTIVITYPUB]).

# Implementation Status

*Note: This section is to be removed before publishing as an RFC.*

There are no implementations of this document yet.

# Document History

*Note: This section is to be removed before publishing as an RFC.*

- draft-goto-url-handle-verification-00
  - Initial draft.

{backmatter}

# Examples {#examples}

This appendix shows the resolution of URL handles. The identity documents of the ActivityPub and IndieAuth examples are real at the time of writing, and are abbreviated; the Solid example shows what a Solid server would serve as a controlled identifier document. None of them names an issuer yet, so each shows what would be added to opt in. The values will change over time.

## Solid WebID

```
Input:         https://timbl.solidcommunity.net/profile/card#me
Handle:        https://timbl.solidcommunity.net/profile/card
GET https://timbl.solidcommunity.net/profile/card
  -> Content-Type: application/cid
     { "id": "https://timbl.solidcommunity.net/profile/card",
       "service": [{ "id": "#handle_verification",
                     "type": "HandleVerification",
                     "serviceEndpoint":
                       "https://solidcommunity.net" }] }
Identifier:    https://timbl.solidcommunity.net/profile/card
Issuer:        https://solidcommunity.net
```

## ActivityPub Actor

```
Handle:        https://w3c.social/users/goto
GET https://w3c.social/users/goto
  -> Content-Type: application/activity+json
     { "id": "https://w3c.social/users/goto", "type": "Person",
       "webfinger": "goto@w3c.social", ... }
Identifier:    https://w3c.social/users/goto
To opt in, add to the actor:
  "service": [{ "id": "#handle_verification",
                "type": "HandleVerification",
                "serviceEndpoint": "https://w3c.social" }]
Issuer:        https://w3c.social
```

## Website That Serves an Actor at Another URL

The website serves the actor of an account whose identifier is at another URL on the same origin. Resolution fetches the identifier, and replaces the handle with it.

```
Input:         https://bumblefudge.com
Handle:        https://bumblefudge.com/
GET https://bumblefudge.com/
  -> Content-Type: application/activity+json
     { "id": "https://bumblefudge.com/did:scid:vh:1:QmWu.../actor",
       "url": "https://bumblefudge.com/", ... }
GET https://bumblefudge.com/did:scid:vh:1:QmWu.../actor
  -> { "id": "https://bumblefudge.com/did:scid:vh:1:QmWu.../actor",
       ... }                                     (id ok)
Identifier:    https://bumblefudge.com/did:scid:vh:1:QmWu.../actor
To opt in, add to the actor:
  "service": [{ "id": "#handle_verification",
                "type": "HandleVerification",
                "serviceEndpoint": "https://bumblefudge.com" }]
Issuer:        https://bumblefudge.com
```

## IndieAuth Website

The website serves HTML, and names its issuer the way it names its IndieAuth endpoints.

```
Handle:        https://aaronparecki.com/
GET https://aaronparecki.com/
  -> Content-Type: text/html
     Link: <https://aaronparecki.com/auth>;
             rel="authorization_endpoint"
Identifier:    https://aaronparecki.com/
To opt in, add a header or an element:
  Link: <https://aaronparecki.com>; rel="handle-verification"
  <link rel="handle-verification" href="https://aaronparecki.com">
Issuer:        https://aaronparecki.com
```

# Acknowledgments

This document builds on the Handle Verification Protocol, on Controlled Identifiers, on the WebID, Solid WebID Profile, and Solid-OIDC specifications of the Solid community, on the Linked Web Storage protocol, on ActivityPub, and on IndieAuth. Thanks to Elf Pavlik for pointing to Controlled Identifiers.
