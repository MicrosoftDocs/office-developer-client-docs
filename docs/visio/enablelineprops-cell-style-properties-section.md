---
title: "EnableLineProps Cell (Style Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251696
 
localization_priority: Normal
ms.assetid: 9f619416-36ff-1479-6232-225c11827e01
description: "Determines whether a style includes line properties."
---

# EnableLineProps Cell (Style Properties Section)

Determines whether a style includes line properties.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Include line properties.  <br/> |
|FALSE  <br/> |Exclude line properties.  <br/> |
   
## Remarks

To get a reference to the EnableLineProps cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |EnableLineProps  <br/> |
   
To get a reference to the EnableLineProps cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowStyle** <br/> |
|Cell index:  <br/> |**visStyleIncludesLine** <br/> |
   

