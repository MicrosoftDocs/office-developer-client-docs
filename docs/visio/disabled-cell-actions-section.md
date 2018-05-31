---
title: "Disabled Cell (Actions Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251337
 
localization_priority: Normal
ms.assetid: ebf66729-d794-a398-268a-84d761bf06b6

description: "Indicates whether an item on a shortcut or action tag menu is disabled."
---

# Disabled Cell (Actions Section)

Indicates whether an item on a shortcut or action tag menu is disabled.
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Disable (dim) command name.  <br/> |
|FALSE  <br/> |Enable the command name (the default).  <br/> |
   
## Remarks

To get a reference to the Disabled cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Actions. *name*  .Disabled           where Actions. *name*  is the name of the Actions row  <br/> |
   
To get a reference to the Disabled cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionAction** <br/> |
|Row index:  <br/> |**visRowAction** +  *i*           where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visActionDisabled** <br/> |
   

