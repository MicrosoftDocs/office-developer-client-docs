---
title: "Initials Cell (Reviewer Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60045
 
ms.localizationpriority: medium
ms.assetid: 8f5d34f0-4c4b-5265-83c1-5b86b73d464f
description: "Contains the initials of a document reviewer."
---

# Initials Cell (Reviewer Section)

Contains the initials of a document reviewer.
  
## Remarks

This value defaults to the initials in the **Initials** box on the **General** tab in the **Visio Options** dialog box (click the **File** tab, click **Options**, and then click **General** ). 
  
To get a reference to the Initials cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Reviewer.Initials [  *i*  ] where  *i*  = <1>, 2, 3... |
   
To get a reference to the Initials cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionReviewer** <br/> |
| **Row index:**  <br/> |**visRowReviewer** +  *i*  where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visReviewerInitials** <br/> |
   

