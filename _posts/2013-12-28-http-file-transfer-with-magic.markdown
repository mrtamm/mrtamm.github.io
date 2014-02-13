---
layout: post
title:  "HTTP &#150; File Transfer With Magic"
date:   2013-12-28 23:30:00
categories: internet http
---

The most used service on the Internet, [the Web](http://en.wikipedia.org/wiki/World_Wide_We), would not be possible
without [Hypertext Transfer Protocol](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) (HTTP). It is
a peculiar protocol, indeed. It's basically a file transfer protocol for viewing (mostly) public resources on an
Internet domain (server). By resource, I mostly mean hypertext documents -- human readable text files composed using
[Hypertext Markup Language](http://en.wikipedia.org/wiki/HTML) (HTML). These documents complement HTTP as they contain
links to other resources on that site. A client first fetches the root HTML page, and, using hyperlinks from that file,
can navigate further in the web site by issuing more HTTP requests.

### Breaking up HTML
 
Despite of close partnership between HTTP and HTML, hypertext linking was also designed to support other protocols (e.g.
FTP, FILE) and resources (e.g. PDFs, Microsoft Word documents). However, I doubt that at the moment when the first HTML
solution was created, it was foreseen the need for scripting and styling that could be independent from the HTML
document. Actually, it's pretty normal to think that all information of a document is contained in one file (as it is
with PDFs and Word documents). However, nowadays most websites separate
[JavaScripts](http://en.wikipedia.org/wiki/JavaScript) and [CSS](http://en.wikipedia.org/wiki/Cascading_Style_Sheets)
styles from the markup/content as it is more network-efficient. When a browser has already downloaded the latest scripts
and stylesheets of the web site, it can save time and effort by just downloading new HTML content.

In recent times, the need for separation goes even further: when a site uses common layouts for displaying its content,
perhaps the layout _markup can be predefined_, and the client side can just _download the data_ to be displayed on the
page. The most common data serialization standards are [eXtensible Markup Language](http://en.wikipedia.org/wiki/XML)
(XML) and [JavaScript Object Notation](http://en.wikipedia.org/wiki/JSON) (JSON), the latter being more popular while
both are supported by most popular web browsers. To pre-emptively download all the site templates, site administrators
can use [Manifest](http://en.wikipedia.org/wiki/Cache_manifest_in_HTML5) files. The browser would download the files in
background and cache them. When asked for an HTML resource, a script can just download the data and then render the
template using the data. This approach has really a drastic effect on page load speed.

### The Many Faces of HTTP

Unlike [FTP](http://en.wikipedia.org/wiki/FTP), HTTP has many built-in features that make it superior thanks to message
headers in both requests and responses:

1. A method in HTTP request defines an action to be performed on a server-side resource;
2. conditional requests indicate the server not to perform an action when resource hash or last modified date does not
   comply;
3. HTTP enables payload compression, caching, and partial responses, as well;
4. HTTP is mostly for public access but can also define privileged access (with credentials check) to resources;
5. an HTTP connection can be upgraded to another communication protocol (e.g. 
   [WebSocket](http://en.wikipedia.org/wiki/WebSocket), [HTTP2](http://en.wikipedia.org/wiki/HTTP2)) when server agrees.

There are many predefined actions (HTTP methods) to apply on resources, the most common ones being ``GET`` and ``POST``,
though a resource can choose which methods it supports. The HTTP standard also defines a great set of response codes
that a server could respond with to describe the status. It makes it all a bit complicated but enables quite easy
debugging when neccessary.

### The Many Faces of a Resource

HTTP version 1.1 broke the common view of resources as files. When usually human users distinct files by looking at the
file extension then HTTP does not follow that habbit. Instead, a resource _should not have an extension_ because it does
not have a role for HTTP responses. The new feature called
[content negotiation](http://en.wikipedia.org/wiki/Content_negotiation) _enables multiple formats_ for displaying the
resource data. Since extensions are ignored, clients indicate most and least preferred response formats (in the header
of the request message) and the server can choose one of them for returning the resource in that particular format.
There is _no standard default file format_ to be supported. The choices for available formats _depends on that
particular resource_. For example, a JavaScript resource can only be served as JavaScript content while a data resource
might be served as HTML, XML, or JSON, the former being the default one.

Content negotiation is incredibly fantastic and revolutionary feature. Why download an HTML file to parse data from it
when it's also available in JSON format? However, this cool solution departs from the originally visioned hyperlinked
world. JSON and XML can contain [URL](http://en.wikipedia.org/wiki/URL)s as data but it needs human intervention to say
how and when it can be used. For example, it might be a [URI](http://en.wikipedia.org/wiki/URI), which is not a link but
some kind of semantic data type. Therefore, _the linking feature breaks_ and now possible URLs need to be manifested in
other ways, most commonly via developer documentation. The problem is somewhat new and there are different solutions to
cope with it. It's a matter of time until standards appear.

### Summary

It's clear that HTTP and HTML are closely related technologies as they enable both resource linking and discovery. While
HTML is perfect for rendering [user interfaces](http://en.wikipedia.org/wiki/User_interface) (UI) of remote web
services, it's not that amusing for programs trying to extract data from these HTML documents. On the other hand, 
considering that user interfaces need to be responsive, HTML documents have switched from one monolithic file to many
files approach where each file has its own role to play (view layout, scripting, styles, and data). The browser needs to
download only those resources that it already does not have cached. Although the number of remote files increases, this
approach is superior in terms of network resource usage and page load speed.

HTTP has become the mainstream protocol on the web thanks to its extensible headers and built-in optimization options.
It also enables construction of more convenient web sites where resources are not just some static files but a resource
is some specific data that might be possible to be returned in different formats (pre-defined by the resource, service,
or server). With this convenience, the resource linking issue has become apparent and has forced web service providers
to handle it as conveniently as possible. However, it takes some time to become standardized.

