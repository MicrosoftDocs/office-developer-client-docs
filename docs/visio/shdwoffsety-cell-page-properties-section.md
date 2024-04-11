---
title: "ShdwOffsetY Cell (Page Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm930
 
ms.localizationpriority: medium
ms.assetid: f3f53a7d-7450-b2b0-b508-6044a87450d9
description: "Determines the distance in page units that a shape's drop shadow is offset vertically from the shape."
---

# ShdwOffsetY Cell (Page Properties Section)

Determines the distance in page units that a shape's drop shadow is offset vertically from the shape.
  
## Remarks

This value is set in the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow). This value is independent of the scale of the drawing. If the drawing is scaled, the shadow offset remains the same. 
  
To get a reference to the ShdwOffsetY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | ShdwOffsetY  <br/> |
   
To get a reference to the ShdwOffsetY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowPage** <br/> |
| **Cell index:**  <br/> |**visPageShdwOffsetY** <br/> |
   

