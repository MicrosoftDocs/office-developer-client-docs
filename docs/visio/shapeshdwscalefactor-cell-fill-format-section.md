---
title: "ShapeShdwScaleFactor Cell (Fill Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033175
 
localization_priority: Normal
ms.assetid: 94ec06c5-8d2f-dd27-1eed-1abaf93daba8
description: "Specifies the percentage by which the shadow of a shape can be enlarged or reduced."
---

# ShapeShdwScaleFactor Cell (Fill Format Section)

Specifies the percentage by which the shadow of a shape can be enlarged or reduced.
  
## Remarks

Each shadow has a shadowed pin location, which is a point on the shadow that corresponds to the shape's pin. For example, if a shape's pin is in the center of the shape, then the shadowed pin location would be the point in the center of the shadow. When applying scale to simple shadows, magnification is centered at the shadowed pin location; when applying scale to oblique shadows, magnification is applied in the oblique direction. 
  
To set this value for all the shapes on a page, use the ShdwScaleFactor cell in the Page Properties section.
  
This value corresponds to the value of the **Magnification** setting in the **Shadow** dialog box (on the **Home** tab, in the **Shape** group, click **Shadow**, and then click **Shadow Options**).
  
To get a reference to the ShapeShdwScaleFactor cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |ShapeShdwScaleFactor  <br/> |
   
To get a reference to the ShapeShdwScaleFactor cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowFill** <br/> |
|Cell index:  <br/> |**visFillShdwScaleFactor** <br/> |
   

