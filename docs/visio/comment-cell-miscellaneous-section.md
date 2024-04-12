---
title: "Comment Cell (Miscellaneous Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm170
 
ms.localizationpriority: medium
ms.assetid: 6f52ed60-d58b-86e6-f7e2-2ef19d4afa75
description: "Contains the comment text in string format for a shape."
---

# Comment Cell (Miscellaneous Section)

Contains the comment text in string format for a shape.
  
## Remarks

You can also insert a comment by clicking **New Comment** on the **Review** tab. 
  
To get a reference to the Comment cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Comment  <br/> |
   
To get a reference to the Comment cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowMisc** <br/> |
|**Cell index:**  <br/> |**visComment** <br/> |
   

