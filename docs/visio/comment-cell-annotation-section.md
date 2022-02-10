---
title: "Comment Cell (Annotation Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60033
 
ms.localizationpriority: medium
ms.assetid: b367841a-f31c-4b55-4491-2abab5811dbe

description: "Contains the text that appears in a comment."
---

# Comment Cell (Annotation Section)

Contains the text that appears in a comment.
  
> [!NOTE]
> This cell is used for tracking comments only when opening a .vsd file in Microsoft Visio 2013 or when saving a .vsdx file in the .vsd file format. It is not used for tracking comments in .vsdx documents in Visio 2013. 
  
## Remarks

To get a reference to the Comment cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Annotation.Comment[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the Comment cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionAnnotation** <br/> |
| Row index:  <br/> |**visRowAnnotation** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visAnnotationComment** <br/> |
   

