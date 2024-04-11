---
title: "Color Cell (Character Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm160
 
ms.localizationpriority: medium
ms.assetid: 1c9aab2e-6c2f-0684-4e66-c35ac71883d6

description: "Determines the color used for the shape's text."
---

# Color Cell (Character Section)

Determines the color used for the shape's text.
  
## Remarks

To set the color, enter a number from 0 to 23.
  
To enter a custom color, use the RGB or HSL function. The value of a custom color is its RGB color, and RGB( *r, g, b*), rather than a number, will be shown in the ShapeSheet window. When used in numeric operations, custom colors have values of 24 and above. 
  
You can set the transparency of the text color in the Transparency cell.
  
To get a reference to the Color cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Char.Color[ *i*  ]           where  *i*  = <1>, 2, 3, ... |
   
To get a reference to the Color cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionCharacter** <br/> |
|**Row index:**  <br/> |**visRowCharacter** +  *i*           where  *i*  = 0, 1, 2, ... |
|**Cell index:**  <br/> |**visCharacterColor** <br/> |
   

