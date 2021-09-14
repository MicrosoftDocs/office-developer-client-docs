---
title: "Y Cell (Annotation Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60095
 
ms.localizationpriority: medium
ms.assetid: 527a4615-2013-a4b4-81cd-7f5d71c1803c

description: "The y -coordinate of the comment marker in page coordinates."
---

# Y Cell (Annotation Section)

The  *y*  -coordinate of the comment marker in page coordinates. 
  
> [!NOTE]
> This cell is used for tracking comments only when opening a .vsd file in Microsoft Visio 2013 or when saving a .vsdx file in the .vsd file format. It is not used for tracking comments in .vsdx documents in Visio 2013. 
  
## Remarks

To get a reference to the Y cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Annotation.Y [  *i*  ]            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the Y cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionAnnotation** <br/> |
| Row index:  <br/> |**visRowAnnotation** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visAnnotationY** <br/> |
   

