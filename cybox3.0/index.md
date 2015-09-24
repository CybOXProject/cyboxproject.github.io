---
layout: flat
title: CybOX 3.0
---


##Goals
* Simplification
* Elimination of ambiguity
    * Having only one way of representing specific entities
* Refactoring of CybOX Objects for accuracy, consistency, and to align with above goals

##Ideas

### "Core" CybOX Objects
Refacoring the existing CybOX Objects (as needed) for semantic accuracy and consistency is a large undertaking, and so it might make sense to focus on the Objects that meet the 80% solution (or thereabouts) for CybOX 3.0. This entails refactoring the most commonly used Objects (for various use cases), as well as those that may provide a large amount of value. Future minor releases of CybOX (e.g., CybOX 3.1) could then be devoted to refactoring and also adding Objects specific to a particular subset or domain, such as network-centric Objects.

The diagram below illustrates the Objects that we're currently considering for the "core" set. This selection was informed by the recent CybOX Object survey, as well as some of our own judgment. In this diagram, red lines denote new Objects (or significant refactoring of existing ones), and dashed lines denote Objects that would be subjects of potential refactoring.

<a href="cybox_object_categories_3.0_core.png" target="_blank">
<img src="cybox_object_categories_3.0_core.png" style="border:1px solid black;max-width:100%;" alt="Core CybOX Objects">
</a>



