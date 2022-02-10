---
title: "ExtraInfo Cell (Hyperlinks Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm360
 
ms.localizationpriority: medium
ms.assetid: 55834445-8619-f79a-aea0-0f6a1780e016

description: "Represents a string that passes information to be used in resolving a URL, such as the coordinates of an image map. For example, in the ExtraInfo cell,x=41&amp;y=7specifies the coordinates of an image map."
---

# ExtraInfo Cell (Hyperlinks Section)

Represents a string that passes information to be used in resolving a URL, such as the coordinates of an image map. For example, in the ExtraInfo cell, "x=41&amp;y=7" specifies the coordinates of an image map.
  
## Remarks

Event cells are evaluated only when the event occurs, not upon formula entry.
  
To get a reference to the ExtraInfo cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Hyperlink.  *name*  .ExtraInfo            where Hyperlink.  *name*  is the row name  <br/> |
   
To get a reference to the ExtraInfo cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionHyperlink** <br/> |
| Row index:  <br/> |**visRow1stHyperlink** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visHLinkExtraInfo** <br/> |
   

