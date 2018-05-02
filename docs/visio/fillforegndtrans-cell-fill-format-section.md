---
title: "FillForegndTrans Cell (Fill Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82253231
 
localization_priority: Normal
ms.assetid: 8b1b3904-6635-3fd1-31a9-ff32c19394af
description: "Determines the transparency level for the foreground (fill) color of the shape's fill pattern."
---

# FillForegndTrans Cell (Fill Format Section)

Determines the transparency level for the foreground (fill) color of the shape's fill pattern.
  
|**Value**|**Description**|
|:-----|:-----|
|0 - 100  <br/> |Represents the percentage of transparency. The default is 0% (completely opaque).  <br/> |
   
## Remarks

Values are rounded to the nearest half percent. A value of 100% is completely transparent. Although a shape with a completely transparent fill appears the same as a shape with no fill on the drawing page, it will interact with other objects on the page in the same ways as if its transparency is 0%.
  
You can also set this value using the slider control in the **Fill** dialog box (on the **Home** tab, in the **Shape** group, click **Fill**, and then click **Fill Options**). This value controls the value of both the background and foreground fill transparencies. To set these values independently, you must enter them in the ShapeSheet window.
  
To get a reference to the FillForegndTrans cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |FillForegndTrans  <br/> |
   
To get a reference to the FillForegndTrans cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowFill** <br/> |
|Cell index:  <br/> |**visFillForegndTrans** <br/> |
   

