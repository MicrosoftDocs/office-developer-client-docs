---
title: "Date Cell (Annotation Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60036
 
ms.localizationpriority: medium
ms.assetid: f1f11803-614b-a40d-0a2d-131093e7609e

description: "Contains the date and time the comment was last edited."
---

# Date Cell (Annotation Section)

Contains the date and time the comment was last edited. 
  
> [!NOTE]
> This cell is used for tracking comments only when opening a .vsd file in Microsoft Visio 2013 or when saving a .vsdx file in the .vsd file format. It is not used for tracking comments in .vsdx documents in Visio 2013. 
  
## Remarks

Only the date appears in the comment box in the user interface.
  
To get a reference to the Date cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Annotation.Date[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the Date cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionAnnotation** <br/> |
| **Row index:**  <br/> |**visRowAnnotation** +  *i*            where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visAnnotationDate** <br/> |
   

