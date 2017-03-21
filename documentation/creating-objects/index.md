---
layout: flat
title: How to Create a CybOX Object
---

This page is intended to explain the process of creating a new CybOX Object for
characterizing cyber observable data outside the scope of the current [CybOX
Object set](../objects). The concept of a **CybOX Object** referred to here is,
more specifically, a set of schema-defined properties that can be used to
characterize a given object in the cyber domain.

This guide assumes that the reader has some proficiency in both the CybOX
Language and XML Schema; the [Background](../background) page provides more
detailed information about topics whose knowledge is assumed by this guide.
Please look to the [Further Reading](#further-reading) section for more CybOX
Language and XML Schema authoring resources.

***

**Use the following steps to create and use a new CybOX Object:**

1. Decide what it is you want to represent in CybOX.
2. Determine what fields/attributes can be used to characterize that CybOX
   Object.
3. Map those field data types to existing CybOX Object Property Types.
4. Review existing CybOX Objects to see if the capabilities defined in steps
   1-3 are already supported by an existing CybOX Object. Identify capability
   gaps if an existing CybOX object supports a subset of desired capabilities.
5. Define a namespace for the object.
6. Create the object schema.
7. Add documentation to the schema.
8. Use the newly-created object in CybOX content.


## Walkthrough: Creating a Simple IP Address Object

This walkthrough demonstrates the creation of a CybOX Object for the
characterization of IP address information. 

**Note:** CybOX already provides an `AddressObjectType` which can be used to
characterize IP address, CIDR block, Email address, and other cyber address
information. This walkthrough will demonstrate the creation of a CybOX Object
which is a subset of the `AddressObject`. This walkthrough largely pretends
that the `AddressObject` schema and its data types does not exist.


### 1. Decide What to Represent

For this walkthrough, we want to characterize IP Address information.


### 2. Determine Important Fields and Attributes

An IP address by itself is conceptually fairly simple. We will want to provide
the following fields:

* Address value (e.g., `10.0.0.1`)
* Address category (e.g., `ipv4` or `ipv6`)
* Source or destination flags (e.g., `is_source` or `is_destination`)


### 3. Map Fields to CybOX Data Types

The following represents a notional mapping of fields to CybOX data types:

* **Address value:** `StringObjectPropertyType`
  * An IPv4 address is typically represented in a dotted-decimal format which
    lends itself to `String` data. 
  * An IPv6 address is typically represented in a notation specified in [RFC
    5952](http://tools.ietf.org/html/rfc5952) which lends itself to `String`
    data.
  * Pattern authors may want to express ranges, lists, or regular expressions
    for IP addresses. As such, this field lends itself to [CybOX
    patterning](../background#cybox-patterning).
* **Address category:** `xs:string XML attribute`
  * Address categories in this case will either be `ipv4` or `ipv6`, which
    typically does not lend itself to [CybOX
    patterning](../background#cybox-patterning) capabilities as authors would
    likely not define regular expressions for category types, ranges of
    categories, boundaries on categories (e.g., `GreaterThan`) or lists of
    categories. As such, we will record this data within an XML attribute.
* **Source and Destination flags:** `xs:boolean XML attributes`
  * Like the `Address category` field mentioned above, this field does not lend
    itself to CybOX Patterning, as the flags will only contain `boolean` data. 


### 4. Review Existing CybOX Objects

At this point, a CybOX Object author should review the [existing set of CybOX
Objects](../objects) to determine if:

* the desired capabilities already exist in one or more CybOX Objects, 
* a subset of capabilities exist in one or more CybOX Objects, or 
* it is not possible to represent the current cyber observable data using
  existing CybOX Objects.


#### Desired Capabilities Already Exist

Work smart, not hard! That is to say, a CybOX author shouldn't redefine
existing capabilities if they don't have to. 

Using existing CybOX Objects for the characterization of cyber observable
information is strongly encouraged over implementing a third-party Object type!
Using existing CybOX Objects reinforces the practice of consistent
representation of cyber observable information, and thereby promotes
interoperability among CybOX consumers.

This walkthrough is actually a bit of an example of what **not** to do! Though
we're ignoring it for the sake of demonstration, the CybOX Language already
provides an Object for representation of cyber address information, including
IP addresses: `AddressObjectType`. A review of the existing set of CybOX
Objects would have revealed the `AddressObjectType`, allowing the CybOX author
to leverage it rather than create an entirely new CybOX Object for the
representation of IP address information.


#### A Subset of Desired Capabilities Exist

If a CybOX Object exists that supports a subset of the desired capabilities it
is encouraged that CybOX Object authors identify the capability gaps with that
existing CybOX Object and extend it to fill in the gaps rather than creating an
entirely new CybOX Object which redefines its existing structure, fields, and
capabilities. Duplicating fields and capabilities across CybOX Objects and XML
namespaces can introduce inconsistent methods for representing cyber observable
information and could potentially fragment the state of the practice with
respect to CybOX content authoring and consumption.

An example where the CybOX XML Schema demonstrates Object extension is the
`WindowsFileObjectType` schema definition. Many of the fields that could be
used to characterize Windows File observable information were already defined
in the `FileObjectType` schema definition. Rather than redefining the existing
fields and the structure of `FileObjectType`, the `WindowsFileObjectType` was
designed to extend the `FileObjectType`, thereby inheriting fields from
`FileObjectType` such as `File_Name` and `Size_In_Bytes`. The
`WindowsFileObjectType` then defines its own fields which are specific to the
characterization of Windows file observables.

```xml
<xs:complexType name="WindowsFileObjectType">
  <xs:annotation>
    <xs:documentation>The WindowsFileObjectType type is intended to characterize Windows files.</xs:documentation>
  </xs:annotation>
  <xs:complexContent>
    <xs:extension base="FileObj:FileObjectType">
      <!-- INHERITS PROPERTIES FROM FILEOBJECTTYPE -->
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```


#### No Existing Object Supports Desired Capabilities

Though the CybOX Language defines many Objects for the representation of cyber
observable information, CybOX content authors may wish to characterize cyber
observable information that is not currently possible given the set of existing
Object types. If there are no existing CybOX Objects which support capabilities
desired by a CybOX author, the creation of an entirely new CybOX Object may be
required. This is accomplished by defining a CybOX Object that extends the
[ObjectPropertiesType](../background#object-base-data-type:-objectpropertiestype).

Because this walkthrough ignores the existence of the `AddressObject`, we will
need to create a brand new CybOX Object which extends the base
`ObjectPropertiesType`.


### 5. Define a Namespace for the Object

Like other CybOX Objects, this Object will reside within its own XML namespace.
If this Object is being designed to be used internally by an organization, the
namespace will likely reflect that organizations identity. For example, the
core set of CybOX Objects refer to `mitre.org` in their namespaces (e.g.,
`http://cybox.mitre.org/objects#AddressObject-2` for the CybOX v2.1
`AddressObject` namespace).

For this example, we will define this Object schema within the
`http://example.com/objects#IPAddressObject-1` namespace as this will be
version `1.0` of the schema. Please refer to the [CybOX Object
Namespaces](../background#cybox-object-namespaces) for more information
regarding this format.


### 6. Create the Object Schema

Now that the fields for this Object have been identified and mapped to CybOX
and XML data types and the namespace for this Object has been created, the
Object is ready to be defined in XML Schema.

```xml
<xs:schema elementFormDefault="qualified"
  xmlns:xs="http://www.w3.org/2001/XMLSchema" 
  xmlns:cyboxCommon="http://cybox.mitre.org/common-2"
  xmlns:IPAddressObj="http://example.com/objects#IPAddressObject-1" 
  targetNamespace="http://example.com/objects#IPAddressObject-1"
  version="1.0">
 
  <!-- Import CybOX Common schema so that we can use its data types -->
  <xs:import namespace="http://cybox.mitre.org/common-2" schemaLocation="http://cybox.mitre.org/XMLSchema/common/2.1/cybox_common.xsd"/>
</xs:schema>
```

The XML snippet above defines our root `xs:schema` element and sets up all the
necessary namespace definitions and schema imports. The
`elementFormDefault="qualified"` line states that any elements used by an XML
instance document which were defined in this schema must be namespace
qualified.

Now we can create our `IPAddressObjectType` implementation of
`ObjectPropertiesType`.

```xml

<xs:schema elementFormDefault="qualified"
  xmlns:xs="http://www.w3.org/2001/XMLSchema" 
  xmlns:cyboxCommon="http://cybox.mitre.org/common-2" 
  xmlns:IPAddressObj="http://example.com/objects#IPAddressObject-1" 
  targetNamespace="http://example.com/objects#IPAddressObject-1"
  version="1.0">
  
  <xs:import namespace="http://cybox.mitre.org/common-2" schemaLocation="http://cybox.mitre.org/XMLSchema/common/2.1/cybox_common.xsd"/>
  
  <xs:element name="IP_Address" type="IPAddressObj:IPAddressObjectType"/>
  
  <xs:complexType name="IPAddressObjectType">
    <xs:complexContent >
      <xs:extension base="cyboxCommon:ObjectPropertiesType"/>
    </xs:complexContent>
  </xs:complexType>
</xs:schema>
```

The above XML snippet introduces two new global XML structures: an `IP_Address`
element and an `IPAddressObjectType` implementation of `ObjectPropertiesType`.
By extending `ObjectPropertiesType`, we inherit fields like `Custom_Properties`
and `object_reference` and enable it to be inserted into the CybOX `Object`
data model via the `Properties` field, which is of type `ObjectPropertiesType`.

Now that the basic structure for `IPAddressObjectType` has been put in place,
we can start adding the fields we defined in [Step
3](#3.-map-fields-to-cybox-data-types).

```xml
<xs:schema elementFormDefault="qualified"
  xmlns:xs="http://www.w3.org/2001/XMLSchema" 
  xmlns:cyboxCommon="http://cybox.mitre.org/common-2" 
  xmlns:IPAddressObj="http://example.com/objects#IPAddressObject-1" 
  targetNamespace="http://example.com/objects#IPAddressObject-1"
  version="1.0">
  
  <xs:import namespace="http://cybox.mitre.org/common-2" schemaLocation="http://cybox.mitre.org/XMLSchema/common/2.1/cybox_common.xsd"/>
  
  <xs:element name="IP_Address" type="IPAddressObj:IPAddressObjectType"/>
  
  <xs:complexType name="IPAddressObjectType">
    <xs:complexContent>
      <xs:extension base="cyboxCommon:ObjectPropertiesType">
        <xs:sequence>
          <!-- Add IP_Address_Value StringObjectProperty type field-->
          <xs:element name="IP_Address_Value" type="cyboxCommon:StringObjectPropertyType" minOccurs="0"/>
        </xs:sequence>
        <!-- Add category attribute for declaring IPv4 or IPv6 -->
        <xs:attribute name="category" type="xs:string" use="optional"/>
        
        <!-- Add is_source attribute for declaring if IP address is a source address -->
        <xs:attribute name="is_source" type="xs:boolean" use="optional"/>
        
        <!-- Add is_destination attribute for declaring if IP address is a destination address -->
        <xs:attribute name="is_destination" type="xs:boolean" use="optional"/>
      </xs:extension>
    </xs:complexContent>
  </xs:complexType>
</xs:schema>
```

At this point, we have defined the `IPAddressObjectType` and given it the
following fields: `IP_Address_Value`, `category`, `is_source`, and
`is_address`. All of these field names and types align with the [CybOX Language
design patterns](../background#cybox-language-design-patterns), [data
type](../background#cybox-xml-schema-data-types) usages, and [naming
conventions](../background#cybox-naming-conventions).

We can take this another step further, however. The `category` attribute is
currently defined as being of type `xs:string`, meaning content authors can
insert anything they wish into that field as a value. In reality, we only want
that field to convey whether the described IP address is an IPv4 or IPv6
address. To restrict the set of allowable field values, we can establish an
enumeration of `category` values.

```xml
<xs:simpleType name="CategoryTypeEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="ipv4"/>
    <xs:enumeration value="ipv6"/>
  </xs:restriction>
</xs:simpleType>
```

The above XML snippet defines an enumeration of `category` values. Now we set
the `category` attribute type to `CategoryTypeEnum` to restrict the set of
allowable values to this enumeration.

```xml
<xs:attribute name="category" type="IPAddressObj:CategoryTypeEnum" use="optional"/>
```

The entire schema looks like this:

```xml
<xs:schema elementFormDefault="qualified"
  xmlns:xs="http://www.w3.org/2001/XMLSchema" 
  xmlns:cyboxCommon="http://cybox.mitre.org/common-2" 
  xmlns:IPAddressObj="http://example.com/objects#IPAddressObject-1" 
  targetNamespace="http://example.com/objects#IPAddressObject-1"
  version="1.0">
  
  <xs:import namespace="http://cybox.mitre.org/common-2" schemaLocation="http://cybox.mitre.org/XMLSchema/common/2.1/cybox_common.xsd"/>
  
  <xs:element name="IP_Address" type="IPAddressObj:IPAddressObjectType"/>
  
  <xs:complexType name="IPAddressObjectType">
    <xs:complexContent>
      <xs:extension base="cyboxCommon:ObjectPropertiesType">
        <xs:sequence>
          <xs:element name="IP_Address_Value" type="cyboxCommon:StringObjectPropertyType" minOccurs="0"/>
        </xs:sequence>
        <xs:attribute name="category" type="IPAddressObj:CategoryTypeEnum" use="optional"/>
        <xs:attribute name="is_source" type="xs:boolean" use="optional"/>
        <xs:attribute name="is_destination" type="xs:boolean" use="optional"/>
      </xs:extension>
    </xs:complexContent>
  </xs:complexType>
  
  <xs:simpleType name="CategoryTypeEnum">
    <xs:restriction base="xs:string">
      <xs:enumeration value="ipv4"/>
      <xs:enumeration value="ipv6"/>
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```


### 7. Add Documentation

The CybOX Schema types and elements are thoroughly documented, so it is
strongly suggested that when creating a CybOX Object, authors document their
CybOX Objects, types, and fields. The following XML Schema shows the
`IPAddressObject` schema we defined above in a fully-documented state:

```xml
<xs:schema elementFormDefault="qualified"
  xmlns:xs="http://www.w3.org/2001/XMLSchema" 
  xmlns:cyboxCommon="http://cybox.mitre.org/common-2" 
  xmlns:IPAddressObj="http://example.com/objects#IPAddressObject-1" 
  targetNamespace="http://example.com/objects#IPAddressObject-1"
  version="1.0">
  
  <xs:import namespace="http://cybox.mitre.org/common-2" schemaLocation="http://cybox.mitre.org/XMLSchema/common/2.1/cybox_common.xsd"/>
  
  <xs:element name="IP_Address" type="IPAddressObj:IPAddressObjectType">
    <xs:annotation>
      <xs:documentation>An element instance of IPAddressObjectType.  Used for the characterization of IP address information.</xs:documentation>
    </xs:annotation>
  </xs:element>
  
  <xs:complexType name="IPAddressObjectType">
    <xs:annotation>
      <xs:documentation>The IPAddressObjectType characterizes IP address information.</xs:documentation>
    </xs:annotation>
    <xs:complexContent >
      <xs:extension base="cyboxCommon:ObjectPropertiesType">
        <xs:sequence>
          <xs:element name="IP_Address_Value" type="cyboxCommon:StringObjectPropertyType" minOccurs="0">
            <xs:annotation>
              <xs:documentation>The IP_Address_Value field is used for recording an IP Address value (e.g., 10.0.0.1).</xs:documentation>
            </xs:annotation>
          </xs:element>
        </xs:sequence>
        <xs:attribute name="category" type="IPAddressObj:CategoryTypeEnum" use="optional">
          <xs:annotation>
            <xs:documentation>The category field is used for recording the IP address category. Permitted values are defined by the CategoryTypeEnum.</xs:documentation>
          </xs:annotation>
        </xs:attribute>
        <xs:attribute name="is_source" type="xs:boolean" use="optional">
          <xs:annotation>
            <xs:documentation>The is_source field can be set to 'true' if the IP address is a source address.</xs:documentation>
          </xs:annotation>
        </xs:attribute>
        <xs:attribute name="is_destination" type="xs:boolean" use="optional">
          <xs:annotation>
            <xs:documentation>The is_destination field can be set to 'true' if the IP address is a destination address.</xs:documentation>
          </xs:annotation>
        </xs:attribute>
      </xs:extension>
    </xs:complexContent>
  </xs:complexType>
  
  <xs:simpleType name="CategoryTypeEnum">
    <xs:annotation>
      <xs:documentation>The CategoryTypeEnum defines categories (e.g., IPv4/IPv6) of IP Addresses.</xs:documentation>
    </xs:annotation>
    <xs:restriction base="xs:string">
      <xs:enumeration value="ipv4">
        <xs:annotation>
          <xs:documentation>An IPv4 IP address.</xs:documentation>
        </xs:annotation>
      </xs:enumeration>
      <xs:enumeration value="ipv6">
        <xs:annotation>
          <xs:documentation>An IPv6 IP address.</xs:documentation>
        </xs:annotation>
      </xs:enumeration>
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```

***


### 8. Use the New Object!

Inserting a custom object into an instance XML document is done through the
same process as one would follow when inserting a core CybOX Object. The
following steps define how to write a simple CybOX XML instance document that
leverages the `IPAddressObject` we just created.

The first step is setting up a base CybOX Observables document.

```xml
<cybox:Observables
    xmlns:cybox="http://cybox.mitre.org/cybox-2"
    xmlns:cyboxCommon="http://cybox.mitre.org/common-2"
    xmlns:IPAddressObj="http://example.com/objects#IPAddressObject-1"
    xmlns:example="http://example.com"
    cybox_major_version="2" cybox_minor_version="1" cybox_update_version="0">
    <cybox:Observable id="example:Observable-6dde4f72-cca0-44f0-8206-f381accf6b87">
        <!-- Fill in Object -->
    </cybox:Observable>
</cybox:Observables>
```

The XML snippet above defines a base CybOX `Observables` document and
establishes namespace aliases for our `IPAddressObject` namespace, CybOX Core,
CybOX Common, and `http://example.com` namespaces. The `http://example.com`
namespace exists for the  `id` attributes, which are of type
[QName](http://en.wikipedia.org/wiki/QName) and must reference a defined
namespace.

**Note:** Adding the namespace alias for the IP Address Object CybOX Object
    allows us to insert the Object using an
    [xsi:type](../background#xsi-typing) declaration on a field.

Now that the base Observables document has been created, we can define an IP
Address Object instance.

```xml
<cybox:Object>
    <cybox:Description>An IP Address</cybox:Description>
    <cybox:Properties xsi:type="IPAddressObj:IPAddressObjectType" is_source="true">
        <IPAddressObj:IP_Address_Value>10.0.0.1</IPAddressObj:IP_Address_Value>  
    </cybox:Properties>
</cybox:Object>
```

The above XML snippet defines a CybOX `Object` instance whose `Properties`
element is an instance of the `IPAddressObjectType`. The `Properties`
implementation is explicitly declared via the `xsi:type` attribute.

The full XML instance document is detailed below.

```xml
<cybox:Observables 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:cybox="http://cybox.mitre.org/cybox-2"
    xmlns:IPAddressObj="http://example.com/objects#IPAddressObject-1"
    xmlns:example="http://example.com/"
    xsi:schemaLocation="
    http://cybox.mitre.org/cybox-2 http://cybox.mitre.org/XMLSchema/core/2.1/cybox_core.xsd
    http://example.com/objects#IPAddressObject-1 http://example.com/some/path/to/IPAddressObject.xsd"
    
    cybox_major_version="2" cybox_minor_version="1" cybox_update_version="0">
    <cybox:Observable id="example:Observable-6dde4f72-cca0-44f0-8206-f381accf6b89">
        <cybox:Object>
            <cybox:Description>An IP Address</cybox:Description>
            <cybox:Properties xsi:type="IPAddressObj:IPAddressObjectType" category="ipv4" is_source="true">
                <IPAddressObj:IP_Address_Value>10.0.0.1</IPAddressObj:IP_Address_Value>
            </cybox:Properties>
        </cybox:Object>
    </cybox:Observable>
</cybox:Observables>
```


## Publishing

Have you written a CybOX Object and want to have it included in the CybOX
Language? Simply subscribe to the open [CTI Users List](http://cyboxproject.github.io/community/#cti-users-list) or the [CTI TC Public Comment List](http://cyboxproject.github.io/community/#public-comment-list), and make your submission.


## Further Reading

* [Getting Started With CybOX](https://github.com/CybOXProject/schemas/wiki/Getting-Started)
* [CybOX Authoring Suggested Practices](https://github.com/CybOXProject/schemas/wiki/Suggested-Practices)
* [STIX Documentation Website](https://oasis-open.github.io/cti-documentation/)
* [Principles of XML Design: When to Use Elements vs. Attributes](http://www.ibm.com/developerworks/library/x-eleatt/)
* [Principles of XML Design: Considering Container Elements](http://www.ibm.com/developerworks/xml/library/x-contain/index.html)


## Feedback

Let us know if there are ways we can improve this documentation! If there is
anything we didn't explain well (or completely left out on accident) tell us by
submitting an issue to the [CybOX schema issue
tracker](https://github.com/CybOXProject/schemas/issues), or by subscribing and submitting comments to the [CTI Users List](http://cyboxproject.github.io/community/#cti-users-list) or the [CTI TC Public Comment List](http://cyboxproject.github.io/community/#public-comment-list).
