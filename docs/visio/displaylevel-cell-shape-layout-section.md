---
title: "DisplayLevel Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm80001
 
localization_priority: Normal
ms.assetid: 08b730c4-5dd8-106e-ddf3-da2c942e2ef6
description: "Determines the display level band (the relative range of Z-order grouping) for the shape."
---

# DisplayLevel Cell (Shape Layout Section)

Determines the display level band (the relative range of Z-order grouping) for the shape.
  
## Remarks

Z-order is the display order for shapes on the drawing page. A shape that is higher in the Z-order appears in front of a shape that is lower in the Z-order when one of the shapes overlays the other one. 
  
The display level divides shapes into groupings, or bands. All shapes in a given band have a higher Z-order than the shapes in a lower band. By default, most shapes have a display level of zero (0).
  
The range of display levels is from -32,767 to +32,767. Shapes that have the same display level are combined into a single band, within which they are also ranked relative to one another by Z-order.
  
You can change the Z-order of shapes within a band by using the commands **Bring Forward**, **Send Backward**, **Bring to Front**, and **Send to Back**. If those commands move a shape out of its given band, Microsoft Visio displays the reserved value -32768 in the shape's DisplayLevel cell, unless the cell is guarded. In that case, the shape cannot be moved to a different band, and Visio displays the warning "Shape protection and/or layer properties prevent complete execution of this command." 
  
To get a reference to the DisplayLevel cell by name from another formula or from a program by using the **CellsU** property, use the following. 
  
|||
|:-----|:-----|
|Cell name:  <br/> |DisplayLevel  <br/> |
   
To get a reference to the DisplayLevel cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowShapeLayout** <br/> |
|Cell index:  <br/> |**visSLODisplayLevel** <br/> |
   

