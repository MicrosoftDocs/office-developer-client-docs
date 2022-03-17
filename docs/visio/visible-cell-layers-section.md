---
title: "Visible Cell (Layers Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1110
 
ms.localizationpriority: medium
ms.assetid: 02048012-a814-410b-f26e-56fcfbe106e6
description: "Specifies whether shapes belonging to the layer are visible on the drawing page."
---

# Visible Cell (Layers Section)

Specifies whether shapes belonging to the layer are visible on the drawing page.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Shapes are visible. |
|FALSE  <br/> |Shapes are hidden. |
   
## Remarks

This cell corresponds to the **Visible** option in the **Layer Properties** dialog box (on the **Home** tab, in the **Editing** group, click **Layers**, and then click **Layer Properties** ). 
  
To get a reference to the Visible cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Layers.Visible[ *i*  ] where  *i*  = <1>, 2, 3... |
   
To get a reference to the Visible cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionLayer** <br/> |
|**Row index:**  <br/> |**visRowLayer** +  *i*  where  *i*  = 0, 1, 2... |
|**Cell index:**  <br/> |**visLayerVisible** <br/> |
   

