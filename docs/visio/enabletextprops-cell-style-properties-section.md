---
title: "EnableTextProps Cell (Style Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251697
 
ms.localizationpriority: medium
ms.assetid: 8c59abaf-d2cc-94c9-08ba-004bc40efd9e
description: "Determines whether a style includes text properties."
---

# EnableTextProps Cell (Style Properties Section)

Determines whether a style includes text properties.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Include text properties.  <br/> |
|FALSE  <br/> |Exclude text properties.  <br/> |
   
## Remarks

To get a reference to the EnableTextProps cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |EnableTextProps  <br/> |
   
To get a reference to the EnableTextProps cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowStyle** <br/> |
|Cell index:  <br/> |**visStyleIncludesText** <br/> |
   

