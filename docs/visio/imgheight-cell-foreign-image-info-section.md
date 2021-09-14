---
title: "ImgHeight Cell (Foreign Image Info Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm445
 
ms.localizationpriority: medium
ms.assetid: decb86a4-b711-35e1-b9dc-744a84ee177c
description: "Determines the height of the object's image within its border. The default formula is:"
---

# ImgHeight Cell (Foreign Image Info Section)

Determines the height of the object's image within its border. The default formula is:
  
= Height \* 1
  
## Remarks

To get a reference to the ImgHeight cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ImgHeight  <br/> |
   
To get a reference to the ImgHeight cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowForeign** <br/> |
| Cell index:  <br/> |**visFrgnImgHeight** <br/> |
   

