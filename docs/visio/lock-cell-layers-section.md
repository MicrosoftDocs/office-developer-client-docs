---
title: "Lock Cell (Layers Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm590
 
ms.localizationpriority: medium
ms.assetid: 47bb268f-acdd-7369-716c-bd51a32b8a49
description: "Specifies whether shapes belonging to the layer are locked against being selected or edited."
---

# Lock Cell (Layers Section)

Specifies whether shapes belonging to the layer are locked against being selected or edited.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Shapes are locked.  <br/> |
|FALSE  <br/> |Shapes are not locked.  <br/> |
   
## Remarks

You can also set this value by selecting **Lock** in the **Layer Properties** dialog box (on the **Home** tab, in the **Editing** group, click **Layers**, and then click **Layer Properties**).
  
To get a reference to the Lock cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Layers.Locked[ *i*  ] where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the Lock cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionLayer** <br/> |
|Row index:  <br/> |**visRowLayer** +  *i*  where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visLayerLock** <br/> |
   

