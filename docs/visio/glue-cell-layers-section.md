---
title: "Glue Cell (Layers Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm415
 
ms.localizationpriority: medium
ms.assetid: 75f2ea45-52ac-ddfa-14ea-402933ae2449
description: "Specifies whether shapes belonging to the layer can be glued."
---

# Glue Cell (Layers Section)

Specifies whether shapes belonging to the layer can be glued.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Glue is enabled. |
|FALSE  <br/> |Glue is disabled. |
   
## Remarks

This cell corresponds to the **Glue** option in the **Layer Properties** dialog box (on the **Home** tab, in the **Editing** group, click **Layers**, and then click **Layer Properties** ). 
  
To get a reference to the Glue cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Layers.Glue[  *i*  ] where  *i*  = <1>, 2, 3... |
   
To get a reference to the Glue cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionLayer** <br/> |
|**Row index:**  <br/> |**visRowLayer** +  *i*  where  *i*  = 0, 1, 2... |
|**Cell index:**  <br/> |**visLayerGlue** <br/> |
   

