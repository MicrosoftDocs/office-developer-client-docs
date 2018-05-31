---
title: "Transparency Cell (Layers Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm50130
 
localization_priority: Normal
ms.assetid: 7382e2aa-5e18-19d2-88d8-c4a19a385106
description: "Determines the transparency level for a layer color."
---

# Transparency Cell (Layers Section)

Determines the transparency level for a layer color.
  
|**Value**|**Description**|
|:-----|:-----|
|0 - 100  <br/> |Represents the percentage of transparency. The default is 0% (completely opaque).  <br/> |
   
## Remarks

Values are rounded to the nearest half percent. A value of 100% is completely transparent. Although a layer that has completely transparent color appears the same on the drawing page as a layer that has no color, it interacts with other objects on the page in the same way as if its transparency were 0%. You can also set this value by using the slider control in the **Layer Properties** dialog box (on the **Home** tab, in the **Editing** group, click **Layers**, and then click **Layer Properties**).
  
To get a reference to the Transparency cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Layers.ColorTrans[ *i*  ] where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the Transparency cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionLayer** <br/> |
|Row index:  <br/> |**visRowLayer** +  *i*  where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visLayerColorTrans** <br/> |
   

