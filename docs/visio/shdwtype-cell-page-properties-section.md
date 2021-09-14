---
title: "ShdwType Cell (Page Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60084
 
ms.localizationpriority: medium
ms.assetid: 551166d0-3aaa-0fd7-e742-cf3450ba90ed
description: "Indicates the default shadow type for a page."
---

# ShdwType Cell (Page Properties Section)

Indicates the default shadow type for a page.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 1  <br/> | Simple  <br/> |**visFSTSimple** <br/> |
| 2  <br/> | Oblique  <br/> |**visFSTOblique** <br/> |
|3  <br/> |Inner  <br/> |**visFSTInner** <br/> |
   
## Remarks

 The shadow type described in this cell is used whenever the ShapeShdwType Cell (the shadow type for an individual shape on the page) is set to Page Default (**visFSTPageDefault** ). 
  
Simple shadow types are described as offset shadows in the user interface (UI). A simple shadow gives the effect of the shape being shadowed onto a parallel plane located some distance behind it. Oblique shadows are described as oblique shadows in the UI and give the effect of a shadow being cast onto a plane perpendicular to the shape. 
  
For a list of predefined simple and oblique shadow types, see the **Style** list on the **Shadows** tab of the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow). 
  
To get a reference to the ShdwType cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ShdwType  <br/> |
   
To get a reference to the ShapeShdwOffsetX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPage** <br/> |
| Cell index:  <br/> |**visPageShdwType** <br/> |
   

