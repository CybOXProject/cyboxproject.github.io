---
layout: flat
title: CybOX Background
---

This page describes some basic information about XML Schema and the CybOX
language that is necessary to understanding [how to create a new CybOX
object](../creating-objects).


## CybOX XML Schema Data Types

The [CybOX Common
schema](https://github.com/CybOXProject/schemas/blob/master/cybox_common.xsd)
defines several constructs that can and should be leveraged when creating CybOX
Objects (e.g., a file on disk or network packet) as a whole or individual
Object Properties (e.g., a filename or TCP Header checksum).


### Object Base Data Type: ObjectPropertiesType

The `ObjectPropertiesType` is an abstract type defined in the [CybOX Common
schema](https://github.com/CybOXProject/schemas/blob/master/cybox_common.xsd)
which serves as the base type for all CybOX Objects (e.g., `AddressObjectType`,
`FileObjectType`, etc.). Extension of `ObjectPropertiesType` can be done either
[directly](#direct-extension-of-objectpropertiestype) or
[indirectly](#indirect-extension-of-objectpropertiestype).

By extending from `ObjectPropertiesType` a CybOX Object can be plugged into any
field that is of type `ObjectPropertiesType`. This includes the `Properties`
field, which is a field found on the CybOX Core schema `ObjectType`.


#### Direct Extension of ObjectPropertiesType

Many CybOX Objects directly extend the `ObjectPropertiesType` which serves as
the root base type for all CybOX Objects. The following XML snippet shows how
the `FileObjectType` directly extends from the base `ObjectPropertiesType`.

```xml
<xs:complexType name="FileObjectType">
  <xs:complexContent>
    <xs:extension base="cyboxCommon:ObjectPropertiesType">
      <!-- SNIP -->
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```


#### Indirect Extension of ObjectPropertiesType

The CybOX Language is designed to promote [Object reuse](#cybox-object-reuse)
so as to facilitate consistent methods for the characterization of cyber
observable information. One method of CybOX Object reuse is Object extension
wherein a CybOX Object type extends not from `ObjectPropertiesType` directly,
but instead from another CybOX Object. 

Through this form of extension, a CybOX Object is able to inherit properties
and fields from a parent CybOX Object without having to redefine or
re-implement the parent Object's structure under a new [XML
namespace](#namespaces).

The following example shows how the `PDFFileObjectType` extends from
`FileObjectType`.

```xml
<xs:complexType name="PDFFileObjectType">
  <xs:complexContent>
    <xs:extension base="FileObj:FileObjectType">
      <!-- SNIP -->
    </xs:extension>
  </xs:complexContent>
</xs:complextType>
```

**Note:** Each CybOX Object MUST extend from `ObjectPropertiesType`, either
directly or indirectly. The example above, the `PDFFileObjectType` extended
from the `FileObjectType`. Because `FileObjectType` extends from
`ObjectPropertiesType`, the `PDFFileObjectType` also extends from
`ObjectPropertiesType`.


### Object Property Data Types: ObjectPropertyType

The CybOX Language defines data types to be used for each Object property
(e.g., a filename or a TCP header checksum). The following data types are
defined within the [CybOX Common
schema](https://github.com/CybOXProject/schemas/blob/master/cybox_common.xsd)
to be used for capturing field data.

The `BaseObjectPropertyType` is the base type for the more specific property
types below. These properties can express multiple values by providing them
using a delimiter-separated list. The default delimiter is `##comma##` and as
such, use of the delimiter string in values is prohibited. Note that whitespace
is preserved and so, when specifying a list of values, do not include a space
following the delimiter in a list unless the first character of the next list
item should, in fact, be a space.

The following table maps CybOX object property types to the corresponding [XML
data type](http://www.w3.org/TR/xmlschema-2/#built-in-datatypes) they are
intended to capture. Note that the `datatype` attribute can be used to override
the default interpretation of the value stored in the field.

| CybOX Type | XML Data Type |
| ---------- | ------------- |
| `IntegerObjectPropertyType` | `int`/`integer` |
| `StringObjectPropertyType` | `string` |
| `NameObjectPropertyType` | `Name` |
| `DateObjectPropertyType` | `date` |
| `DateTimeObjectPropertyType` | `dateTime` |
| `FloatObjectPropertyType` | `float` |
| `DoubleObjectPropertyType` | `double` |
| `UnsignedLongObjectPropertyType` | `unsignedLong` |
| `UnsignedIntegerObjectPropertyType` | `unsignedInt` |
| `PositiveIntegerObjectPropertyType` | `positveInteger` |
| `HexBinaryObjectPropertyType` | `hexBinary` |
| `LongObjectPropertyType` | `long` |
| `NonNegativeIntegerObjectPropertyType` | `nonNegativeInteger` |
| `AnyURIObjectPropertyType` | `anyURI` |
| `DurationObjectPropertyType` | `duration` |
| `TimeObjectPropertyType` | `time` |
| `Base64BinaryObjectPropertyType` | `base64Binary` |


## CybOX Object Property Requirements

Generally speaking, CybOX Object Properties (fields) are optional by design.
Defining an Object property as optional is accomplished via setting
`minOccurs="0"` on the field definition.


**Example**

The follow example demonstrates optional Object properties via setting
`minOccurs="0"` on the `Domain_Name` field found in the `WhoisObjectType`.

```xml
<xs:complexType name="WhoisObjectType">
  <xs:complexContent>
    <xs:extension base="cyboxCommon:ObjectPropertiesType">
      <xs:sequence>
        <!-- SNIP -->
        <!-- Note that setting minOccurs="0" renders this field as optional -->
        <xs:element name="Domain_Name" type="URIObj:URIObjectType" minOccurs="0">
          <xs:annotation>
            <xs:documentation>The Domain_Name field specifies the corresponding domain name for this whois entry</xs:documentation>
          </xs:annotation>
        </xs:element>
        <!-- SNIP -->
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
<xs:complexType>   
```


### Why Optional?

Defining fields as optional is done to better support [CybOX
patterning](#cybox-patterning), wherein pattern authors may write patterns
against a particular field or set of fields. Requiring the presence of Object
properties forces pattern authors to include those fields in their patterns.
Forcing the inclusion of fields may yield undesired behaviors and results from
pattern evaluation tools.


## CybOX Naming Conventions

The CybOX XML Schema follows naming conventions for CybOX Object schemas, data
types, controlled vocabularies, object names, namespace aliases, elements, and
attributes.


### CybOX Object Schema Names

Underscore-separated, first letter of terms capitalized (unless an acronym is
being used, in which case all letters of the acronym are capitalized) and
ending with `_Object.xsd`.

**Examples:**  

* `Account_Object.xsd`
* `DNS_Cache_Object.xsd` (DNS acronym capitalized)


### CybOX Object Namespaces

`[Object Authoring Identity]#[ObjectName]-[Version]`

Broken into three parts:

* **Object Authoring Identity:** The namespace for the authoring person/organization/party
* **ObjectName:** The name of the CybOX Object
* **Version:** The major version of the Object schema (e.g., `2` if the version of the schema is `2.1`)

**Examples:**

* `http://cybox.mitre.org/objects#AddressObject-2` : Address Object v2.1 schema namespace
* `http://cybox.mitre.org/objects#PacketObject-2` : Network Packet Object v2.1 Object schema namespace


### CybOX Object Namespace Aliases

Camel-cased and ending with `Obj`. If the Object namespace includes an acronym,
each letter of the acronym is capitalized.

**Examples:**  

* `AccountObj`
* `UnixProcessObj`
* `PDFFileObj` (PDF is capitalized)


### CybOX Data Types

The CybOX Language defines naming conventions for various data types and date
type classifications.


#### Complex Types

Camel-cased and ending with `ObjectType` if the `complexType` defines the
root-level, `ObjectPropertiesType` implementation for the schema.

**Examples:** 

* `AddressObjectType`
* `AccountObjectType`
* `FileObjectType`

Camel-cased and ending with `Type` if the `complexType` defines a
non-ObjectPropertiesType, non-controlled-vocabulary data type.

**Examples:**  

* `StructuredAuthenticationMechanismType`
* `FilePathType`

**Note:** Controlled vocabulary implementations are an exception to these
`complexType` conventions. See the [Controlled
Vocabulary](#controlled-vocabularies) section for more details regarding naming
conventions for controlled vocabularies.


#### Simple Types

Camel-cased and ending with `TypeEnum`.

All global `simpleType` definitions are used in CybOX to define
non-controlled-vocabulary enumerations. 

**Examples:**  

* `SourceTypeEnum`
* `ToolReferenceTypeEnum`


#### Controlled Vocabularies

Controlled vocabularies sit at the intersection of `complexType` and
`simpleType` naming conventions, with additional conventions of their own
sprinkled on top.

A controlled vocabulary is made up of two components: A `simpleType`
enumeration of vocabulary terms and a corresponding `complexType`
implementation of the `ControlledVocabularyStringType` which leverages the
`simpleType` enumeration of vocabulary terms.

The `simpleType` enumeration and the `complexType` implementation names will
share a prefix and a version but will deviate otherwise:  

* `[CamelCasedPrefix]TypeEnum-x.y.z` for the `simpleType` enumeration of terms.
* `[CamelCasedPrefix]TypeVocab-x.y.z` for the `complexType` vocabulary implementation

In both cases, the `x.y.z` portion of the type name reflect the
`major.minor.update` version of the controlled vocabulary. The `update` part of
the version string can be omitted if there have been no update revisions of the
controlled vocabulary.

**Example:**

The following demonstrates the naming conventions for the controlled vocabulary
for CybOX Object relationship types:  

* `ObjectRelationshipTypeEnum-1.1` (the `simpleType` enumeration of Object relationship terms)
* `ObjectRelationshipTypeVocab-1.1` (the `complexType` vocabulary implementation)


#### XML Elements

Underscore-separated with first letter of each term capitalized (unless the
term is an acronym in which case each letter is capitalized).

**Examples:**  

* `File_Path`
* `Number_Of_Objects`
* `PDF_File`


#### XML Attributes

Underscore separated with each term being lowercase.

**Examples:**  
* `vocab_reference`
* `is_case_sensitive`


## CybOX Language Design Patterns

The CybOX Language follows XML Schema design patterns described below.


### Container Elements

In XML Schema, authors can define flat lists of elements by setting the
`maxOccurs` attribute on an element definition to either `unbounded` or to a
value greater than `1`. Instances of a schema with flat listing such as this
will contain several elements all with the same name.

The following examples demonstrate a flat listing of `book` elements contained
within a `library` element.

**XML Schema**

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"> 
  <xs:element name="library" type="LibraryType"/>
  
  <xs:complexType name="LibraryType">
    <xs:sequence>
     <xs:element name=”name” type=”xs:string”/>
      <xs:element name=”address” type=”xs:string”/>
      <xs:element name="book" maxOccurs="unbounded" type=”xs:string”/>
    </xs:sequence>
  </xs:complexType>
</xs:schema>
```

**XML Instance**

```xml
<library>
  <name>The Foo Library</name>
  <address>101 Binary Lane Somerville, MA 02144</address>
  <book>The Fellowship of the Ring</book>
  <book>The Two Towers</book>
  <book>The Return of the King</book>
</library>
```

The CybOX XML schemas utilize a “container element" pattern, where lists of
elements are collected under a parent container element. Using the example
above, to align with CybOX design patterns we would encapsulate the `book`
element instances within a `books` container element. This would require the
creation of a collection data type called `BooksType`.

**XML Schema**

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"> 
  <!-- root element -->
  <xs:element name="library" type="LibraryType"/>
  
  <!-- book container -->
  <xs:complexType name="BooksType">
    <xs:sequence>
      <xs:element name="book" type="xs:string" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:complexType>
  
  <!-- LibraryType data type -->
  <xs:complexType name="LibraryType">
    <xs:sequence>
      <xs:element name="name" type="xs:string"/>
      <xs:element name="address" type="xs:string"/>
      <xs:element name="books" type="BooksType"/>
    </xs:sequence>
  </xs:complexType>
</xs:schema>
```

**XML Instance**

```xml
<library>
  <name>The Foo Library</name>
  <address>101 Binary Lane Somerville, MA 02144</address>
  <books>
    <book>The Fellowship of the Ring</book>
    <book>The Two Towers</book>
    <book>The Return of the King</book>
  </books>
</library>
```


### Global Data Types

XML Schema allows data types to be defined from within element definitions
(i.e, inline). In CybOX, we define all of our data types at the global level
(i.e., outside of element definitions) so as to better enable reuse of data
types.


#### XML Schema (anonymous inline type definition)

The following XML Schema example demonstrates a `library` with a `books`
element containing an inline `complexType` definition. Notice that the inline
`complexType` has no `name` attribute, meaning it is anonymous and cannot be
referenced from outside its parent `element`.

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"> 
  <!-- root element -->
  <xs:element name="library" type="LibraryType"/>
  
  <!-- LibraryType data type -->
  <xs:complexType name="LibraryType">
    <xs:sequence>
      <xs:element name="name" type="xs:string"/>
      <xs:element name="address" type="xs:string"/>
      <xs:element name="books">
        <!-- inline complexType -->
        <xs:complexType>
          <xs:sequence>
            <xs:element name="book" type="xs:string" maxOccurs="unbounded"/>
          </xs:sequence>
        </xs:complexType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:schema>
```


#### CybOX Schema (global type definition)

The following example takes the schematic structure above, but aligns itself
with the CybOX XML "global type definition" pattern.

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"> 
  <!-- root element -->
  <xs:element name="library" type="LibraryType"/>
  
  <!-- book container -->
  <xs:complexType name="BooksType">
    <xs:sequence>
      <xs:element name="book" type="xs:string" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:complexType>
  
  <!-- LibraryType data type -->
  <xs:complexType name="LibraryType">
    <xs:sequence>
      <xs:element name="name" type="xs:string"/>
      <xs:element name="address" type="xs:string"/>
      <xs:element name="books" type="BooksType"/>
    </xs:sequence>
  </xs:complexType>
</xs:schema>
```


### CybOX Object Reuse

The CybOX XML Language is designed to facilitate Object reuse, so as to enforce
consistent methods for characterizing cyber observable information. This is
enabled via the definition of [global data types](#global-data-types) and
unique [CybOX Object namespaces](#namespaces).


#### Example

The following example demonstrates Object reuse through the `WhoisObjectType`,
which utilizes the `AddressObjectType` for the characterization of IP address
information.

```xml
<xs:complexType name="WhoisObjectType">
  <xs:complexContent>
    <xs:extension base="cyboxCommon:ObjectPropertiesType">
      <xs:sequence>
        <!-- SNIP -->
        <xs:element name="IP_Address" type="AddressObj:AddressObjectType" minOccurs="0">
          <xs:annotation>
            <xs:documentation>The IP_Address field specifies the corresponding ip address for this whois entry. The usually corresponds to a nameserver lookup.</xs:documentation>
          </xs:annotation>
        </xs:element>
        <!-- SNIP -->
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

Another form of Object reuse is demonstrated through the extension of CybOX
Object definitions as described in the [Indirect Extension of
ObjectPropertiesType](#indirect-extension-of-objectpropertiestype) section. As
detailed in that section, by extending existing CybOX Objects the CybOX
Language enforces consistent methods for the representation of cyber
oberservable information.


## CybOX Patterning

CybOX patterns are a generalization of CybOX content. They allow users and
developers to characterize a set, a range, or other generalized characteristics
of a cyber observable and its properties. For instance, one could use CybOX
patterns to describe a URL that matches one of a set of possible URL values.


### Example

The following XML snippet expresses a pattern on a file where a regular
expression is applied to the `File_Name` field:

```xml
<cybox:Object id="example:Object-dae8802e-b0df-4989-9ac3-d816b153842b">
  <cybox:Properties xsi:type="FileObj:FileObjectType">
    <FileObj:File_Name pattern_type="Regex">bad_file[0-9]{2,5}\.exe</FileObj:File_Name>
  </cybox:Properties>
</cybox:Object>
```


## CybOX Object Versioning

The [CybOX Language Versioning
Policy](http://cybox.mitre.org/language/versioning_policy.html) details the
current methodology for determining whether a new revision will require a major
version change, minor version change, or a version update, and how version
information is represented and conveyed in the CybOX Language.


## XML Considerations

The CybOX Language is currently defined in XML Schema and as such, it is
necessary to understand XML Schema when creating a CybOX Object. This is not
intended to be a tutorial on XML Schema but only an introduction of XML Schema
design considerations that may come up when working to define a CybOX Object.


### Complex vs. Simple Types

When creating a data type in XML Schema, an author can define it as a
`simpleType` or a `complexType`. 

A `simpleType` is an XML structure which can contain only textual data, whether
that textual data is a string, hexbinary, a date, an integer, or something else
entirely. A `simpleType` can specify a restriction on allowed values (e.g., via
an enumeration of acceptable values or a bounded range). An important aspect of
the `simpleType` is that instances cannot have nested child elements or
attributes.

**Example `simpleType` instance:**

```xml
<foo:bar>hello world!</foo:bar>
```

A `complexType` structure can contain textual data (just as with a
`simpleType`) or nested structures and also make use of attributes.

**Example `complexType` instance:**

```xml
<foo:exampleComplexTypeInstance id="1">
   <foo:bar>hello world!</foo:bar>
</foo:exampleComplexTypeInstance>
```

**Note:** Almost all CybOX Object fields are `complexTypes` because of the need
for attributes that support patterning or other capabilities and use cases.


### Namespaces

XML namespaces provide a method of avoiding naming conflicts for elements and
attributes. Each CybOX XML Schema defines a separate namespace, allowing for
mixing of data types and fields between and within schemas. When creating a
CybOX Object, an author will need to define their own namespace for their
schema types and fields to exist within.


### XSI Typing

XML Schema Instance (XSI) Typing refers to a mechanism by which XML instance
data explicitly asserts its implementation type.

The CybOX Language makes use of XSI Typing when leveraging CybOX Objects,
Controlled Vocabularies, and other extension points where authors can override
default CybOX constructs or plug in new constructs not defined by the CybOX
Language itself.

When writing content that leverages CybOX Objects, authors will leverage the
`xsi:type` attribute to declare the type of CybOX Object being used.

**Example CybOX Object instance:**

```xml
<cybox:Object>
  <cybox:Properties xsi:type="AddressObj:AddressObjectType" category="ipv4-addr">
    <AddressObj:Address_Value>192.168.0.5</AddressObj:Address_Value>
  </cybox:Properties>
</cybox:Object>
```

The example above uses `xsi:type="AddressObj:AddressObjectType"` to declare
this object as being of type, `AddressObjectType`.


### Elements vs. Attributes

The question of whether to use attributes or elements for data fields is often
debatable and difficult to answer in a generic sense. The IBM developerWorks
article, ["Principles of XML design: When to use elements versus
attributes"](http://www.ibm.com/developerworks/library/x-eleatt/) does a
fantastic job of describing the considerations one must make when modeling data
in XML Schema with respect to XML elements and attributes.

Thankfully, when it comes to CybOX the answer to “element vs. attribute” debate
is a bit more clear. CybOX provides [data types](#cybox-xml-schema-data-types)
which can be leveraged when defining properties for a CybOX Object. These data
types provide attributes for CybOX patterning as well as other use cases which
may want to be leveraged when defining properties for a CybOX Object. If Object
field data lends itself to [patterning capabilities](#cybox-patterning) then it
should be defined using an XML element whose type is one of the [CybOX Object
Property Types](#object-property-data-types:-objectpropertytype).

**Note:** There is no `BooleanObjectPropertyType` so typically attributes are
used for recording boolean data. CybOX leverages elements for almost all data
fields with the exception of `boolean` data, so a good rule of thumb is to
first assume that a field in CybOX should defined as an element and only after
careful consideration should it be defined as an attribute instead.
