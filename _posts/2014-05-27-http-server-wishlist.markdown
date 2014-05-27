---
layout: post
title:  "Wishlist for HTTP servers"
date:   2014-05-27 09:25:00
categories: internet http
---

There are quite many HTTP server implementations out there implemented in
various programming languages. The most important criteria for a server seems
to be its capability to handle as much requests as possible, and ease of
configurability. However, these expectations are too common. What else should
an HTTP server be good at so that site administrators could better concentrate
on the content rather than technical tuning? Here is my wishlist.

### 1. HTTP As a Unified API for Services

HTTP boasts quite many features such as content negotiation, range requests,
caching, authentication for restricted content. Usually when servers support
any of them, these features need to be configured in a server specific way (for
turning them on and for setting the supported options). However, it should
require minimum of fuss.

For example, HTTP service developers ought to not implement header field parsing
and formatting when it is already common and standard. In the case of HTTP
header based authentication, the service could only declare the authentication
method and/or just handle username/password checking. In case of representation
formats and content negotiation, a service could provide callbacks to provide
options while server would control the process. Having a standard programmatic
HTTP API to let services implement all that with minimum fuss will increase
productivity and reduce waste in HTTP service development.

In addition, HTTP API is not just for static resources (files) but also for
serving dynamic content (containing data from external resource). Having a
common API helps to implement both needs. Keeping multiple servers just to
handle static (file-server) and non-static (application server) content
separately seems to me as a burden because then both need to be managed and
monitored.

Nowadays, HTTP servers only provide a general HTTP API for working with
requests and responses but I claim that it is not enough. I would like to
highlight that site developers ought to not worry much about how HTTP works or
what headers it serves with the content. Developers should be able to focus on
content and its properties (media type, cache-behaviour, and representation
renderer for dynamic content) while the server would take care of serving these
properties to HTTP clients in the correct way.

Finally, I would like to note that from the above it may look that it is the
task of a development framework to address these issues. However, I suggest
that these features would be built right into an HTTP server to achieve better
clarity and efficiency. Build once rather than let frameworks implement the
same standard features over and over again, which in turn is a sad but
inevitable waste in the world of software.

### 2. Extendable HTTP

The HTTP standard enables some parts of it to be extendable. For example,
custom header fields, custom transfer encodings, custom representation types
(MIME-types). So its obvious that servers enable us to extend them. However,
what intrigues is how well the HTTP server enables to implement extensions
uniformly. Usually servers support extensions as plugins, although these are
static content servers. What about application servers?

In the context of the previous wishlist item, HTTP features could also be
extended through the common API. It is probably not often needed but this
property of the API is important for enabling customizations where the HTTP
standard allows it and also for being prepared for the future.

### 3. Introspection

When an HTTP server is running, it would be great to see its runtime
(effective) settings, e.g. compressions, HTTP request processing modules (which
would include "features from plugins") and their order. It would surely help
when some issues with them need to be solved.

In addition, let's take a step further and also think about HTTP services
(resources). Wouldn't it be great if the server could also enlist all the
services it contains, the resources (URLs) that it serves and can describe
their HTTP-related properties. Usually we have to guess URLs or look into the
code to discover that information. It would make URL testing much easier. Site
administrators would surely like to understand more about their dynamic web
service, especially when they deploy third-party HTTP services.

Well, how to achieve that? It may be easy with static content but looking at
how dynamic content is nowadays served, it does not seem sufficient. Instead,
HTTP servers need to define requirements how the service content is structured
and interpreted. One such approach is a tree of resources (like file-system for
static content but programmatic). Before throwing in a solution, I think there
are quite many ways to achieve that, and therefore leave it undecided for now.

### 4. Server Dashboard

Very few HTTP servers come with a dashboard, whether it is a command line or
with a graphical user interface. Usually there are third-party providers for
measuring activity of a server instance. However, I'd like to push this feature
forward: each standalone HTTP server should provide means for humans to see
what the server knows about its configuration and services, and also the server
should explain how busy it is, what are the most used services and URLs, what's
the typical response codes, etc. Integrating a server with third-party
monitoring solution is time-consuming and having a built-in dashboard would be
a huge benefit for us, the users.

Regarding how a dashboard could be implemented, I recommend that it would not
be an HTTP service on the server because it would introduce a risk that
outsiders could get access to somewhat sensitive information. I would recommend
a command-line based interface especially for remote servers without a GUI, and
a desktop application for rich interfaces. However, it does not matter if the
HTTP server monitor is built right into the server, or it is a secondary
application (bundled with a server) that communicates with the server.

## Summary

I described here four features for HTTP servers that I find lacking although
all of them are more or less successfully implemented somehow. I use this post
to encourage HTTP server developers to think more about these parts as well now
that the standard HTTP part is working splendidly. These are not for making
HTTP better but to improve how effectively people can work with HTTP servers.
