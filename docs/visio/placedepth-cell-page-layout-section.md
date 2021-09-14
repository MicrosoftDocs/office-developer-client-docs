---
title: "PlaceDepth Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1230
 
ms.localizationpriority: medium
ms.assetid: 02c139db-fe67-f550-1d07-8c8a9a4fb427
description: "Determines the method by which the drawing is analyzed before creating the layout, and determines the type of layout."
---

# PlaceDepth Cell (Page Layout Section)

Determines the method by which the drawing is analyzed before creating the layout, and determines the type of layout.
  
|**Value**|**Placement depth for vertical and horizontal layouts**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Page default  <br/> |**visPLOPlaceDepthDefault** <br/> |
| 1  <br/> | Medium  <br/> |**visPLOPlaceDepthMedium** <br/> |
| 2  <br/> | Deep  <br/> |**visPLOPlaceDepthDeep** <br/> |
| 3  <br/> | Shallow  <br/> |**visPLOPlaceDepthShallow** <br/> |
   
## Remarks

To get a reference to the PlaceDepth cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | PlaceDepth  <br/> |
   
To get a reference to the PlaceDepth cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPageLayout** <br/> |
| Cell index:  <br/> |**visPLOPlaceDepth** <br/> |
   

