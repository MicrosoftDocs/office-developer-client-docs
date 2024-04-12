---
title: "ShdwForegndTrans Cell (Fill Format Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82253253
 
ms.localizationpriority: medium
ms.assetid: c42d4d2e-f8f0-bc5b-6018-4bb4ffa81b64
description: "Determines the transparency level for the color used for the foreground (stroke) of the shape's drop shadow fill pattern."
---

# ShdwForegndTrans Cell (Fill Format Section)

Determines the transparency level for the color used for the foreground (stroke) of the shape's drop shadow fill pattern.
  
|**Value**|**Description**|
|:-----|:-----|
|0 - 100  <br/> |Represents the percentage of transparency. The default is 0% (completely opaque). |
   
## Remarks

Values are rounded to the nearest half percent. A value of 100% is completely transparent. Although a shadow that has a completely transparent fill appears the same on the drawing page as a shadow that has no fill, it interacts with other objects on the page in the same ways as if its transparency were 0%.
  
You can also set this value by using the slider control in the **Shadow** dialog box (on the **Home** tab, in the **Shape** group, click **Shadow**, and then click **Shadow Options**). This value controls the value of both the background and foreground shadow transparencies. To set these values independently, you must enter them in the ShapeSheet window.
  
To get a reference to the ShdwForegndTrans cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |ShdwForegndTrans  <br/> |
   
To get a reference to the ShdwForegndTrans cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowFill** <br/> |
|**Cell index:**  <br/> |**visFillShdwForegndTrans** <br/> |
   

