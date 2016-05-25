---
layout: flat
title: Suggested Practices
---

This page contains suggested practices for developing and consuming CybOX
content. There's a [similar page](https://stixproject.github.io/documentation/suggested-practices/) for Structured Threat Information eXpression (STIX™).

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
When creating references, you will typically use the `idref` attribute:

```xml
<cybox:Related_Object idref="acme:mutexobj-3c1221bd-2037-45ec-8129-4ba8d791e86b" />
```

In a VERY limited set of circumstances (e.g., when specifying Attachments or Links within the Email_Message Object), you will use the `object_reference` attribute rather than `idref`. The `object_reference` field, like the `idref` field, specifies a unique ID reference to an Object defined elsewhere. Unlike the general use of `idref` which references the full Object, the `object_reference` field allows for the re-use of the defined Properties of one Object within another, without allowing the embedding of the full Object in the location from which it is being referenced. Thus, this ID reference is intended to resolve to just the Properties of the Object that it points to. Situations where `object_reference` should be used rather than `idref` are explicitly documented within the object property schemas that utilize this approach.

```xml
<cybox:Observable id="example:Observable-db066ea1-925b-43df-a341-f513ece3ae94">
  <cybox:Object id="example:Object-e0e87eef-6315-410f-8025-086968129f41">
    <cybox:Properties xsi:type="EmailMessageObj:EmailMessageObjectType">
      <EmailMessageObj:Header>
        <EmailMessageObj:Subject>Syria strategic plans leaked</EmailMessageObj:Subject>
      </EmailMessageObj:Header>
      <EmailMessageObj:Attachments>
      	<EmailMessageObj:File object_reference="example:Object-107a9290-30aa-4059-aa01-b441f6aa0cc6"/>
      <EmailMessageObj:Attachments>
    </cybox:Properties>
  </cybox:Object>
</cybox:Observable>
```
 
When using either the `idref` or `object_reference` attribute, you should avoid putting any other attributes
or elements in the reference element.

## Using Vocabularies
Many places in CybOX use controlled vocabularies to represent data. When
possible, you should use the vocabularies included in the CybOX defaults. If
necessary, you can use your own vocabulary or even use strings outside of any
vocabularies.

If you do this to add values that you think might be useful for other CybOX
users, you should let us know by subscribing and submitting comments to the [CTI Users List](http://cyboxproject.github.io/community/#cti-users-list) or the [CTI TC Public Comment List](http://cyboxproject.github.io/community/#public-comment-list) so we can consider adding it to the default
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

CybOX Objects schemas define sets of properties for common cyber objects. 

To support practical use, CybOX provides an extensive set of Object property specifications by default.

This predefined set includes a broad range of object types across the cyber domain (network, host, files, memory, devices, etc.), as well as objects of varying levels of specificity/abstraction intended for differing use cases.

The approach to [defining Objects](../creating-objects) (especially those across varying levels of specificity/abstraction) is intended to pursue architectural consistency and reuse by having more complex or specific variations on Objects leverage other more abstract existing Objects for sets of properties.

There are two primary variations of this:

* Objects that derive from other Objects of the same basic type along a spectrum of abstract to more specific.
 * For example, **File -> Win File -> Win EXE File** where CybOX defines a basic [File Object] ({{site.stix_url}}/FileObj/FileObjectType) with general file properties applicable across platforms, a more specific [Win_File Object] ({{site.stix_url}}/WinFileObj/WindowsFileObjectType) that extends the general File Object and adds Windows-specific file properties, and an even more specific [Win_Executable_File Object] ({{site.stix_url}}/WinExecutableFileObj/WindowsExecutableFileObjectType) which extends the Win_File Object and adds properties for executable files under Windows.
* Objects that leverage other Objects to define more specific properties for differing and more specialized use cases.
  * For example, the set of Objects specified that can contain an **IP Address**.
    * [Address Object] ({{site.stix_url}}/AddressObj/AddressObjectType) enables the specification of a particular IP Address (or other type of address) value and its type (e.g., ipv4-addr) without any other context. This can be used when you desire to characterize an IP Address but not to assert any given context for where you might find it (e.g., it may appear in any of a wide variety of logs). This Object also provides consistent specification of address properties for its use on its own, or by more specific Objects that need to characterize addresses within more specific contexts.
    * [Socket_Address Object] ({{site.stix_url}}/SocketAddressObj/SocketAddressObjectType) enables the specification of a particular IP Address (or Hostname) and Port pairing. This obviously lets you characterize a more specific context for an IP Address but still leverages the AddressObjectType for its IP Address structure yielding consistency across the two Objects.
    * [Network_Connection Object] ({{site.stix_url}}/NetworkConnectionObj/NetworkConnectionObjectType) enables the specification of properties related to a network connection including Layer3, Layer4 and Layer7 details as well as details of the source socket and destination socket of the connection. This object leverages the SocketAddressType for its source and destination socket structures. This enables the characterization of very specific contextual details around an IP Address.
 

**It is suggested practice to always utilize the most specific CybOX Object possible for the context you are looking to convey and based on the properties you need to represent.**

* For example, if you know you are looking to describe a situation of network traffic to a particular IP Address, use the Network_Connection Object but if all you know is that an IP Address was seen or might be seen but you have no further context, use the Address Object. This also applies to the use of platform-agnostic Objects (e.g., File) and their derived platform-specifc Objects (e.g., Win_File). If you need to characterize properties from a more specific variation of an Object (e.g., the SID of a file), utilize that Object (e.g., Win_File) otherwise use the simplest version available that supports the properties you need to characterize.

**One clear exception to this is if conformance to a specific language Profile is required and that Profile restricts the set of available objects or directly specifies a particular Object to be used.**


###Common Object-to-Object Relationships

CybOX supports a broad range of Object types and provides the capability to relate/associate Objects together along with a characterization of how they are related. 

To encourage consistency in the characterization of relationships between Objects, CybOX provides a default controlled vocabulary ([ObjectRelationshipVocab-1.1](http://stixproject.github.io/data-model/1.1.1/cyboxVocabs/ObjectRelationshipVocab-1.1/)) for use with the Relationship field. This vocabulary contains a broad range of values to characterize many of the potentially relevant Object-to-Object relationships.

####Suggested vocabulary values to use in some of the more common Object-to-Object relationship usage scenarios include:

<br/>

**Desired Association (Network-centric Object relationships)**|**Source Object**|**Related Object**|**"Relationship" Vocabulary Value**
---------------------- | ---------- | ---------- | -----------
A network naming structure (e.g., Domain or Hostname) and an IP Address</br> it resolves to | [Domain_Name Object](http://stixproject.github.io/data-model/1.1.1/DomainNameObj/DomainNameObjectType/) | [Address Object](http://stixproject.github.io/data-model/1.1.1/AddressObj/AddressObjectType/) |  “**Resolved_To**”
 | Address Object | Domain_Name Object |  “**Resolved_To**”
 | [Hostname Object](http://stixproject.github.io/data-model/1.1.1/HostnameObj/HostnameObjectType/) |  Address Object | “**Resolved_To**”
 | Address Object  | Hostname Object  |  “**Resolved_To**”
An IP Address and an Autonomous System | Address Object  | [AS Object](http://stixproject.github.io/data-model/1.1.1/ASObj/ASObjectType/)  |  “**Contained_By**”
 | AS Object  | Address Object  |  “**Contains**”
A network naming structure (e.g., Domain or Hostname) and a Whois response | Domain_Name Object  | [Whois Object](http://stixproject.github.io/data-model/1.1.1/WhoisObj/WhoisObjectType/)  |  “**Characterized_By**”
 | Whois Object  | Domain_Name Object  |  “**Characterizes**”
 | Hostname Object  | Whois Object  |  “**Characterized_By**”
 | Whois Object  | Hostname Object  |  “**Characterizes**”
A network naming structure (e.g., Domain or Hostname) and a DNS Query | Domain_Name Object  | [DNS_Query Object](http://stixproject.github.io/data-model/1.1.1/DNSQueryObj/DNSQueryObjectType/)  |  “**Properties_Queried_By**”
 | DNS_Query Object  | Domain_Name  |  “**Properties_Queried**”
 | Hostname Object  | DNS_Query Object  |  "**Properties_Queried_By**”
 | DNS_Query Object  | Hostname Object  |  “**Properties_Queried**”
A network naming structure (e.g., Domain or Hostname) and a DNS Record | Domain_Name Object  | [DNS_Record Object](http://stixproject.github.io/data-model/1.1.1/DNSRecordObj/DNSRecordObjectType/)  |  “**Characterized_By**”
 | DNS_Record Object  | Domain_Name Object  |  “**Characterizes**”
 | Hostname Object  | DNS_Record Object  |  “**Characterized_By**”
 | DNS_Record )Object | Hostname Object  |  “**Characterizes**”
A DNS Record and a resolving IP Address within that record | DNS_Record Object  | Address Object  |  “**Contains**”
 | Address Object  | DNS_Record Object   |  “**Contained_Within**”
A DNS Query and a DNS Record that resulted from the query | DNS_Query Object  | DNS Record Object  |  “**Searched_For**”
 | DNS Record Object  | DNS_Query Object  |  “**Searched_For_By**”
A URL and the Domain contained within it | [URI Object](http://stixproject.github.io/data-model/1.1.1/URIObj/URIObjectType/)  | Domain_Name Object  |  “**Contains**”
 | Domain_Name Object  | URI Object  |  “**Extracted_From**”
One Domain and another Domain that is a sub-part of it | Domain_Name Object (supra) | Domain_Name Object (sub) |  “**Supra-domain_Of**”
 |  |  |  or “**FQDN_Of**”
 | Domain_Name Object (sub)  | Domain_Name Object (supra)  |  “**Sub-domain_Of**”

<br/>
<br/>

**Desired Association (Host-centric Object relationships)**|**Source Object**|**Related Object**|**"Relationship" Vocabulary Value**
---------------------- | ---------- | ---------- | -----------
The characteristics of a File and the actual bits of the file | [File Object](http://stixproject.github.io/data-model/1.1.1/FileObj/FileObjectType/)  | [Artifact Object](http://stixproject.github.io/data-model/1.1.1/ArtifactObj/ArtifactObjectType/)  |  “**Characterizes**”
 | Artifact Object  | File Object  |  “**Characterized_By**”
An Email and characteristics of a file attachment to the email | [Email_Message Object](http://stixproject.github.io/data-model/1.1.1/EmailMessageObj/EmailMessageObjectType/)  | File Object  |  “**Contains**”
 | File Object  | Email_Message Object  |  “**Contained_Within**”
An Email and the actual bits of a file attachment to the email | Email_Message Object  | Artifact Object  |  “**Contains**”
 | Artifact Object  | Email_Message Object  |  “**Contained_Within**”
An Email and a Link (URL) within the email | Email_Message Object  | [Link](http://stixproject.github.io/data-model/1.1.1/LinkObj/LinkObjectType/)  |  “**Contains**”
 | Link Object  | Email_Message Object  |  “**Contained_Within**”
A File and another File contained within it | File Object (outer)  | FileObject (inner)  |  “**Contains**”
 | File Object (inner)  | File Object (outer)  |  “**Contained_Within**”
A File and another File that it places on a system | File Object (dropper)  | File Object (dropped file)  |  “**Dropped**”
 | File Object (dropped file)  | File Object (dropper)  |  “**Dropped_By**”
A File and the URL, Domain, or Hostname from which it was downloaded  | File Object  | URI Object  |  “**Downloaded_From**”
 | URI Object  | File Object  |  “**Downloaded**”
 | File Object  | Domain Name Object  |  “**Downloaded_From**”
 | Domain Name Object  | File Object  |  “**Downloaded**”
 | File Object  | Hostname Object  |  “**Downloaded_From**”
 | Hostname Object  | File Object  |  “**Downloaded**”



### Capturing Custom Tool Properties
Sometimes, a tool will capture properties about a CybOX object that aren't in
the schema for that object type. In some cases, this is because the schemas need
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

## Domain Name and Hostname Objects

The release of CybOX 2.1 included the addition of two new objects: the [`Domain
Name` object](https://stixproject.github.io/data-model/1.1.1/DomainNameObj/DomainNameObjectType/)
and the [`Hostname` object](https://stixproject.github.io/data-model/1.1.1/HostnameObj/HostnameObjectType/).
Although the terms "domain name" and "hostname" are often used interchangeably,
the terms have precise (and distinct) meanings in some contexts, and neither
term completely encompasses the other. This document hopes to clarify the
intent of these two objects and provide a set of suggested practices for their
use.


### Background

The concepts of a "domain" (in the context of DNS, *not* Windows Active
Directory domains) and a "host" (a generic term for a computing system) are
certainly distinct, but the names used to represent these entities are often
indistinguishable.  Given the name `www.example.com`, does that string
represent a domain? A host?  Both? In this case, there is most likely a host
that responds to web requests at an IP address which a DNS query for that name
would respond with. However, there are some valid domain names that do not
correspond to hosts (e.g., top-level domains such as "org" or "co.uk"). There are
also host names (e.g., local names in a `hosts` file) which may not correspond
to a name in any domain name system.

### General Principle

So, which type of object should you use?

In general, the `Hostname` object should be used in "concrete" cases when you
know there is a host with a given name (for instance, when there is a network
connection between two machines). The `Domain Name` object should be used in
more abstract scenarios when it is not clear if an actual connection is
occurring (DNS queries) or if there is the potential for more than one IP or
host to be involved (load balancer, etc.).

### Specific Cases

1. If you are looking to represent a "local hostname" (in other words, what a
   system calls *itself*), there is a `Hostname` property of the [`System`
   object](https://stixproject.github.io/data-model/1.1.1/SystemObj/SystemObjectType/)
   that should be used.

    ```xml
    <SystemObj:System>
      <SystemObj:Hostname>plato</SystemObj:Hostname>
    </SystemObj:System>
    ```

1. There are two cases in which using the `Hostname` object is used explicitly:
   within the [`Socket Address`
   object](https://stixproject.github.io/data-model/1.1.1/SocketAddressObj/SocketAddressObjectType/)
   (which is used in the [`Network Connection`
   object](https://stixproject.github.io/data-model/1.1.1/NetworkConnectionObj/NetworkConnectionObjectType/)),
   and within a [`URL History Entry`
   component](https://stixproject.github.io/data-model/1.1.1/URLHistoryObj/URLHistoryEntryType/)
   of the [`URL History`
   object](https://stixproject.github.io/data-model/1.1.1/URLHistoryObj/URLHistoryObjectType/).
   In each case, this represents an actual host involved in communication, so
   this matches the general principle.

    ```xml
    <URLHistoryObj:URL_History>
      <URLHistoryObj:URL_History_Entry>
        <URLHistoryObj:URL type="URL">
          <URIObj:Value>http://www.example.com/index.html</URIObj:Value>
        </URLHistoryObj:URL>
        <URLHistoryObj:Hostname>
          <HostnameObj:Hostname_Value>www.example.com</HostnameObj:Hostname_Value>
        </URLHistoryObj:Hostname>
      </URLHistoryObj:URL_History_Entry>
    </URLHistoryObj:URL_History>
    ```

    ```xml
    <NetworkConnectionObj:Network_Connection>
      <NetworkConnectionObj:Layer7_Protocol>HTTP</NetworkConnectionObj:Layer7_Protocol>
      <NetworkConnectionObj:Source_Socket_Address>
        <SocketAddressObj:IP_Address>
          <AddressObj:Address_Value>192.168.1.10</AddressObj:Address_Value>
        </SocketAddressObj:IP_Address>
        <SocketAddressObj:Port>
          <PortObj:Port_Value>12345</PortObj:Port_Value>
          <PortObj:Layer4_Protocol>TCP</PortObj:Layer4_Protocol>
        </SocketAddressObj:Port>
      </NetworkConnectionObj:Source_Socket_Address>
      <NetworkConnectionObj:Destination_Socket_Address>
        <SocketAddressObj:Hostname>www.example.com</SocketAddressObj:Hostname>
        <SocketAddressObj:Port>
          <PortObj:Port_Value>80</PortObj:Port_Value>
          <PortObj:Layer4_Protocol>TCP</PortObj:Layer4_Protocol>
        </SocketAddressObj:Port>
      </NetworkConnectionObj:Destination_Socket_Address>
    </NetworkConnectionObj:Network_Connection>
    ```

    **NOTE**: In reality, TCP/IP network connections are not actual made based
    on the hostname; rather, the hostname is used to look up an IP address,
    which is then used for the connection. The `Socket_Address` object supports
    a `Hostname` property for instances where the actual IP address is not
    significant to what is being expressed. For example, in dynamic malware
    sandboxes, DNS responses are frequently modified to return a different IP
    address (often a private IP address). In these cases, the actual IP address
    used for the connection is not important, and representing the hostname
    that the malware uses for C2 as a direct property of the network connection
    is desirable; it avoids the use of `Related Object`s and the need to
    include IP addresses that aren't informative.

1. In the [`DNS Record` object](https://stixproject.github.io/data-model/1.1.1/DNSRecordObj/DNSRecordObjectType/),
   the `Domain Name` field uses the [`URI` object](https://stixproject.github.io/data-model/1.1.1/URIObj/URIObjectType/).
   This is because the `DNS Record` object predates the `Domain Name` object.
   This may be corrected in a future major release of CybOX, but for now, use a
   `URI` object with `type="Domain Name"` (as this is the only schema-valid
   type for this field).

    ```xml
    <DNSRecordObj:DNS_Record>
      <DNSRecordObj:Domain_Name type="Domain Name">
        <URIObj:Value>www.example.com</URIObj:Value>
      </DNSRecordObj:Domain_Name>
      <DNSRecordObj:IP_Address category="ipv4-addr">
        <AddressObj:Address_Value>192.168.1.42</AddressObj:Address_Value>
      </DNSRecordObj:IP_Address>
      <DNSRecordObj:Entry_Type>A</DNSRecordObj:Entry_Type>
    </DNSRecordObj:DNS_Record>
    ```

1. If you don't want to capture the entire DNS record, you can also use a
   `Domain Name` object, along with one or more related [`Address`
   objects](https://stixproject.github.io/data-model/1.1.1/AddressObj/AddressObjectType/),
   using the `Resolved_To` relationship.

    ```xml
    <cybox:Object>
      <cybox:Properties xsi:type="DomainNameObj:DomainNameObjectType">
        <DomainNameObj:Value>www.google.com</DomainNameObj:Value>
      </cybox:Properties>
      <cybox:Related_Objects>
        <cybox:Related_Object>
          <cybox:Properties xsi:type="AddressObj:AddressObjectType" category="ipv4-addr">
            <AddressObj:Address_Value>74.125.196.100</AddressObj:Address_Value>
          </cybox:Properties>
          <cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Resolved_To</cybox:Relationship>
        </cybox:Related_Object>
        <cybox:Related_Object>
          <cybox:Properties xsi:type="AddressObj:AddressObjectType" category="ipv4-addr">
            <AddressObj:Address_Value>74.125.196.138</AddressObj:Address_Value>
          </cybox:Properties>
          <cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Resolved_To</cybox:Relationship>
        </cybox:Related_Object>
        <cybox:Related_Object>
          <cybox:Properties xsi:type="AddressObj:AddressObjectType" category="ipv4-addr">
            <AddressObj:Address_Value>74.125.196.113</AddressObj:Address_Value>
          </cybox:Properties>
          <cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Resolved_To</cybox:Relationship>
        </cybox:Related_Object>
        ...
      </cybox:Related_Objects>
    </cybox:Object>
    ```

1. The `is_domain_name` attribute on the `Hostname` object can be used when it
   is important to indicate whether or not the provided hostname is query-able
   via DNS. However, if you aren't sure whether a name actually corresponds to
   a host, don't use the `Hostname` object with this attribute set to `true`.

1. When capturing domain names as part of a "malicious domain watchlist" or
   other list of domains, the `Domain Name` object should be used. 

The CybOX team is investigating ways to make the use of these objects even more
clear in a future release. Suggestions and/or proposed changes are always
welcome by subscribing and submitting comments to the [CTI Users List](http://cyboxproject.github.io/community/#cti-users-list) or the [CTI TC Public Comment List](http://cyboxproject.github.io/community/#public-comment-list)!

## File Object

The `FileObjectType` contains several fields for recording name and path
information about the file.

* `File_Name`
* `File_Path`
* `Device_Path`
* `Full_Path`
* `File_Extension`


### Instance Data

For File instance observables, the `File_Name` and `File_Path` are sufficient
for the vast majority of use cases.  Given the file
`C:\Users\ExampleUser\Documents\ProjectX\MeetingNotes_2014-08-01.txt`, the file
name and the path of the directory which contains the file should be separated
and stored in these two fields. Note the trailing `\` in the `File_Path`.

```xml
<cybox:Properties xsi:type="FileObj:FileObjectType">
  <FileObj:File_Name>MeetingNotes_2014-08-01.txt</FileObj:File_Name>
  <FileObj:File_Path>C:\Users\ExampleUser\Documents\ProjectX\</FileObj:File_Path>
</cybox:Properties>
```

If the file path is unknown, or you do not wish to include it, it can be
omitted.

The `Device_Path` field MAY be used to specify the path to the *file system
partition* on which the file resides.  On Windows, `Device_Path` could be a
path such as `\Device\Harddisk0\Partition0`. On Unix-like systems, this could
be a path like `/dev/sda1`. You should not use a path to a physical disk, such
as `\\.\PhysicalDrive1` on Windows or `/dev/sda` on Unix-like systems, since
file systems are generally tied to partitions rather than physical disks.

The `Full_Path` field is used to specify a combination of `Device_Path` plus
`File_Path`. You SHOULD NOT use this field unless it is not possible to split
the `Full_Path` into the `Device_Path` and the `File_Path` fields; it is
preferable to include this information separately under the component fields.

The `File_Extension` field SHOULD NOT be used on instance data.


### Pattern Data

Representing file name and path data as CybOX patterns is more complex, as
there is much more variation in what is being represented. A few examples are
shown below, but this is far from an exhaustive list. Note that some examples
can be combined to represent more complex conditions.

#### Representing a file with a given extension

This is the time to use the `File_Extension` field. Do not use a
`condition="EndsWith"` on the `File_Name` field.

```xml
<cybox:Properties xsi:type="FileObj:FileObjectType">
  <FileObj:File_Extension condition="Equals">txt</FileObj:File_Extension>
</cybox:Properties>
```

#### Representing a file in a given directory

Use the `EndsWith` condition on the `File_Path` field (or `Equals` if you know
the full path to the directory).

```xml
<cybox:Properties xsi:type="FileObj:FileObjectType">
  <FileObj:File_Path condition="EndsWith">ProjectX\</FileObj:File_Path>
</cybox:Properties>
```

```xml
<cybox:Properties xsi:type="FileObj:FileObjectType">
  <FileObj:File_Path condition="Equals">C:\Users\ExampleUser\Documents\ProjectX\</FileObj:File_Path>
</cybox:Properties>
```


#### Representing a file anywhere beneath a given directory

If you know a directory somewhere in the file path, but not necessarily the
directory which directly contains the file, you can use `StartsWith` or
`Contains`.

```xml
<cybox:Properties xsi:type="FileObj:FileObjectType">
  <FileObj:File_Path condition="StartsWith">C:\Users\ExampleUser\Documents\</FileObj:File_Path>
</cybox:Properties>
```

```xml
<cybox:Properties xsi:type="FileObj:FileObjectType">
  <FileObj:File_Path condition="Contains">Documents</FileObj:File_Path>
</cybox:Properties>
```
