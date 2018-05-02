---
title: "ShdwObliqueAngle Cell (Page Properties Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033178
 
localization_priority: Normal
ms.assetid: 2e0b9754-3e3b-3a26-4e1a-e09102055c20
description: "Contains a number specifying the angle of oblique direction when applying the default page shadow type."
---

# ShdwObliqueAngle Cell (Page Properties Section)

Contains a number specifying the angle of oblique direction when applying the default page shadow type.
  
## Remarks

A value of zero (0) in this cell indicates that the angle direction is straight up and is measured moving clockwise.
  
 The angle described in this cell is used whenever the ShapeShdwType Cell (the shadow type for a shape on the page) is set to Page Default ( **visFSTPageDefault** ), and the shadow type is oblique. The default page shadow type is defined in the ShdwType cell. 
  
To set this behavior for an individual shape, use the ShapeShdwObliqueAngle cell in the Fill Format section.
  
To get a reference to the ShdwObliqueAngle cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ShdwObliqueAngle  <br/> |
   
To get a reference to the ShdwObliqueAngle cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPage** <br/> |
| Cell index:  <br/> |**visPageShdwObliqueAngle** <br/> |
   

