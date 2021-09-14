---
title: "ObjType Cell (Miscellaneous Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm745
 
ms.localizationpriority: medium
ms.assetid: 3afee07b-e91a-a91c-fba2-0e3251dd6385
description: "Determines whether objects are placeable or routable in diagrams when you use the Configure Layout dialog box to lay out shapes."
---

# ObjType Cell (Miscellaneous Section)

Determines whether objects are placeable or routable in diagrams when you use the **Configure Layout** dialog box to lay out shapes. 
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|&amp;H0  <br/> |Default. The application decides based on the drawing context.  <br/> |**visLOFlagsVisDecides** <br/> |
|&amp;H1  <br/> |Shape is placeable.  <br/> |**visLOFlagsPlacable** <br/> |
|&amp;H2  <br/> |Shape is routable. Must be a one-dimensional (1-D) shape.  <br/> |**visLOFlagsRoutable** <br/> |
|&amp;H4  <br/> |Shape is not placeable, not routable.  <br/> |**visLOFlagsDont** <br/> |
|&amp;H8  <br/> |Group contains placeable/routable shapes.  <br/> |**visLOFlagsPNRGroup** <br/> |
   
## Remarks

By default, the ObjType cell is set to No Formula for a shape, which evaluates to 0, meaning that the application determines whether the shape can be placeable depending on its context. For example, if you draw a simple rectangle, the value of its ObjType cell is 0. If you then use the **Connector** tool to connect the rectangle to another shape, Visio resets the value of the rectangle's ObjType cell to 1 (placeable). 
  
The value of the ObjType cell can be a combination of values. If the non-placeable bit is set (&amp;H4), however, it takes precedence over other values except the group value (&amp;H8).
  
To get a reference to the ObjType cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |ObjType  <br/> |
   
To get a reference to the ObjType cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowMisc** <br/> |
|Cell index:  <br/> |**visLOFlags** <br/> |
   

