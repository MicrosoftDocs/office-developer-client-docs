---
title: "NoQuickDrag Cell (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm80004
 
localization_priority: Normal
ms.assetid: 8491f459-9de2-8e75-5532-7d3bd0986734
description: "Determines whether a shape can be selected or dragged when the user clicks the filled area defined by the Geometry section."
---

# NoQuickDrag Cell (Geometry Section)

Determines whether a shape can be selected or dragged when the user clicks the filled area defined by the Geometry section.
  
## Remarks

To get a reference to the NoQuickDrag cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Geometry  *i*  .NoQuickDrag, where  * i *  - <1>, 2, 3...  <br/> |
   
To get a reference to the NoQuickDrag cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionFirstComponent** +  *i*  , where  *i*  = 0, 1, 2...  <br/> |
|Row index:  <br/> |**visRowComponent** <br/> |
|Cell index:  <br/> |**visCompNoQuickDrag** <br/> |
   

