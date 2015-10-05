---
layout: flat
title: CybOX Maturity Spectrum
---

To help the broader community and ourselves assess the current state of CybOX, we've developed a three-tiered “maturity spectrum” for categorizing the major entities and their corresponding models. This is based on two factors:

* The semantic completeness/accuracy of the model around the entity, as well as the sense of community agreement/disagreement with regards to the data model.
* The use of the model (through serialization) in existing implementations.

### Metric

#### High (green)
* **Semantic consensus**: Little to no known semantic issues. Virtually no disagreement about the data model in the community.
* **Existing use**: Widely used in existing implementations.

#### Medium (yellow)
* **Semantic consensus**: Several minor known semantic issues, or one or two larger issues. Some level of disagreement about the data model in the community.
* **Existing use**: Some known use in existing implementations.

#### Low (red)
* **Semantic consensus**: One or more major known semantic issues. Significant disagreement about the data model in the community.
* **Existing use**: Little to no known use in existing implementations.

### Spectrum

The table below captures the current maturity spectrum as of CybOX v2.1. Note that is a subjective rating as assigned by the CybOX SC co-chairs and development team, and is open to personal interpretation.

<table>
<col>
<colgroup span="2"></colgroup>
<colgroup span="2"></colgroup>
<colgroup span="2"></colgroup>
<tr>
  <td rowspan="2"></td>
  <th colspan="2" scope="colgroup">Low</th>
  <th colspan="2" scope="colgroup">Medium</th>
  <th colspan="2" scope="colgroup">High</th>
</tr>
<tr>
  <th scope="col">Semanic Consensus</th>
  <th scope="col">Existing Use</th>
  <th scope="col">Semanic Consensus</th>
  <th scope="col">Existing Use</th>
  <th scope="col">Semanic Consensus</th>
  <th scope="col">Existing Use</th>
</tr>
<tr>
  <th scope="row"><b>Observable (instance)</b></th>
  <td colspan="2"></td>
  <td colspan="2"></td>
  <td style="background-color: green;"></td>
  <td style="background-color: green;"></td>
</tr>
<tr>
  <th scope="row"><b>Observable (pattern)</b></th>
  <td colspan="2"></td>
  <td style="background-color: yellow;"></td>
  <td style="background-color: green;"></td>
  <td colspan="2"></td>
</tr>
</table>
