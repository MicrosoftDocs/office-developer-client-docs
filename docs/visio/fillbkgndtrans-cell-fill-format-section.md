---
title: "FillBkgndTrans Cell (Fill Format Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82253230
 
ms.localizationpriority: medium
ms.assetid: 87065350-ba9a-aae8-47f6-f263f6700d08
description: "Determines the transparency level for the background (fill) color of the shape's fill pattern."
---

# FillBkgndTrans Cell (Fill Format Section)

Determines the transparency level for the background (fill) color of the shape's fill pattern.
  
|**Value**|**Description**|
|:-----|:-----|
|0 - 100  <br/> |Represents the percentage of transparency. The default is 0% (completely opaque). |
   
## Remarks

Values are rounded to the nearest half percent. A value of 100% is completely transparent. Although a shape with a completely transparent fill appears the same as a shape with no fill on the drawing page, it will interact with other objects on the page in the same ways as if its transparency is 0%.
  
You can also set this value using the slider control in the **Fill** dialog box (on the **Home** tab, in the **Shape** group, click **Fill**, and then click **Fill Options**). This value controls the value of both the background and foreground fill transparencies. To set these values independently, you must enter them in the ShapeSheet window.
  
To get a reference to the FillBkgndTrans cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |FillBkgndTrans  <br/> |
   
To get a reference to the FillBkgndTrans cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowFill** <br/> |
|**Cell index:**  <br/> |**visFillBkgndTrans** <br/> |
   

