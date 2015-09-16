---
layout: post
title:  "The Babel of Programming Languages"
date:   2015-09-16 22:10:00
categories: general
---

The question of why there are so many programming languages has been raised and
answered several times. Yet this question still comes to my mind when I discover
another new programming language that I didn't know about before. I wonder which
niche it will try to occupy, who will be developing with it, and who will be
maintaining it. After all, programming languages need developers to use and to
"grow" them. Therefore, over a hundred programming languages to choose from
seems like madness for both experienced programmers and for newcomers, as well.

I prefer to think about programming languages in wider context. There are
languages, which are interpreted (SQL, JavaScript, HTML), which are compiled
directly into machine code (the C language) or into some intermediary \[byte\]
code (Java Virtual Machine based languages). Usually, it's the lower-level
languages that compile into machine-code, and higher-level languages that are
interpreted by some existing programs in order to execute them.

So how are developers supposed to handle this Babel of programming languages?

### The Symptoms

Since the cause of why new programming languages are created has been explained
several times, I would like to just cover the main drivers for this need:

1. a need to improve over existing languages;
2. provide another approach to writing and executing code (e.g. functional
   vs. object-oriented programming; also its targeted user-group, e.g. BASIC
   was created for beginners to help them learn programming);
3. competition: to attract and keep developers at a certain platform (major
   software companies have their own programming languages because of this);
4. to solve a specific scenario where intent could be expressed as easily as
   possible (e.g.HTML for documents, CSS for document design, SQL for relational
   databases);
5. personal endeavours (learning, experimenting).

To put it into one sentence, I would say that all programming languages are
created to "scratch a personal itch", until they succeed and live on on their
own, supported by a community of users.

It is important to emphasize that adding a new programming language just to
have a cooler syntax is not a simple task. Besides the syntax, every programming
language as a platform needs a standard API. Now imagine operating system
bindings, network stack, security tools, etc reinvented in every platform!
That's a huge amount of work and lots of maintenance for developers, and also
oportunities for bugs and incompatibilities.

The problem is that it's difficult to create a universal language that would
enable all programmers to express intents in the most concise and simple
manner as possible. So people keep inventing new languages, reinventing the
if-statements and for-loops to fit a particular style. However, how long this
will continue?

### The Situation

All programming languages compete with each other. The competition is driven by
the preferences of software companies, university curriculums, and hacker
communities.

By now, there are already many good programming languages to choose from. The
market for them is also quite saturated: by looking into forums and mainstream
platforms we can guess the most commonly used languages.

Programming languages are often \[deliberately\] created for some kind of
audience: the web platform languages, database languages (mostly SQL), JVM (Java
Virtual Machine) languages (Java, Groovy, Scala, JRuby, etc), and operating
system specific languages (by Apple and Microsoft). I included mainstream
languages here but I would like to emphasize that they tend to live in their
niches.

However, there are also even smaller niches (problem domains) that need their
own customizations. For example, R as a language for statistical computing, the
Go language, which has found a warm welcome on server-side due to its
concurrency support and simplicity. These are mostly higher-level languages
implemented in lower-level languages in order to have good performance. The key
here is that these are not designed as general purpose languages that include
support for everything. Instead they go for a small niche, where general purpose
language are not good enough anymore.

Higher-level of abstraction is what developers building large systems need.
Program variables nowadays should not be hardware dependent anymore. Even
further, since developers tend to solve same problems over and over again, it
is clear that these solutions need to be encapsulated and be consumed by calling
out with custom parameters. Adding support for these common needs right into a
language is definately a huge win. (For example, the simple parallel execution
support or concurrency in the Go language is definately its major feature.)

I hope that new languages, when they do appear, at least follow this principle
of higher-level abstraction. There are already many low-level languages out
there, and their competion is almost settled.

### The Legacy

There will be new programmers who are going to see these oh-so-many-choices for
learning programming. Important is to be not intimidated by these choices but
to first think about what kind of programming needs to be done. There are these
traditional choices, such as the C programming language, which has a huge effect
on the style of other languages. In addition, there are popular or mainstream
languages, such as Java, C#, Python or Ruby, for which it is easier to find a
job. Also JavaScript as a web platform programming language is quite popular and
is a good place to start for its simplicity.

However, once it becomes clear what type of applications need to be developed,
it would be wise to get familiar with other tools and languages made for that
field. They may prove useful to get the job done faster and in a more elegant
way. Besides, when an application needs to run on different platforms, it might
also require the use of several programming languages depending on what is and
what is not supported by a platform.

On the other hand, it's not worth chasing all the new platforms and languages,
at least in their beginning. Of course, they may be tested to see how well they
perform, but it also takes time for its community to grow and to discover and
fix its design mistakes. A new programming language as a tool may be taken to
production as it becomes stable and mature over the years.

### Conclusion

There is no universal language, so we have many paths to express our intents to
devices. However, since the competition in general programming languages is
already quite tough, it would be wiser to design languages for specific problem
domains, where there are no good solutions yet.

The legacy is the programming languages we already have. Not all of them will
survive in the long run. Therefore, new programmers should choose carefully
where to begin. On the other hand, experienced programmers should also watch out
for new solutions that could simplify their work in the problem domain they are
mostly dealing with. These new tools could vastly improve work efficiency, so it
is natural to spend time on investigating further possibilities.

Hopefully now the great variety of programming languages does not seem so
annoying after all. There are many good platforms to target application
development. Just let the competition identify the best ones.

