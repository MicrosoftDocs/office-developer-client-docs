---
title: "ShapeShdwType Cell (Fill Format Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033173
 
localization_priority: Normal
ms.assetid: 1461148d-90a9-6f7c-1b28-9310ffaf0e3b
description: "Specifies the type of shadow for a shape."
---

# ShapeShdwType Cell (Fill Format Section)

Specifies the type of shadow for a shape. 
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Use page default (the default)  <br/> |**visFSTPageDefault** <br/> |
|1  <br/> |Simple  <br/> |**visFSTSimple** <br/> |
|2  <br/> |Oblique  <br/> |**visFSTOblique** <br/> |
   
## Remarks

Use this cell to apply a shape shadow that is different from the page default (the page default shadow type is defined in the ShdwType cell in the Page Properties Section).
  
Simple shadow types are described as offset shadows in the user interface (UI). A simple shadow gives the effect of the shape being shadowed onto a parallel plane located behind the shape. Oblique shadows are described as oblique shadows in the UI and give the effect of a shadow being cast onto a plane perpendicular to the shape. 
  
For a list of predefined simple and oblique shadow types, see the **Style** box in the **Shadow** dialog box (on the **Home** tab, in the **Shape** group, click **Shadow**, and then click **Shadow Options**).
  
To get a reference to the ShapeShdwType cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |ShapeShdwType  <br/> |
   
To get a reference to the ShapeShdwType cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowFill** <br/> |
|Cell index:  <br/> |**visFillShdwType** <br/> |
   

