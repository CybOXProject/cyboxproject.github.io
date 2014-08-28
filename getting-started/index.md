---
layout: flat
title: Getting Started
---

## Understand the Concept
The first and most important step to getting started with CybOX is to
understand why it was developed, what problems it is designed to solve, and how
you can use it to solve those problems. The [CybOX Introductory
Brochure](http://makingsecuritymeasurable.mitre.org/docs/cybox-intro-handout.pdf)
is a great start to understanding this.

## Familiarize yourself with the Data Model and Schemas
In CybOX 2.1, the data model is represented as an XML Schema. The CybOX schemas
define the canonical CybOX data model and the only official way to share CybOX
information is through XML instance documents that conform to these schemas.

If you're an XML person, now would be a good time to download the schemas. To
do so, visit [the release page](http://cybox.mitre.org/language/version2.1/)
and choose which bundle of content you want to download. The recommended
download is the [All Files
(Offline)](http://cybox.mitre.org/language/version2.1/cybox_v2.1_offline.zip)
bundle. It contains all the CybOX schemas, and all extension/external schemas.
In other words, everything you need to validate CybOX instance documents. We do
not suggest using the schemas from this GitHub schemas repository unless you
know what you're doing: these are development versions and are not optimized
for ease of use.

## Review the Schema Documentation
In either case, the schema documentation is available both for those of you
that aren't as familiar with XML Schema and those that are but don't want to
have to pour through XML. This documentation is available on the [release
page](http://cybox.mitre.org/language/version2.1/), under the "Documentation"
column.

## Look through the Samples
If you're like many people, there's no substitute for good sample data when
working with a new language or tool. With each release of CybOX, the CybOX
project provides a [samples download
bundle](http://cybox.mitre.org/language/version2.1/#samples) for just that
reason, containing short, use-case driven samples.

## Next Steps
Once you understand the core concepts of how CybOX works and have either the
schemas or the documentation so you can look up any data model questions, there
are a couple options for where to look next:

* If you're interested in user-level tooling and programmatic support, go to
  the [Tools](/documentation/tools) page
* Finally, if you want to get started creating content, you want the
  [Suggested Practices](/documentation/suggested-practices).
* Have a question? It may already have an answer at our
  [FAQs](http://cybox.mitre.org/about/faqs.html)
