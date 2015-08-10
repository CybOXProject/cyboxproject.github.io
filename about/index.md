---
layout: flat
title: About CybOX
---

## The Challenge
The concept of observable events or properties in the operational cyber realm is a central underlying element of many of the different activities involved in cyber security. Today, there exists no uniform standard mechanism for specifying, capturing, characterizing or communicating these cyber observables. Each activity area, each use case and often each supporting tool vendor uses its own unique approach that inhibits consistency, efficiency, interoperability and overall situational awareness.

## What is CybOX?
The Cyber Observable eXpression (CybOX™) is a standardized language for encoding and communicating high-fidelity information about cyber observables. CybOX is not targeted at a single cyber security use case but rather is intended to be flexible enough to offer a common solution for all cyber security use cases requiring the ability to deal with cyber observables. It is also intended to be flexible enough to allow both the high-fidelity description of instances of cyber observables that have been measured in an operational context as well as more abstract patterns for potential observables that may be targets for observation and analysis apriori. By specifying a common structured schematic mechanism for these cyber observables, the intent is to enable the potential for detailed automatable sharing, mapping, detection and analysis heuristics.

Through utilization of the standardized CybOX language, relevant observable events or properties can be captured and shared, defined in indicators and rules or used to adorn the appropriate portions of attack patterns and malware profiles in order to tie the logical pattern constructs to real-world evidence of their occurrence or presence for attack detection and characterization. Incident response and management can then take advantage of all of these capabilities to investigate occurring incidents, improve overall situational awareness and improve future attack detection, prevention and response.

## What can CybOX do?

- Threat intelligence
- Malware characterization
- Security operations
- SIEM / Logging
- Incident response
- Indicator sharing
- Digital forensics

>  CybOX allows organizations to share indicators and detections for incoming computer network attacks in a standard format.

## Frequently Asked Questions

Captured here are some common questions and answers relating to CybOX. Please see the [FAQs](/documentation/faqs) page for other questions/answers.

###  What are "cyber observables"?

Cyber observables are events or stateful properties that occur, or may occur, in the operational cyber domain, such as the value of a registry key, deletion of a file, or the receipt of an http GET.

### Why CybOX? Is there a lot of support for something like this?

CybOX was developed to promote consistent capture of cyber observable content and to standardize the transfer of this information across the entire spectrum of security activities, tools and services. It was developed as a foundational language for describing many base level system and network elements that are used in higher level schemas, languages, and conventions, such as the Structured Threat Information eXpression (STIX™), the Common Attack Pattern Enumeration and Classification (CAPEC™), and the Malware Attribute Enumeration and Characterization (MAEC™). It is an international, information security, community effort developed by a broad spectrum of industry, academia, and government organizations from around the world.

### What is the difference between "cyber observables" and "cyber indicators"?

Cyber observables are statements of fact; they capture what was observed or could be observed in the cyber operational domain. Cyber indicators are cyber observable patterns with relevant contextual information that provide meaning and guidance around the observable patterns, such as a registry key value associated with a known bad actor or a spoofed email address used on this date and sent to these accounts on this date.

### Which areas of cyber security does CybOX address?

CybOX supports a wide range of relevant cyber security domains including: threat assessment and characterization (detailed attack patterns), malware characterization, operational event management, logging, cyber situational awareness, incident response, indicator sharing, digital forensics, and more.

### How can CybOX help me?

CybOX provides a common language for describing observable events or objects that occur within the operational cyber domain. The CybOX Language and supporting schemas provide a common, structured format for characterizing cyber observables and facilitating automation in the processing and use of such observables.

### How is CybOX licensed?

See the [Terms of Use](http://cybox.mitre.org/about/termsofuse.html).

## Relationships to Other Efforts

### STIX

The Structured Threat Information eXpression (STIX™) uses the CybOX Language to describe cyber observables. The CybOX schema is natively imported and used within STIX to characterize system and network events and behaviors observed within the operational cyber domain or observable patterns for use within cyber indicators.

### MAEC

The Malware Attribute Enumeration and Characterization (MAEC™) is a standardized language for encoding and communicating high-fidelity information about malware based upon attributes such as behaviors, artifacts, and attack patterns. MAEC uses the CybOX Language to describe cyber observables. The CybOX schema is imported and used within MAEC to characterize malware-related system and network events and behaviors observed within the operational cyber domain.

### CAPEC

The Common Attack Pattern Enumeration and Classification (CAPEC™) is a publicly available, community-developed list of common attack patterns along with a comprehensive schema and classification taxonomy. The CybOX schema is imported and used within CAPEC to characterize system and network events and behaviors observed within the operational cyber domain.

### TAXII

The Trusted Automated eXchange of Indicator Information (TAXII™) is a related U.S. Department of Homeland Securityâ€“led effort of the office of Cybersecurity and Communications to securely share automated cyber threat information. TAXII uses the Structured Threat Information eXpression (STIX™) to represent cyber threat information in a standardized and structured manner, and STIX uses CybOX to represent cyber observables.

