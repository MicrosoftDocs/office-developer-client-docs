---
title: "Invisible Cell (Actions Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60046
 
ms.localizationpriority: medium
ms.assetid: 070b4468-c907-b201-1633-1d3e10ecc2b2
description: "Indicates whether the action is visible on the action tag or shortcut menu."
---

# Invisible Cell (Actions Section)

Indicates whether the action is visible on the action tag or shortcut menu. 
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |The action is not visible on the menu. |
|FALSE  <br/> |The action is visible on the menu (the default). |
   
## Remarks

To get a reference to the Invisible cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Actions. *name*  .Invisiblewhere Actions.  *name*  is the name of the Actions row  <br/> |
   
To get a reference to the Invisible cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionAction** <br/> |
|**Row index:**  <br/> |**visRowAction** +  *i*  where  *i*  = 0, 1, 2... |
|**Cell index:**  <br/> |**visActionInvisible** <br/> |
   

