---
title: "Name Cell (Reviewer Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1030992
 
localization_priority: Normal
ms.assetid: be39cd0b-56bf-a070-f5d8-c9a440d81ee2
description: "Contains the name of a document reviewer."
---

# Name Cell (Reviewer Section)

Contains the name of a document reviewer.
  
## Remarks

 This value defaults to the name found in the **User name** box on the **General** tab of the **Visio Options** dialog box (click the **File** tab, click **Options**, and then click **General**). 
  
To get a reference to the Name cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Reviewer.Name [  *i*  ] where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the Name cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionReviewer** <br/> |
| Row index:  <br/> |**visRowReviewer** +  *i*  where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visReviewerName** <br/> |
   

