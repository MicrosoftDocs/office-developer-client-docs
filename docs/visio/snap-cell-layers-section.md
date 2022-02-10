---
title: "Snap Cell (Layers Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251355
 
ms.localizationpriority: medium
ms.assetid: c1b24e45-6f08-686b-b53d-e85fb9087a50
description: "Determines whether other shapes can snap to shapes assigned to the layer. Shapes assigned to the layer can snap to other shapes, but other shapes can't snap to them."
---

# Snap Cell (Layers Section)

Determines whether other shapes can snap to shapes assigned to the layer. Shapes assigned to the layer can snap to other shapes, but other shapes can't snap to them.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Other shapes can snap to shapes on the layer. |
|FALSE  <br/> |Other shapes cannot snap to shapes on the layer. |
   
## Remarks

You can also set the value of this cell using the **Snap** option in the **Layer Properties** dialog box (on the **Home** tab, in the **Editing** group, click **Layers**, and then click **Layer Properties**).
  
To get a reference to the Snap cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Layers.Snap[ *i*  ] where  *i*  = <1>, 2, 3... |
   
To get a reference to the Snap cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionLayer** <br/> |
|Row index:  <br/> |**visRowLayer** +  *i*  where  *i*  = 0, 1, 2... |
|Cell index:  <br/> |**visLayerSnap** <br/> |
   

