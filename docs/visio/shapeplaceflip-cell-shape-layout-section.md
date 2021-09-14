---
title: "ShapePlaceFlip Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82253247
 
ms.localizationpriority: medium
ms.assetid: 40008507-d9e4-9c0e-603f-d5e6da73a94b
description: "Determines how a placeable shape flips, rotates, or both on the page when you are laying out shapes by using the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options)."
---

# ShapePlaceFlip Cell (Shape Layout Section)

Determines how a placeable shape flips, rotates, or both on the page when you are laying out shapes by using the **Configure Layout** dialog box (on the **Design** tab, in the **Layout** group, click **Re-Layout Page**, and then click **More Layout Options**).
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Use page default.  <br/> |**visLOFlipDefault** <br/> |
|1  <br/> |Flip horizontal.  <br/> |**visLOFlipX** <br/> |
|2  <br/> |Flip vertical.  <br/> |**visLOFlipY** <br/> |
|4  <br/> |Flip in 90 degree increments between 0 and 270.  <br/> |**visLOFlipRotate** <br/> |
|8  <br/> |Do not flip.  <br/> |**visLOFlipNone** <br/> |
   
## Remarks

The value in the ShapePlaceFlip cell helps orient a placeable shape toward the next placeable shape it is connected to.
  
To set this behavior for  *all*  the shapes on the drawing page, use the PlaceFlip cell in the Page Layout section. 
  
To get a reference to the ShapePlaceFlip cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |ShapePlaceFlip  <br/> |
   
To get a reference to the ShapePlaceFlip cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowShapeLayout** <br/> |
|Cell index:  <br/> |**visSLOPlaceFlip** <br/> |
   

