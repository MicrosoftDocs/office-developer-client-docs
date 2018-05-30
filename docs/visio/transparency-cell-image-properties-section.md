---
title: "Transparency Cell (Image Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm51095
 
localization_priority: Normal
ms.assetid: 5b265356-1602-4241-fbe1-4d5a55392a52
description: "Determines the transparency level for a layer color."
---

# Transparency Cell (Image Properties Section)

Determines the transparency level for a layer color.
  
|**Value**|**Description**|
|:-----|:-----|
|0 - 100  <br/> |Represents the percentage of transparency. The default is 0% (completely opaque).  <br/> |
   
## Remarks

Values are rounded to the nearest half percent. A value of 100% is completely transparent. Although a layer that has completely transparent color appears the same on the drawing page as a layer that has no color, it interacts with other objects on the page in the same way as if its transparency were 0%. You can also set this value by using the slider control in the **Layer Properties** dialog box (on the **Home** tab, in the **Editing** group, click **Layers**, and then click **Layer Properties**).
  
To get a reference to the Transparency cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Transparency  <br/> |
   
To get a reference to the Transparency cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowImage** <br/> |
|Cell index:  <br/> |**visImageTransparency** <br/> |
   

