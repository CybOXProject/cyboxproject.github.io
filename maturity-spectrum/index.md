---
layout: flat
title: CybOX Maturity Spectrum
---

To help the broader community and ourselves assess the current state of CybOX, we've developed a three-tiered “maturity spectrum” for categorizing the major entities and their corresponding models. This is based on the following factors:

* The relative sense of community agreement/disagreement with regards to the data model and what it's attempting to model (i.e., does it make sense? is it accurate?).
* The relative semantic completeness of the model around the entity (i.e., does it, without any doubt, completely capture the properties of the entity?).
* The relative use of the model (through serialization) in existing implementations.

### Metric

#### High (green)
* **Semantic consensus**: Little to no known semantic issues and/or virtually no disagreement about the data model in the community.
* **Semantic completeness**: No known missing fields/capabilities and/or a sense of certainty that the model is "complete". Capable of being used effectively in ALL applicable domains.
* **Existing use**: Widely used in existing implementations.

#### Medium (yellow)
* **Semantic consensus**: Several minor known semantic issues, or one or two larger issues and/or some level of disagreement about the data model in the community.
* **Semantic completeness**: One or two known minor missing fields and/or some uncertainty around complete coverage of the entity. Capable of being used effectively in most applicable domains.
* **Existing use**: Some known use in existing implementations.

#### Low (red)
* **Semantic consensus**: One or more major known semantic issues and/or significant disagreement about the data model in the community.
* **Semantic completeness**: One or two known major missing fields/capabilities and/or major uncertainty about coverage of the entity. Generally not useful for all or most applicable domains.
* **Existing use**: Little to no known use in existing implementations.

### Spectrum

The table below captures the current maturity spectrum as of CybOX v2.1. **Note**: this is a subjective rating as assigned by the CybOX SC co-chairs and development team, and is open to personal interpretation. 

Each entity is assigned an individual maturity score for semantic consensus, semantic completeness, and existing use, as well as an "overall" maturity score based on the lowest of its three scores. Also, each entity links to a CybOX wiki page that describes the rationale behind the scores and discussion of the maturity score around each entity, including applications where it is being used.

<table>
<col>
<colgroup span="3"></colgroup>
<colgroup span="3"></colgroup>
<colgroup span="3"></colgroup>
<tr>
  <td rowspan="2" style="font-size:12px; white-space: nowrap"></td>
  <th colspan="3" scope="colgroup" style="width:25%; text-align:center; font-size:24px">Low</th>
  <th colspan="3" scope="colgroup" style="width:25%; text-align:center; font-size:24px">Medium</th>
  <th colspan="3" scope="colgroup" style="width:25%; text-align:center; font-size:24px">High</th>
</tr>
<tr>
  <th scope="col" style="text-align:center; font-size:12px">Sem. Consensus</th>
  <th scope="col" style="text-align:center; font-size:12px">Sem. Completeness</th>
  <th scope="col" style="text-align:center; font-size:12px">Existing Use</th>
  <th scope="col" style="text-align:center; font-size:12px">Sem. Consensus</th>
  <th scope="col" style="text-align:center; font-size:12px">Sem. Completeness</th>
  <th scope="col" style="text-align:center; font-size:12px">Existing Use</th>
  <th scope="col" style="text-align:center; font-size:12px">Sem. Consensus</th>
  <th scope="col" style="text-align:center; font-size:12px">Sem. Completeness</th>
  <th scope="col" style="text-align:center; font-size:12px">Existing Use</th>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Observable-(instance)"><b>Observable (instance)</b></a></th>
  <td colspan="3"></td>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Observable-(pattern)"><b>Observable (pattern)</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Events"><b>Events</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Actions"><b>Actions</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Account-Object"><b>Account Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Address-Object"><b>Address Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-API-Object"><b>API Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Archive-File-Object"><b>Archive File Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-ARP-Cache-Object"><b>ARP Cache Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Artifact-Object"><b>Artifact Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-AS-Object"><b>AS Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Code-Object"><b>Code Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Custom-Object"><b>Custom Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Device-Object"><b>Device Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Disk-Object"><b>Disk Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Disk-Partition-Object"><b>Disk Partition Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-DNS-Cache-Object"><b>DNS Cache Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-DNS-Query-Object"><b>DNS Query Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-DNS-Record-Object"><b>DNS Record Object</b></a></th>
  <td colspan="3"></td>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Domain-Name-Object"><b>Domain Name Object</b></a></th>
  <td colspan="3"></td>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Email-Message-Object"><b>Email Message Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-File-Object"><b>File Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-GUI-Object"><b>GUI Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-GUI-Dialogbox-Object"><b>GUI Dialogbox Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-GUI-Window-Object"><b>GUI Window Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Hostname-Object"><b>Hostname Object</b></a></th>
  <td colspan="3"></td>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-HTTP-Session-Object"><b>HTTP Session Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Image-File-Object"><b>Image File Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Library-Object"><b>Library Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Link-Object"><b>Link Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Linux-Package-Object"><b>Linux Package Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Memory-Object"><b>Memory Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Mutex-Object"><b>Mutex Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Network-Connection-Object"><b>Network Connection Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Network-Flow-Object"><b>Network Flow Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Network-Packet-Object"><b>Network Packet Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Network-Route-Entry-Object"><b>Network Route Entry Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Network-Route-Object"><b>Network Route Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Network-Socket-Object"><b>Network Socket Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Network-Subnet-Object"><b>Network Subnet Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-PDF-File-Object"><b>PDF File Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Pipe-Object"><b>Pipe Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Port-Object"><b>Port Object</b></a></th>
  <td colspan="3"></td>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Process-Object"><b>Process Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Product-Object"><b>Product Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Semaphore-Object"><b>Semaphore Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-SMS-Message-Object"><b>SMS Message Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Socket-Address-Object"><b>Socket Address Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-System-Object"><b>System Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Unix-File-Object"><b>Unix File Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Unix-Network-Route-Entry-Object"><b>Unix Network Route Entry Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Unix-Pipe-Object"><b>Unix Pipe Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Unix-Process-Object"><b>Unix Process Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Unix-User-Account-Object"><b>Unix User Account Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Unix-Volume-Object"><b>Unix Volume Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-URI-Object"><b>URI Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-URL-History-Object"><b>URL History Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-User-Account-Object"><b>User Account Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-User-Session-Object"><b>User Session Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Volume-Object"><b>Volume Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-WHOIS-Object"><b>WHOIS Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Computer-Account-Object"><b>Win. Computer Account Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Critical-Section-Object"><b>Win. Critical Section Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Driver-Object"><b>Win. Driver Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Event-Log-Object"><b>Win. Event Log Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Event-Object"><b>Win. Event Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Executable-File-Object"><b>Win. Executable File Object</b></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-File-Object"><b>Win. File Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Filemapping-Object"><b>Win. Filemapping Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Handle-Object"><b>Win. Handle Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Hook-Object"><b>Win. Hook Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Kernel-Hook-Object"><b>Win. Kernel Hook Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Mailslot-Object"><b>Win. Mailslot Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Memory-Page-Region-Object"><b>Win. Memory Page Region Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Mutex-Object"><b>Win. Mutex Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Network-Route-Entry-Object"><b>Win. Network Route Entry Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Network-Share-Object"><b>Win. Network Share Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Pipe-Object"><b>Win. Pipe Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Prefetch-Object"><b>Win. Prefetch Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Process-Object"><b>Win. Process Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Registry-Key-Object"><b>Win. Registry Key Object</b></a></th>
  <td colspan="3"></td>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Semaphore-Object"><b>Win. Semaphore Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Service-Object"><b>Win. Service Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-System-Object"><b>Win. System Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-System-Restore-Object"><b>Win. System Restore Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Task-Object"><b>Win. Task Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-User-Account-Object"><b>Win. User Account Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Volume-Object"><b>Win. Volume Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-Win.-Waitable-Timer-Object"><b>Win. Waitable Timer Object</b></a></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><a href="https://github.com/CybOXProject/specifications/wiki/Maturity:-X509-Certificate-Object"><b>X509 Certificate Object</b></a></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
</table>
