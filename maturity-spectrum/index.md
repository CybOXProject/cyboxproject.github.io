---
layout: flat
title: CybOX Maturity Spectrum
---

To help the broader community and ourselves assess the current state of CybOX, we've developed a three-tiered “maturity spectrum” for categorizing the major entities and their corresponding models. This is based on three factors:

* The relative sense of community agreement/disagreement with regards to the data model and what it's attempting to model (i.e., does it make sense? is it accurate?).
* The relative semantic completeness of the model around the entity (i.e., does it, without any doubt, completely capture the properties of the entity?).
* The relative use of the model (through serialization) in existing implementations.

### Metric

#### High (green)
* **Semantic consensus**: Little to no known semantic issues. Virtually no disagreement about the data model in the community.
* **Semantic completeness**: No known missing fields/capabilities - i.e., a sense of certainty that the model is "complete". Generally capable of being used for all applicable domains.
* **Existing use**: Widely used in existing implementations.

#### Medium (yellow)
* **Semantic consensus**: Several minor known semantic issues, or one or two larger issues. Some level of disagreement about the data model in the community.
* **Semantic completeness**: One or two known minor missing fields/capabilities. Capable of being used for most applicable domains.
* **Existing use**: Some known use in existing implementations.

#### Low (red)
* **Semantic consensus**: One or more major known semantic issues. Significant disagreement about the data model in the community.
* **Semantic completeness**: One or two known major missing fields/capabilities. Generally not useful for all or most applicable domains.
* **Existing use**: Little to no known use in existing implementations.

### Spectrum

The table below captures the current maturity spectrum as of CybOX v2.1. **Note**: this is a subjective rating as assigned by the CybOX SC co-chairs and development team, and is open to personal interpretation. Each entity is assigned an individual maturity score for both semantic consensus and existing use, as well as an "overall" maturity score based on the lowest of its two individual scores.

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
  <th scope="row"><b>Observable (instance)</b></th>
  <td colspan="3"></td>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
</tr>
<tr>
  <th scope="row"><b>Observable (pattern)</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Events</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Actions</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Account Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Address Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>API Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Archive File Object</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>ARP Cache Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Artifact Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>AS Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Code Object</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Custom Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Device Object</b></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Disk Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Disk Partition Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>DNS Cache Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>DNS Query Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>DNS Record Object</b></th>
  <td colspan="3"></td>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
</tr>
<tr>
  <th scope="row"><b>Domain Name Object</b></th>
  <td colspan="3"></td>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
</tr>
<tr>
  <th scope="row"><b>Email Message Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>File Object</b></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>GUI Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>GUI Dialogbox Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>GUI Window Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Hostname Object</b></th>
  <td colspan="3"></td>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
</tr>
<tr>
  <th scope="row"><b>HTTP Session Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Image File Object</b></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Library Object</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Link Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Linux Package Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Memory Object</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Mutex Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Network Connection Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Network Flow Object</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Network Packet Object</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Network Route Entry Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Network Route Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Network Socket Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Network Subnet Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>PDF File Object</b></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Pipe Object</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Port Object</b></th>
  <td colspan="3"></td>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
</tr>
<tr>
  <th scope="row"><b>Process Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Product Object</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Semaphore Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>SMS Message Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Socket Address Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>System Object</b></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Unix File Object</b></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Unix Network Route Entry Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Unix Pipe Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Unix Process Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Unix User Account Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Unix Volume Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>URI Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>URL History Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>User Account Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>User Session Object</b></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Volume Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>WHOIS Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Computer Account Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Critical Section Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Driver Object</b></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Event Log Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Event Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Executable File Object</b></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. File Object</b></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Filemapping Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Handle Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Hook Object</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Kernel Hook Object</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Mailslot Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Memory Page Region Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Mutex Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Network Route Entry Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Network Share Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Pipe Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Prefetch Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Process Object</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Registry Key Object</b></th>
  <td colspan="3"></td>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Semaphore Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Service Object</b></th>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. System Object</b></th>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. System Restore Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Task Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. User Account Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Volume Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>Win. Waitable Timer Object</b></th>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: tomato;"></td>
  <td colspan="3"></td>
  <td colspan="3"></td>
</tr>
<tr>
  <th scope="row"><b>X509 Certificate Object</b></th>
  <td colspan="3"></td>
  <td style="border: 1px solid #ddd; background-color: forestgreen;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td style="border: 1px solid #ddd; background-color: gold;"></td>
  <td colspan="3"></td>
</tr>
</table>
