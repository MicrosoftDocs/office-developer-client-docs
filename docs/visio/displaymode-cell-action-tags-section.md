---
title: "DisplayMode Cell (Action Tags Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60039
 
localization_priority: Normal
ms.assetid: 0dfad40b-f97e-0c4a-2102-7344d1317b82

description: "Determines whether the action tag appears when the user moves the pointer over the tag, when the shape is selected, or all the time."
---

# DisplayMode Cell (Action Tags Section)

Determines whether the action tag appears when the user moves the pointer over the tag, when the shape is selected, or all the time.
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
|**Value**|**Display Mode**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Appears when the mouse is paused over the tag (the default).  <br/> |**visSmartTagDispModeMouseOver** <br/> |
| 1  <br/> | Appears while the shape is selected.  <br/> |**visSmartTagDispModeShapeSelected** <br/> |
| 2  <br/> | Appears all the time.  <br/> |**visSmartTagDispModeAlways** <br/> |
   
## Remarks

Action tags do not appear on printed or published output. 
  
If an action tag is defined for a page, and this cell contains a value of 1, the tag never appears because a page cannot be selected. 
  
To get a reference to the DisplayMode cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | SmartTags.  *name*  .DisplayMode           where SmartTags. *name*  is the name of the action tag row  <br/> |
   
To get a reference to the DisplayMode cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionSmartTag** <br/> |
| Row index:  <br/> |**visRowSmartTag** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visSmartTagDisplayMode** <br/> |
   

