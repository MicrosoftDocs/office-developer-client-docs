---
title: "PageShapeSplit Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033777
 
localization_priority: Normal
ms.assetid: 4d3bdf77-0ad4-86a4-d215-1d5a5fbe33f7
description: "Indicates whether shapes on the page can be automatically split."
---

# PageShapeSplit Cell (Page Layout Section)

Indicates whether shapes on the page can be automatically split.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Do not allow automatic shape splitting.  <br/> |**visPLOSplitNone** <br/> |
|1  <br/> |Allow automatic shape splitting (the default).  <br/> |**visPLOSplitAllow** <br/> |
   
## Remarks

Automatic splitting of shapes is enabled and disabled at three different levels: application, page, and shape. By default, splitting is enabled at the application and page levels. The default setting for shapes varies by drawing type. 
  
To enable or disable splitting at the application level, use the **Enable connector splitting** setting on the **Advanced** tab of the **Visio Options** dialog box (click the **Office** button, click **Options** on the **Visio** tab, and then click **Advanced** ). 
  
To enable or disable splitting at the shape level, see the ShapeSplit and ShapeSplittable cells. 
  
To get a reference to the PageShapeSplit cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |PageShapeSplit  <br/> |
   
To get a reference to the PageShapeSplit cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPageLayout** <br/> |
|Cell index:  <br/> |**visPLOSplit** <br/> |
   

