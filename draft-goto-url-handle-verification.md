%%%
title = "URL Handle Verification Protocol"
abbrev = "URL-HVP"
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

This document defines the URL Handle Verification Protocol (URL-HVP), which extends the Handle Verification Protocol ([@!HVP]) to *URL handles*: users who are identified by an `https` URL, such as a Solid WebID, an ActivityPub actor, or the URL of an IndieAuth personal website. A URL handle is resolved by fetching it, with content negotiation, and reading the canonical identifier of the account and the issuer that the user has authorized to vouch for it, named by a `handleIssuer` property of the document or by a `handle-issuer` link. The browser then obtains a Handle Verification Token (HVT) from that issuer, and presents it to a verifier, exactly as for a domain handle in HVP. The resolution is not specific to any ecosystem.

.# Discussion Venues

*Note: This section is to be removed before publishing as an RFC.*

Source for this draft and an issue tracker can be found at https://github.com/samuelgoto/handle-verification.

{mainmatter}

# Introduction

The Handle Verification Protocol ([@!HVP]) lets a browser obtain a signed Handle Verification Token (HVT) attesting that the user controls a handle, and present it to a verifier, without the user typing the handle and without revealing the verifier to the issuer. HVP covers domain handles, such as `@alice.example`. This document extends it to URL handles, and the Username Handle Verification Protocol ([@?UHVP]) builds on this document to cover username handles, such as `@alice@social.example`, by mapping them to the URL of their account with WebFinger.

Several ecosystems identify users with an `https` URL instead:

- Solid identifies users with a WebID ([@?WEBID]), such as Tim Berners-Lee's `https://timbl.solidcommunity.net/profile/card#me`, whose profile document describes the user ([@?SOLID-WEBID-PROFILE]).
- ActivityPub ([@?ACTIVITYPUB]) identifies actors with the URL of their actor object, such as `https://bumblefudge.com/`, which serves Bumblefudge's actor. Handles of the form `@alice@social.example` are a convention of some implementations, and are covered by [@?UHVP]; the actor URL is the identifier that ActivityPub itself defines.
- IndieAuth ([@?INDIEAUTH]) identifies users with the URL of their personal website, such as Aaron Parecki's `https://aaronparecki.com/`.

In each, fetching the URL returns a document about the user: Solid and ActivityPub servers serve it as JSON-LD ([@?JSON-LD11]) through content negotiation ([@!RFC9110]), and an IndieAuth website serves HTML with `Link` headers and `<link>` elements. This document calls such a URL a *URL handle*, and extends HVP so that it can be verified. It replaces HVP's resolution with one that fetches the URL, finds the canonical identifier of the account in the document, and reads the issuer that the user has authorized from a new `handleIssuer` property or a `handle-issuer` link. Everything after resolution, that is, the issuer metadata, the HVT request, the HVT, its key binding, and the verification of the HVT+KB, is that of HVP, except that the HVT request carries only the handle, which is also the unique user identifier.

The resolution does not depend on the ecosystem: it reads the same property, with the same algorithm, from a Solid profile, an ActivityPub actor, or any other JSON-LD document, and the same link from any HTML page.

# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 [@!RFC2119] [@!RFC8174] when, and only when, they appear in all capitals, as shown here.

This document uses the terms issuer, issuer identifier, authorized issuer, Handle Verification Token (HVT), HVT+KB, and verifier as defined in [@!HVP], and the following terms:

URL handle:
: A handle that is an `https` URL, such as `https://alice.solidcommunity.net/profile/card#me` or `https://social.example/users/alice`. Unlike domain handles and username handles, it is displayed as is, without a leading `@`. See (#url-handles).

Identity document:
: The document that is served at a URL handle, which describes the user. See (#resolution).

Unique user identifier:
: As in [@!HVP], an identifier of the user's account that resolution produces, and that the HVT carries in its `sub` claim. For a URL handle, it is the canonical URL of the account, as named by its identity document. Resolution replaces the URL handle with it ((#why-canonical)).

# Protocol Flow {#protocol-flow}

The protocol flow is the flow of [@!HVP], with the following differences:

- The handle is a URL handle ((#url-handles)).
- The browser and the verifier resolve the handle as described in (#resolution), by fetching it, rather than through a DID.
- The HVT request carries only the handle, which is also the unique user identifier, and the `handle` and `sub` claims of the HVT are both that URL ((#issuance)).

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
                               |            |   (handle)         |
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

A URL handle can have a path, a query, and a fragment. The fragment is part of the handle, as in a WebID such as `https://alice.solidcommunity.net/profile/card#me`, which identifies a person rather than the document that describes them ([@?WEBID]), but is not sent when the handle is fetched.

## Normalization {#normalization}

The *normalized* form of a URL handle is the result of parsing it and serializing it with the URL parser and serializer of [@!WHATWG.URL], which, among other things, converts the scheme and host to lowercase, removes the default port, and adds a `/` path to a URL that has none. Every URL handle and unique user identifier in this protocol is in normalized form, and every comparison of them is a byte-for-byte comparison of normalized forms.

## Parsing User Input {#parsing}

To parse a URL handle that a user typed:

1. Strip leading and trailing ASCII whitespace.
2. If the input does not start with `https://`, compared ASCII case-insensitively, it is not a URL handle; it can still be a domain handle, parsed as described in [@!HVP], or a username handle, parsed as described in [@?UHVP].
3. Normalize the input ((#normalization)), and check that it satisfies (#url-handle-syntax).

If any step fails, the input is not a URL handle.

| Input | Handle |
|-------|--------|
| `https://Social.Example/users/alice` | `https://social.example/users/alice` |
| `https://alice.example` | `https://alice.example/` |
| `alice.example`, `@alice.example` | not a URL handle (domain handle, see [@!HVP]) |
| `http://alice.example/`, `https://192.0.2.1/` | not a handle |

A URL handle is always typed with its scheme, which distinguishes it from a domain handle: `alice.example` is a domain handle, and `https://alice.example/` is a URL handle. The two are resolved differently, and need not refer to the same account.

# Handle Resolution {#resolution}

*Resolution* takes a normalized URL handle and produces the user's unique user identifier and the authorized issuer for the handle. Both the browser and the verifier perform resolution, for the same reasons as in [@!HVP], and the rules that [@!HVP] applies to every resolution step (on HTTP requests, redirects, limits, and caching) apply here too.

Given a normalized URL handle *handle*:

1. **Fetch.** `GET` *handle*, without its fragment, with the following `Accept` header. The response MUST have a 2xx status code. The *final URL* is the URL of the response, after any redirects.

    ```
    Accept: application/ld+json;
              profile="https://www.w3.org/ns/activitystreams",
            application/ld+json;
              profile="http://www.w3.org/ns/json-ld#expanded";q=0.9,
            application/ld+json;q=0.8,
            text/html;q=0.5
    ```

2. **Parse.** If the media type of the response is `application/json`, `application/ld+json`, `application/activity+json`, or another media type with the `+json` structured syntax suffix ([@!RFC6839]), parse it as JSON, and find its subject node for *handle* ((#subject-node)); if there is none, fail. If the media type is `text/html`, parse it as HTML ([@!WHATWG.HTML]). Otherwise fail.

3. **Unique user identifier.** For a JSON document, the unique user identifier is the `id` of the subject node ((#subject-node)), normalized ((#normalization)); if it does not satisfy (#url-handle-syntax), fail. For an HTML document, it is the final URL, with the fragment of *handle*, if any.

4. **Identity document.** If the unique user identifier, without its fragment, is identical to the final URL, the response of step 1 is the identity document. Otherwise, the document names an account at another URL: `GET` the unique user identifier, as in step 1, and parse it, as in step 2. The final URL of this response MUST be same origin with the unique user identifier, the response MUST be a JSON document, and the `id` of its subject node for the unique user identifier MUST be identical to the unique user identifier. Otherwise fail. This response is the identity document. This step is not repeated: an identity document that names yet another account fails.

5. **Issuer.** Collect the issuer identifiers that the identity document names: from its `Link` header fields ([@!RFC8288]) whose relation type is `handle-issuer` ((#handle-issuer-link)); for a JSON document, from the `handleIssuer` property of its subject node ((#handle-issuer-property)); and for an HTML document, from its `<link>` elements whose relation type is `handle-issuer` ((#handle-issuer-link)). If there are none, or they are not all identical, or they are not an issuer identifier ([@!HVP]), fail. Otherwise, it is the authorized issuer.

If any step fails, resolution fails.

Resolution replaces the URL handle with the unique user identifier: from this point on, the unique user identifier is the handle, in the HVT request, in the HVT, and in what the browser displays. In most cases, the two are identical; they differ when the URL that the user typed serves a document about an account at another URL, or redirects to it. See (#why-canonical).

For example, an ActivityPub actor resolves as follows:

```
GET https://social.example/users/alice
Accept: application/ld+json; profile="...activitystreams", ...
  -> Content-Type: application/activity+json
     { "id": "https://social.example/users/alice",
       "type": "Person",
       "handleIssuer": "https://social.example", ... }
User identifier: https://social.example/users/alice
Issuer:          https://social.example
```

> Open Issue: Some ActivityPub servers, such as Mastodon servers with "authorized fetch" enabled, serve actors only to requests that are signed with the key of another server's actor, and respond to the unsigned requests of resolution with a 401 (Unauthorized) response, so that resolution of their actors fails. Resolving parties cannot sign their requests, because they have no actor, and because a signature would identify them. Such servers would need to serve their actors, or at least the `handle-issuer` link of their responses ((#handle-issuer-link)), to unsigned requests. This needs to be discussed with Mastodon as an implementation detail.

## The Subject Node {#subject-node}

Resolving parties do not perform JSON-LD processing ([@?JSON-LD11]): they read JSON documents in the forms that Solid and ActivityPub servers serve, as follows. The *subject node* of a JSON document for a URL *url* is:

- If the document is a JSON object that has no `@graph` member, and that has an `id` or `@id` member whose value is a string, that object. Its `id` is the value of that member. This is the compacted form, which ActivityPub servers serve ([@?ACTIVITYPUB]).
- Otherwise, if the document is a JSON array, or a JSON object whose `@graph` member is a JSON array, the element of that array that is a JSON object whose `@id` member, normalized ((#normalization)), is identical to *url*. Its `id` is the value of that member. This is the expanded or flattened form, which Solid servers serve ([@?SOLID-PROTOCOL]).
- Otherwise, the document has no subject node.

The *value* of a property of the subject node, whose short name is *name* and whose IRI is *iri*, is read from the member *name*, or else from the member *iri*, of the subject node. Its value MUST be a string, a JSON object whose `@id` or `@value` member is a string, or a JSON array of exactly one of these, and the property's value is that string. A property whose member is present with any other value is invalid, and resolution fails.

> Open Issue: Reading JSON-LD without JSON-LD processing means that a document whose `@context` gives `handleIssuer` another meaning, or that uses another term or a compact IRI for the property, is read differently by a resolving party than by a JSON-LD processor. Resolving parties all read it the same way, so this does not let the browser and the verifier disagree, but whether this is acceptable to the JSON-LD community, or whether the `@context` should be checked, needs to be discussed.

> Open Issue: A user who types the URL of their Solid profile document, such as `https://alice.solidcommunity.net/profile/card`, rather than their WebID, which ends in `#me`, gets the document's node as the subject node, which has no `handleIssuer` property. Whether resolution should follow the `foaf:primaryTopic` of the document to the WebID needs to be investigated.

## The handleIssuer Property {#handle-issuer-property}

An identity document names the issuer authorized to vouch for its handle with the `handleIssuer` property of its subject node, whose IRI is `https://w3id.org/handle-verification#handleIssuer`, and whose value is an issuer identifier ([@!HVP]). A subject node names at most one issuer.

In an ActivityPub actor, which is served in compacted form, the property is defined in the actor's `@context`:

```json
{
  "@context": [
    "https://www.w3.org/ns/activitystreams",
    { "handleIssuer": {
        "@id": "https://w3id.org/handle-verification#handleIssuer",
        "@type": "@id" } }
  ],
  "id": "https://social.example/users/alice",
  "type": "Person",
  "inbox": "https://social.example/users/alice/inbox",
  "outbox": "https://social.example/users/alice/outbox",
  "handleIssuer": "https://social.example"
}
```

In a Solid WebID profile, which is authored in Turtle, the property is added to the WebID:

```
@prefix hvp: <https://w3id.org/handle-verification#> .
<#me> hvp:handleIssuer <https://solidcommunity.net> .
```

and the Solid server serves it, in expanded JSON-LD, as:

```json
[{
  "@id": "https://alice.solidcommunity.net/profile/card#me",
  "https://w3id.org/handle-verification#handleIssuer":
    [{ "@id": "https://solidcommunity.net" }]
}]
```

Resolving parties do not parse Turtle: Solid servers serve every RDF document as JSON-LD on request ([@?SOLID-PROTOCOL]).

As in [@!HVP], authorization is explicit: resolution does not infer an issuer from the identity document's other properties, such as the `solid:oidcIssuer` of a Solid WebID ([@?SOLID-OIDC]), the origin of an ActivityPub actor, or the `authorization_endpoint` of an IndieAuth website. See (#why-new-term).

> Open Issue: The IRI of the property, the namespace it belongs to, and whether a JSON-LD context document should be published for it.

## The handle-issuer Link {#handle-issuer-link}

An identity document can also name the issuer authorized to vouch for its handle with a link whose relation type is `handle-issuer` ((#iana)), whose target is an issuer identifier, and whose context is the identity document: in a `Link` header field ([@!RFC8288]) of the response, with any media type, or, in an HTML document, in a `<link>` element ([@!WHATWG.HTML]), whose `href` is resolved against the document's base URL:

```http
HTTP/1.1 200 OK
Content-Type: text/html
Link: <https://issuer.example>; rel="handle-issuer"

<!doctype html>
<link rel="handle-issuer" href="https://issuer.example">
```

This is how IndieAuth websites already name their authorization endpoints ([@?INDIEAUTH]), and it lets a website that cannot vary its responses by media type, such as a static website, use its URL as a URL handle by serving HTML.

# Issuance and Verification {#issuance}

Issuance and verification are those of [@!HVP]: the issuer metadata, the HVT request, its error responses, the HVT, the key binding, and the verification of the HVT+KB, with the following substitutions:

- Wherever [@!HVP] resolves a handle, the resolving party resolves a URL handle as described in (#resolution).
- The body of the HVT request has a single member, `handle` (REQUIRED): the URL handle, which is the unique user identifier that resolution produced ((#resolution)), byte-for-byte. It has no `did` or `url` member: because resolution replaces the URL handle with the unique user identifier, the two are the same value, which is sent once.
- On receipt of an HVT request, the issuer verifies that `handle` satisfies (#url-handle-syntax) and is in normalized form, and that the body has no `did` or `url` member; otherwise it returns an `invalid_request` error. It then checks that the cookies represent a signed-in user whose account is the `handle`.
- The `handle` and `sub` claims of the HVT are both the unique user identifier, byte-for-byte as it appeared in the `handle` member of the HVT request.
- When verifying an HVT, the browser and the verifier accept a `handle` claim that satisfies (#url-handle-syntax), resolve it as described in (#resolution), and verify that the unique user identifier that resolution produces is identical to both `handle` and `sub`.

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

A verifier distinguishes the unique user identifiers of URL handles from DIDs by their form, and from the unique user identifiers of username handles ([@?UHVP]) by the `handle` claim, which is a URL only for a URL handle.

# Privacy Considerations

The privacy considerations of [@!HVP] apply. In particular, the issuer does not learn which verifier the user signs in to, and handles and unique user identifiers are public identifiers.

Resolution of a URL handle is specific to one user: it fetches the user's identity document. When the browser resolves a URL handle, the server that hosts it, and, when step 4 of (#resolution) fetches another URL, the server that hosts that URL, can observe that the user's device is resolving that handle, but not which verifier is involved, because the requests carry no credentials or referrer. When the verifier resolves it, these servers see the verifier's network address, as described in [@!HVP]. The server that hosts an identity document is usually the user's issuer, which can therefore often correlate the HVTs it issues with the resolutions that follow. The mitigations described in [@!HVP], such as caching and resolving through a shared intermediary, apply.

Identity documents can contain more information about the user than their handle, such as their name, picture, or contacts. Resolving parties read only the properties and links that this document defines, but the user's choice to use a URL handle shares the whole identity document with the verifier.

# Security Considerations

The security considerations of [@!HVP] apply, with the following additions.

## Documents That Name Other Accounts {#other-accounts}

An identity document is controlled by the server that hosts its URL, and names both the unique user identifier and the issuer. A document at one URL could name another user's account as its `id`, and an issuer of its own choosing:

```
https://evil.example/ -> id:           https://social.example/users/bob
                         handleIssuer: https://evil.example
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

- Relation Name: `handle-issuer`
- Description: Refers to the issuer that the context authorizes to issue Handle Verification Tokens for its handle.
- Reference: (#handle-issuer-link) of this document

# Design Rationale

## Why a New Property, Rather Than solid:oidcIssuer? {#why-new-term}

A Solid WebID profile already names the OpenID Connect issuers that can authenticate the user with `solid:oidcIssuer` ([@?SOLID-OIDC]). But an HVT is not an OpenID Connect token: OpenID Connect is a two-party protocol, in which the issuer issues tokens to the relying party, and learns who it is, while HVP is a three-party protocol, in which the browser obtains the token and hides the verifier from the issuer. A user who authorized an issuer to sign them in with OpenID Connect has not necessarily authorized it to make statements that the browser presents to verifiers that the issuer does not know. A profile can also list several OpenID Connect issuers, while a handle has a single authorized issuer in HVP. A new property, which is the same for every ecosystem, makes the user's opt-in explicit, as the `HandleIssuer` service does for DIDs ([@!HVP]).

## Why Content Negotiation?

ActivityPub servers serve actors through content negotiation ([@?ACTIVITYPUB]), and Solid servers serve every RDF document as Turtle or JSON-LD through content negotiation ([@?SOLID-PROTOCOL]). Requiring them to serve identity documents at another URL, such as a well-known URL, would require changes to every server, and would not fit identifiers that are not at the root of a domain. Websites that cannot vary their responses by media type can name their issuer in HTML instead ((#handle-issuer-link)).

The `Accept` header requests JSON-LD with the ActivityStreams profile first, because ActivityPub servers are required to serve actors for it, and expanded JSON-LD next, because it can be read without a JSON-LD processor ((#subject-node)).

> Open Issue: Requesting the ActivityStreams profile ties the `Accept` header to ActivityPub. Whether a profile that is not specific to any ecosystem can be requested instead, and how existing ActivityPub servers would respond to it, needs to be investigated.

## Why Replace the Handle With the Canonical Identifier? {#why-canonical}

A URL that the user types can serve a document about an account at another URL, or redirect to it, for example when a personal website serves the actor of an account whose identifier is at a longer URL on the same server. Resolution then has two URLs: the one that the user typed, and the one that identifies the account. Verifying the typed URL as a handle of the account would require the account to agree to it, with a back-link from the account's identity document to the typed URL. This document instead replaces the typed URL with the account's identifier, which needs no back-link, because the server that hosts the account names the issuer itself. Typed URLs that the account agrees to could be supported later.

> Open Issue: Whether to let an identity document keep the URL that the user typed as its handle, when the document lists it, for example in its `alsoKnownAs` or `url` property.

## Why Not Process JSON-LD?

A JSON-LD processor fetches remote contexts, which adds requests, latency, and attack surface to resolution, and is a large dependency for a browser and for verifiers. ActivityPub explicitly allows its documents to be processed as plain JSON ([@?ACTIVITYPUB]), and expanded JSON-LD has no contexts to process, so reading both forms as plain JSON ((#subject-node)) covers the documents that Solid and ActivityPub servers serve.

# Implementation Status

*Note: This section is to be removed before publishing as an RFC.*

There are no implementations of this document yet.

# Document History

*Note: This section is to be removed before publishing as an RFC.*

- draft-goto-url-handle-verification-00
  - Initial draft.

{backmatter}

# Examples {#examples}

This appendix shows the resolution of URL handles. The identity documents of the Solid, ActivityPub, and IndieAuth examples are real at the time of writing, and are abbreviated. None of them names an issuer yet, so each shows what would be added to opt in. The values will change over time.

## Solid WebID

```
Handle:        https://timbl.solidcommunity.net/profile/card#me
GET https://timbl.solidcommunity.net/profile/card
  -> Content-Type: application/ld+json   (expanded)
     [ ..., { "@id": "https://timbl.solidcommunity.net/profile/card#me",
              "http://www.w3.org/ns/solid/terms#oidcIssuer":
                [{ "@id": "https://solidcommunity.net/" }], ... } ]
Identifier:    https://timbl.solidcommunity.net/profile/card#me
To opt in, add to the WebID (oidcIssuer is not read):
  <#me> hvp:handleIssuer <https://solidcommunity.net> .
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
  "handleIssuer": "https://w3c.social"
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
  "handleIssuer": "https://bumblefudge.com"
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
  Link: <https://aaronparecki.com>; rel="handle-issuer"
  <link rel="handle-issuer" href="https://aaronparecki.com">
Issuer:        https://aaronparecki.com
```

# Acknowledgments

This document builds on the Handle Verification Protocol, on the WebID, Solid WebID Profile, and Solid-OIDC specifications of the Solid community, on ActivityPub, and on IndieAuth.
