---
title: "HideForApply Cell (Style Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251698
 
ms.localizationpriority: medium
ms.assetid: 62d87db9-b8ca-60b6-bf27-5168c718ec96
description: "Determines where a style is shown in the Microsoft Visio user interface."
---

# HideForApply Cell (Style Properties Section)

Determines where a style is shown in the Microsoft Visio user interface.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Show the style only in the **Drawing Explorer**. |
| FALSE  <br/> | Show the style in the **Drawing Explorer**. |
   
## Remarks

When you base a new style on a style that is hidden, the new style does not inherit this attribute.
  
To get a reference to the HideForApply cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | HideForApply  <br/> |
   
To get a reference to the HideForApply cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowStyle** <br/> |
| **Cell index:**  <br/> |**visStyleHidden** <br/> |
   

