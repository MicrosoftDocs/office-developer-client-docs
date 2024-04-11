---
title: "Transparency Cell (Character Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm50135
 
ms.localizationpriority: medium
ms.assetid: ab835a1a-9e90-126e-279f-463882c48e93
description: "Determines the transparency level for a range of a shape's text color."
---

# Transparency Cell (Character Section)

Determines the transparency level for a range of a shape's text color.
  
|**Value**|**Description**|
|:-----|:-----|
|0 - 100  <br/> |Represents the percentage of transparency. The default is 0% (completely opaque). |
   
## Remarks

Values are rounded to the nearest half percent. A value of 100% is completely transparent. Although a shape that has completely transparent text appears the same on the drawing page as a shape that has no text, it interacts with other objects on the page in the same way as if its transparency were 0%.
  
You can also set this value by using the slider control on the **Font** tab in the **Text** dialog box (on the **Home** tab, click the **Font** arrow). 
  
If the Characters section contains multiple rows, the Transparency cell contains formatting information applied to a sub-range of a shape's text. Otherwise, it contains formatting information for all of the shape's text.
  
To get a reference to the Transparency cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Char.ColorTrans[ *i*  ] where  *i*  = <1>, 2, 3... |
   
To get a reference to the Transparency cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionCharacter** <br/> |
|**Row index:**  <br/> |**visRowCharacter** +  *i*  where  *i*  = 0, 1, 2... |
|**Cell index:**  <br/> |**visCharacterColorTrans** <br/> |
   

