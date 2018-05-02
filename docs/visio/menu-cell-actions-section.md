---
title: "Menu Cell (Actions Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm690
 
localization_priority: Normal
ms.assetid: 29af746c-b081-24cf-a30d-a56353ee849e
description: "Defines the name of a menu item that appears on a shortcut or action tag menu for a shape or page."
---

# Menu Cell (Actions Section)

Defines the name of a menu item that appears on a shortcut or action tag menu for a shape or page. 
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
## Remarks

To insert a separator into the menu above this item, use the BeginGroup cell. To display the command at the bottom of the menu, prefix the name with a percent character (%) .
  
To get a reference to the Menu cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Actions. *name*  .Menuwhere Actions.  *name*  is the name of the Actions row  <br/> |
   
To get a reference to the Menu cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionAction** <br/> |
|Row index:  <br/> |**visRowAction** +  *i*  where i = 0, 1, 2, ...  <br/> |
|Cell index:  <br/> |**visActionMenu** <br/> |
   

