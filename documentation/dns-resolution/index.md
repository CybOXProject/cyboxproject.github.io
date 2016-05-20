---
layout: flat
title: Capturing DNS Resolution
---

CybOX supports a number of Objects and associated methods related to the capture of domain name system (DNS) resolution information. This page is intended to provide guidance on the appropriate use case for when each Object and/or method should be used.

## Capturing DNS Resource Records

Resource records are the basic data elements of the domain name system (DNS), and are used to store the types of information that can be retrieved via a DNS query. Such records capture data about the name and type of record, as well as the specific information contained in the record. Capturing and sharing information about DNS resource records without any additional context can be accomplished through the use of the [DNS Record Object](http://stixproject.github.io/data-model/1.1.1/DNSRecordObj/DNSRecordObjectType/), which includes the structure for natively representing any DNS resource record. 

### Example
This XML example demonstrates how an observed instance of an `A` record (which contains a 32-bit IPv4 address) for `fictionaldomain.net` that points to `192.168.1.42` would be captured and represented with the [DNS Record Object](http://stixproject.github.io/data-model/1.1.1/DNSRecordObj/DNSRecordObjectType/).

```xml
<cybox:Observable id="example:Observable-6775a719-bd39-4fe4-9ec8-cc9645b07eb6">
  <cybox:Object id="example:Object-449c075f-aa8d-4e63-bca0-30a2a78f3ff9">
    <cybox:Properties xsi:type="DNSRecordObj:DNSRecordObjectType">
      <DNSRecordObj:Domain_Name type="Domain Name">
        <URIObject:Value>fictionaldomain.net</URIObject:Value>
      </DNSRecordObj:Domain_Name>
      <DNSRecordObj:IP_Address category="ipv4-addr">
        <AddressObj:Address_Value>192.168.1.42</AddressObj:Address_Value>
      </DNSRecordObj:IP_Address>
      <DNSRecordObj:Entry_Type>A</DNSRecordObj:Entry_Type>
    </cybox:Properties>
  </cybox:Object>
</cybox:Observable>
```

## Capturing DNS Queries

There are two different contexts that pertain to the capture of data relating to DNS Queries:
* The capture of the information that can be expressed in a DNS query message.
* The capture of the activity that revolves around performing a DNS query, including the sending of the DNS query message and returned DNS record(s). 

### Capturing DNS Query Messages

DNS Query messages contain the structure that defines the particular domain name that is being queried, along with additional data such as the type of DNS record that is being requested. The content of such messages can be natively captured through the use of the [DNS Query Object](http://stixproject.github.io/data-model/1.1.1/DNSQueryObj/DNSQueryObjectType/). 

#### Example

This XML example demonstrates how an observed instance of a DNS Query message for the `AAAA` record of `asdfginc.org` would be captured and represented with the [DNS Query Object](http://stixproject.github.io/data-model/1.1.1/DNSQueryObj/DNSQueryObjectType/). 

```xml
<cybox:Observable id="example:Observable-76ebfe01-e83e-44fe-b387-64a68bb7a494">
  <cybox:Object id="example:Object-d8faea51-a541-4b4c-bac4-b2dd3a3fc419">
    <cybox:Properties xsi:type="DNSQueryObj:DNSQueryObjectType">
      <DNSQueryObj:Question>
        <DNSQueryObj:QName>
          <URIObject:Value>asdfginc.net</URIObject:Value>
        </DNSQueryObj:QName>
        <DNSQueryObj:QType>AAAA</DNSQueryObj:QType>
      </DNSQueryObj:Question>
    </cybox:Properties>
  </cybox:Object>
</cybox:Observable>
```

### Capturing DNS Query Activity

The activity around a DNS Query involves sending a request to a DNS server to retrieve a DNS record regarding a particular domain name, and thus can be thought of as a dynamic entity with two discrete components: 
* The query message component that contains the domain name and type of DNS record requested (e.g., A, MX, etc.).
* The response component that contains the requested DNS record information.

Therefore, as a dynamic entity, the activity around a DNS query can best be represented in CybOX through the use of an [Action](http://stixproject.github.io/data-model/1.1.1/cybox/ActionType/). In order to describe the nature of the action in a standard fashion, the [Action](http://stixproject.github.io/data-model/1.1.1/cybox/ActionType/) instance should set its `Name` field to a value of `Send DNS Query`, from the corresponding [Action Name Vocabulary](http://stixproject.github.io/data-model/1.1.1/cyboxVocabs/ActionNameVocab-1.1/). 

Accordingly, for capturing the information on the DNS query and returned resource record, the [Action](http://stixproject.github.io/data-model/1.1.1/cybox/ActionType/) should embed two distinct [Associated Objects](http://stixproject.github.io/data-model/1.1.1/cybox/AssociatedObjectType/) in its `Associated_Objects` field:

* An [Associated Object](http://stixproject.github.io/data-model/1.1.1/cybox/AssociatedObjectType/) that includes an instance of a [DNS Query Object](http://stixproject.github.io/data-model/1.1.1/DNSQueryObj/DNSQueryObjectType/), for capturing the details of the query itself, including the queried domain name and type of DNS record requested. The `Association_Type` field for this Object should be set to a value of `Utilized` from the [Action->Object Association Vocabulary](http://stixproject.github.io/data-model/1.1.1/cyboxVocabs/ActionObjectAssociationTypeVocab-1.0/), indicating that it is used and therefore sent in the action.
* An [Associated Object](http://stixproject.github.io/data-model/1.1.1/cybox/AssociatedObjectType/) that includes an instance of a [DNS Record Object](http://stixproject.github.io/data-model/1.1.1/DNSRecordObj/DNSRecordObjectType/), for capturing the details of the DNS record returned for the DNS query. The `Association_Type` field for this Object should be set to a value of `Returned` from the [Action->Object Association Vocabulary](http://stixproject.github.io/data-model/1.1.1/cyboxVocabs/ActionObjectAssociationTypeVocab-1.0/), indicating that it was returned as part of the action.

#### Example

This XML example demonstrates how an observed instance of the activity around a DNS Query for the `A` record of `mitre.org` would be captured and represented with an [Action](http://stixproject.github.io/data-model/1.1.1/cybox/ActionType/) that incorporates a [DNS Query Object](http://stixproject.github.io/data-model/1.1.1/DNSQueryObj/DNSQueryObjectType/) (representing the DNS query) and [DNS Record Object](http://stixproject.github.io/data-model/1.1.1/DNSRecordObj/DNSRecordObjectType/) (representing the returned DNS resource record). There are a few things worth noting here:
* The [Action](http://stixproject.github.io/data-model/1.1.1/cybox/ActionType/) is captured as part of an [Event](http://stixproject.github.io/data-model/1.1.1/cybox/EventType/), specifically in its `Actions` field. The [Event](http://stixproject.github.io/data-model/1.1.1/cybox/EventType/) entity is the higher-level structure in CybOX that is used for capturing observables that are dynamic in nature.
* The `Date_Ran` field in the [DNS Query Object](http://stixproject.github.io/data-model/1.1.1/DNSQueryObj/DNSQueryObjectType/) is used to capture the date/time that the DNS query was performed.

```xml
<cybox:Observable id="example:Observable-e7a976ab-1e05-4d13-9b3c-387816441f7f">
  <cybox:Event>
    <cybox:Actions>
      <cybox:Action id="example:Action-b17269f3-6e20-49d4-bfe1-c7e1ce48c0ac">
        <cybox:Name xsi:type="cyboxVocabs:ActionNameVocab-1.1">Send DNS Query</cybox:Name>
        <cybox:Associated_Objects>
          <cybox:Associated_Object>
            <cybox:Properties xsi:type="DNSQueryObj:DNSQueryObjectType">
              <DNSQueryObj:Question>
                <DNSQueryObj:QName>
                  <URIObject:Value>mitre.org</URIObject:Value>
                </DNSQueryObj:QName>
                <DNSQueryObj:QType>A</DNSQueryObj:QType>
              </DNSQueryObj:Question>
              <DNSQueryObj:Date_Ran>2014-09-24T09:00:00Z</DNSQueryObj:Date_Ran>
            </cybox:Properties>
            <cybox:Association_Type xsi:type="cyboxVocabs:ActionObjectAssociationTypeVocab-1.0">Utilized</cybox:Association_Type>
          </cybox:Associated_Object>
          <cybox:Associated_Object>
            <cybox:Properties xsi:type="DNSRecordObj:DNSRecordObjectType">
              <DNSRecordObj:IP_Address category="ipv4-addr">
                <AddressObj:Address_Value>107.21.104.61</AddressObj:Address_Value>
              </DNSRecordObj:IP_Address>
            </cybox:Properties>
            <cybox:Association_Type xsi:type="cyboxVocabs:ActionObjectAssociationTypeVocab-1.0">Returned</cybox:Association_Type>
          </cybox:Associated_Object>
        </cybox:Associated_Objects>
      </cybox:Action>
    </cybox:Actions>
  </cybox:Event>
</cybox:Observable>    
```

## Capturing Basic DNS Resolution Information

Basic DNS resolution can be thought of as a simple abstraction of the DNS record information that may result from a DNS query, but without necessarily knowing the specifics of the query itself or when it was performed. As such, it typically involves:

* The domain name being resolved.
* The IP address(es) to which the domain name resolves, as obtained from a DNS record.
* The date/time that the resolution was recorded (but not necessarily when the corresponding DNS query was performed).

Therefore, the use of the [DNS Query Object](http://stixproject.github.io/data-model/1.1.1/DNSQueryObj/DNSQueryObjectType/) and [DNS Record Object](http://stixproject.github.io/data-model/1.1.1/DNSRecordObj/DNSRecordObjectType/) would be unnecessarily verbose for this case, since we do not need to capture any metadata about the record(s) returned. Instead, the capture of such basic DNS resolution can be accomplished through the use of the [Domain Name Object](http://stixproject.github.io/data-model/1.1.1/DomainNameObj/DomainNameObjectType/) and [Address Object](http://stixproject.github.io/data-model/1.1.1/AddressObj/AddressObjectType/), along with a simple relationship -- specifically, the "Resolved_To" relationship from the [Object Relationship Vocabulary](http://stixproject.github.io/data-model/1.1.1/cyboxVocabs/ObjectRelationshipVocab-1.1/).

### Example
This XML example demonstrates how an observed instance of basic DNS resolution for `mitre.org` would be captured and represented with the [Domain Name Object](http://stixproject.github.io/data-model/1.1.1/DomainNameObj/DomainNameObjectType/) and [Address Object](http://stixproject.github.io/data-model/1.1.1/AddressObj/AddressObjectType/), in conjunction with a simple relationship. Note that the time that this resolution was recorded is captured with the `Observable_Source/Time/Start_Time` field.

```xml

<cybox:Observable id="example:Observable-f95dd1a3-8c7c-4c46-ba8e-74a6cb4ca217">
  <cybox:Observable_Source>
    <cyboxCommon:Time>
      <cyboxCommon:Start_Time>2014-09-24T09:00:00Z</cyboxCommon:Start_Time>
    </cyboxCommon:Time>
  </cybox:Observable_Source>
  <cybox:Object id="example:Object-7846639e-f23c-4f22-accf-39b44ab610d1">
    <cybox:Properties xsi:type="DomainNameObj:DomainNameObjectType" type="TLD">
      <DomainNameObj:Value>mitre.org</DomainNameObj:Value>
    </cybox:Properties>
    <cybox:Related_Objects>
      <cybox:Related_Object>
        <cybox:Properties xsi:type="AddressObj:AddressObjectType" category="ipv4-addr">
          <AddressObj:Address_Value>107.21.104.61</AddressObj:Address_Value>
        </cybox:Properties>
        <cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Resolved_To</cybox:Relationship>
      </cybox:Related_Object>
    </cybox:Related_Objects>
  </cybox:Object>
</cybox:Observable>

```

## Capturing DNS Cache Information

Sometimes it can be necessary to capture DNS records outside the context of a DNS query. One of the most common such uses is for capturing DNS cache information stored on a local machine. Such DNS cache information can be natively represented using the [DNS Cache Object](http://stixproject.github.io/data-model/1.1.1/DNSCacheObj/DNSCacheObjectType/), which makes use of the [DNS Record Object](http://stixproject.github.io/data-model/1.1.1/DNSRecordObj/DNSRecordObjectType/) for representing the DNS record(s) stored in the cache. 

### Example
This XML example demonstrates how an observed instance of a DNS cache entry for `stix.readthedocs.org` would be captured and represented with the [DNS Cache Object](http://stixproject.github.io/data-model/1.1.1/DNSCacheObj/DNSCacheObjectType/). 

```xml
<cybox:Observable id="example:Observable-5863145c-8055-4b0f-9b09-e137f31fd357">
  <cybox:Object id="example:Object-f8c22190-9dee-41fb-9207-ef638a93ecc5">
    <cybox:Properties xsi:type="DNSCacheObj:DNSCacheObjectType">
      <DNSCacheObj:DNS_Cache_Entry>
        <DNSCacheObj:DNS_Entry>
          <DNSRecordObj:Domain_Name type="Domain Name">
            <URIObj:Value>stix.readthedocs.org</URIObj:Value>
          </DNSRecordObj:Domain_Name>
          <DNSRecordObj:IP_Address category="ipv4-addr">
            <AddressObj:Address_Value>162.209.114.75</AddressObj:Address_Value>
          </DNSRecordObj:IP_Address>
          <DNSRecordObj:Record_Type>A</DNSRecordObj:Record_Type>
          <DNSRecordObj:Data_Length>4</DNSRecordObj:Data_Length>
        </DNSCacheObj:DNS_Entry>
        <DNSCacheObj:TTL>92</DNSCacheObj:TTL>
      </DNSCacheObj:DNS_Cache_Entry>
    </cybox:Properties>
  </cybox:Object>
</cybox:Observable>

```

## Capturing DNS-related Patterns

There are a number of patterns related to DNS queries and records that one may wish to express. In this section, we'll cover two of the most common such patterns.

### Attempted Domain Resolution

One of the most common patterns around DNS revolves around the attempted resolution of a particular domain via DNS query, which could be used to test for malware beaconing to a command and control (C2) domain, for instance. In such cases, one typically does not care about whether the resolution was successful or what address(es) it resolved to; instead, the fact that the resolution was attempted at all is enough to trigger the pattern. 

Since this pattern revolves around an explicit DNS query and implicitly associated network traffic, it makes the most sense to use the [DNS Query Object](http://stixproject.github.io/data-model/1.1.1/DNSQueryObj/DNSQueryObjectType/), as it is designed to represent discrete queries in this fashion. As with the Full DNS Query use case, we'll want to capture the QName value that corresponds to the domain name being resolved; the difference in this case is that we'll want to set the "condition" attribute on the `URIObj:Value` field to denote that we're specifying a pattern. Unlike the DNS Query use case, we shouldn't populate any other fields, since we care only about the attempted resolution itself and not the associated record data.

#### Example

This XML example demonstrates how a pattern for attempted DNS resolution for `somedomain.com` would be represented using the [DNS Query Object](http://stixproject.github.io/data-model/1.1.1/DNSQueryObj/DNSQueryObjectType/). Note how the `condition` field is set on each of the allowable fields.

```xml
<cybox:Observable id="example:Observable-98d7719b-5b95-4c52-b687-de6a00575246">
  <cybox:Object id="example:Object-e671ce52-e41b-4892-b1df-c5846252186d">
    <cybox:Properties xsi:type="DNSQueryObj:DNSQueryObjectType">
      <DNSQueryObj:Question>
        <DNSQueryObj:QName type="Domain Name">
          <URIObj:Value condition="Equals">somedomain.com</URIObj:Value>
        </DNSQueryObj:QName>
      </DNSQueryObj:Question>
    </cybox:Properties>
  </cybox:Object>
</cybox:Observable>
```

### Domain Resolution to Specific Address(es)

Another common pattern relating to DNS resolution involves DNS records that may indicate a particular domain name resolving to a specific address or set of addresses, which could be used to test whether a particular DNS cache has been poisoned, for instance. In such cases, one typically does not care about the particular DNS query that produced the domain/address mapping, but rather the existence of the DNS record and/or domain->IP address mapping itself.

Since domain name resolution to a specific address or set of addresses can be considered in a number of contexts, we'll refer to two different scenarios here:

* Generic domain name resolution to a specific address or set of addresses.
* DNS records that indicate a domain resolving to a specific address or set of addresses as part of a DNS cache.

Patterns for the first scenario, that of generic domain name resolution to a specific address or set of addresses, can be expressed through the use of the [Domain Name Object](http://stixproject.github.io/data-model/1.1.1/DomainNameObj/DomainNameObjectType/) and [Address Object](http://stixproject.github.io/data-model/1.1.1/AddressObj/AddressObjectType/), along with a simple relationship. This is almost identical to the Capturing Basic DNS Resolution use case, with the sole exception that we'll need to set the `condition` fields on the Domain and Address Objects in order to denote that we're specifying a pattern and not an instance.

Patterns for the second scenario, that of DNS records that indicate domain name resolution to a specific address or set of addresses in a DNS cache, can be expressed through the use of the [DNS Cache Object](http://stixproject.github.io/data-model/1.1.1/DNSCacheObj/DNSCacheObjectType/). This is very similar to the Capturing DNS Cache Information use case, with the exception that we'll need to set the `condition` fields on the `URIObj:Value` field and `AddressObj:Address_Value` field in order to denote that we're specifying a pattern and not an instance. Populating the other fields, such as `TTL`, is optional depending on the particular use case and accordingly whether we care about detecting on these values as well as the domain name --> address resolution.

#### Example - Generic Domain Name Resolution --> Address(es)

This XML example demonstrates how a pattern for generic DNS resolution for `baddomain.net` to `192.168.1.26` would be captured and represented with the [Domain Name Object](http://stixproject.github.io/data-model/1.1.1/DomainNameObj/DomainNameObjectType/) and [Address Object](http://stixproject.github.io/data-model/1.1.1/AddressObj/AddressObjectType/), in conjunction with a simple relationship. Note how the `condition` field is set on each of the allowable fields.

```xml
<cybox:Observable id="example:Observable-7a675df3-0444-434b-8e60-839a192e13227">
  <cybox:Object id="example:Object-77e07cdf-74a1-45cb-bfeb-c09b88ed96ad">
    <cybox:Properties xsi:type="DomainNameObj:DomainNameObjectType" type="TLD">
      <DomainNameObj:Value condition="Equals">baddomain.net</DomainNameObj:Value>
    </cybox:Properties>
    <cybox:Related_Objects>
      <cybox:Related_Object>
        <cybox:Properties xsi:type="AddressObj:AddressObjectType" category="ipv4-addr">
          <AddressObj:Address_Value condition="Equals">192.168.1.26</AddressObj:Address_Value>
        </cybox:Properties>
        <cybox:Relationship xsi:type="cyboxVocabs:ObjectRelationshipVocab-1.1">Resolved_To</cybox:Relationship>
       </cybox:Related_Object>
     </cybox:Related_Objects>
   </cybox:Object>
</cybox:Observable>
```

#### Example - DNS Cache Domain Name Resolution --> Address(es)

This XML example demonstrates how a pattern for a DNS cache entry for `someotherdomain.com` that resolves to `192.168.0.2` would be captured and represented with the [DNS Cache Object](http://stixproject.github.io/data-model/1.1.1/DNSCacheObj/DNSCacheObjectType/). Note how the `condition` field is set on each of the allowable fields.

```xml
<cybox:Observable id="example:Observable-02a5cf44-b324-41a5-b097-efa8d909e018">
  <cybox:Object id="example:Object-206759f0-7cc8-42fe-b569-515b4312477f">
    <cybox:Properties xsi:type="DNSCacheObj:DNSCacheObjectType">
      <DNSCacheObj:DNS_Cache_Entry>
        <DNSCacheObj:DNS_Entry>
          <DNSRecordObj:Domain_Name type="Domain Name">
            <URIObj:Value condition="Equals">someotherdomain.com</URIObj:Value>
          </DNSRecordObj:Domain_Name>
          <DNSRecordObj:IP_Address category="ipv4-addr">
            <AddressObj:Address_Value condition="Equals">192.168.0.2</AddressObj:Address_Value>
          </DNSRecordObj:IP_Address>
         </DNSCacheObj:DNS_Entry>
       </DNSCacheObj:DNS_Cache_Entry>
     </cybox:Properties>
   </cybox:Object>
</cybox:Observable>
```
