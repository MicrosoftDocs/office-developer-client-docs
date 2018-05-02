---
title: "DefaultTabstop Cell (Text Block Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm220
 
localization_priority: Normal
ms.assetid: 3b3e458a-206c-8699-8bf7-da80f4350706
description: "Determines the interval of the default tab stops in a text block."
---

# DefaultTabstop Cell (Text Block Format Section)

Determines the interval of the default tab stops in a text block. 
  
## Remarks

The default value is 0.5 inches for documents created in imperial units and 1.5 centimeters for documents created in metric units.
  
To get a reference to the DefaultTabstop cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |DefaultTabstop  <br/> |
   
To get a reference to the DefaultTabstop cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowText** <br/> |
|Cell index:  <br/> |**visTxtBlkDefaultTabStop** <br/> |
   

