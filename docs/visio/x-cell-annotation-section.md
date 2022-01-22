---
title: "X Cell (Annotation Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1028735
 
ms.localizationpriority: medium
ms.assetid: f9db8623-9fcf-7037-2d11-d509f463025d

description: "The x -coordinate of the comment marker in page coordinates."
---

# X Cell (Annotation Section)

The *x*  -coordinate of the comment marker in page coordinates. 
  
> [!NOTE]
> This cell is used for tracking comments only when opening a .vsd file in Microsoft Visio 2013 or when saving a .vsdx file in the .vsd file format. It is not used for tracking comments in .vsdx documents in Visio 2013. 
  
## Remarks

To get a reference to the X cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Annotation.X[  *i*  ]            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the X cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionAnnotation** <br/> |
| Row index:  <br/> |**visRowAnnotation** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visAnnotationX** <br/> |
   

