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

CybOX Objects schemas define sets of properties for common cyber objects. 

To support practical use, CybOX provides an extensive set of Object property specifications by default.

This predefined set includes a broad range of object types across the cyber domain (network, host, files, memory, devices, etc.) as well as objects of varying levels of specificity/abstraction intended for differing use cases.

The approach to [defining Objects](../creating-objects) (especially those across varying levels of specificity/abstraction) is intended to pursue architectural consistency and reuse by having more complex or specific variations on Objects leverage other more abstract existing Objects for sets of properties.

There are two primary variations of this:

* Objects that derive from other Objects of the same basic type along a spectrum of abstract to more specific.
 * For example, **File -> Win File -> Win EXE File** where CybOX defines a basic [File Object] ({{site.stix_url}}/FileObj/FileObjectType) with general file properties applicable across platforms, a more specific [Win_File Object] ({{site.stix_url}}/WinFileObj/WindowsFileObjectType) that extends the general File Object and adds Windows-specific file properties, and an even more specific [Win_Executable_File Object] ({{site.stix_url}}/WinExecutableFileObj/WindowsExecutableFileObjectType) which extends the Win_File Object and adds properties for executable files under Windows.
* Objects that leverage other Objects to define more specific properties for differing and more specialized use cases.
  * For example, the set of Objects specified that can contain an **IP Address**.
    * [Address Object] ({{site.stix_url}}/AddressObj/AddressObjectType) enables the specification of a particular IP Address (or other type of address) value and its type (e.g. ipv4-addr) without any other context. This can be used when you desire to characterize an IP Address but not to assert any given context for where you might find it (e.g. it may appear in any of a wide variety of logs). This Object also provides consistent specification of address properties for its use on its own or by more specific Objects that need to characterize addresses within more specific contexts.
    * [Socket_Address Object] ({{site.stix_url}}/SocketAddressObj/SocketAddressObjectType) enables the specification of a particular IP Address (or Hostname) and Port pairing. This obviously lets you characterize a more specific context for an IP Address but still leverages the AddressObjectType for its IP Address structure yielding consistency across the two Objects.
    * [Network_Connection Object] ({{site.stix_url}}/NetworkConnectionObj/NetworkConnectionObjectType) enables the specification of properties related to a network connection including Layer3, Layer4 and Layer7 details as well as details of the source socket and destination socket of the connection. This object leverages the SocketAddressType for its source and destination socket structures. This enables the characterization of very specific contextual details around an IP Address.
 

**It is suggested practice to always utilize the most specific CybOX Object possible for the context you are looking to convey and based on the properties you need to represent.**

* For example, if you know you are looking to describe a situation of network traffic to a particular IP Address, use the Network_Connection Object but if all you know is that an IP Address was seen or might be seen but you have no further context, use the Address Object. This also applies to the use of platform-agnostic Objects (e.g. File) and their derived platform-specifc Objects (e.g. Win_File). If you need to characterize properties from a more specific variation of an Object (e.g. the SID of a file), utilize that Object (e.g. Win_File) otherwise use the simplest version available that supports the properties you need to characterize.

**One clear exception to this is if conformance to a specific language Profile is required and that Profile restricts the set of available objects or directly specifies a particular Object to be used.**

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
`C:\Users\ExampleUser\Documents\ProjectX\MeetingNotes_2014-08-01.txt` or
`/home/exampleuser/ProjectX/MeetingNotes_2014-08-01.txt`

1. The `File_Name` field should specify the base name of the file, including
   extension.

    ```xml
    <cybox:Properties xsi:type="FileObj:FileObjectType">
      <FileObj:File_Name>MeetingNotes_2014-08-01.txt</FileObj:File_Name>
    </cybox:Properties>
    ```

2. The `File_Path` field should contain the path of the directory containing
   the file.  It should not contain the name of the file itself; instead, use
   the `File_Name` field for this information. The `File_Path` field should end
   with a path separator (slash `/` or backslash ` \ `, depending on the
   operating system).


    ```xml
    <cybox:Properties xsi:type="FileObj:FileObjectType">
      <FileObj:File_Name>MeetingNotes_2014-08-01.txt</FileObj:File_Name>
      <FileObj:File_Path>C:\Users\ExampleUser\Documents\ProjectX\</FileObj:File_Path>
    </cybox:Properties>
    ```

    ```xml
    <cybox:Properties xsi:type="FileObj:FileObjectType">
      <FileObj:File_Name>MeetingNotes_2014-08-01.txt</FileObj:File_Name>
      <FileObj:File_Path>/home/exampleuser/ProjectX/</FileObj:File_Path>
    </cybox:Properties>
    ```

3. Although the `File_Path` may be either relative or fully qualified, it
   should be fully qualified unless the file which the ``File_Path`` is
   relative to is specified via a `RelatedObject`. If you specify a relative
   path (with `fully_qualified="false"`), you should include a related object,
   either embedded or by reference.

    ```xml
    <cybox:Object id="example:File-1">
      <cybox:Properties xsi:type="FileObj:FileObjectType">
        <FileObj:File_Name>MeetingNotes_2014-08-01.txt</FileObj:File_Name>
        <FileObj:File_Path fully_qualified="false">ProjectX</FileObj:File_Path>
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

4. The `Device_Path` field specifies the path to the *partition* on which the
   file resides. This is *not* the same as the drive letter (`C:`); instead,
   use the `Drive` field on the `WindowsFileObject` for this. On Windows,
   `Device_Path` could be a path such as `\Device\Harddisk0\Partition0`. On
   Unix-like systems, this could be a path like `/dev/sda1`. You should not use
   a path to a physical disk, such as `\\.\PhysicalDrive1` on Windows or
   `/dev/sda` on Unix-like systems, since file systems are generally tied to
   partitions rather than physical disks.

5. The `Full_Path` field is used to specify a combination of `Device_Path` plus
   `File_Path`. You should not use this field unless it is not possible to
   split the `Full_Path` into the `Device_Path` and the `File_Path` fields; it
   is preferable to include this information separately under the component
   fields.

6. The `File_Extension` field should not be used for CybOX instance data;
   instead, the file extension should be included as part of the `File_Name`
   field.

   When expressing a CybOX pattern to match any file with a specific extension,
   a file, use the `condition="Equals"` attribute on the `File_Extension`
   field, rather than `condition="EndsWith"` or a regular expression on the
   `File_Name` field.

    **BAD**

    ```xml
    <cybox:Properties xsi:type="FileObj:FileObjectType">
      <FileObj:File_Name condition="EndsWith">.txt</FileObj:File_Name>
    </cybox:Properties>
    ```

    **GOOD**

    ```xml
    <cybox:Properties xsi:type="FileObj:FileObjectType">
      <FileObj:File_Extension condition="Equals">.txt</FileObj:File_Extension>
    </cybox:Properties>
    ```
