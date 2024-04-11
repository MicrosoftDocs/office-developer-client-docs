---
title: "DrawingSizeType Cell (Page Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm275
 
ms.localizationpriority: medium
ms.assetid: 7fe270e8-0dff-bf1f-dfc0-c0608af79f59
description: "Determines the drawing size."
---

# DrawingSizeType Cell (Page Properties Section)

Determines the drawing size.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Same as printer  <br/> |**visPrintSetup** <br/> |
|1  <br/> |Fit page to drawing contents  <br/> |**visTight** <br/> |
|2  <br/> |Standard  <br/> |**visStandard** <br/> |
|3  <br/> |Custom page size  <br/> |**visCustom** <br/> |
|4  <br/> |Custom scaled drawing size  <br/> |**visLogical** <br/> |
|5  <br/> |Metric (ISO)  <br/> |**visDSMetric** <br/> |
|6  <br/> |ANSI Engineering  <br/> |**visDSEngr** <br/> |
|7  <br/> |ANSI Architectural  <br/> |**visDSArch** <br/> |
   
## Remarks

To set the drawing size, use the **Page Setup** dialog box (click the **Page Setup** arrow on the **Design** tab) or manually resize the page with the mouse. 
  
To get a reference to the DrawingSizeType cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |DrawingSizeType  <br/> |
   
To get a reference to the DrawingSizeType cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowPage** <br/> |
|**Cell index:**  <br/> |**visPageDrawSizeType** <br/> |
   

