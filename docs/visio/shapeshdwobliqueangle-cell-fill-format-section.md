---
title: "ShapeShdwObliqueAngle Cell (Fill Format Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033174
 
ms.localizationpriority: medium
ms.assetid: bad4c512-e91f-d459-d65c-a4ab725c3c14
description: "Specifies the angle of oblique direction of a shape's shadow."
---

# ShapeShdwObliqueAngle Cell (Fill Format Section)

Specifies the angle of oblique direction of a shape's shadow.
  
## Remarks

A value of zero (0) in this cell indicates that the angle direction is straight up and is measured moving clockwise.
  
This value corresponds to the value of the **Direction** setting in the **Shadow** dialog box (on the **Home** tab, in the **Shape** group, click **Shadow**, and then click **Shadow Options**).
  
To get a reference to the ShapeShdwObliqueAngle cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | ShapeShdwObliqueAngle  <br/> |
   
To get a reference to the ShapeShdwObliqueAngle cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowFill** <br/> |
| **Cell index:**  <br/> |**visFillShdwObliqueAngle** <br/> |
   

