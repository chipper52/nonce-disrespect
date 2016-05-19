Nonce-Disrespecting Adversaries
===============================

We provide supplemental material to our research on AES-GCM nonce reuse vulnerabilities in TLS.

Research paper
==============

* [Nonce-Disrespecting Adversaries: Practical Forgery Attacks on GCM in TLS](https://eprint.iacr.org/2016/475)

Background
==========

We investigate nonce reuse issues with the GCM block cipher mode as
used in TLS and focus in particular on AES-GCM, the most widely
deployed variant. With an Internet-wide scan we identified 184 HTTPS
servers repeating nonces, which fully breaks the authenticity of the
connections. Affected servers include large corporations, financial
institutions, and a credit card company. We present a proof of
concept of our attack allowing to violate the authenticity of affected
HTTPS connections which in turn can be utilized to inject seemingly
valid content into encrypted sessions. Furthermore, we discovered
over 70,000 HTTPS servers using random nonces, which puts them at risk
of nonce reuse, in the unlikely case that large amounts of data are
sent via the same session.

This repository provides supplemental code and information.

Code
====

* [getnonce](getnonce/) - scan tool and OpenSSL patch used for our Internet-wide scan.
* [gcmproxy](gcmproxy/) - attack implemented in Go.
* [tool](tool/) - helper tools used by attack code.

All our code is published as CC0 / public domain.

Data
====

* [Nonce values from Internet-wide scan on scans.io](https://scans.io/study/nonce-disrespect)

Advisories
==========

Security advisories from affected vendors:
* [Security Bulletin: Vulnerability in IBM Domino Web Server TLS AES GCM Nonce Generation (CVE-2016-0270)](https://www-01.ibm.com/support/docview.wss?uid=swg21979604)
* [Radware / SA18456: Security Advisory Explicit Initialization Vector for AES-GCM Cipher](https://kb.radware.com/Questions/SecurityAdvisory/Public/Security-Advisory-Explicit-Initialization-Vector-f)

Misc
====

* [TLS Symmetric Crypto (Blogpost by Adam Langley with the initial idea for this research)](https://www.imperialviolet.org/2014/02/27/tlssymmetriccrypto.html)
* [Authentication Failures in NIST version of GCM (Antoine Joux, source for Forbidden Attack against GCM)](http://csrc.nist.gov/groups/ST/toolkit/BCM/documents/comments/800-38_Series-Drafts/GCM/Joux_comments.pdf)
* [Youtube video showing XSS injection on visa.dk](https://www.youtube.com/watch?v=qByIrRigmyo)
* [Black Hat USA 2016 talk announcement](https://www.blackhat.com/us-16/briefings/schedule/#nonce-disrespecting-adversaries-practical-forgery-attacks-on-gcm-in-tls-3483)
* [Slides from talk at BerlinSec Meetup](https://www.int21.de/slides/berlinsec-gcm/)
