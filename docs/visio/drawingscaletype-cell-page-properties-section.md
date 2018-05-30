---
title: "DrawingScaleType Cell (Page Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm270
 
localization_priority: Normal
ms.assetid: 5d4f1cf8-bc1f-07b8-1da5-7253808e337e
description: "Determines the drawing scale selected in the Page Setup dialog box (click the Page Setup arrow on the Home tab)."
---

# DrawingScaleType Cell (Page Properties Section)

Determines the drawing scale selected in the **Page Setup** dialog box (click the **Page Setup** arrow on the **Home** tab). 
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | No Scale  <br/> |**visNoScale** <br/> |
| 1  <br/> | Architectural Scale  <br/> |**visArchitectural** <br/> |
| 2  <br/> | Civil Engineering Scale  <br/> |**visEngineering** <br/> |
| 3  <br/> | Custom Scale  <br/> |**visScaleCustom** <br/> |
| 4  <br/> | Metric  <br/> |**visScaleMetric** <br/> |
| 5  <br/> | Mechanical Engineering Scale  <br/> |**visScaleMechanical** <br/> |
   
## Remarks

To get a reference to the DrawingScaleType cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | DrawingScaleType  <br/> |
   
To get a reference to the DrawingScaleType cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPage** <br/> |
| Cell index:  <br/> |**visPageDrawScaleType** <br/> |
   

