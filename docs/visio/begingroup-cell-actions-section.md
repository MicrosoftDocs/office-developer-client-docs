---
title: "BeginGroup Cell (Actions Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60022
 
localization_priority: Normal
ms.assetid: 1ae7f629-fb9f-1a11-1194-b381d6c9de5b

description: "Indicates whether a separator is inserted into the menu above this action."
---

# BeginGroup Cell (Actions Section)

Indicates whether a separator is inserted into the menu above this action. 
  
> [!NOTE]
> 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |A separator is inserted into the menu above this action.  <br/> |
|FALSE  <br/> |A separator is not inserted into the menu above this action (the default).  <br/> |
   
## Remarks

To get a reference to the BeginGroup cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Actions.  *name*  .BeginGroup            where Actions.  *name*  is the name of the Actions row  <br/> |
   
To get a reference to the BeginGroup cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionAction** <br/> |
|Row index:  <br/> |**visRowAction** +  *i*           where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visActionBeginGroup** <br/> |
   

