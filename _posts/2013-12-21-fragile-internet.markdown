---
layout: post
title:  "Fragile Internet"
date:   2013-12-21 23:30:00
categories: internet
---

On the Internet, take nothing for granted. It's one tricky world where everything is not what it seems. Besides content,
I'd like to focus on security and what it takes for a site domain to serve on a public network. The key concpets of
[information security](http://en.wikipedia.org/wiki/Information_security) are _availability_, _integrity_,
_confidentiality_, _authenticity_, and _non-repudiation_. The following shows how each of them are put under pressure
for each valuable service on the Internet.

**Availability** is about information being accessible to other services/clients on demand. It's difficult to forecast
when a service is going to be used more often than usual. Advanced systems can scale to increase hardware support for
handling requests. Sometimes availability can be jeopardized by attacks on DNS entries (when DNSSEC is not implemented)
or by DDOS attacks on TCP/IP that aim to exhaust avilable resources on the domain for accepting more requests. However,
the disruption might also be caused by poor service implementation (including slow queries to backend database) and due
to external factors, such as power outage or system reboot. Availability can be supported by multiple machines where the
service handles requests. Disruption in one machine might not affect others when service is properly mirrored. On the
other hand, TCP/IP and other connection related parameters must be reviewed and tested to reduce chances of being
surprised.

**Integrity** means that data is not altered during the transit over the network. It's not about avoiding data
manipulation but about avoiding it happening without notice. Considering that quite many network protocols provide no
encryption nor hash-calculation of sent data, and that information passes many computing devices before reaching
destination, integrity is at high risk. To compensate the risk, strong hashing and encryption methods should be applied.
This overhead will at least provide better confidence.

**Confidentiality** usually translates to encrypted communication channel and non-availability of sensitive information
to third-parties. Although the channel may be encrypted, it must be checked that no other less or non-encrypted channels
exist.

**Authenticity** is used to describe that the data claiming something is genuine. So there must be somekind of
verification process. The most common and standard is a certificate, but PGP signatures can be used as well.

The last of them, **non-repudiation**, means that the individual, who made some (legal) actions, can be later proven to
be that same person. It's the most complicated one to achieve since it's not enough to say that authenticated
credentials matched. It must be possible to prove that the same person also sat at the computer where the actions were
started, and that computer was not compromised. How to achieve that, I can't give any complete answers.

The previous sections were quick run-down of major security concepts. However, that's enough to make some remarks
regarding the Internet:

1. The Internet comes with no security built-in. Security is provided by _add-ons_ (need to be installed by experts).
2. The data, that are transferred, pass many (virtual) eyes before reaching destination, so assume it's visible.
3. Services on the Internet must be ready for high load of traffic, bad requests, and verification of certificates.
4. The main methods for securing a domain:
   a) system/network configuration,
   b) domain certificates and encrypted connections (TLS),
   c) optimized and tested service code,
   d) content hashing.

Dear reader, if you see a lot of problems with the current Internet architecture, like I do, I encourage you to think
about it and to dream and share ideas for smarter Internet. There are alternatives like
[GNUNet](http://en.wikipedia.org/wiki/GNUnet), however, the simplicity and data richness of current Internet should
remain to be competitive. Therefore, our Internet is still immature, but hopefully no more than a century later, the
Internet protocols will be safer and wiser.

### Summary

To provide a service on the Internet, security must be part of the plan. The main concepts of security are availability,
integrity, confidentiality, authenticity, and non-repudiation. Unfortunately security is not for granted, and requires
custom deployment per service. Without a good security plan, the service better be insignificant. However good security
for an Internet domain includes site certificate(s), TLS connections (e.g. HTTPS), content hashing, and expert security
administrators. Hopefully Internet can still develop to a network where data security is no longer primary concern.

