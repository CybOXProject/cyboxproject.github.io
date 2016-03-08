---
layout: flat
title: CybOX Language Frequently Asked Questions (FAQs)
---

Answers to commonly asked questions about the [CybOX Language](http://cyboxproject.github.io/releases/2.1/) are included below. See the [About CybOX](http://cyboxproject.github.io/about/) page for answers to [general questions](http://cyboxproject.github.io/about/#frequently-asked-questions) about CybOX. 

### What is an observable by itself (in the simplest case)?

An observable is a set of properties or characteristics that describe an entity within the operational cyber environment, such as a UNIX file, a library, or a Windows Registry Key.

### Which objects currently have representations defined in CybOX?

See the list of available Objects in the [latest CybOX release](/releases/2.1).

### How do you use CybOX objects? Do they all need to be used? Can they be represented in multiple ways?

CybOX includes two core schemas — CybOX_Core and CybOX_Common — that provide the essential CybOX structure and functionality. The CybOX Objects, enumerated in individual schema files, are precise characterizations of particular types of observable cyber entities, such as an HTTP session, a Windows Registry Key, and a DNS query. Use of the two core schemas is required, whereas use of object schemas is cafeteria-style: users select and use only those objects and corresponding schemas that are needed. The modular design of the CybOX architecture means importing the whole CybOX suite of schemas is not necessary.

In some cases, such as the file object, both generic/parent ("file") and more specific/child ("UNIX file", "Win File") object schemas are available. This is to facilitate flexibility and pattern identification. Only the appropriate schema needs to be used.

### What are the python-cybox APIs?

The python-cybox APIs are a set of Python libraries that enable higher-level interaction with CybOX by facilitating the use of and interaction with the CybOX Python bindings. Whereas the CybOX Python bindings are tied to directly to the CybOX XML schemas, the python-cybox APIs further simplify interaction with CybOX documents (parsing, editing, creating, etc.), making it easier for Python developers to more natively work with CybOX.

The python-cybox APIs are hosted in the [CybOXProject GitHub Repository](https://github.com/CybOXProject/python-cybox).

### What is the CybOX Artifact object?

Whereas other CybOX objects characterize the properties of an observable object, the CybOX Artifact object captures the raw, binary representation (or "chunk-of-bits") of an object, such as a file, memory region, or Packet Capture (PCAP) data. The CybOX Artifact object also includes capabilities to enable object packaging, such as encrypting, compressing or encoding the object to make it smaller and easier to disseminate.

### How do CybOX patterns work? Can I define regex patterns on various content?

CybOX patterns are a generalization of CybOX content. They allow users and developers to characterize a set, a range, or other generalized characteristics of a cyber observable. For instance, one could use CybOX patterns to describe a URL that matches one of a set of possible URL values.

Regular expression (regex) patterns are also possible. See [CybOX Regular Expression Support](http://cyboxproject.github.io/documentation/regex-support/) for details.

### What type of file hashes does CybOX support?

A wide variety of file hash values can be represented in CybOX. While typically only a simple hash value and type is needed, such SHA1 or MD5, the flexibility inherent in CybOX also supports additional hash formats, such as hash digests, fuzzy hashes, hash algorithms, and custom hash expressions.

### How do Identifiers (IDs) work?

IDs allow unique referencing of a distinct portion of CybOX content from other places within a CybOX document or elsewhere. For instance, Observables, Actions, and Objects can all have IDs specified for them. IDs in CybOX come in the form of two attributes, @id and @idref, on any construct that is ID-referenceable. The two attributes are mutually exclusive, meaning that only one should be used on any given construct. The @id attribute defines a unique identifier on a content construct at its point of characterization. Conversely, the @idref attribute is used to reference a content construct that is defined elsewhere; @idref inclusion means the referenced content construct is considered as fully present as its point of reference (macro-style). This use of @id and @idref enables unique referencing and reuse of content.

### How are Identifiers (IDs) formatted?

IDs within CybOX are XML Qualified names (QNames). A QName consists of a global prefix name (usually in the form of a namespace) followed by a colon followed by local postfix name (e.g., following a namespace declaration of xmlns:foo="http://foo.com", foo:bar would be a Qname).

For CybOX, suggested practice is for the ID prefix to be a globally unique namespace controlled by the producer of the content being identified (this could be an organization, sub-organization, individual, etc.) and for the postfix to be some form of identifier that is unique within the prefix namespace. This combination guarantees that CybOX IDs are globally unique. ID specifiers are free to use whatever format they desire for the postfix (to enable flexibility among differing use cases) but suggested practice is to use the format ‘[hint] - guid’ where [hint] is a simple appellation labeling the type of construct being identified (e.g., ‘MITRE:Object - 869cf174-9dfb-42ef-b816-4356ce2bce83’ where the MITRE namespace alias has been previously declared).

### When should I define Identifiers (IDs) for content?

CybOX content authors are free to decide when and where to provide IDs of CybOX content constructs but suggested practice is that specification of content using the primary constructs of Observable, Event, Action, and Object should always specify IDs as part of the content. For other non-primary constructs it is purely up to the author's discretion and no guidance is given.

### What are Object Properties and how are they expressed? What is the xsi:type attribute within the Object Properties element?

Object Properties represent observable characteristics specific to particular types of objects. For example, the Disk Object includes properties such as Disk_Name, Disk_Size, Free_Space, and Partition_List, while the Process Object includes properties such as PID, Name, Creation_Time, Parent_PID, and Argument_List. The CybOX objects directory defines dozens of Object schemas, each identifying a set of properties for a particular type of object. As such, Object Properties represent specific details of an observed object using characteristics specific to that Object type.

Within a CybOX object, the specific type of Object (and thus which properties will be specified) is indicated through the use of the XML xsi:Type attribute. Specifically, within the `<Properties>` element, an author would add an attribute with the name "xsi:Type" and whose value was the name of the XML type in which the given object’s properties are defined. Each object schema defines at least one XML type that extends the ObjectPropertiesType and whose name could be used as the value of the xsi:Type attribute. The xsi:Type capability is a special feature of XML type inheritance, allowing the author of an XML file to determine which child type they will be utilizing at the time of document authoring (rather than having that type hard-coded into the schema). Use of the xsi:Type feature of XML allows CybOX to provide authors with a great deal of flexibility as to which Object properties they wish to define, while still allowing those authors to be guided by well-defined schemas.

More simply, when one is documenting an observable Object, one should:

Identify the type of Object one is attempting to characterize.
From that Object’s schema file, identify the XML complexType that extends ObjectPropertiesType. (This is almost always the first complexType defined in the Object schema.)
In the XML file, within the `<Object>` element, add a `<Properties>` element and in that element add an attribute named xsi:Type whose value is the name of the complexType identified in step 2.
The children and attributes of the `<Properties>` element will now conform to the named type identified in step 2. Fill in the appropriate Object Properties within the <Properties> element according to that schema.
For example, in the xml excerpt below, the xsi:type has been set to FileObj:FileObjectType, which identifies the CybOX File_Object:

```xml
    <cybox:Object>
        <cybox:Properties xsi:type="FileObj:FileObjectType">
            ...
        </cybox:Properties>
    </cybox:Object>
```

### How can a new Object Schema be added to CybOX?

In order to add a new Object Schema to CybOX, one must first create a schema file. Next, create a type that extends the ObjectPropertiesType or another defined Object type (e.g., FileObjectType) within the schema file. Third, populate the child type with the information you are trying to capture about some observable, and, finally, it will work natively with CybOX. The simplest way to do this may to use an existing CybOX Object as a template. If you want to share it with the larger CybOX Community, send it to the [Cyber Threat Intelligence (CTI) Technical Committee (TC) Public Comment List](http://www.oasis-open.org/committees/comments/form.php?wg_abbrev=cti) for review and vetting, and then it can become part of the core CybOX distribution, or it can remain a private object.

### What is the "condition" attribute applied to object properties?

The condition attribute is an operator used to specify conditional characteristics within objects for defining observable patterns. Condition allows specification of expressions such as equals, greater than, less than, included in range, member of a particular set, and conforms to a particular regular expression. The following provides one example of how condition is used in CybOX:

```xml
<cybox:Observable xmlns:cybox="http://cybox.mitre.org/cybox-2">
    <cybox:Object>
        <cybox:Properties xsi:type="AddrObj:AddressObjectType" category="ipv4-addr">
            <AddrObj:Address_Value
                condition="InclusiveBetween">1.166.0.0,1.167.255.255</AddrObj:Address_Value>
        </cybox:Properties>
    </cybox:Object>
</cybox:Observable>
```

### What is the difference between CybOX Events and Actions?

The CybOX Event construct enables specification of a cyber observable event that is dynamic in nature with specific action(s) taken against specific cyber relevant objects (e.g., a file is deleted, a registry key is created or an HTTP Get Request is received). The CybOX Actions construct enables specification of one or more cyber observable actions. Events are higher-level constructs than Actions; an Event is composed of one or more Actions.

### How do I describe a relationship between two objects in CybOX?

The Object structure in CybOX has a Related Objects substructure or child. Within Related Objects, you would point to another CybOX object or set of objects and declare a type of relationship.

### How do objects work inside of an action in CybOX?

An action in the operational cyber domain usually acts on or uses an object (e.g., create file); the CybOX Language supports this usage by offering an Associated_Object construct within the Action type. The Associated_Objects construct enables the specification of cyber Objects relevant to (e.g., initiating or affected by) this Action. Any number of Associated_Objects may be specified.

The following is an example of an Action with an Associated_Object.

The ‘Returned’ value of the Association_Type element in the Associated_Object, in combination with the Action Type and Name, implies that this File Object was created as a result of this Action.

### Why do some CybOX Defined Objects inherit from each other?

CybOX offers the flexibility to characterize both general and specific instantiations of some objects, such as the File object. In some cases, the lower level detail of a specific object type, such as a UNIX file, is needed. In other cases, the more general object provides the ability to capture characteristics across objects, such as across all file types.

### What is CDATA and how do I use it in an XML instance?

CDATA is character data, and it is used to tell the XML parser to interpret information as characters and not markup. This is typically used for conveying content in non-XML formats that could confuse an XML parser.

### How is CybOX versioned?

See the [CybOX Language Versioning Policy](http://cyboxproject.github.io/documentation/versioning-policy/).

### Are there plans to support other forms of data interchange for CybOX (e.g., JSON, YAML, etc.)?

Yes. An updated formal CybOX implementation-independent specification will be produced, to include guidance for developing technology-specific implementations such as JavaScript Object Notation (JSON), Resource Description Framework (RDF)/Web Ontology Language (OWL), YAML Ain’t Markup Language (YAML), or other implementations. XML was used in the initial release to enable rapid development and support implementation.

## Using CybOX

### How do I use CybOX? What tools/utilities are available for this effort?

For programmatic development and use of CybOX, Python bindings, as well as Python APIs (higher-level helper functions), are provided.

Currently available tools/utilities are hosted in the [CybOXProject GitHub Repositories](https://github.com/CybOXProject).

### What is included in a CybOX release?

A CybOX release includes the new version of the CybOX Core schemas, the latest versions of the independently-versioned CybOX Object schemas, the latest versions of the independently-versioned CybOX vocabulary schemas, and references to the relevant version CybOX extension schemas.

See [Releases](http://cyboxproject.github.io/releases/2.1/) for additional information and the latest release.

### Where can I find examples of CybOX data? Are there any CybOX repositories?

Some examples of CybOX data are included in the [current release](http://cyboxproject.github.io/releases/2.1/) of CybOX. Additional examples will be produced and posted on this website, included in the language specification, and included in the code repository. At present, there are no repositories of CybOX data, nor are there any CybOX Community plans to establish one. Community members interested in hosting a CybOX data repository are strongly encouraged to do so.

### How do I represent an IP Address in CybOX? What about different kinds of IP addresses (IPv4, IPv6, CIDR, etc.)?

IP addresses are commonly shared in a variety of threat intelligence and cyber defense communiques.

CybOX supports the following address types:

* IPv4 Address Specifies an IPV4 address in dotted decimal form. CIDR notation is also accepted.
* IPv6 Address Specifies an IPV6 address, which is represented by eight groups of 16-bit hexadecimal values separated by colons (:) in the form a:b:c:d:e:f:g:h. CIDR notation is also accepted.
* Host Name Specifies a host name. For compatibility reasons, this could be any string. Even so, it is best to use the proper notation for the given host type. For example, web hostnames should be written as fully qualified hostnames in practice.
* MAC Address Specifies a MAC address, which is represented by six groups of 2 hexadecimal digits, separated by hyphens (-) or colons (:) in transmission order.

Example:

* IPV4 Address: 199.192.156.134
* IPV6 Address: 2607:f8b0:4004:803::1015
* IPV4 Address Range: 223.167.0.0-223.167.255.255

CybOX Representation:

#### IPV4 Address: 199.192.156.134

```xml
<cybox:Object id="example:Object-15be6630-c2df-4bf9-8750-3f45ca9e19cf">
    <cybox:Properties xsi:type="AddressObj:AddressObjectType" category="ipv4-addr">
        <AddressObj:Address_Value>199.192.156.134</AddressObj:Address_Value>
    </cybox:Properties>
</cybox:Object>
```

#### IPV6 Address: 2607:f8b0:4004:803::1015

```xml
<cybox:Object id="example:Object-481e8ff6-7b7e-46bb-bec7-76bcbe9e67fd">
    <cybox:Properties xsi:type="AddressObj:AddressObjectType" category="ipv6-addr">
        <AddressObj:Address_Value>2607:f8b0:4004:803::1015</AddressObj:Address_Value>
    </cybox:Properties>
</cybox:Object>
```
 
#### IPV4 Address Range: 223.167.0.0-223.167.255.255

```xml
<cybox:Object id="example:Object-15be6630-c2df-4bf9-8750-3f45ca9e19cf">
    <cybox:Properties xsi:type="AddressObj:AddressObjectType" category="ipv4-addr">
        <AddressObj:Address_Value condition="InclusiveBetween"
		apply_condition="ANY">223.167.0.0,223.167.255.255</AddressObj:Address_Value>
    </cybox:Properties>
</cybox:Object>
```

### How do I represent a URL in CybOX?

CybOX represents URLs as a case of the URIObj object, as shown in the following example:

```xml
<cybox:Object id="example:Object-37be6630-b2df-4bf9-8750-3f45ca9e19cf">
    <cybox:Properties xsi:type="URIObject:URIObjectType" type="URL">
        <URIObject:Value>http://example.com/index1.html</URIObject:Value>
    </cybox:Properties>
</cybox:Object>
```

### How do I represent a File? How do I represent a file hash? Can CybOX represent fuzzy hashes? How do I represent an executable file?

In CybOX, the FileObject object is used to characterize a file. FileHash is one of the properties of FileObject for representing file hashes. Both simple and fuzzy hashes can be represented in CybOX via the HashType type and simple and fuzzy hash elements. Windows PE files can be represented in CybOX using the WinExecutableFileObj object. The following example shows a simple file with a file name, file path, file extension, file size, and an MD5 file hash property.

### How do I represent an Email?

CybOX uses the EmailMessageObj object to represent an email, as shown [here](http://cybox.mitre.org/language/version2.1/xsddocs/objects/Email_Message_Object.html).

### If I only want to represent a File (or an Email, or a Process, or a device, etc.), do I need to use all of CybOX?

The CybOX Core schemas are always used. The CybOX Object schemas are used cafeteria-style: you select and use only those objects you need. If you are just representing a file, you would use the CyboX Core schemas and the File_Object schema (or appropriate, more granular file schema, such as Win_File_Object, UNIX_File_Object, or PDF_File_Object).


