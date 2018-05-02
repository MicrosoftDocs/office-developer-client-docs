---
title: "Disabled Cell (Action Tags Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60038
 
localization_priority: Normal
ms.assetid: bf0a80c9-0fdb-e2cf-3ab0-74cb6338fdce

description: "Indicates whether the action tag appears in the drawing window."
---

# Disabled Cell (Action Tags Section)

Indicates whether the action tag appears in the drawing window.
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | The action tag is disabled.  <br/> |
| FALSE  <br/> | The action tag is enabled (the default).  <br/> |
   
## Remarks

When an action tag is disabled, it does not appear at all until it is re-enabled. 
  
To get a reference to the Disabled cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | SmartTags.  *name*  .Disabled           where SmartTags. *name*  is the name of the action tag row  <br/> |
   
To get a reference to the Disabled cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionSmartTag** <br/> |
| Row index:  <br/> |**visRowSmartTag** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visSmartTagDisabled** <br/> |
   

