---
layout: flat
title: Suggested Practices
---

This page contains suggested practices for developing and consuming CybOX
content. There's a [similar page](https://stixproject.github.io/documentation/suggested-practices/) for STIX.

Note that these are simply suggested practices. In many cases, operational or
technical concerns may prohibit you from implementing them or they may just not
make sense in your situation. That's perfectly fine, these are just
suggestions.

# General Practices

## Formatting IDs
CybOX IDs are [XML QNames](http://en.wikipedia.org/wiki/QName). Each ID
includes both a namespace portion (optional) and an ID portion (required)
separated by a colon (:). The recommend approach to creating CybOX IDs is to
define a producer namespace and namespace prefix, then use the form:

`[ns prefix]:[construct type]-[GUID]`

The "ns prefix" should be a namespace prefix bound to a namespace
owned/controlled by the producer of the content.

Some examples:

```
acme:event-ce431003-ad07-4c96-bd7a-a50a3196e2a0
acme:action-bf8bc5d5-c7e6-46b0-8d22-7500fea77196
acme:observable-79090715-8d6a-46b7-943b-c0bb9e063788
acme:fileobj-965e1140-2c22-4408-a423-b7acc08290a7
```

In order to use this approach, you will need to define that namespace prefix in
the head of your XML document:

```xml
<cybox:Observables xmlns:acme="http://acme.example.com" ...
```

This format provides high assurance that IDs will be both unique and
meaningful, because the producer namespace denotes who's producing it, the
construct name denotes what it is, and the GUID guarantees uniqueness.

When generating CybOX Observables and Objects from source data that contains
identification information, CybOX authors should record the mapping of their
source IDs to their newly generated CybOX IDs using some storage mechanism
outside of CybOX (e.g., a database). This will allow authors to quickly refer
to and/or alter source data when new information regarding a particular CybOX
Observable or Object presents itself in the future. Newly generated IDs may
contain a namespace prefix which refers to the source vendor or tool used to
generate the source data.

## Referencing vs. Embedding
In many cases, you'll have an option to either include a component (an object,
for example) within the parent component or to reference the component by ID to
a representation in a global location.

For example, an Object can include Related Objects. One way of doing this is to
include the related object inline in the parent object:

```xml
<cybox:Object id="acme:fileobj-f7304dae-94c6-4592-b943-398e1e6916a7">
  <cybox:Properties xsi:type="FileObj:FileObjectType">
    <!-- SNIP -->
  </cybox:Properties>
  <cybox:Related_Objects>
    <cybox:Related_Object id="acme:mutexobj-3c1221bd-2037-45ec-8129-4ba8d791e86b">
      <cybox:Properties xsi:type="MutexObj:MutexObjectType">
        <!-- SNIP -->
      </cybox:Properties>
    <cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.0">Created</cybox:Relationship>
  </cybox:Related_Object>
</cybox:Object>
```

The other alternative is to reference that TTP, which would be represented
elsewhere:

```xml
<cybox:Object id="acme:fileobj-f7304dae-94c6-4592-b943-398e1e6916a7">
  <cybox:Properties xsi:type="FileObj:FileObjectType">
    <!-- SNIP -->
  </cybox:Properties>
  <cybox:Related_Objects>
    <cybox:Related_Object idref="acme:mutexobj-3c1221bd-2037-45ec-8129-4ba8d791e86b" />
    <cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.0">Created</cybox:Relationship>
  </cybox:Related_Object>
</cybox:Object>
```

These situations are a judgment call, but when making that judgment you should
consider whether the related construct (object in this case) has value
individually or only within the context of the parent? If it only has value in
the parent, embedding it may be appropriate. Otherwise it's probably better to
reference it. If you're unsure, it's generally safer to reference it.

## Creating References
When creating references, you'll use the idref attribute:

```xml
<cybox:Related_Object idref="acme:mutexobj-3c1221bd-2037-45ec-8129-4ba8d791e86b" />
```

When using this idref attribute, you should avoid putting any other attributes
or elements in the reference element.

## Creating documents for human consumption
These suggestions only apply when you're creating documents you intend to be
human-readable. They simply make the document more readable and easy to
validate by XML editors but are not important for automated processing.

For best readability:

* Only include necessary namespaces
* Use the namespace prefixes as defined in the schemas
* Affinity-group or alphabetize namespaces
* Do not include attributes that have default attributes if you're simply setting the attribute to the default (i.e. @negate on indicators).

To ease validation in XML editors:

* Include schemaLocation attributes to the hosted versions of the CybOX schemas

## Using Vocabularies
Many places in CybOX use controlled vocabularies to represent data. When
possible, you should use the vocabularies included in the CybOX defaults. If
necessary you can use your own vocabulary or even use strings outside of any
vocabularies.

If you do this to add values that you think might be useful for other CybOX
users, you should let us know so we can consider adding it to the default
vocabulary.

## Creating Timestamps
To remove ambiguity regarding the timezone, all times should include an
explicit timezone if possible.

# Specific Elements

## Observables

### Pattern vs. Instance
CybOX observables are capable of representing both instance observables
(specific events or properties that were observed) or pattern observables
(patterns of events or properties that may potentially be observed). The
conditional nature of patterns is expressed through the use of the @condition
attribute on the fields within the observable. If the @condition attribute is
set, that denotes that the field is part of a pattern.

Because it doesn't make sense to mix pattern fields with instance field, if
@condition is set on any fields it should be set on all fields. You should not
mix and match fields with @condition set and fields without @condition set.

## Objects

### CybOX Object selection

CybOX Object schemas define sets of properties for common cyber objects. CybOX provides an extensive set of pre-defined Objects.  This predefined set includes a broad range of object types across the cyber domain (network, host, files, memory, devices, etc.) as well as objects of varying levels of specificity/abstraction intended for differing use cases.  The set of CybOX objects is designed to be extensible, allowing the definition of new object types, if required.  CybOX objects can build on other CybOX objects using one or both of the following mechanisms:

* Inheritance/Derivation:  Objects that derive from other Objects.
 * For example, **File -> Win File -> Win EXE File** where CybOX defines a basic [File Object] ({{site.stix_url}}/FileObj/FileObjectType) with general file properties applicable across platforms, a more specific [Win_File Object] ({{site.stix_url}}/WinFileObj/WindowsFileObjectType) that extends the general File Object and adds Windows-specific file properties, and an even more specific [Win_Executable_File Object] ({{site.stix_url}}/WinExecutableFileObj/WindowsExecutableFileObjectType) which extends the Win_File Object and adds properties for executable files under Windows.
* Composition: Objects that incorporate other Objects to define more specific properties for differing and more specialized use cases.
  * For example, the set of Objects specified that can contain an **IP Address**.
    * [Address Object] ({{site.stix_url}}/AddressObj/AddressObjectType) enables the specification of a particular IP Address (or other type of address) value and its type (e.g. ipv4-addr) without any other context. This can be used when you desire to characterize an IP Address but not to assert any given context for where you might find it (e.g. it may appear in any of a wide variety of logs). This Object also provides consistent specification of address properties for its use on its own or by more specific Objects that need to characterize addresses within more specific contexts.
    * [Socket_Address Object] ({{site.stix_url}}/SocketAddressObj/SocketAddressObjectType) enables the specification of a particular IP Address (or Hostname) and Port pairing. This obviously lets you characterize a more specific context for an IP Address but still leverages the AddressObjectType for its IP Address structure yielding consistency across the two Objects.
    * [Network_Connection Object] ({{site.stix_url}}/NetworkConnectionObj/NetworkConnectionObjectType) enables the specification of properties related to a network connection including Layer3, Layer4 and Layer7 details as well as details of the source socket and destination socket of the connection. This object leverages the SocketAddressType for its source and destination socket structures. This enables the characterization of very specific contextual details around an IP Address.
 

**It is suggested practice to always utilize the most specific CybOX Object possible for the context you are looking to convey and based on the properties you need to represent.**

* For example, if you know you are looking to describe a situation of network traffic to a particular IP Address, use the Network_Connection Object but if all you know is that an IP Address was seen or might be seen but you have no further context, use the Address Object. This also applies to the use of platform-agnostic Objects (e.g. File) and their derived platform-specifc Objects (e.g. Win_File). If you need to characterize properties from a more specific variation of an Object (e.g. the SID of a file), utilize that Object (e.g. Win_File) otherwise use the simplest version available that supports the properties you need to characterize.

**One clear exception to this is if conformance to a specific language Profile is required and that Profile restricts the set of available objects or directly specifies a particular Object to be used.**


###Common Object-to-Object Relationships

CybOX supports a broad range of Object types and provides the capability to relate/associate Objects together along with a characterization of how they are related. 

To encourage consistency in the characterization of relationships between Objects, CybOX provides a default controlled vocabulary ([ObjectRelationshipVocab-1.1](http://stixproject.github.io/data-model/1.1.1/cyboxVocabs/ObjectRelationshipVocab-1.1/)) for use with the Relationship field. This vocabulary contains a broad range of values to characterize many of the potentially relevant Object-to-Object relationships.

####Suggested vocabulary values to use in some of the more common Object-to-Object relationship usage scenarios include:

**Network-centric Object relationships:**


* **When you want to talk about an association pairing between a network naming structure (e.g. Domain or Hostname) and an IP Address it resolves to**
  * [Domain_Name Object](http://stixproject.github.io/data-model/1.1.1/DomainNameObj/DomainNameObjectType/) -> [Address Object](http://stixproject.github.io/data-model/1.1.1/AddressObj/AddressObjectType/)   (Relationship = “**Resolved_To**”)
  * Address Object -> Domain_Name Object   (Relationship = “**Resolved_To**”)
  * [Hostname Object](http://stixproject.github.io/data-model/1.1.1/HostnameObj/HostnameObjectType/) -> Address Object   (Relationship = “**Resolved_To**”)
  * Address Object -> Hostname Object   (Relationship = “**Resolved_To**”)
* **When you want to talk about the association between an IP Address and an Autonomous System**
      * Address Object -> [AS Object](http://stixproject.github.io/data-model/1.1.1/ASObj/ASObjectType/) (Relationship = “**Contained_By**”)
      * AS Object -> Address Object (Relationship = “**Contains**”)
* **When you want to talk about the association between a  network naming structure (e.g. Domain or Hostname) and a Whois response**
      * Domain_Name Object -> [Whois Object](http://stixproject.github.io/data-model/1.1.1/WhoisObj/WhoisObjectType/)   (Relationship = “**Characterized_By**”)
      * Whois Object -> Domain_Name Object   (Relationship = “**Characterizes**”)
      * Hostname Object -> Whois Object   (Relationship = “**Characterized_By**”)
      * Whois Object -> Hostname Object    (Relationship = “**Characterizes**”)
* **When you want to talk about the association between a network naming structure (e.g. Domain or Hostname) and a DNS Query**
      * Domain_Name Object -> [DNS_Query Object](http://stixproject.github.io/data-model/1.1.1/DNSQueryObj/DNSQueryObjectType/) Object   (Relationship = “**Properties_Queried_By**”)
      * DNS_Query Object -> Domain_Name Object   (Relationship = “**Properties_Queried**”)
      * Hostname Object -> DNS_Query Object   (Relationship = “**Properties_Queried_By**”)
      * DNS_Query Object -> Hostname Object    (Relationship = “**Properties_Queried**”)
* **When you want to talk about the association between a network naming structure (e.g. Domain or Hostname) and a DNS Record**
      * Domain_Name Object -> [DNS_Record Object](http://stixproject.github.io/data-model/1.1.1/DNSRecordObj/DNSRecordObjectType/)   (Relationship = “**Characterized_By**”)
      * DNS_Record Object -> Domain_Name Object   (Relationship = “**Characterizes**”)
      * Hostname Object -> DNS_Record Object   (Relationship = “**Characterized_By**”)
      * DNS_Record Object -> Hostname Object    (Relationship = “**Characterizes**”)
* **When you want to talk about the association between a DNS Record and a resolving IP Address within that record**
      * DNS_Record Object -> Address Object    (Relationship = “**Contains**”)
      * Address Object -> DNS_Record Object    (Relationship = “**Contained_Within**”)
* **When you want to talk about the association between a DNS Query and a DNS Record that resulted from the query**
      * DNS_Query Object -> DNS Record Object    (Relationship = “**Searched_For**”)
      * DNS_Record Object -> DNS_Query Object    (Relationship = “**Searched_For_By**”)
* **When you want to talk about the association between a URL and the Domain contained within it**
      * [URI Object](http://stixproject.github.io/data-model/1.1.1/URIObj/URIObjectType/) - > Domain_Name Object    (Relationship = “**Contains**”)
      * Domain_Name Object - > URI Object    (Relationship = “**Extracted_From**”)
* **When you want to talk about the association between one Domain and another Domain that is a sub-part of it**
      * Domain_Name Object (supra) -> Domain_Name Object (sub)    (Relationship = “**Supra-domain_Of**” or “**FQDN_Of**” depending on context)
      * Domain_Name Object (sub) -> Domain_Name Object (supra)    (Relationship = “**Sub-domain_Of**”)

**Host-centric Object relationships:**


* **When you want to talk about the association between the characteristics of a File and the actual bits of the file**
      * [File Object](http://stixproject.github.io/data-model/1.1.1/FileObj/FileObjectType/) -> [Artifact Object](http://stixproject.github.io/data-model/1.1.1/ArtifactObj/ArtifactObjectType/) (Relationship = “**Characterizes**”)
      * Artifact Object -> File Object (Relationship = “**Characterized_By**”)
* **When you want to talk about the association between an Email and characteristics of a file attachment to the email**
      * [Email_Message Object](http://stixproject.github.io/data-model/1.1.1/EmailMessageObj/EmailMessageObjectType/) -> File Object (Relationship = “**Contains**”)
      * File Object -> Email_Message Object (Relationship = “**Contained_Within**”)
* **When you want to talk about the association between an Email and the actual bits of a file attachment to the email**
      * Email_Message Object -> Artifact Object (Relationship = “**Contains**”)
      * Artifact Object -> Email_Message Object (Relationship = “**Contained_Within**”)
* **When you want to talk about the association between an Email and a Link (URL) within the Email**
      * Email_Message Object -> [Link](http://stixproject.github.io/data-model/1.1.1/LinkObj/LinkObjectType/) Object (Relationship = “**Contains**”)
      * Link Object -> Email_Message Object (Relationship = “**Contained_Within**”)
* **When you want to talk about the association between a File and another File contained within it**
      * File Object (outer) -> FileObject (inner) (Relationship = “**Contains**”)
      * File Object (inner) -> File Object (outer) (Relationship = “**Contained_Within**”)
* **When you want to talk about the association between a File and another File that it places on a system**
      * File Object (dropper) -> FileObject (dropped file) (Relationship = “**Dropped**”)
      * File Object (dropped file) -> File Object (dropper) (Relationship = “**Dropped_By**”)
* **When you want to talk about the association between a File and the URL, Domain or Hostname from which it was downloaded**
      * File Object - > URI Object    (Relationship = “**Downloaded_From**”)
      * URI Object - > File Object    (Relationship = “**Downloaded**”)
      * File Object - > Domain_Name Object    (Relationship = “**Downloaded_From**”)
      * Domain_Name Object - > File Object    (Relationship = “**Downloaded**”)
      * File Object - > Hostname Object    (Relationship = “**Downloaded_From**”)
      * Hostname Object - > File Object    (Relationship = “**Downloaded**”)



### Capturing Custom Tool Properties
Sometimes, a tool will capture properties about a CybOX object that aren't in
the schema for that object type. In some cases this is because the schemas need
to be expanded to cover that property, but in other cases this is because the
tool is collecting derived information or other properties that are not
generally represented for that object type.

In either case, those properties should be collected using the
`Custom_Properties` element of the object properties. This is essentially a
simple list of key/value pairs:

```xml
<cybox:Properties xsi:type="FileObj:FileObjectType">
  <cyboxCommon:Custom_Properties>
    <cyboxCommon:Property name="Property Name">Property Value</cyboxCommon:Property>
  </cyboxCommon:Custom_Properties>
  <!-- Other properties from the FileObjectType schema -->
</cybox:Properties>
```

When capturing the output from a tool, the suggested practice is to set the
`@name` attribute of the custom property to the exact field name used in the
tool. If possible, the `@datatype` attribute should be set to the datatype that
will be output and the value formatted to fit that datatype's formatting. If
that's not possible, the exact value reported by the tool should be used and
the `@datatype` attribute should be omitted.

#### Example
The Bro tool captures the HTTP Transaction depth of an HTTP connection. In the
Bro output, this field is called `trans_depth` and the value will be set to
some integer (whatever the depth is). So the `@name` attribute should be set to
`trans_depth`, the value should be set to the output from Bro, and the
`@datatype` attribute should be set to `int` (Integer). That would give you
something like:

```xml
<cyboxCommon:Custom_Properties>
  <cyboxCommon:Property name="trans_depth" datatype="int">3</cyboxCommon:Property>
</cyboxCommon:Custom_Properties>
```

## File Object

The `FileObjectType` contains several fields for recording name and path
information about the file.

* File_Name
* File_Path
* Device_Path
* Full_Path
* File_Extension

The following practices are recommended for the use of these fields. Consider a
file located at
``C:\Users\ExampleUser\Documents\ProjectX\MeetingNotes_2014-08-01.txt`` or
``/home/exampleuser/ProjectX/MeetingNotes_2014-08-01.txt``

1. The ``File_Name`` field should specify the base name of the file, including extension

    ```xml
    <cybox:Properties xsi:type="FileObj:FileObjectType">
      <FileObj:File_Name>MeetingNotes_2014-08-01.txt</FileObj:File_Name>
    </cybox:Properties>
    ```

2. The ``File_Path`` field should contain the path to the file.

    ```xml
    <cybox:Properties xsi:type="FileObj:FileObjectType">
      <FileObj:File_Path>C:\Users\ExampleUser\Documents\ProjectX\MeetingNotes_2014-08-01.txt</FileObj:File_Path>
    </cybox:Properties>
    ```
    ```xml
    <cybox:Properties xsi:type="FileObj:FileObjectType">
      <FileObj:File_Path>/home/exampleuser/ProjectX/MeetingNotes_2014-08-01.txt</FileObj:File_Path>
    </cybox:Properties>
    ```

3. The ``File_Path`` should contain the name of the file if the ``File_Name``
field is not provided. If the ``File_Name`` field is provided, the name in the
``File_Path`` field must not conflict with the ``File_Name`` field. If the
``File_Path`` field does not contain the file name, it should end with a path
separator (slash `/` or backslash `\`, depending on the operating system).

    **OK**

    ```xml
    <cybox:Properties xsi:type="FileObj:FileObjectType">
      <FileObj:File_Name>MeetingNotes_2014-08-01.txt</FileObj:File_Name>
      <FileObj:File_Path>C:\Users\ExampleUser\Documents\ProjectX\MeetingNotes_2014-08-01.txt</FileObj:File_Path>
    </cybox:Properties>
    ```

    **BETTER**

    ```xml
    <cybox:Properties xsi:type="FileObj:FileObjectType">
      <FileObj:File_Name>MeetingNotes_2014-08-01.txt</FileObj:File_Name>
      <FileObj:File_Path>C:\Users\ExampleUser\Documents\ProjectX\</FileObj:File_Path>
    </cybox:Properties>
    ```

4. Although the path may be either relative or fully qualified, it should be
fully qualified unless the file which the ``File_Path`` is relative to is
specified via a RelatedObject. If you specify a relative path (with
`fully_qualified="false"`), you should include a related object, either
embedded or by reference.

    ```xml
    <cybox:Object id="example:File-1">
      <cybox:Properties xsi:type="FileObj:FileObjectType">
        <FileObj:File_Path fully_qualified="false">ProjectX\MeetingNotes_2014-08-01.txt</FileObj:File_Path>
      </cybox:Properties>
      <cybox:Related_Objects>
        <cybox:Related_Object id="example:File-2">
          <cybox:Properties xsi:type="FileObj:FileObjectType">
            <FileObj:File_Path>C:\Users\ExampleUser\Documents\</FileObj:File_Path>
          </cybox:Properties>
        </cybox:Related_Object>
      </cybox:Related_Objects>
    </cybox:Object>
    ```

5. The `Device_Path` field specifies the path to the device on which the file resides. This is *not* the drive letter, which has its own property on The WindowsFileObject (though it could be `\\.\C:`). On Windows, this could be a path such as `\\.\PhysicalDrive1` or `\Device\Harddisk0\Partition0`. On Unix-like systems, this could be a path like `/dev/sda1`. In general, it is better to include a relationship to a DeviceObject which contains the file, rather than using this field.

6. The `Full_Path` field is used to specify a combination of `Device_Path` plus `Full_Path`. In general, it is preferable to include this information separately under the component fields rather than the `Full_Path` field, unless it is not possible or desired to separate the information apart. Furthermore, this should not be used for files on Unix-like systems, since addressing a file by combination of device path and file path is not typically valid (`/dev/sda1/home/exampleuser/ProjectX/MeetingNotes_2014-08-01.txt`).

7. The `File_Extension` field is best used in CybOX patterns, rather than using an `EndsWith` condition on any of the other name or path fields.

    **OK**

    ```xml
    <cybox:Properties xsi:type="FileObj:FileObjectType">
      <FileObj:File_Name condition="EndsWith">.txt</FileObj:File_Name>
    </cybox:Properties>
    ```

    **BETTER**

    ```xml
    <cybox:Properties xsi:type="FileObj:FileObjectType">
      <FileObj:File_Extension condition="Equals">.txt</FileObj:File_Extension>
    </cybox:Properties>
    ```
