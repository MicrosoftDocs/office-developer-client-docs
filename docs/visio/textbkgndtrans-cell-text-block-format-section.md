---
title: "TextBkgndTrans Cell (Text Block Format Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82253240
 
ms.localizationpriority: medium
ms.assetid: b2f9d317-cc42-bec5-66f9-f988bcbdcc24
description: "Determines the transparency level for the background color of the shape's text block."
---

# TextBkgndTrans Cell (Text Block Format Section)

Determines the transparency level for the background color of the shape's text block.
  
|**Value**|**Description**|
|:-----|:-----|
|0 - 100  <br/> |Represents the percentage of transparency. The default is 0% (completely opaque). |
   
## Remarks

Values are rounded to the nearest half percent. A value of 100% is completely transparent. Although a shape that has a completely transparent text background appears the same on the drawing page as a shape that has no text background, it interacts with other objects on the page in the same way as if its transparency were 0%.
  
You can also set this value using the slider control on the **Font** tab of the **Text** dialog box (on the **Home** tab, click the **Font** arrow). 
  
To get a reference to the TextBkgndTrans cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |TextBkgndTrans  <br/> |
   
To get a reference to the TextBkgndTrans cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowText** <br/> |
|**Cell index:**  <br/> |**visTxtBlkBkgndTrans** <br/> |
   

