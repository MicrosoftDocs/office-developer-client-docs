---
title: "LineColor Cell (Line Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm535
 
localization_priority: Normal
ms.assetid: d857b48b-9a3d-a1e1-5ad2-6816a492c8ab
description: "Determines the line color of the shape."
---

# LineColor Cell (Line Format Section)

Determines the line color of the shape.
  
## Remarks

To set the line color, enter a number from 0 to 23, which is an index into a collection of line colors. You can view the line color collection in the **Line** dialog box (on the **Home** tab, in the **Shape** group, click **Line**, point to **Weight**, and then click **More Lines**). You can also set the value of LineColor in the **Line** dialog box. 
  
To enter a custom color, use the RGB or HSL function. The value of a custom color is its RGB color, and RGB( *r, g, b*  ), rather than a number, will be shown in the ShapeSheet window. When used in numeric operations, custom colors have values of 24 and above. 
  
You can set the transparency of the line color in the LineColorTrans cell.
  
To get a reference to the LineColor cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |LineColor  <br/> |
   
To get a reference to the LineColor cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowLine** <br/> |
|Cell index:  <br/> |**visLineColor** <br/> |
   

