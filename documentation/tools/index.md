---
layout: flat
title: Tools and Programmatic Support
---

This page gives an overview of the tools and utilities that are available to
help you work with (and learn) CybOX. It does not go into depth on each tool,
but links to the in-depth documentation for that tool directly.

Most of these tools are provided directly by the CybOX project, but if the
community develops and publishes a tool we would be happy to link to it here.
Note that any tool provided by the CybOX project, with the exception of the
bindings, is intended primarily as an illustrative example of what can be done
rather than a production-quality capability.

## User-level Tooling
User-level tooling can help abstract away the CybOX XML and provide you with
different views or capabilities for working with CybOX that may not require you
to know XML at all. Currently, the CybOX project provides the CybOX-to-HTML
tool to present CybOX XML instance documents in a more readable manner.

### CybOX-to-HTML

CybOX-to-HTML is an XSLT stylesheet that can take a CybOX XML document and turn
it into a more readable HTML view. 

That said, the XSLT is easy enough to use if you understand how it works and if
you run it directly it's easy to transform dozens of CybOX documents at once.

* [Documentation](https://github.com/CybOXProject/cybox-to-html/blob/master/README.md)
* [Source Code](https://github.com/CybOXProject/cybox-to-html)

## Developer Tools and Utilities

### Email-to-CybOX

The Email-to-CybOX tool is written in Python and used to convert email (MIME
documents) into CybOX Observable documents. It can parse out IP address
information from the message contents and perform whois and DNS lookups, as
well as convert the Email message structure into the CybOX format.

* [Source Code](https://github.com/CybOXProject/email-to-cybox)

### OpenIOC-to-CybOX
OpenIOC-to-CybOX is a Python utility to convert Mandiant's
[OpenIOC](http://www.openioc.org) format into CybOX Observables.

While useful for it's stated purpose, the other way to use this tool is as an
example of how to generate CybOX content programatically using the bindings.
Looking through the source code is a great way to see how they work and how to
import/use them.

* [Source Code](https://github.com/CybOXProject/openioc-to-cybox)

### X.509-to-CybOX
The X.509-to-CybOX utility is written in Python and converts X.509-compliant
certificates into CybOX Observable documents.

* [Source Code](https://github.com/CybOXProject/x509-to-cybox)

### CybOX-to-OVAL
The CybOX-to-OVAL utility is written in Python and translates CybOX Observable
documents, containing CybOX Objects to the 
[Open Vulnerability and Assessment Language (OVAL™)](https://oval.cisecurity.org/).

* [Source Code](https://github.com/CybOXProject/cybox-to-oval)

## Programmatic Support

### Python

The CybOX project currently provides bindings and higher-level APIs to the CybOX Language through the python-cybox project.

* [Download](https://pypi.python.org/pypi/cybox)
* [Source Code](https://github.com/CybOXProject/python-cybox)
* [Documentation](https://cybox.readthedocs.org/)

### Community-Developed Tools
The tools and libraries listed below are developed by CybOX community members
and offer the ability to parse, create, edit, or otherwise make use of CybOX
documents. We would love to have more entries in this section, so if you'd like
to see yours included, please let us know by by subscribing and submitting comments to the [CTI Users List](/community/#cti-users-list) or the [CTI TC Public Comment List](/community/#public-comment-list)!

## IOCextractor
The IOCextractor is a Python utility developed by Stephen Brannon which
includes support for exporting CybOX Observables. Its documentation states the
following:

> IOC (Indicator of Compromise) Extractor: a program to help extract IOCs from
text files. The general goal is to speed up the process of parsing structured
data (IOCs) from unstructured or semi-structured data (like case reports or
security bulletins).

* [Source Code](https://github.com/stephenbrannon/IOCextractor)
