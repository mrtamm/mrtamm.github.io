---
layout: post
title:  "What Is an HTTP Resource?"
date:   2014-02-11 01:00:00
categories: internet http
---

The Web consists of hosts (servers) providing resources (information, in
general) and usually the resources also link to each other. The term _resource_
is defined in HTTP specification and I believe that it definitely deserves some
time and thinking to understand what it really is.

## Common Properties of HTTP Resources

When talking about server resources, people usually think about HTML,
JavaScript, CSS, and multimedia files. However, these are just some common
examples, and we should not think about resources as some files on a server. A
resource can also be an interface to a car, toaster, nuclear station, etc. It
usually returns an HTML file not because _it is_ that file but _as a
representation format_ for displaying its state. For this reason, I've tried to
describe here how resources are used using HTTP protocol. The definitive guide
is, of course, HTTP/1.1 specification that also describes the exceptional
cases, but what I have outline here is general view from the perspective of an
HTTP resource.

### 1. Each resource has its own path (URL)

1. Here it does not matter how many request handlers are used to implement the
   resource on server-side: _a path identifies exactly one HTTP resource_.
2. Two URLs point to the same resource if their protocols, hosts, ports, and
   paths are same, only parameters can differ.
3. A resource exists when the HTTP response status is 2xx (OK) or 3xx
   (redirection), although it might have not existed before request (PUT
   method), or it may be removed after request (DELETE method).

### 2. Resources can be interacted with using HTTP methods

1. Supported HTTP methods depend on resource and server. GET is the most common
   method but does not have to be implemented by all resources.
2. In addition, a resource can take input from URL parameters or request
   payload (or both). It is important to distinguish these two sources. For
   example, URL parameters should not "hide" form data (payload) parameters
   with the same name. 
3. A resource may also consider stored HTTP session data (including HTTP
   cookies), authentication credentials, however, _should not care_ about by
   HTTP request headers, which should be handled by HTTP servers.

### 3. Resource can have from zero to many representations
1. By _representation_ I mean _payload format_ for returning a resource state.
   The format is identified by MIME-type, which is also used in e-mail standard
   for storing attachments together with mail message.
2. The representation is chosen by an HTTP server that makes the decision based
   on HTTP headers, optionally using information from request path and
   parameters, and on the available choices by the resource.
3. When no representation is available, the server may ignore requested
   MIME-types.
4. When request expectations and available choices do not match, the server can
   respond with error and a list of available MIME-types.
5. When multiple types qualify for response, the server may choose the one with
   stronger qualifier, or the first acceptable.
6. When request provides no preferences for representations where there are
   many available, the server ought to send the most browser-friendly (e.g.
   HTML) or respond with a redirect containing links to the available
   representations.
7. Server should not process a request beforehand when it is about to be
   indecisive about the ultimate representation type.
8. _Last but not least_: a server can ignore HTTP request  preferences for
   response media-types, although, it should be consistent with that to avoid
   sending mixed signals to client about when negotiation works or not.

## Content Negotiation: HTTP header vs. URI

Previously I explained that URLs point to HTTP resources, which can support
multiple representations (MIME-types), and that the path extension or
parameters theoretically have no direct effect on the returned format. At
least, this is how content negotiation is envisioned to work using
`Accept-Type` HTTP header field, and browsers have embraced it, as well.

On the other hand, when an HTTP resource has many representations available
that cannot be selected directly using URL, a browser or an HTTP server will
usually make the choice for us. This is a good case for demonstrating why
sometimes resource (*/profile*) URL also needs to have an influence on the
returned format, either by path extension (*/profile.json*) or via a known
parameter (*/profile?format=json*). This, of course, needs to override the
`Accept-Type` header based content-negotiation on the server to be effective.

When accessing a resource with multiple representations (*/profile*), the
server should preferrably respond immediately by sending a browser-friendly
HTML document (optionally with hint: `Content-Location: /profile.html`) but it
can also send a redirect with the links to available representations for the
user to decide: */profile.html*, */profile.json*, */profile.xml*, etc. The
current content negotiation algorithm, however, is not yet standardized, and
leaves much freedom to HTTP server and application developers on how and when
to implement.

## Summary

Here I have laid out some fundamental properties of HTTP resources. They are
some _unspecified creatures_ on a (remote) host. I can manipulate them using
HTTP method, URL parameters, and payload, but sometimes they are also affected
by authentication credentials, HTTP session and cookies data. And perhaps most
importantly, resources usually have representations available so I could view
them. However, since user-agents tend to choose a representation itself, it
would be really helpful, if a representation could also be selected by adding
some extra information to the URL whenever such a critical situation would
arise.
