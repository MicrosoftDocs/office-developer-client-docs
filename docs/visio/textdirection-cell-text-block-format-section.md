---
title: "TextDirection Cell (Text Block Format Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm995
 
localization_priority: Normal
ms.assetid: 1df3a50e-7ea5-9244-1286-c1d00c217a9a
description: "Determines the direction of the characters in a text block."
---

# TextDirection Cell (Text Block Format Section)

Determines the direction of the characters in a text block.
  
|**Value**|**Direction**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Horizontal  <br/> |**visTxtBlkLeftToRight** <br/> |
| 1  <br/> | Vertical  <br/> |**visTxtBlkTopToBottom** <br/> |
   
## Remarks

In Visio version 5.0 Japanese products, the value of this cell was stored in the VerticalText cell in the Miscellaneous section.
  
To get a reference to the TextDirection cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | TextDirection  <br/> |
   
To get a reference to the TextDirection cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowText** <br/> |
| Cell index:  <br/> |**visTxtBlkDirection** <br/> |
   

