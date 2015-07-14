---
layout: flat
title: Use Cases
---
CybOX provides a common foundation for all cyber security use cases requiring the ability to deal with cyber observables. CybOX is flexible, and directly supports use case domain-specific standards and solutions by providing them with a unified and consistent foundational definition of cyber observables. For most use cases, the utilization of CybOX should be indirect with primary focus on the use case domain-specific standard or solution which leverages CybOX as an enabler.

CybOX adheres to the following principles for scoping of informational content:

* Informational content regarding cyber observables is included in CybOX if it is of general use to multiple use cases and is not in conflict with any specific supported use cases.
* Informational content regarding cyber observables that is specific to a single supported use case domain should be managed in a use case domain specific standard or solution that leverages CybOX for all general cyber observable informational content.

Flexible extension mechanisms are incorporated into CybOX to support this sort of use by use case domain-specific standards and solutions.

The following table lists a sampling of some of the current use cases targeted by CybOX and some of the primary CybOX-leveraging use case domain-specific standards and solutions available for each use case.

|Supported Use Case|Relevant Process|Domain Specific Standard|
|------------------|----------------|------------------------|
|Analyze event data from diverse set of sensors of different types and different vendors|Event Management|CybOX|
|Detect malicious activity utilizing attack patterns|Attack Detection|[Common Attack Pattern Enumerationand Classification (CAPEC™)](http://capec.mitre.org)|
|Detect malicious activity utilizing malware behavior characterizations|Attack Detection|[Malware Attribute Enumeration and Characterization (MAEC™)](http://maec.mitre.org)|
|Enable automated attack detection signature rule generation|Attack Detection|CybOX, MAEC, CAPEC, [Structured Threat Information eXpression (STIX™)](http://stix.mitre.org)|
|Characterize malicious activity utilizing attack patterns|Incident Response/Management|CAPEC, STIX|
|Identify new attack patterns|Threat Characterization|CAPEC|
|Prioritize existing attack patterns based on tactical reality|Security Testing and Secure Development|CAPEC, STIX|
|Characterize malware behavior|Malware Analysis|MAEC|
|Guide malware analysis utilizing attack patterns|Malware Analysis|MAEC, CAPEC|
|Detect malware effects|AttackDetection and Incident Response/Management|[Open Vulnerability and Assessment Language (OVAL®)](http://oval.mitre.org/), MAEC, STIX|
|Enable collaborative attack indicator sharing|Information Sharing||
|Empower and guide incident management utilizing attack patterns and malware characterizations|Incident Response/Management|STIX, CAPEC, MAEC, CybOX|
|Enable consistent, useful and automation-capable incident alerts|Incident Response/Management|STIX, MAEC, CAPEC|
|Enable automatic application of mitigations specified in attack patterns|Incident Response/Management|STIX|
|Enable incident information sharing|Incident Response/Management|STIX|
|Support correlation between observed properties and malicious indicators as part of digital forensics|Digital Forensics|[Digital Forensics XML (DFXML)](http://www.forensicswiki.org/wiki/Category:Digital_Forensics_XML), STIX, MAEC, CAPEC|
|Capture digital forensics analysis results|Digital Forensics|DFXML|
|Capture digital forensics provenance information|Digital Forensics|DFXML|
|Enable collaborative sharing of digital forensics information|Digital Forensics|DFXML|
|Enable explicit and implicit sharing controls for cyber observable information|Information Sharing|STIX, CybOX, [Trusted Automated eXchange of Indicator Information (TAXII™)](http://taxii.mitre.org/)|
|Enable new levels of meta-analysis onoperational cyber observables|Cyber Situational Awareness|CybOX, STIX|


