---
layout: flat
title: About CybOX
---

## The Challenge
The concept of observable events or properties in the operational cyber realm is a central underlying element of many of the different activities involved in cybersecurity. Before CybOX, there was no uniform standard mechanism for specifying, capturing, characterizing, or communicating these cyber observables. Each activity area, each use case, and often each supporting tool vendor would use its own unique approach. This inhibited consistency, efficiency, interoperability, and overall situational awareness. CybOX solves these problems.

## What Is CybOX?
[Cyber Observable eXpression (CybOX™)](http://cyboxproject.github.io/releases/2.1/) is a standardized language for encoding and communicating high-fidelity information about cyber observables. 

CybOX is not targeted at a single cyber security use case, but rather is intended to be flexible enough to offer a common solution for all cybersecurity use cases requiring the ability to deal with cyber observables. It is also intended to be flexible enough to allow both the high-fidelity description of instances of cyber observables that have been measured in an operational context, as well as more abstract patterns for potential observables that may be targets for observation and analysis apriori. 

By specifying a common structured schematic mechanism for these cyber observables, CybOX enables the potential for detailed automatable sharing, mapping, detection, and analysis heuristics.

Through utilization of the standardized CybOX Language, relevant observable events or properties can be captured and shared, defined in indicators and rules, or used to adorn the appropriate portions of attack patterns and malware profiles in order to tie the logical pattern constructs to real-world evidence of their occurrence or presence for attack detection and characterization. Incident response and management can then take advantage of all of these capabilities to investigate occurring incidents, improve overall situational awareness, and improve future attack detection, prevention, and response.

## What Can CybOX Do?

- Threat intelligence
- Malware characterization
- Security operations
- SIEM / Logging
- Incident response
- Indicator sharing
- Digital forensics

>  CybOX allows organizations to share indicators and detections for incoming computer network attacks in a standard format.

## CybOX Community
CybOX has been transitioned to [OASIS](https://www.oasis-open.org/committees/cti). See the [Community](http://cyboxproject.github.io/community/) page for details. 

Some shortcuts:  

[OASIS Cyber Threat Intelligence (CTI) Technical Committee (TC)](https://www.oasis-open.org/committees/cti) - CybOX is developed by the CybOX subcommittee of the CTI TC. 

[Mailing Lists](http://cyboxproject.github.io/community/#discussion-lists-amp-archives) - Stay up-to-date on development and usage. 

[Developer Resources](https://cyboxproject.github.io/documentation/tools/) - The central location for development of the specifications, tools, and documentation (including this site). 

## Frequently Asked Questions

Answers to general questions about CybOX are included below. Please see the [CybOX Language FAQs](http://cyboxproject.github.io/faqs/) for answers to commonly asked questions about the CybOX Language.

###  What are "cyber observables"?

Cyber observables are events or stateful properties that occur, or may occur, in the operational cyber domain, such as the value of a registry key, deletion of a file, or the receipt of an http GET.

### Why CybOX? Is there a lot of support for something like this?

CybOX was developed to promote consistent capture of cyber observable content and to standardize the transfer of this information across the entire spectrum of security activities, tools and services. It was developed as a foundational language for describing many base level system and network elements that are used in higher level schemas, languages, and conventions, such as the [Structured Threat Information eXpression (STIX™)](https://stixproject.github.io/), [Common Attack Pattern Enumeration and Classification (CAPEC™)](https://capec.mitre.org/), and [Malware Attribute Enumeration and Characterization (MAEC™)](https://maecproject.github.io/). It is an international cybersecurity community effort developed by a broad spectrum of industry, academia, and government organizations from around the world.

### What is the difference between "cyber observables" and "cyber indicators"?

Cyber observables are statements of fact; they capture what was observed or could be observed in the cyber operational domain. Cyber indicators are cyber observable patterns with relevant contextual information that provide meaning and guidance around the observable patterns, such as a registry key value associated with a known bad actor or a spoofed email address used on this date and sent to these accounts on this date.

### Which areas of cybersecurity does CybOX address?

CybOX supports a wide range of relevant cybersecurity domains including: threat assessment and characterization (detailed attack patterns), malware characterization, operational event management, logging, cyber situational awareness, incident response, indicator sharing, digital forensics, and more.

### How can CybOX help me?

CybOX provides a common language for describing observable events or objects that occur within the operational cyber domain. The CybOX Language and supporting schemas provide a common, structured format for characterizing cyber observables and facilitating automation in the processing and use of such observables.

### How is CybOX licensed?

See the [Terms of Use](https://cyboxproject.github.io/tou.html).

## Relationships to Other Efforts

### STIX

[Structured Threat Information eXpression (STIX™)](https://stixproject.github.io/) is a structured language for describing cyber threat information so it can be shared, stored, and analyzed in a consistent manner. STIX uses the CybOX Language to describe cyber observables. The CybOX schema is natively imported and used within STIX to characterize system and network events and behaviors observed within the operational cyber domain or observable patterns for use within cyber indicators.

### MAEC

[Malware Attribute Enumeration and Characterization (MAEC™)](https://maecproject.github.io/) is a standardized language for encoding and communicating high-fidelity information about malware based upon attributes such as behaviors, artifacts, and attack patterns. MAEC uses the CybOX Language to describe cyber observables. The CybOX schema is imported and used within MAEC to characterize malware-related system and network events and behaviors observed within the operational cyber domain.

### CAPEC

[Common Attack Pattern Enumeration and Classification (CAPEC™)](https://capec.mitre.org/) is a publicly available, community-developed list of common attack patterns along with a comprehensive schema and classification taxonomy. The CybOX schema is imported and used within CAPEC to characterize system and network events and behaviors observed within the operational cyber domain.

### TAXII

[Trusted Automated eXchange of Indicator Information (TAXII™)](http://taxiiproject.github.io/) is the main transport mechanism for cyber threat information represented in STIX. Through the use of TAXII services, organizations can share cyber threat information in a secure and automated manner. TAXII uses STIX to represent cyber threat information in a standardized and structured manner, and STIX uses CybOX to represent cyber observables.

