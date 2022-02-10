---
title: "Active Cell (Layers Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm10
 
ms.localizationpriority: medium
ms.assetid: 4c8e366f-9e9b-30ea-a89f-57c8d7a1168e
description: "Specifies whether the layer is active. Shapes without pre-assigned layers are assigned to the active layer(s) when you drag them onto the drawing page."
---

# Active Cell (Layers Section)

Specifies whether the layer is active. Shapes without pre-assigned layers are assigned to the active layer(s) when you drag them onto the drawing page.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Layer is active. |
|FALSE  <br/> |Layer is not active. |
   
## Remarks

The value in this cell corresponds to the **Active** setting in the **Layer Properties** dialog box (in the **Editing** group on the **Home** tab, click **Layers**, and then click **Layer Properties**).
  
To get a reference to the Active cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Layers.Active[ *i*  ]           where  *i*  = <1>, 2, 3... |
   
To get a reference to the Active cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionLayer** <br/> |
|Row index:  <br/> |**visRowLayer** +  *i*           where  *i*  = 0, 1, 2... |
|Cell index:  <br/> |**visLayerActive** <br/> |
   

