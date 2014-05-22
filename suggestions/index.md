---
layout: flat
title: 
---

## General readability of XML
Only include namespaces that are actually used

Use standardized namespace prefix names 

Group your namespaces together logically

Leave out default attributes unless specifically using it (i.e. `@negate` for an Indicator)

Include schemaLocation attributes pointing to the `mitre.org` hosted CybOX schemas


## IDs should be unique

Each item represented in CybOX is assumed to be globally unique, and follows the format for [XML QNames](http://en.wikipedia.org/wiki/QName)

You should define a namespace prefix based on the person or tool creating the indicator, appended to the type of indicator and a Globally Unique ID 

For instance if Acme Corp. is creating an indicator of the `observable` type:

`acme:observable-79090715-8d6a-46b7-943b-c0bb9e063788`

Define the `acme` namespace prefix in the head of your XML document like so:

```xml
<cybox:Observables xmlns:acme="http://acme.example.com" >
```

You should maintain a mapping of an indicator's CybOX ID in order to modify it in the future.

## Abstracting files and processes as objects

The way you represent common objects should [follow these conventions](/suggestions/objects) 


## Referencing an object elsewhere

Use the `idref` attribute by itself in a `Related_Object` to point to a different object:

```xml
<cybox:Related_Object idref="acme:mutexobj-3c1221bd-2037-45ec-8129-4ba8d791e86b" />
```


## Embedding an object directly

Objects can also be contained within another CybOX object

For instance, to encapsulate a `mutex` value created by an executable file: 

```xml
<cybox:Object id="acme:fileobj-f7304dae-94c6-4592-b943-398e1e6916a7">
  <cybox:Properties xsi:type="FileObj:FileObjectType"> 
  </cybox:Properties>
  <cybox:Related_Objects>
    <cybox:Related_Object id="acme:mutexobj-3c1221bd-2037-45ec-8129-4ba8d791e86b">
      <cybox:Properties xsi:type="MutexObj:MutexObjectType"> 
      </cybox:Properties>
    <cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.0">Created
    </cybox:Relationship>
  </cybox:Related_Object>
</cybox:Object>
```

In most cases, it's preferrable to reference the object by `idref` as follows:

```xml
<cybox:Object id="acme:fileobj-f7304dae-94c6-4592-b943-398e1e6916a7">
  <cybox:Properties xsi:type="FileObj:FileObjectType">
  </cybox:Properties>
  <cybox:Related_Objects>
    <cybox:Related_Object idref="acme:mutexobj-3c1221bd-2037-45ec-8129-4ba8d791e86b" />
    <cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.0">Created</cybox:Relationship>
  </cybox:Related_Object>
</cybox:Object>
```


## Using Vocabularies

A `vocabulary` is an optional way of limiting options for a given field. For instance, the relationship between objects may be limited to `Created`, `Read_From`, etc.

We provide a [default set ](https://github.com/CybOXProject/schemas/blob/master/cybox_default_vocabularies.xsd) that should cover the majority of use cases.

Custom vocabularies can be defined to cover your particular need

## Pattern vs. Instance
CybOX observables are capable of representing both instance observables
(specific events or properties that were observed) or pattern observables (patterns of events or properties that may potentially be observed). The conditional nature of patterns is expressed through the use of the @condition attribute on the fields within the observable. If the @condition attribute is set, that denotes that the field is part of a pattern.

Because it doesn't make sense to mix pattern fields with instance field, if @condition is set on any fields it should be set on all fields. You should not mix and match fields with @condition set and fields without @condition set.

## Capturing Custom Tool Properties
Sometimes, a tool will capture properties about a CybOX object that aren't in the schema for that object type. In some cases this is because the schemas need to be expanded to cover that property, but in other cases this is because the tool is collecting derived information or other properties that are not generally represented for that object type.

In either case, those properties should be collected using the ```Custom_Properties``` element of the object properties. This is essentially a simple list of key/value pairs:

```
<cybox:Properties xsi:type="FileObj:FileObjectType">
  <cyboxCommon:Custom_Properties>
    <cyboxCommon:Property name="Property Name">Property Value</cyboxCommon:Property>
  </cyboxCommon:Custom_Properties>
  <!-- Other properties from the FileObjectType schema -->
</cybox:Properties>
```

When capturing the output from a tool, the suggested practice is to set the ```@name``` attribute of the custom property to the exact field name used in the tool. If possible, the ```@datatype``` attribute should be set to the datatype that will be output and the value formatted to fit that datatype's formatting. If that's not possible, the exact value reported by the tool should be used and the ```@datatype``` attribute should be omitted.

## Example
The Bro tool captures the HTTP Transaction depth of an HTTP connection. In the Bro output, this field is called "trans_depth" and the value will be set to some integer (whatever the depth is). So the ```@name``` attribute should be set to ```trans_depth```, the value should be set to the output from Bro, and the ```@datatype``` attribute should be set to "int" (Integer). That would give you something like:

```
<cyboxCommon:Custom_Properties>
  <cyboxCommon:Property name="trans_depth" datatype="int">3</cyboxCommon:Property>
</cyboxCommon:Custom_Properties>
```
