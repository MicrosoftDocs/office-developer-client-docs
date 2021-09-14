---
title: "OutputFormat Cell (Document Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251617
 
ms.localizationpriority: medium
ms.assetid: 17238019-c800-5d3a-32f6-fb0008d4e25f
description: "Determines the output format for a drawing. Drawing pages are usually formatted for printing (default); however, you can choose other output formats."
---

# OutputFormat Cell (Document Properties Section)

Determines the output format for a drawing. Drawing pages are usually formatted for printing (default); however, you can choose other output formats.
  
|**Value**|**Output format**|
|:-----|:-----|
| 0  <br/> | Printing (default)  <br/> |
| 1  <br/> | PowerPoint slide show  <br/> |
| 2  <br/> | HTML or GIF output  <br/> |
   
## Remarks

To get a reference to the OutputFormat cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | OutputFormat  <br/> |
   
To get a reference to the OutputFormat cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowDoc** <br/> |
| Cell index:  <br/> |**visDocOutputFormat** <br/> |
   

