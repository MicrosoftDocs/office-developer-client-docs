---
title: "Description Cell (Action Tags Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60037
 
localization_priority: Normal
ms.assetid: feb29b91-0f6e-6353-3dd0-7a280843a517

description: "Contains a string that describes the action tag, which appears as a tool tip when users place their pointer over the tag."
---

# Description Cell (Action Tags Section)

Contains a string that describes the action tag, which appears as a tool tip when users place their pointer over the tag.
  
## Remarks

To get a reference to the Description cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | SmartTags.  *name*  .Description           where SmartTags. *name*  is the name of the action tag row  <br/> |
   
To get a reference to the Description cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionSmartTag** <br/> |
| Row index:  <br/> |**visRowSmartTag** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visSmartTagDescription** <br/> |
   

