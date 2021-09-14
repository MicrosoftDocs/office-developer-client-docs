---
title: "Action Cell (Actions Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm5
 
ms.localizationpriority: medium
ms.assetid: 435e49ee-0b51-8ce3-0589-3f0717026f4a
description: "Contains the formula to be executed when a user chooses a command on a shortcut or action tag menu."
---

# Action Cell (Actions Section)

Contains the formula to be executed when a user chooses a command on a shortcut or action tag menu.
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
## Remarks

An Action cell is evaluated only when the action occurs, not when the formula is entered.
  
To get a reference to the the Action cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Actions.  *name*  .Action           where Actions. *name*  is the name of the actions row  <br/> |
   
To get a reference to thethe Action cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionAction** <br/> |
| Row index:  <br/> |**visRowAction** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visActionAction** <br/> |
   

