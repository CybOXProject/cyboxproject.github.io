---
layout: flat
title: Versioning Policy
---
This document details the current methodology for determining whether a new revision will require a major version change, minor version change, or a version update, and how version information is represented and conveyed in the CybOX Language.

Versioning for the four broad categories of the CybOX Language schemas:

* "CybOX Core," which consists of the cybox_core.xsd and cybox_common.xsd schemas. 
* "CybOX Objects," which consists of all the Object schema files located within the "objects" directory. 
* "CybOX Vocabularies," which consists of the cybox_default_vocabularies.xsd schema. 
* "CybOX Extensions," which consists of all the schema files located within the "extensions" directory — is also included. 

### CybOX Language Versioning
The version number is formatted as: ‘Major.Minor.Update’. The Update value may be omitted if it is 0.

**Major Version** — A major release is for adding features that require breaking backward compatibility with previous versions or represent fundamental changes to concepts. For a major release, the MAJOR component is incremented by one and the MINOR and UPDATE components are set to zero.

**Minor Version** — A minor release is for adding features that do not break backward compatibility with previous versions. For a minor release, the MINOR component is incremented by one and the UPDATE component is set to zero.

**Update Version** — An update release may only be initiated to address critical defects that affect usability. Fixes may break backward compatibility if necessary. New functionality outside of what was intended in the previous MAJOR.MINOR release is not permitted. However, once an update release is agreed to, other non-critical fixes and clarifications may be addressed. When an update version change is made, the UPDATE component is incremented by one.

A particular release of the CybOX Language (i.e., a specific version) pins the following:

* The Major, Minor, and Update values of the CybOX Core. The version of these schema files is always identical to the version of the CybOX Language they support.
* A list of supported CybOX Objects and the Major, Minor, and Update values of those supported CybOX Objects. The version of these Object files usually differs from the version of the CybOX Language that uses them.
* The Major and Minor values of the CybOX Vocabularies schema. The Major and Minor version of the CybOX Vocabularies schema is always identical to the Major and Minor version of the CybOX Language in which it is used. The Update value of the CybOX Vocabularies may differ from the Update value of the overall CybOX Language in which it is used.
* A list of recommended CybOX Extension schemas and the Major, Minor, and Update version of those schemas. The version of individual Extension schemas usually differs from the version of the CybOX Language that recommends their use.

In all cases, the XML namespace of an XML file includes the major version of that file. The XML namespace of a schema does not change under a Minor or an Update revision.

#### CybOX Core Versioning
The CybOX Core (cybox_core.xsd and cybox_common.xsd schemas) is always versioned in lock-step with the CybOX Language. These files always have the same version as each other, and always have the same version as the CybOX Language overall.

#### CybOX Object Versioning
CybOX Objects are versioned independently of each other and independently of the CybOX Language. Each version of the CybOX Language indicates the list of supported Object schemas and the version for each of these Object schemas.

Most Object schemas will probably remain unchanged across revisions of the CybOX Language, with both the old and new version of the CybOX Language supporting the same version of the Object schema.In most cases where an Object schema is revised, the new versions of the Object schema is released simultaneously with a new release of the CybOX Language, although the Object’s schema version will differ from the CybOX Language version.

On rare occasions, a new version of a CybOX Object schema might be released outside of a release of the CybOX Language. However, this new version of the CybOX Object is not associated with any version of the CybOX Language until there is a new CybOX Language release that utilizes this new Object schema.
Tools that support a given version of the CybOX Language are not required to support every type of CybOX Object associated with that version of the CybOX language. However, for CybOX Objects that such tools do support, they must support the specific version of those Objects associated with the supported version of the CybOX Language. Tools may support older and/or newer versions of those same Objects, but are not required to do so.

Note that, in CybOX, objects are considered extension points. As such, authors can utilize custom CybOX Objects other than those associated by a given release. However, this is considered to be a customized use of the CybOX Language and compatibility is not guaranteed. Any use of a CybOX Object version other than the specific version associated with a particular CybOX Language release (i.e., an Object that is either an earlier version or a later version) is considered a customized use of CybOX with the associated compatibility risks.

#### CybOX Vocabularies Versioning
The CybOX Vocabularies (in cybox_default_vocabularies.xsd) represent a set of default controlled vocabularies for use in CybOX content. These vocabularies are broken out from the CybOX Core schemas to support customized extension and replacement of these vocabularies in content. Nonetheless, it is expected that most CybOX authors will utilize the provided default vocabularies, and most tools that parse CybOX should support those vocabularies where appropriate.

Any individual CybOX vocabulary may be revised at any time, including between releases of the CybOX Language. Authors and tools may begin utilizing this new vocabulary immediately.

To facilitate this, each version of a given controlled vocabulary (an XML SimpleType that resolves to an enumeration) is assigned a different version number. An individual vocabulary has a Major and Minor version number, but no Update number. For a vocabulary:

* A "Minor revision" is associated with the addition of one or more terms to the vocabulary. Thus any content created using the previous version of the vocabulary is still valid using the new vocabulary.
* A "Major revision" is associated with the removal or modification of one or more terms in the vocabulary (possibly along with the addition of one or more other terms). Thus, some content using the old vocabulary might no longer be valid when using the new vocabulary. When the Major version number is incremented, the Minor number is set to 0.
* The version of the vocabulary is appended to the end of the name of the XML type that defines that vocabulary. Specifically, all types used to define a controlled vocabulary end in "-Major.Minor" where Major is the vocabulary’s Major number and Minor is the vocabulary’s Minor number. For example, version 1.3 of the Object State controlled vocabulary has the name ObjectStateVocab-1.3 and uses the ObjectStateEnum-1.3 enumeration. If new terms are added to this vocabulary, new types are created with the names of ObjectStateVocab-1.4 and ObjectStateEnum-1.4. If terms are deleted from the vocabulary, new types are created with the names of ObjectStateVocab-2.0 and ObjectStateEnum-2.0.

Every time any of the vocabularies in cybox_default_vocabularies.xsd changes, the Update number of the schema’s @version attribute increments. The Major and Minor numbers of the schema’s version only change in conjunction with a Major or Minor revision to the CybOX Language, and always match the Major and Minor numbers of the CybOX Language in which it is used. A change to the Update number in the CybOX Language does not impact the version of the cybox_default_vocabularies.xsd schema.

Within a single Major release of the CybOX Language, the cybox_default_vocabularies.xsd contains every version of all of the controlled vocabularies that were defined. Thus, if the Object State controlled vocabulary went through version 1.0, 1.1, 2.0, and 2.1 all within version 2.* of the CybOX Language, the cybox_default_vocabularies.xsd schema contains all of the following XML types:

* ObjectStateVocab-1.0 and ObjectStateEnum-1.1
* ObjectStateVocab-1.1 and ObjectStateEnum-1.0
* ObjectStateVocab-2.0 and ObjectStateEnum-2.0
* ObjectStateVocab-2.1 and ObjectStateEnum-2.1

This means that a single version of cybox_default_vocabularies.xsd can be used to validate content that uses any version of a supported vocabulary up to and including the latest version of the given vocabulary present in the schema file within any Major version of CybOX. In the case of a Major revision of CybOX, older versions of vocabularies may be removed. However, the individual version numbers of vocabularies do not reset when this happens. E.g., if the Object State controlled vocabulary was on revision 2.1 (ObjectStateVocab-2.1 and ObjectStateEnum-2.1) and then there was a major revision to CybOX to 3.0, the new version of the cybox_default_vocabularies.xsd is assigned version 3.0 and might not contain types for previous versions of the Object State vocabulary, but the Object State vocabulary is still in version 2.1, and is represented by the types ObjectStateVocab-2.1 and ObjectStateEnum-2.1.

For a given version of the CybOX Language, use of any version of a controlled vocabulary within a cybox_default_vocabularies.xsd associated with that Language version. That is, authors may use version 1.2 of a particular vocabulary and be considered compliant with the CybOX Language even if the latest version of that vocabulary for that Language version is version 1.4. However, authors should be aware that there may be differences in support for various versions of the CybOX default vocabularies even between tools that support the same version of the CybOX Language.

As noted earlier, controlled vocabularies are considered extension points and the default vocabularies can be extended or replaced by authors. However, in doing this the author is considered to be utilizing a customized version of the CybOX Language and might encounter compatibility issues.

#### CybOX Extension Versioning
The CybOX Extensions schemas are used for structured representation of data using externally defined schemas. For example, there is an extension schema that allows for the identification of software and hardware platforms using the U.S. National Institute of Standards and Technology’s (NIST) Common Platform Enumeration (CPE) Applicability Language schema. Rather than importing these schemas directly into CybOX, these external schemas are captured in CybOX Extension schemas, which can be hooked into CybOX at certain defined extension points.

The CybOX Extension schemas represent the recommended way of structuring certain information using existing, externally defined XML schemas (following CybOX’s design objective of "reuse rather than reinvent"). However, no author is ever required to use any of the recommended extension schemas nor are tools required to process those extension schemas. No use case of CybOX requires the use of extension schemas, although authors may wish to use them to achieve greater expressivity in certain situations.

Each CybOX Extension schema is versioned independently. Releases of revised extension schemas usually, but not always, coincide with a revision of the CybOX Language. A given release of the CybOX Language contains recommendations as to the CybOX Extension schemas to use for certain purposes. This recommendation includes the Major, Minor, and Update numbers for each of those extension schemas.

Extension schemas, as the name indicates, represent extension points in the CybOX Language. Instead of using one of the recommended extension schemas, authors may define their own extension schemas. The use of custom extension schemas is considered to be utilizing a customized version of the CybOX Language and might result in compatibility issues.

