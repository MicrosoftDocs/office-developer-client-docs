---
title: "ShapeFixedCode Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm880
 
ms.localizationpriority: medium
ms.assetid: a1736a5c-421c-2bdb-b164-76a8cd06cc3d
description: "Specifies placement behavior for a placeable shape."
---

# ShapeFixedCode Cell (Shape Layout Section)

Specifies placement behavior for a placeable shape.
  
|**Value**|**Selection mode**|**Automation constant**|
|:-----|:-----|:-----|
|&amp;H1  <br/> |Don't move this shape when shapes are laid out by using the **Configure Layout** dialog box. |**visSLOFixedPlacement** <br/> |
|&amp;H2  <br/> |Don't move this shape and do not allow shapes that plow to be placed on top of it. |**visSLOFixedPlow** <br/> |
|&amp;H4  <br/> |Don't move this shape and allow shapes that plow to be placed on top of it. |**visSLOFixedPermeablePlow** <br/> |
|&amp;H20 (32)  <br/> |Ignore connection point locations when being routed to. |**visSLOFixedConnPtsIgnore** <br/> |
|&amp;H40 (64)  <br/> |Only allow routing to sides with connection points. |**visSLOFixedConnPtsOnly** <br/> |
|&amp;H80 (128)  <br/> |Don't glue to the perimeter of this shape. Glue to the shape's alignment box instead. |**visSLOFixedNoFoldToShape** <br/> |
   
## Remarks

You can also set the value of this cell on the **Placement** tab in the **Behavior** dialog box (with a shape selected, on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, in the **Shape Design** group, click **Behavior**, and then click the **Placement** tab). 
  
You can set any combination of these values for this cell. For example, you can enter the value 3 (&amp;H3), which eliminates movement when you lay out shapes by using the **Configure Layout** dialog box (on the **Design** tab, in the **Layout** group, click **Re-Layout Page**, and then click **More Layout Options** ) and when other placeable shapes are placed on or near the shape. 
  
In versions earlier than Visio 2000, you set this behavior using the ObjInteract cell in the Miscellaneous section. 
  
To get a reference to the ShapeFixedCode cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |ShapeFixedCode  <br/> |
   
To get a reference to the ShapeFixedCode cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowShapeLayout** <br/> |
|Cell index:  <br/> |**visSLOFixedCode** <br/> |
   

