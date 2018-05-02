---
title: "Prompt Cell (Shape Data Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251343
 
localization_priority: Normal
ms.assetid: 42f42d73-a00c-ca93-adc9-4f8869b9cd42
description: "Specifies descriptive or instructional text that appears as a tip when the mouse is paused over a value in the Shape Data window."
---

# Prompt Cell (Shape Data Section)

Specifies descriptive or instructional text that appears as a tip when the mouse is paused over a value in the **Shape Data** window. 
  
## Remarks

To get a reference to the Prompt cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Prop.  *Name*  .Prompt where  *Name*  is the row name  <br/> |
   
To get a reference to the Prompt cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionProp** <br/> |
| Row index:  <br/> |**visRowProp +** *i*  where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visCustPropsPrompt** <br/> |
   

