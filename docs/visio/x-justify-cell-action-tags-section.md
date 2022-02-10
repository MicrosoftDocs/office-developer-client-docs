---
title: "X Justify Cell (Action Tags Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1026936
 
ms.localizationpriority: medium
ms.assetid: a8995020-3eaa-2b2c-eca0-dd475de4d06f

description: "The x -offset of the action tag button relative to the point defined by the X and Y cells."
---

# X Justify Cell (Action Tags Section)

The *x*  -offset of the action tag button relative to the point defined by the X and Y cells. 
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Left justified (the default). |**visSmartTagXJustifyLeft** <br/> |
| 1  <br/> | Centered. |**visSmartTagXJustifyCenter** <br/> |
| 2  <br/> | Right justified. |**visSmartTagXJustifyRight** <br/> |
   
## Remarks

The X Justify and Y Justify cells determine where the action tag button is placed in relation to the point defined in the X and Y cells. 
  
To get a reference to the X Justify cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | SmartTags.  *name*  .XJustify           where SmartTags. *name*  is the name of the action tag row  <br/> |
   
To get a reference to the X Justify cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionSmartTag** <br/> |
| Row index:  <br/> |**visRowSmartTag** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visSmartTagXJustify** <br/> |
   

