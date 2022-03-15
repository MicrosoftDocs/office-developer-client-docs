---
title: "Color Cell (Reviewer Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60032
 
ms.localizationpriority: medium
ms.assetid: c1e3d7bf-e6b6-65f1-ae40-80c8ba4821cd

description: "An RGB value that represents the color assigned to a document reviewer's markup."
---

# Color Cell (Reviewer Section)

An RGB value that represents the color assigned to a document reviewer's markup. 
  
## Remarks

Colors are assigned to reviewers in the following sequence: red, blue, green, violet, orange, turquoise, gray. These colors are cycled through again for any remaining reviewers. 
  
Comments entered on the original drawing page are always colored yellow, regardless of the color assigned to a reviewer in the Color cell. 
  
To get a reference to the Color cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Reviewer.Color [  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the Color cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionReviewer** <br/> |
| **Row index:**  <br/> |**visRowReviewer** +  *i*            where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visReviewerColor** <br/> |
   

