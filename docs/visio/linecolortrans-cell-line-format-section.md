---
title: "LineColorTrans Cell (Line Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm50120
 
localization_priority: Normal
ms.assetid: b68054b5-7efd-1156-9dc1-5ec94e18d227
description: "Determines the transparency level of a shape's line color."
---

# LineColorTrans Cell (Line Format Section)

Determines the transparency level of a shape's line color.
  
|**Value**|**Description**|
|:-----|:-----|
|0 - 100  <br/> |Represents the percentage of transparency. The default is 0% (completely opaque).  <br/> |
   
## Remarks

Values are rounded to the nearest half percent. A value of 100% is completely transparent. Although a shape with a completely transparent line color appears the same as a shape with no lines on the drawing page, it will interact with other objects on the page in the same ways as if its transparency is 0%. 
  
You can also set this value by using the slider control in the **Line** dialog box (on the **Home** tab, in the **Shape** group, click **Line**, point to **Weight**, and then click **More Lines**).
  
To get a reference to the LineColorTrans cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |LineColorTrans  <br/> |
   
To get a reference to the LineColorTrans cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowLine** <br/> |
|Cell index:  <br/> |**visLineColorTrans** <br/> |
   

