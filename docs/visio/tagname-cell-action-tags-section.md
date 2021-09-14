---
title: "TagName Cell (Action Tags Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60088
 
ms.localizationpriority: medium
ms.assetid: 28d1cd60-4fb6-9feb-1a13-0962798ac1ad

description: "Name of the action tag that is used as a key to associate the action tag with its actions."
---

# TagName Cell (Action Tags Section)

Name of the action tag that is used as a key to associate the action tag with its actions.
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
## Remarks

 The TagName cell in the Action Tags section works together with the TagName cell in the Actions section to associate an action tag with its actions. Rows in the Actions section also have a TagName cell, and those rows with the same TagName cell value as this cell define actions to take for this action tag. 
  
To get a reference to the TagName cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | SmartTags.  *name*  .TagName           where SmartTags. *name*  is the name of the action tag row  <br/> |
   
To get a reference to the TagName cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionSmartTag** <br/> |
| Row index:  <br/> |**visRowSmartTag** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visSmartTagName** <br/> |
   

