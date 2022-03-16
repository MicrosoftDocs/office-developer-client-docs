---
title: "Color Cell (Layers Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm165
 
ms.localizationpriority: medium
ms.assetid: 61c19342-46fb-48d4-6375-c9ea8306286d

description: "Specifies the color used to display the layer."
---

# Color Cell (Layers Section)

Specifies the color used to display the layer.
  
## Remarks

To set the color, enter a number from 0 to 23.
  
This cell value corresponds to the **Layer color** setting in the **Layer Properties** dialog box (in the **Editing** group on the **Home** tab, click **Layers** and then click **Layer Properties**).
  
To enter a custom color, use the RGB or HSL function. The value of a custom color is its RGB color, and RGB( *r, g, b*), rather than a number, will be shown in the ShapeSheet window. When used in numeric operations, custom colors have values of 24 and above. A value of 255 indicates that the layer has no color. 
  
You can set the transparency of the layer color in the Transparency cell.
  
To get a reference to the Color cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Layers.Color[ *i*  ]           where  *i*  = <1>, 2, 3, ... |
   
To get a reference to the Color cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionLayer** <br/> |
|**Row index:**  <br/> |**visRowLayer** +  *i*           where  *i*  = 0, 1, 2, ... |
|**Cell index:**  <br/> |**visLayerColor** <br/> |
   

