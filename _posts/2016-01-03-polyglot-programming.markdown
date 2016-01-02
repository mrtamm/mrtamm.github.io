---
layout: post
title:  "On Polyglot Programming"
date:   2016-01-03 00:30:00
categories: general
---

Polyglot programming is an everyday chore for many developers. And it's normal!
I want to emphasize that it is ok to extend the list of different languages in
use.

There is no single tool to solve different kinds of problems. You pick the most
appropriate tool depending on the problem type being solved. In [my previous
post]({% post_url 2015-09-16-programming-languages %}), I also outlined that
programming languages are designed depending on the type of problems they are
targeting.

It's hard to draw the line where one problem domain ends and another begins. It
seems that all kinds of problems could be solved by just using a general purpose
programming language. However, SQL seems more efficient for retrieving data from
database, HTTP excels at content query from a remote server. Yet, both SQL and
HTTP are implemented using a general purpose programming language, though they
are more efficient in what they target.

Our applications depend on different kinds of resources for its operations.
Examples include configuration (from file or database), content store (database,
repository), external services (remote servers) using different types of
protocols (HTTP, SMTP, proprietary, etc) and formats (HTML, and many others).
Although the application can be considered as one whole thing, it actually
consists of parts that handle their own specific details.

Again, it is possible to solve many specific problems with a main programming
language of choice, however, that is not always considered efficient. For
example, HTML templates are in common scenarios rendered according to the rules
of a template language. And SQL is still a preferred choice for data retrieval
from a database. Therefore, polyglot programming is a normal and sane part of
developer's everyday work.

Notice how different systems/modules need need some glue in-between. For
example, the "glue" between a programm and its rendered HTML is a template file
and rendering engine. The "glue" between between two systems might be JSON over
HTTP, while the programs will work with the data through a JSON library (API is
the "glue" here).

Although an API can be expressive, also consider as an option to express an
intent through some other medium the module in use could access and evaluate.
Again, the HTML template is a classical example here, but also configuration,
public/private keys, SQL queries with placeholders, etc, which can be expressed
off the code.

As a remark, for some reason it does not seem elegant to see another programming
language code within the main code. This usually occurs at the crossing point
where different domains meet. It would be much nicer to devise a specific
language construct to deal with the boundary of two different systems.

Different tools depending on the problem being solved seems normal. However, it
leaves the question of what is the use of general purpose languages? As
mentioned above, these are used to implement problem-specific languages and
corresponding APIs. In addition, they can be thought of glue for binding
together and orchestrating communication flow between the problem-specific
modules that our application consists of. Big systems use smaller components
to delegate tasks to. When such system cannot be divided into modules, it's
likely to be spaghetti.

All in all, don't be restricted by the choices of main programming languages.
They are just needed for building more powerful and expressive tools, which need
an expressive API and friendly syntax!

